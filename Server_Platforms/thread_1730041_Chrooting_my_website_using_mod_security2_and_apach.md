---
title: "Chrooting my website using mod_security2 and apache2?"
date: 2011-04-15
forum: Server Platforms
---

### Post by korgoth28 on 2011-04-15
My website works fine until I try to chroot it. I added the following line to 
apache2.conf, in the mod_security part: 

```
SecChrootDir /var/www  

```Then I change the line in sites-enabled/000-default from: 

```
DocumentRoot /var/www
```to: 
```
DocumentRoot / 
```Now, when I try to access var/www/index.html through iceweasal I get "access denied". Where am I going wrong? Thanks in advance!

---

### Post by espressobeanie on 2011-04-15
Can you access it without the chroot line?

---

### Post by korgoth28 on 2011-04-15
Yes, but only after changing DocumentRoot back to /var/www as well. I also have to run fuser -k -n tcp 80 after changing everything back to get it to work again.

---

### Post by HermanAB on 2011-04-15
Howdy,

Chroot is not considered to be particularly useful anymore.  Rather use App Armor.

---

### Post by korgoth28 on 2011-04-15
Thanks for the advice! However, I'm going to be setting up both Ubuntu and Debian servers. This page:
[http://wiki.apparmor.net/index.php/Distro_debian#Tools](http://wiki.apparmor.net/index.php/Distro_debian#Tools)
Makes it sound like it would be difficult to use app armor with Debian.

I know this is an Ubuntu forum, but is there a third option that would work with Debian or should I keep trying to chroot?

---

### Post by usatonycuba on 2011-04-15
```

 /etc/init.d/apparmor stop 
 update-rc.d -f apparmor remove 
 aptitude remove apparmor apparmor-utils

```
That is what always do in a Debian Based server.. in this case.. Ubuntu server have more "easy" and "less" conflicts with it... since apparmor created more problems that it will be solve

[QUOTE=Falko]
From  [perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2]("http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2") by falko

...AppArmor is a security extension (similar to SELinux) that should provide extended security. In my opinion you don't need it to configure a secure system, and it usually causes more problems than advantages (think of it after you have done a week of trouble-shooting because some service wasn't working as expected, and then you find out that everything was ok, only AppArmor was causing the problem). 

[/QUOTE]

---

### Post by usatonycuba on 2011-04-15
> **hermanab said:**
> howdy,

chroot is not considered to be particularly useful anymore...
+1

---

### Post by duesentriebchen on 2012-10-22
Dear professionals :)

Please excuse my silly question in advance, im  just a neewby running a 12.04.1 server installed from scratch with apache2 v2.2.22 trying to get an idea of the last post...

I've got vsftpd, exim4 and imapdssl running on the box.
I also do have lamp running, ports closed by IPtables.
I want to create a website, myfirstwebsite :D, running securely on the box -> meaning not to get any too big trouble from hacking or sqlinjections.

Therefore i spend the last months reading howto's and tutorials for chrooting apache2.

If i got the last post right, running apache2 in a chroot jail is outdated?!
Due to this fact, i cannot find the libapache2-mod-chroot module in the repositories.

I did find the libapache2-modsecurity module.
Is this module an instance of "chrooting" apache2?

Thanks in advance!!!
Kind regards,
duesentriebchen :D

---

