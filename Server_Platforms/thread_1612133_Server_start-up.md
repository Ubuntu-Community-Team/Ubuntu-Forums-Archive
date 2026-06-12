---
title: "Server start-up"
date: 2010-11-02
forum: Server Platforms
---

### Post by dshamson on 2010-11-02
Good Afternoon
 
I have installed Ubuntu Server on a spare machine.  The install seems to have completed and the system rebooted to the log-in.  I entered un and pw and the system goes the the cmd prompt.  
 
This is where I am stuck.  I can't find the command to load GUI.
 
During set-up I installed all apps except print server.
 
I have tried the cmd   sudo get-apt install ubuntu-desktop to no avail.
 
I have also tried GNOME.
 
What am I missing?
Thank You

---

### Post by lisati on 2010-11-02
By default, the server edition installation doesn't include a GUI. If you're more comfortable having one, there are options. This includes installing one with something like this from the command line and then rebooting:
```
sudo apt-get install ubuntu-desktop
```

edit: just noticed that you tried installing the desktop. Did you remember to reboot?

---

### Post by dshamson on 2010-11-02
Yes

---

### Post by chideock on 2010-11-02
the command is apt-get not get-apt as dshamson wrote.

if you want the gui why not load the desktop not the server?

---

### Post by CharlesA on 2010-11-02
[This]("https://help.ubuntu.com/community/ServerGUI") is a good read as well.

---

### Post by dshamson on 2010-11-03
A little background info might help.

I have been working with computers for about 20 yrs.  Have a part time repair business.  I understand servers and how they work.  I have attempted several times to setup my own server for my small business.  ie Windows small business server 2003, and Ubuntu.  Because of the time necessary to set-up and configure, I have never been able to complete a set-up.  Too many interruptions from other responsibilities.

I currently don't really have any more time than before, I just have an increased need.

I have successfully installed Ubuntu server.  Because of my lack of knowledge of command line setup I have chosen GNOME to load at startup.  Which it does.  However I am not able to see any of the server applications.  i.e. LAMP, Email, Apache, FTP etc.

How do I access these in GNOME?

---

### Post by CharlesA on 2010-11-03
There really isn't a way to configure them in Gnome. You mostly need to configure them manually.

Webmin works as a web frontend, but it's kinda "meh" and I don't use it anymore.

---

### Post by dshamson on 2010-11-03
If i could get the server to run from a client then I would un-install GNOME.  I know it can with WEBMIN its just the initial set-up that I'm hung on.

---

### Post by CharlesA on 2010-11-03
What do you mean?

I admin my server just by using SSH without any problems, but that's cuz I'm used to it. :)

I can forward graphical applications over SSH if I need to access something that has a GUI.

---

### Post by dshamson on 2010-11-03
Maybe my mine is working overtime and making this harder than it is.  I imagine a very daunting task of using command line to set-up email accounts, not to even consider building a web site.

how do I access the servers so that I can set-up EMail's, Users Access and web pages?

---

### Post by CharlesA on 2010-11-03
Check out [ispconfig]("http://www.ispconfig.org/") then.

I think you can do the same thing with webmin.

---

### Post by lisati on 2010-11-03
For email, my server's setup is based around [Postfix]("https://help.ubuntu.com/community/PostfixBasicSetupHowto"), with IMAP and POP3 enabled.

As part of my spam-prevention setup I have [spamassassin and clamav]("https://help.ubuntu.com/community/PostfixAmavisNew") together with a number of tweaks of Postfix's gleaned from assorted web pages.

I also have [Squirrelmail]("https://help.ubuntu.com/community/Squirrelmail") and [Roundcube]("https://help.ubuntu.com/community/Roundcube") installed for web access for when I'm using someone else's computer.

---

### Post by CharlesA on 2010-11-03
> **lisati said:**
> For email, my server's setup is based around [Postfix]("https://help.ubuntu.com/community/PostfixBasicSetupHowto"), with IMAP and POP3 enabled.

As part of my spam-prevention setup I have [spamassassin and clamav]("https://help.ubuntu.com/community/PostfixAmavisNew") together with a number of tweaks of Postfix's gleaned from assorted web pages.

I also have [Squirrelmail]("https://help.ubuntu.com/community/Squirrelmail") and [Roundcube]("https://help.ubuntu.com/community/Roundcube") installed for web access for when I'm using someone else's computer.

+1 for that.

I use exim for my server, but it's only relaying mail.

---

### Post by koenn on 2010-11-03
> **CharlesA said:**
> There really isn't a way to configure them in Gnome. You mostly need to configure them manually.

Webmin works as a web frontend, but it's kinda "meh" and I don't use it anymore.

... manually, as in: you edit text in configuration files.
it takes a bit of getting used to, but it's not all that hard

---

### Post by CharlesA on 2010-11-03
> **koenn said:**
> ... manually, as in: you edit text in configuration files.
it takes a bit of getting used to, but it's not all that hard

Yep. It probably helps that there are a ton of howtos about how to configure different services and whatnot. Apache, SSH, and Samba are the ones I know about but I am sure there are more out there.

Good documentation rocks.

---

### Post by koenn on 2010-11-03
> **dshamson said:**
> Maybe my mine is working overtime and making this harder than it is.  I imagine a very daunting task of using command line to set-up email accounts, not to even consider building a web site.

how do I access the servers so that I can set-up EMail's, Users Access and web pages?

you need to do some reading first, so that you'll ask the right questions afterwards.

Have a look through the server guide 
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

or, for a quick hands-on:
[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm)
it's Debian and a bit outdated, but it'll give you an idea of how to go about things.

---

