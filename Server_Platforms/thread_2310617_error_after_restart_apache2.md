---
title: "error after restart apache2"
date: 2016-01-20
forum: Server Platforms
---

### Post by niki85 on 2016-01-20
[COLOR=#111111][FONT=Ubuntu]I use ubuntu 14.04,[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I remove phpmyadmin and then install again phpmyadmin[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]in etc/apache2/apache2.conf i add next:

[HTML]Include /etc/phpmyadmin/apache.conf[/HTML]

and when i try restart apache with next command:

[/FONT][/COLOR]
[HTML]sudo service apache2 restart[/HTML]

[COLOR=#111111][FONT=Ubuntu]I get this error:[/FONT][/COLOR]
[HTML]# sudo service apache2 restart* Restarting web server apache2   [Wed Jan 20 23:32:22.925567 2016] [alias:warn] [pid 29418] AH00671: The Alias directive in /etc/apache2/conf.d                                                                                                                                                      /phpmyadmin.conf at line 3 will probably never match because it overlaps an earlier Alias.[ OK ][/HTML]

anyone help please ?

---

### Post by MAFoElffen on 2016-01-21
@Mods- this should be moved to the Server Section for better exposure. The OP's other thread ([http://ubuntuforums.org/showthread.php?t=2310607](http://ubuntuforums.org/showthread.php?t=2310607)) should be merged into this thread, Duplicate (round about same issue with same server.) This answer should solve both threads.

See the [Ubuntu phpMyAdmin Documentation Page]("https://help.ubuntu.com/community/phpMyAdmin"). 

Specifically, after 13.10, there was a change in how that works. Now is a symlink that points to that file, so you just added a duplicate path to the same. You should not need that "include" line anymore. What the error is telling you, is that it is there twice...

Comment it out, save, and restart the service. 

Tell me what it does then.

---

### Post by deadflowr on 2016-01-21
Moved to **Server Platforms**

---

