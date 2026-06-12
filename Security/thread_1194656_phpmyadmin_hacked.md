---
title: "phpmyadmin hacked"
date: 2009-06-22
forum: Security
---

### Post by maddentim on 2009-06-22
I made a bad mistake with the apache configuration for a phpmyadmin on a server of mine and i was attacked by this sql injection attack: [http://www.hackerscenter.com/index.php?/Feeds/Exploits/phpMyAdmin-PHP-Code-Injection-RCE.html](http://www.hackerscenter.com/index.php?/Feeds/Exploits/phpMyAdmin-PHP-Code-Injection-RCE.html)

So somebody hacked my phpmyadmin install recently and now I am trying to decide what needs to be done to clean it up.  The server does not host valuable websites itself but does contain valuable data and code.  Once I realized I had been hacked, I took phpmyadmin out of apache and then did a complete purge of the package and all its configuration files.  Then I reinstalled it.  phpmyadmin seems to be fixed (including the bonehead error on the apache2 config), but I am concerned what else an attacker might have does while it was hacked.  It was several days before I realized the trouble.

If it was just a vandalism thing and purging/reinstalling phpmyadmin fixes it, then I'll let it go.  But I don't know enough to say that.

---

### Post by philcamlin on 2009-06-23
id be fins with it then 

how do you know your hacked? i have php admin installed...

---

### Post by maddentim on 2009-06-24
The first sign I had was that I could not log into phpmyadmin.  It said something about an invalid host.  in digging around about the error, I found about about the attack and they changes made.  Basically, the file config.inc.php in /var/lib/phpmyadmin was changed to something else (an normal install has an empty file there.  the one ubuntu uses is somewhere else)  Where the hostname for phpmyadmin is specified is had phpinfo() inserted.  You are probably safe.  I had my apache configured incorrectly such that certain phpmyadmin directories where not protected as they should have been.

---

### Post by WitchCraft on 2009-06-25
> **maddentim said:**
> I made a bad mistake with the apache configuration for a phpmyadmin on a server of mine and i was attacked by this sql injection attack: 

LoL, check the logfiles, find the IP, find the ISP, find the tech/legal contact mail-address, write an E-Mail asking them to stop servicing that hacker / issue him a warning. 

Don't ask for his address, they have to abide data privacy protection laws and taking the necessary legal action is too expensive anyway. Besides, it might just be a stupid kid who doesn't know what he/she is doing.

---

