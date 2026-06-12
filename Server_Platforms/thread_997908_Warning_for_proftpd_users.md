---
title: "Warning for proftpd users"
date: 2008-11-30
forum: Server Platforms
---

### Post by johnman145 on 2008-11-30
I just had something weird. I installed proftpd server from the default repo, and used webmin to configure it.
Everything worken as expected and i could login with name&pass. I have 2 accounts configured and depending on what name you use, you get into your own homedirectory. 

I was in shock however when i logged in through vnc on an other computer and got read access to the root of the server  (yeah, /). I looked in the configuration and noticed the setting
DefaultRoot ~
and then all was okay. 
But somehow on the ubuntu 8.04 this is NOT the default and i am pretty sure it was the default before (i also have an older server). Im not sure whether this is a ubuntu or proftpd thing... but im posting it here just to be sure. If you would always got into the root directory it would be even that much of a problem, but when i used filezilla ftp client, IE6 and ff it does work as expected. Only with (i think IE 7) i could see everything from the root up :confused:. 

If it was up to me i would:
- make sure you always get in the same dir, no matter which client you use
- make the default that a user can only access his own dir

---

### Post by engbyrew on 2008-11-30
Hi,
I just had the same thing happen to me last night!

Could see the entire root using IE7 from a Windows machine and using an FTP program on a Windows  machine.
I am using Ubuntu server 8.10 and vsftpd (ver-? I just installed the latest last night).
You say you looked at the config and noticed the DefaultRoot setting, then all was OK, did you change it then, or just open and look?

Hope this helps,
-Rich-

---

### Post by cariboo on 2008-11-30
If you are logging securely with a good strong  password. You have nothing to worry about. You can look, but you can't do anything unless you become root. Logging in with vnc is not very secure. If you look in:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

you will find many threads concerning breakins via vnc.

THe safest way to use vnc is to use ssh to tunnel it. If you are using Windows look here:

[http://home.chattanooga.net/~john/Putty-Tunnel/putty-tunnel.html](http://home.chattanooga.net/~john/Putty-Tunnel/putty-tunnel.html)

For a Linux howto look here:

[http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/](http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/)

Jim

---

### Post by johnman145 on 2008-12-01
> **engbyrew said:**
> Hi,

You say you looked at the config and noticed the DefaultRoot setting, then all was OK, did you change it then, or just open and look?

I opened the config-file, and saw the setting i mentioned before. When i enabled this setting, i didn't saw the root anymore in IE7. When i looked on the older server i noticed that server already had this setting enabled (since i don't remember doing it, i think it was by default)

> If you are logging securely with a good strong password. You have nothing to worry about. You can look In my case it is a disaster if people even could only see the contents on the server.

> you will find many threads concerning breakins via vnc.
It is absolutely impossible to login with vnc on the server. What i did was, log in from MY computer to a windows-box on the internet to check a newly created ftp-account. I thought have a pretty good secured server with 2 firewalls and everything blocked etc.... It's not only a experimentation server, it really does contain some things i don't want to share with the outside world (nothing illegal or anything btw).

---

