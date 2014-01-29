## WP PHP 5.3+

Stub for WordPress themes/plugins that require PHP v5.3+.

### Example Usage in a Typical WordPress Theme/Plugin File

```
<?php
/*
	Plugin Name: My Plugin
	Plugin URI: http://example.com/my-plugin
	Description: Example plugin.
	Author: Example Author.
	Version: 0.1-alpha
	Author URI: http://example.com
	Text Domain: my-plugin
*/
if(require(dirname(__FILE__).'/wp-php53.php')) // TRUE if running PHP v5.3+.
	require dirname(__FILE__).'/my-plugin-code.php'; // OK to load your plugin.
else wp_php53_notice(); // Creates a PHP v5.3+ Dashboard notice for the site owner.
```

---

### Understanding `if(require('wp-php53.php'))`

The `wp-php53.php` file will automatically return `TRUE` upon being included in your scripts, IF (and only if) the installation site is running PHP v5.3+. Otherwise it returns `FALSE`. Therefore, the simplest way to run your check, is to use `if(require('wp-php53.php'))`. **However**, you could also choose to do it this way.

```
<?php
require dirname(__FILE__).'/wp-php53.php';

if(wp_php53())
	require dirname(__FILE__).'/my-plugin-code.php';
else wp_php53_notice();
```

---

### Dashboard Notice that Calls your Software by Name

```
<?php
if(require(dirname(__FILE__).'/wp-php53.php')) // TRUE if running PHP v5.3+.
	require dirname(__FILE__).'/my-plugin-code.php'; // OK to load your plugin.
else wp_php53_notice('My Plugin'); // Dashboard notice mentions your software specifically.
```

---

### Using a Custom Dashboard Notice

```
<?php
if(require(dirname(__FILE__).'/wp-php53.php')) // TRUE if running PHP v5.3+.
	require dirname(__FILE__).'/my-plugin-code.php'; // OK to load your plugin.
else wp_php53_custom_notice('My Plugin requires PHP v5.3+'); // Custom Dashboard notice.
```

---

### What if Multiple Themes/Plugins Use `wp_php53()` Functions?

This is fine. The `wp-php53.php` file uses `function_exists()` as a wrapper; which allows it to be included any number of times, and by any number of plugins; and also from any number of locations. No worries :-)