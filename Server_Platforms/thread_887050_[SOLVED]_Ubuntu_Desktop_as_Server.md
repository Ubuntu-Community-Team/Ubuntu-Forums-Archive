---
title: "[SOLVED] Ubuntu Desktop as Server"
date: 2008-08-11
forum: Server Platforms
---

### Post by z2daj on 2008-08-11
i'm relatively new to Ubuntu, i've used it on virtual machines so i'm familiar with it. I got a few dell optiplex gx1s from my high school. so i decided to turn one of them into a server. i tried ubuntu server, but i didn't feel like learning all the terminal commands, so instead i decided to use the desktop edition as a server. now here is the real question (from a newbie :P). i want FTP, HTTP, and VNC, which i know how to set up, but should i use LAMPP all-in-one or just Apache2, and GPROFTPD alone. What are the benefits of using LAMPP compared to the latter?

---

### Post by DarkStarAeon on 2008-08-11
I can't answer your question but...

...one command would have helped you, the one where you installed a desktop environment so you didn't have to use the terminal for everything in the server edition ;)

---

### Post by cariboo on 2008-08-11
I'd install the lamp server plus openssh, that way you don't need to install an ftp server, use sftp instead, to access the files from windows use wincp to upload and download files. To cut down on the overhead and other problems that installing a gui entail, why not use a web based server administration suite. they are an easier way to administer the server then trying to do it with a desktop. Have a look at webmin and ebox. Have a look at webmin here:

[http://www.webmin.com/](http://www.webmin.com/)

and ebox here:

[http://ebox-platform.com/](http://ebox-platform.com/)

Jim

---

### Post by Iowan on 2008-08-12
> **z2daj said:**
>  What are the benefits of using LAMPP compared to the latter?Installing the LAMP server just installs/integrates MySQL (and/or PostgreSQL) and PHP.  As mentioned, SSH is another installation option (as are a mail server, DHCP server, DNS...).
[This]("http://ubuntuforums.org/showthread.php?t=886583") thread goes into the question about the GUI.

---

### Post by jayson.rowe on 2008-08-12
The server edition does have a different kernel - unless it's changed since I last checked (in 8.04, that is) it doesn't use the tickless feature, and is configured for a 100Hz tick rate.

100Hz is good for most server applications, etc, but the desktop kernel is actually better for Virtualization (if you get into that, and only after you disable the tickless feature).

All being said, you can install the Server kernel on your desktop either through synaptic or with

```
sudo apt-get install linux-server
```

And...

```
 sudo apt-get install linux-restricted-modules-server
```

You'll still have GNOME, and all the GUI doo-dads, but w/ the Server kernel.

You'll also have both kernels in GRUB (unless you remove the Desktop kernel), so you can choose which you want at boot-up.

---

### Post by pparks1 on 2008-08-12
You should be just fine.   You can install everything that you need on the desktop version.   It's probably going to be a bit easier getting your feet wet and used to the environment.  Once you get more comfortable, you may find that you like the command line interface in the end.  Personally, I love the command line as it makes documentation extremely simple.

---

### Post by R.Bucky on 2008-08-12
I am using Ubuntu 7.10. I currently host my personal site using Apache2 with Citadel BBS and Gnump. This is my first server install and site. The learning curve is steep, but not unmanageable. There is plenty of support forums on the web, which has made the process much easier.

---

### Post by fmartinez on 2008-08-12
Right now I'm currently running Ubuntu server edition 7.10 with Apache 2 web server. I would take the time to learn the command line just because you don't want to run any uneeded applications Like X11 or any other apps that run with the GUI especially since it's going to be exposed the internet. that's just my thought. I found installing the server edition and installing apache were fairly simple and straight forward. Hope this helps.

---

### Post by z2daj on 2008-09-28
> **pparks1 said:**
> Yyou may find that you like the command line interface in the end.  Personally, I love the command line as it makes documentation extremely simple.

haha yea, i ended up installing the server edition in the end... what a breeze to set up! i installed the LAMP, openSSH, and Postrsql server and modified permissions so that i can winscp into the /var/www directory. but now here comes another question, what about php scripters such as xoops, phpnuke, and phpbb? i've tried installing xoops but halfway through the set-up it claims that my MySQL database is not active... which it is. any ideas? do i have to forward ports for MySQL? thanks for the responses!

---

