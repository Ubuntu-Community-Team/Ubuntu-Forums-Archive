---
title: "Linux home server"
date: 2008-06-26
forum: Server Platforms
---

### Post by M.karl on 2008-06-26
Hello

I'm currently running Ubuntu as primary OS on my home computer and some amazing environmental utility's has been inserted since I tried Debian a few years ago. Now I'm thinking about setting up a Linux server for home use, the server needs to perform the following tasks:
-Run as a FTP server
-Can be remotely controlled through the network and the web
-Playing music, connecting it to my stereo

What platform do you recommend for this job? Can I just download Ubuntu server and plug n' play?

Thanks for the answers

---

### Post by timcredible on 2008-06-26
you can use ubuntu desktop and add ftp daemon if you want.  server and desktop are the same thing, just different applications.  if security isn't a problem for remote access, i would recommend using xdm instead of vnc.  you can find out how to run xdm by clicking on my sig link.

---

### Post by weryl on 2008-06-26
I dont know about the music, but Ive got pretty much the same thing. id simply follow the ubuntu server guide to do the basic config, install vsftp (for ftp server) and OpenSSH (for remote admin). make sure you forward port 22 to your server (from the router) so that both work from WAN.
its pretty easy to do if you follow the guide, and you certainly dont need a GUI for that (btw i dont recommend webmin, it tried to ruin my setup).

---

