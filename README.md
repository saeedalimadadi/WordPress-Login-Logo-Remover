# WordPress Login Logo Remover

This snippet helps you **remove the WordPress logo** from the login page. By default, the WordPress logo appears above the login form. Hiding this logo can be useful for branding purposes, creating a cleaner login experience, or if you prefer to replace it with your own custom logo.

## Why hide the WordPress logo?

* **Custom Branding:** If you have a custom login page design or want to brand the login area with your own company logo, removing the default WordPress logo is the first step.
* **Cleaner Look:** A minimalist login page can offer a more professional and less cluttered appearance.
* **Security by Obscurity (Minor):** While not a major security measure, it can subtly obscure the fact that the site is running WordPress from a casual observer on the login screen.

## Installation

You have two main ways to implement this code:

### Method 1: As a Standalone Plugin (Recommended)

Using a custom plugin is the most robust method, as it ensures your modification remains active regardless of theme changes.

1.  Create a new folder named `wp-login-logo-hide` in your WordPress site's `wp-content/plugins/` directory.
2.  Inside this new folder, create a file named `wp-login-logo-hide.php`.
3.  Copy and paste the following code into `wp-login-logo-hide.php`:

    ```php
    <?php
    /**
     * Plugin Name: WordPress Login Logo Remover
     * Description: Hides the default WordPress logo from the login screen.
     * Version: 1.0
     * Author: Your Name (Optional)
     */

    function remove_wordpress_logo_in_login() { ?>
        <style type="text/css">
            body.login div#login h1 a {
                background-image: none;
                background-size: 0 0;
                height: 0;
                margin: 0 auto 0;
                width: 0;
            }
        </style>
    <?php
    }
    add_action('login_enqueue_scripts', 'remove_wordpress_logo_in_login');
    ?>
    ```

4.  Go to your WordPress admin dashboard, navigate to **"Plugins"**, and **activate** the "WordPress Login Logo Remover" plugin.

### Method 2: Adding to your Theme's functions.php File

You can add this code directly to your active theme's `functions.php` file. **Before doing so, it's highly recommended to back up your `functions.php` file.**

1.  Navigate to `wp-content/themes/YourThemeName/` (replace `YourThemeName` with the actual name of your active theme).
2.  Open the `functions.php` file.
3.  Add the following code to the end of the file (before the closing `?>` tag, if one exists):

    ```php
    function remove_wordpress_logo_in_login() { ?>
        <style type="text/css">
            body.login div#login h1 a {
                background-image: none;
                background-size: 0 0;
                height: 0;
                margin: 0 auto 0;
                width: 0;
            }
        </style>
    <?php
    }
    add_action('login_enqueue_scripts', 'remove_wordpress_logo_in_login');
    ```

## Contributing

Your contributions are welcome! If you have suggestions or improvements for this code, feel free to open a "Pull Request" or report an "Issue."

## License

This project is licensed under the GPLv2 or later.
