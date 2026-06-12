---
title: "Ubuntu 10.04 Vs Mod_Perl"
date: 2010-06-14
forum: Server Platforms
---

### Post by gineta on 2010-06-14
Hi I have 
**Apache/2.2.14 (Ubuntu) DAV/2 SVN/1.6.6 mod_fcgid/2.3.4 Phusion_Passenger/2.2.14 PHP/5.2.10-2ubuntu6 with Suhosin-Patch configured  In UBUNTU 10.04**

I like to install apache2 mod_perl
I make apt-get install libapache2-mod-perl2

and I get:
> libapache2-mod-perl2 is already the newest version.

Ok I try sudo a2enmod mod_perl
**ERROR: Module perl does not exist!**

Any Idea how I make Perl work in apache2 UBuntu 10.04

---

### Post by gineta on 2010-06-14
I solve
I uninstall perl and install again like that
> sudo apt-get install libapache-dbi-perl libapache2-mod-perl2 libapache2-reload-perl

---

### Post by Wiredfixer on 2010-09-27
How did you uninstall Perl? because when i try:

sudo apt-get remove perl

show me a lot of things to uninstall!!

I have the same problem but i reinstalled Perl and Nothing!

Well, let me try again and back.

---

### Post by gineta on 2010-09-27
I not remember now because this problem is in the test server. But if you use Ubuntu 10.04 and is not the 64 bits version you need to downgrade your apache2 and php version

---

