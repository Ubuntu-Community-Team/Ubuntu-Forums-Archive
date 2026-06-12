---
title: "someone help, please!!"
date: 2008-01-28
forum: Server Platforms
---

### Post by elijahbenraam on 2008-01-28
OK, I've just spent a whole day trying to install apache, php and mysql on 7.10

I've had everything working on 7.04 and didn't think I'd have any problems.

Basically I just cannot get apache2 to show php files. It keeps downloading them. I've read everything I could find on this forum and blogs and tried it all. 

Apache is working. After I install php5, libapache2-mod-php5 and restart apache it keeps downloading the test file. 

Is this a bug in 7.10? But for some people it seems to be working so it must be my setup. Can someone help me to pinpoint the problem? May be some commands I need to run to check things? I'm lost at this point and don't know what to try next.

Please...

---

### Post by cdenley on 2008-01-28
Is the php module enabled? Post the output for this command. The output I posted is what it should be.

```

cdenley@www:~$ ls -l /etc/apache2/mods-enabled/php*
lrwxrwxrwx 1 root root 27 2007-05-31 12:15 /etc/apache2/mods-enabled/php5.conf -> ../mods-available/php5.conf
lrwxrwxrwx 1 root root 27 2007-05-31 12:15 /etc/apache2/mods-enabled/php5.load -> ../mods-available/php5.load

```

---

### Post by elijahbenraam on 2008-01-29
sorry, for taking so long. it was night time over here

here is the output
> 
ilya@ilya-desktop:~$ ls -l /etc/apache2/mods-enabled/php*
ls: /etc/apache2/mods-enabled/php*: No such file or directory

There is nothing in mods-enabled related to php, but there are two files in mods-available: php5.conf and php5.load 
I've created links to them in mods-enabled and restarted apache but still nothing - it just tries to download it.

[SOLVED]
Ok, I've checked everything again and deleted all the lines of manual adding php modules I've made to httpd.conf yesterday and it worked.

But the question is - why were no links added to mods-enabled automatically when I installed php through synaptic?

---

### Post by MJN on 2008-01-29
> **elijahbenraam said:**
> But the question is - why were no links added to mods-enabled automatically when I installed php through synaptic?
 
The modules need enabling independently to installing them - this is the same case as those modules that ship by default in that they aren't all enabled. Perhaps the installation script should advise that this is the case (if it doesn't already).
 
Incidentally, to enable/disable Apache modules use a2enmod/a2dismod.
 
Mathew

---

