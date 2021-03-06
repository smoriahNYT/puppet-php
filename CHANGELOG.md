# Changelog

## 3.0.1
 * Fix typo in package suffix for php-fpm on RHEL in params.pp

## 3.0.0
 * Removes `$php::fpm::pool::error_log`. Use the `php_admin_flag` and
   `php_admin_value` parameters to set the php settings `log_errors` and
   `error_log` instead.
 * Removes support for PHP 5.3 on Debian-based systems. See the notes in the
   README for more information.
 * Removes the `php_version` fact which had only worked on the later puppet runs.
 * Moves CLI-package handling to `php::packages`
 * Allows changing the package prefix via `php::package_prefix`.
 * Moves FPM-package handling from `php::fpm::package` to `php::fpm`
 * Changes `php::packages`, so that `php::packages::packages` becomes
   `php::packages::names` and are installed and `php::packages::names_to_prefix`
   are installed prefixed by `php::package_prefix`.
 * PHPUnit is now installed as phar in the same way composer is installed,
   causing all parameters to change
 * The `php::extension` resource has a new parameter: `zend`. If set to true,
   exenstions that were installed with pecl are loaded with `zend_extension`.

## 2.0.4
 * Style fixes all over the place
 * Module dependencies are now bound to the current major version

## 2.0.3
 * Some issues & bugs with extensions were fixed
 * If you set the `provider` parameter of an extension to `"none"`, no
   extension packages will be installed
 * The EPEL yum repo has been added for RedHat systems

## 2.0.2
 * Adds support for `header_packages` on all extensions
 * Adds `install_options` to pear package provider

## 2.0.1
 * This is a pure bug fix release
   * Fix for CVE 2014-0185 (https://bugs.php.net/bug.php?id=67060)

## 2.0.0
 * Remove augeas and switch to puppetlabs/inifile for configs
   * Old: `settings => [‘set PHP/short_open_tag On‘]`
   * New: `settings => {‘PHP/short_open_tag’ => ‘On‘}`
 * Settings parmeter cleanups
   * The parameter `config` of `php::extension` resources is now called `settings`
   * The parameters `user` and `group` of `php::fpm` have been moved to `php::fpm::config`
   * New parameter `php::settings` for global settings (i.e. CLI & FPM)
 * New parameter `php::cli` to disable CLI if supported

## 1.1.2
 * SLES: PHP 5.5 will now be installed
 * Pecl extensions now autoload the .so based on $name instead of $title

## 1.1.1
 * some nasty bugs with the pecl php::extension provider were fixed
 * php::extension now has a new pecl_source parameter for specifying custom
   source channels for the pecl provider

## 1.1.0
 * add phpunit to main class
 * fix variable access for augeas

## 1.0.2
 * use correct suse apache service name
 * fix anchoring of augeas

## 1.0.1
 * fixes #9 undefined pool_base_dir

## 1.0.0
Initial release

