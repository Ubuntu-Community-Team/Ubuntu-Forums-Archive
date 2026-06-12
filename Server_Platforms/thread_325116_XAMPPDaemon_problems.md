---
title: "XAMPP/Daemon problems"
date: 2006-12-25
forum: Server Platforms
---

### Post by Ghozt on 2006-12-25
I decided to remove my Apache/PHP installations via Synaptic and install XAMPP so that I could have HTTPS/MySQL setup easily. I followed the [instructions](http://www.apachefriends.org/en/xampp-linux.html#377), but I'm having a little problem.

phillip@ubuntu:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.5.5a...
XAMPP: Another web server daemon is already running.
XAMPP: Starting MySQL...
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.

I know that I had Apache2 installed before, but I removed it. I don't ever remember installing an FTP server, and I've removed apache2 from /etc/init.d as suggested in another thread. I've looked on Google for help but all of the people having the same problems as me are speaking in other languages. I've looked in Services and only mysql is running, and netstat doesn't show anything for :80, [http://localhost](http://localhost) also doesn't load, it seems like it's going to and then after about 20 seconds a blank page comes up, no "server not found" error or anything like that.

So, is there any way to tell what's really running? Yes - I've tried uninstalling XAMPP && restarting && reinstalling - same problem. Oh, and I gave up on [ftp://localhost](ftp://localhost) after it wouldn't load for 2+ minutes. I don't think I left anything out, if you'd like me to try anything else then just ask, all comments/suggestions are appreciated, thanks.


- Phillip

---

