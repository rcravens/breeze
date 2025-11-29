This is a Laravel Breeze fork that supports Laravel Fortify. 

Video: [Fortify + Breeze Package](https://tekcasts.com/play/pragmatic-laravel-new-fortify-breeze-package)

The reason this exists is for users with existing Laravel application that chose not to install a starter package initially but now want to add authentication. 
Laravel Fortify will provide you with all the back-end routes / controllers / middleware, but does not provide views. 
Laravel Breeze provides both views (front-end) and controllers (back-end), but is not actively maintained.
I felt like the "safe" way is to wire up the Laravel Breeze views to use the Laravel Fortify back-end. That is what this package provides.

Note: The [pull request](https://github.com/laravel/breeze/pull/476) for these changes was denied in the Laravel Breeze package. 

This package does the following:
1. Installs and configures Laravel Fortify.
2. Installs TailwindCSS v4.
3. Installs Laravel Breeze views.

When you are done, you will have the following routes:

| Method         | URL          | Name                   | Handler |
|:---------------|:-------------|:-----------------------|:--------|
| GET            | /register    | register               | Fortify |
| POST | /register | register               | Fortify |
| GET | /login | login                  | Fortify |
| POST | /login | login.store            | Fortify |
| GET | /forgot-password | password.request       | Fortify |
| POST | /forgot-password | password.email         | Fortify |
| GET | /reset-password | password.reset         | Fortify |
| POST | /reset-password | password.update        | Fortify |
| GET | /email/verify | verification.notice    | Fortify |
| POST | /email/verification-notification | verification.send      | Fortify |
| GET | /email/verify/{id}/{hash} | verification.verify    | Fortify |
| GET | /user/confirm-password | password.confirm       | Fortify |
| POST | /user/confirm-password | password.confirm.store | Fortify |
| GET (json) | /user/confirmed-password-status | password.confirmation | Fortify |
 | GET | /profile | profile.edit | ProfileController |
|PUT | /user/profile-information | user-profile-information.update | Fortify |
|PUT|/user/password | user-password.update | Fortify |
|DELETE | /profile | profile.destroy | ProfileController |


### Laravel Installation
If you are starting from "scratch", I recomment you use one of the official Laravel Starter Kits.

If you want to test out this package:

`laravel new example`

Choose the following options:
- Starter Kit = none
- Testing framework = Pest
- Database = SQLite
- Run npm install / build = Yes


### Package Installation

Note: This package will install Laravel Fortify if it is not already installed.

From inside your project directory:

`composer require rcravens/breeze`

`php artisan breeze:install`

Choose the following options:
- Breeze stack: Laravel Forge + Blade Views
- Dark mode: Yes (your choice though)
- Testing framework: Pest (match Laravel Installation)

That's it. You now have Laravel Breeze front-end backed by Laravel Fortify back-end.
