---
title: "after apt-get Wordpress:  &quot;config file for specified host not under an allowed path&quot;"
date: 2009-12-23
forum: Server Platforms
---

### Post by BioGeek on 2009-12-23
Hi, I have an headless server where I installed wordpress via apt-get. Then I followed the installation instructions from this tutorial: [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

```
$ sudo apt-get install wordpress

# The installation places the files in the /usr/share/wordpress 
# folder. Make a symbolic link to the Apache2 www folder, so that 
# Apache2 knows where to find the installation folder.
sudo ln -s /usr/share/wordpress /var/www/wordpress 

# Install WordPress using the supplied script
sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress localhost

# Restart Apache2
sudo /etc/init.d/apache2 restart

```

If I then browse to [http://myserver/wordpress](http://myserver/wordpress), instead of getting this screen:
[IMG]https://help.ubuntu.com/community/WordPress?action=AttachFile&do=get&target=wordpress1.jpg[/IMG]
I get a screen telling me:
```
The config file for the specified host is not under an allowed path
```

The wp-config.php file is not the standard on, but this Debianised version:
```
<?php
/** WordPress's Debianised default master config file
Please do NOT edit and read about how the configuration works in the README.Debian
**/

    #http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=435289
    #http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=440572 (underscores, not dashes)
    $debian_server = preg_replace('/:.*/', "", $_SERVER['HTTP_HOST']);
    $debian_file = '/etc/wordpress/config-'.strtolower($debian_server).'.php';

    $allowed_paths = array('/etc/wordpress');
    if (!in_array(dirname(realpath($debian_file)), $allowed_paths))
            die("The config file for the specified host is not under an allowed path");

    if (!file_exists($debian_file)) {
        header("HTTP/1.0 404 Not Found");
        echo "404 Not found";
        exit(1);
    }

    require_once($debian_file);

define('ABSPATH', '/usr/share/wordpress/');
define('WP_CORE_UPDATE', false);

require_once(ABSPATH.'wp-settings.php');
?>
```

/usr/share/doc/wordpress/README.Debian tells about quick setup, multiple blogs and upgrading, but nothing about how to prevent this error message.

It is the line ```
if (!in_array(dirname(realpath($debian_file)), $allowed_paths))
``` which triggers the error message, so I guess it is some permission problem somewhere.

Any guidance on how to solve this would be appreciated.

PS: I first went to the Wordpress forums with this question, but there they say they don't support this "[highly customized versions of WordPress]("http://wordpress.org/support/topic/333894?replies=5#post-1324884")".

---

### Post by Queue29 on 2009-12-23
Have you tried raising the permissions on the config file? If you 777 it and it works, remember to re-lower the permissions as low as you can go with it still working.

Anyway, If I were you, I'd either go with the Turnkey Wordpress module, or install wordpress using WP's instructions: avoiding the version in apt altogether. The ubuntu package maintainers have been dropping the ball on it for the past 3 versions or so. This isn't the last bug you'll encounter for using the ubuntu maintained version.

---

