# BrainSteps is an online learning platform for registering for courses with a choice of teachers, for teaching students and preparing for subjects


# Running an Existing WordPress Site Locally

This guide will help you run an existing WordPress site on your local machine.

## 1. Install a Local Server

To run WordPress locally, you need a web server (Apache/Nginx), PHP, and MySQL. Here are some programs you can use:

- **XAMPP** (Windows, macOS, Linux)
- **MAMP** (macOS, Windows)
- **Local by Flywheel** (specialized for WordPress, Windows, macOS)

### Installing XAMPP
1. Download [XAMPP](https://www.apachefriends.org/index.html) and install it.
2. Launch XAMPP and start the **Apache** and **MySQL** modules.

## 2. Export Data from the Server

### Export Site Files
1. Connect to the remote server via FTP (e.g., using FileZilla).
2. Download all WordPress files, including the `wp-content` folder, `wp-config.php` file, and any other files in the WordPress root directory.

### Export the Database
1. Open **phpMyAdmin** on the server (or use the tool provided by your hosting provider).
2. Find and select your site’s database.
3. Go to the **Export** tab and choose the "Quick" method.
4. Save the exported `.sql` file to your computer.

## 3. Import Data to the Local Server

### Move WordPress Files
1. Copy the WordPress files to the `htdocs` folder of your local server (e.g., XAMPP).
2. Name the folder, for example, `my_site`. Your site will now be available at `http://localhost/my_site`.

### Import the Database
1. Open **phpMyAdmin** on your local server (usually `http://localhost/phpmyadmin`).
2. Create a new database, for example, `my_site_db`.
3. Open the newly created database, go to the **Import** tab, and upload the `.sql` database file.

## 4. Configure the `wp-config.php` File
1. Open the `wp-config.php` file in a text editor.
2. Update the database connection settings:

    ```php
    define('DB_NAME', 'my_site_db'); // Local database name
    define('DB_USER', 'root');       // Database user (default is root)
    define('DB_PASSWORD', '');       // Database password (leave empty for XAMPP)
    define('DB_HOST', 'localhost');  // Local host
    ```

3. Save the file.

## 5. Update URLs in the Database

To update old domain links, do the following:

### Using phpMyAdmin
1. Open the database in phpMyAdmin.
2. Go to the `wp_options` table.
3. Update the `siteurl` and `home` values to `http://localhost/my_site`.

### Using a Plugin
Use a plugin like **Better Search Replace** to replace old URLs with the new one (`http://localhost/my_site`) throughout the database.

## 6. Test the Site

Open a browser and go to `http://localhost/my_site`. Your site should load correctly.

---

You’re now ready to develop and test your WordPress site locally!
