# Installing JSON for PHP verions < 5.2 #
ViciClient makes use of the PHP functions json\_encode() and json\_decode(), which until version 5.2 were not included in the core distribution. If your version of PHP is lower than 5.2, you need to install the PECL package JSON by issuing the following command:
```
pecl install json
```
This is dependent on having [PEAR](http://pear.php.net/), the PHP package repository, installed on your system. After installing the package, make sure the line
```
extension=json.so
```
appears in your php.ini file or in one of the included ini files in the php.d directory.

# Installing the PHP-Java bridge for JasperReports #

Download the [PHP-Java Bridge](http://surfnet.dl.sourceforge.net/sourceforge/php-java-bridge/php-java-bridge_5.2.2.1_j2ee.zip). Create a directory for the package, we'll use `/var/java`.

`/usr/bin/java -jar /var/java/JavaBridge.jar SERVLET:8080 5 /var/java/JavaBridge.log &`

Append this to `php.ini` or put it in a new file, `php.d/java.ini`

```
extension = java.so

[java]
java.hosts     = 127.0.0.1:8080
java.servlet   = On
java.log_level  = 3
```

# Checking out the codebase #

svn co http://

# Configuring ViciClient #

## app/config/core.php ##
```
Configure::write('Security.salt', 'DYhGaab0qyJfIxfs2guVoUubWwvniR2G0FgaC9mi');
```

```
Cache::config('default', array(
 		'engine' => 'Xcache', //[required]
 		'duration'=> 3600, //[optional]
 		'probability'=> 100, //[optional]
 		'user' => 'user', //user from xcache.admin.user settings
       'password' => 'password', //plaintext password (xcache.admin.pass)
 	));
```

## app/config/database.php ##
This file contains the definition for the DB connection that ViciClient will use. Change any necessary details here.
```
	var $default = array(
		'driver' => 'mysql',
		'persistent' => true,
		'host' => 'localhost',
		'login' => 'cron',
		'password' => '1234',
		'database' => 'asterisk',
		'prefix' => '',
	);
```


# Modifications to MySQL Database #