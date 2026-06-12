---
title: "After some PHP fatal errors, php do not working, but html is still working."
date: 2011-03-07
forum: Server Platforms
---

### Post by MoonSilver on 2011-03-07
Hello to all!
I have very interesting problem after ~10 PHP Fatal error, php 5(latest one) in apache2(latest one) in Ubuntu Server 10.10(with latest updates) just do not work. So if try any php page it's not working(user see white page), but HTML still work fine.

What that can be? So only restart apache is help to back php. (we are running Wordpress blog 3.1)

Any suggestions?

Log, usually after this one it's crashing. And no message that it's crash.

```


[Sun Mar 06 21:20:02 2011] [error] [client 94.41.223.87] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203, referer: 
[Sun Mar 06 21:20:15 2011] [error] [client 94.41.223.87] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203, referer: 
[Sun Mar 06 21:20:36 2011] [error] [client 83.149.9.173] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203
[Sun Mar 06 21:21:02 2011] [error] [client 88.201.230.98] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203
[Sun Mar 06 21:22:07 2011] [error] [client 66.249.82.66] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203
[Sun Mar 06 21:23:45 2011] [error] [client 178.217.24.18] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203
[Sun Mar 06 21:24:08 2011] [error] [client 95.37.44.1] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203, referer: 2011/03/05/dolgozhdannyiy-notion-ink-adam-predvzyatyiy-obzor/
[Sun Mar 06 21:25:02 2011] [error] [client 94.180.185.106] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203
[Sun Mar 06 21:25:22 2011] [error] [client 94.180.185.106] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203
[Sun Mar 06 21:25:25 2011] [error] [client 95.108.129.207] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203
[Sun Mar 06 21:25:34 2011] [error] [client 94.180.185.106] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203
[Sun Mar 06 21:27:11 2011] [error] [client 95.37.44.1] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203
[Sun Mar 06 21:28:43 2011] [error] [client 78.108.79.137] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203
[Sun Mar 06 21:28:49 2011] [error] [client 78.108.79.137] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/nextgen-gallery/lib/post-thumbnail.php on line 203
[Sun Mar 06 21:28:49 2011] [error] [client 78.108.79.137] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/private-messages-for-wordpress/pm4wp.php on line 501
[Sun Mar 06 21:28:50 2011] [error] [client 78.108.79.137] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/private-messages-for-wordpress/pm4wp.php on line 501
[Sun Mar 06 21:28:50 2011] [error] [client 78.108.79.137] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/private-messages-for-wordpress/pm4wp.php on line 501
[Sun Mar 06 21:28:51 2011] [error] [client 78.108.79.137] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/private-messages-for-wordpress/pm4wp.php on line 501
[Sun Mar 06 21:28:51 2011] [error] [client 78.108.79.137] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/private-messages-for-wordpress/pm4wp.php on line 501
[Sun Mar 06 21:28:51 2011] [error] [client 78.108.79.137] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/private-messages-for-wordpress/pm4wp.php on line 501
[Sun Mar 06 21:28:52 2011] [error] [client 78.108.79.137] PHP Fatal error:  Only variables can be passed by reference in /wp-content/plugins/private-messages-for-wordpress/pm4wp.php on line 501
[Sun Mar 06 21:28:52 2011] [error] [client 78.108.79.137] PHP Fatal error:  Cannot call overloaded function for non-object in /wp-includes/class-wp.php on line 442
[Sun Mar 06 21:28:52 2011] [error] [client 78.108.79.137] PHP Fatal error:  Cannot call overloaded function for non-object in /wp-includes/class-wp.php on line 442
[Sun Mar 06 21:31:32 2011] [error] [client 82.131.6.32] PHP Fatal error:  Cannot call overloaded function for non-object in /wp-includes/class-wp.php on line 442, referer: 
[Sun Mar 06 21:31:35 2011] [error] [client 82.131.6.32] PHP Fatal error:  Cannot call overloaded function for non-object in /wp-includes/class-wp.php on line 442, referer: 
[Sun Mar 06 21:31:35 2011] [error] [client 82.131.6.32] PHP Fatal error:  Cannot call overloaded function for non-object in /wp-includes/class-wp.php on line 442, referer: 
[Sun Mar 06 21:31:36 2011] [error] [client 82.131.6.32] PHP Fatal error:  Cannot call overloaded function for non-object in /wp-includes/class-wp.php on line 442, referer: 
[Sun Mar 06 21:31:37 2011] [error] [client 82.131.6.32] PHP Fatal error:  Cannot call overloaded function for non-object in /wp-includes/class-wp.php on line 442, referer: 


```Thank you!

---

### Post by SeijiSensei on 2011-03-07
Either some required files are not being loaded, or it's a WP problem.  Have you looked on the WordPress site to see if other WP users are having this problem?

---

### Post by MoonSilver on 2011-03-07
Hi, thank for your answer.

Yes, I checked WP forums, did not found anything. There are was problem that sometimes white page appear when upgrading blog, but in my case it's just happen randomly, maybe that because of some plugins, dont know. I will probably deactivated every plugins and try with that.

---

