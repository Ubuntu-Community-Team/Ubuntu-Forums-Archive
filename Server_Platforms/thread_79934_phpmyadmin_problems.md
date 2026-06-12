---
title: "phpmyadmin problems"
date: 2005-10-21
forum: Server Platforms
---

### Post by munkt0n on 2005-10-21
I've installed apache2,php4,mysql & phpmyadmin.

php is working fine (made phpinfo.php, checks out fine)
I can see phpmyadmin in the web root, but if try to access it the browser tries to download the file instead of running it.

I tried to re-install phpmyadmin, and get the following error when trying sudo apt-get remove phpmyadmin

```
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 11.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 77249 files and directories currently installed.)
Removing phpmyadmin ...
/var/lib/dpkg/info/phpmyadmin.prerm: line 12: db_get: command not found
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

what's wrong? it's bad enough being forced to use apache 2 to get php to work. I think I may go back to hoary, at least things worked properly.

[update] 
manually downloaded & installed phpmyadmin, working fine now.
conclusion : phpmyadmin package is broken.

---

### Post by Surfoo on 2005-10-26
Hi,

I had the same problem and i found the solution :

Edit /var/lib/dpkg/info/phpmyadmin.prerm and before the comment "# Package maintainer's commands follow:", add this line :

. /usr/share/debconf/confmodule

without forget the point.
Save, and after apt-get remove phpmyadmin :)

---

### Post by moe458 on 2005-11-03
[QUOTE=Surfoo]Hi,

I had the same problem and i found the solution :

Edit /var/lib/dpkg/info/phpmyadmin.prerm and before the comment "# Package maintainer's commands follow:", add this line :

. /usr/share/debconf/confmodule

without forget the point.
Save, and after apt-get remove phpmyadmin :)[/QUOTE]

i had the same problem..it worked like a charm :) Thanks :D

---

### Post by iluminate on 2005-11-06
Great!
Had the same problem and almost went nuts!
How on earth should ordinary rookies like I know to add -
. /usr/share/debconf/confmodule to be able to uninstall phpmyadmin???
Well well...
It's working now :)
Many thanks!

---

### Post by mjkelly on 2005-11-08
I have the same problem and it wont work. Heres my output after editing that tho.

homeslice@shendo:/usr/share/doc/vxretail$ sudo apt-get remove phpmyadmin
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 11.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 82837 files and directories currently installed.)
Removing phpmyadmin ...
**/var/lib/dpkg/info/phpmyadmin.prerm: line 10: /usr/share/debconf/confmodule: Permission denied**
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
homeslice@shendo:/usr/share/doc/vxretail$

Thats the problem, then take a look at this:

homeslice@shendo:/usr/share/doc/vxretail$ sudo sh /usr/share/debconf/confmodule
Can't exec "/usr/share/debconf/confmodule": Permission denied at /usr/share/perl/5.8/IPC/Open3.pm l ine 168.
open2: exec of /usr/share/debconf/confmodule failed at /usr/share/perl5/Debconf/ConfModule.pm line 44
homeslice@shendo:/usr/share/doc/vxretail$ 

Now what?

---

### Post by zelmak on 2005-11-11
[QUOTE=mjkelly]I have the same problem and it wont work. Heres my output after editing that tho.

homeslice@shendo:/usr/share/doc/vxretail$ sudo apt-get remove phpmyadmin
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 11.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 82837 files and directories currently installed.)
Removing phpmyadmin ...
**/var/lib/dpkg/info/phpmyadmin.prerm: line 10: /usr/share/debconf/confmodule: Permission denied**
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
homeslice@shendo:/usr/share/doc/vxretail$

Thats the problem, then take a look at this:

homeslice@shendo:/usr/share/doc/vxretail$ sudo sh /usr/share/debconf/confmodule
Can't exec "/usr/share/debconf/confmodule": Permission denied at /usr/share/perl/5.8/IPC/Open3.pm l ine 168.
open2: exec of /usr/share/debconf/confmodule failed at /usr/share/perl5/Debconf/ConfModule.pm line 44
homeslice@shendo:/usr/share/doc/vxretail$ 

Now what?[/QUOTE]

/usr/share/debconf/confmodule is meant to be 'sourced' not executed directly as it contains a library of functions to manage the debian stuffs. in your /var/lib/dpkg/info/phpmyadmin.prerm file, it should have a period (.) followed by a space and then the path to confmodule.

thus:
```
. /usr/share/debconf/confmodule
```

will pass this on to the bug trackers if it hasn't already...

---

### Post by MasJ on 2006-01-07
Thanks a lot surfoo. PhpMyAdmin was becoming a pain in the ass as a broken package. With your info I managed to remove it : ).

---

### Post by phoenixleo on 2006-01-11
I knew I could count on Ubuntu Forums to have a solution for me.
Thanks a bunch! :D

---

### Post by nuttyrave on 2006-02-01
This was quite useful. Thx.

---

### Post by FreeZey on 2006-05-02
THANK YOU SO MUCH!!! haha i was about to kick this dam computer on the floor....  that dam error was so annoying NEVER AGAIN will i install this dam package....

---

### Post by normanp on 2008-01-17
I had a similar problem with Ubuntu Server 7.10.
I tried to install phpmyadmin & it failed. Then tried to install quota but this failed as apt-get tried to remove phpmyadmin first and gave up - so didn't install quota! Then tried to uninstall phpmyadmin - failed. 
(messages similar to above posts).
In desparation I edited /var/lib/dpkg/info/phpmyadmin.postrm and emptied it apart from these lines:
#!/bin/sh
exit 0

Then the following worked: dpkg -r phpmyadmin
Followed by: dpkg --purge phpmyadmin

Than apt-get quota worked with no mention of phpmyadmin!

I would conclude that there is a fault in the phpmyadmin.postrm script somewhere (the dot was correctly in place as in the above post though - so what is it?)

As a newb I cannot (yet) understand these scripts properly - so I guess that I have left traces of phpmyadmin on the system somewhere - does this matter?

---

