---
title: "[SOLVED] Apache config, ignore sites-enabled"
date: 2008-10-09
forum: Server Platforms
---

### Post by batfastad on 2008-10-09
Hi everyone

I've been running our intranet database server on Apache2/PHP5/MySQL5 on Windows 2000 for a few years now.
But I've decided to move it over onto a new machine, which is also our NAS

I've set Apache/MySQL to be running on one of the onboard gigabit NICs, and Samba/Netatalk on the 2nd NIC
That's all working great.

I'm struggling with Apache slightly, it seems things have to be configured differently in Ubuntu.
What used to happen was there would be httpd.conf and I would just change that and re-start Apache. I always found it useful to keep backups of that 1 file.
However now there's apache2.conf, httpd.conf as well as individual ones for each enabled module and also some sort of sites-enabled/000-default

I've edited apache2.conf and commented out many of the instructions, and modified them into my httpd.conf
I noticed that apache2.conf just includes all the module confs and httpd.conf anyway
I already commented out the line to include ports.conf, and merged the listen commands into my httpd.conf

But my question is how virtual hosts are enabled/disabled. It seems there's some debian specific commands that can enable/disable vhosts

But instead can I just comment out all that and just specify my virtualhosts and default www <Directory> stuff in my httpd.conf?

Or do I need to use the debian apache commands for enabling/disabling vhosts/sites?

Thanks, B

---

### Post by Iowan on 2008-10-09
[link]("https://help.ubuntu.com/community/ApacheMySQLPHP") is almost a pre-req for me... you may have already seen it. In particular, this section answers your question - at least in part:> Now, we must deactivate the old site, and activate our new one. Ubuntu provides two small utilities that take care of this: a2ensite (apache2enable site) and a2dissite (apache2disable site).

---

### Post by lykwydchykyn on 2008-10-09
Basically, the way it works in Debian/Ubuntu is this:

 - apache2.conf is your master config file
 - in has in it include directives for:
   -- httpd.conf
   -- ports.conf
   -- everything in conf.d
   -- everything in sites-available
   -- everything in mods-available
 - When apache2 starts, it cats all this stuff into one big config file

So, you could just ignore all that and put whatever you want into apache2.conf.  But the idea is to organize these things a bit so that apache2.conf doesn't become an unmanageable mess, and so that you can use some nifty tools.

There is really no special magic to it, it's all just organization.  So to answer your question, yes you can just ignore all that and put things in apache2.conf (or httpd.conf, if you wish).  But if you take time to understand how it's laid out and how convenient it is, you might be sold on the convenience.  Then again, if it's a simple web server with one site, it's all kind of overkill.

---

### Post by batfastad on 2008-10-10
Yeah there will only be 2 different sites. A main root one, and also an SSL-enabled intranet database one.

I think the sites management is a bit overkill, but I do see the benefit if it was running many many sites/virtualhosts

I reckon I will chop everything that I edit into my httpd.conf then I can just back that up every so often

Cheers for the info and thanks for that link Iowan... must be the one LAMP guide I havn't read ;)

Thanks, B

---

