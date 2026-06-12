---
title: "Editing var/www when permissions do not allow."
date: 2006-10-30
forum: Server Platforms
---

### Post by fraiha on 2006-10-30
Well, I've had no problem installing Apache, PHP, or Rails or any of that stuff, my problem comes with actually using Apache. /var/www is set to some permission where I cannot edit it. I first tried sudo mv folder /var/www and my work simply disappeared (assuming permissions would not allow it to its destination). So then I tried chmoding www, then var and all it did was break Linux (which I had to fix going into non-graphical mode). So then I tried to change the path to htdocs in /etc/apache2/sites-available/default. I open it up in vim, try :w, doesn't work, try :w! again does not work. I don't know enough about Linux to use sudo in vim though I had assumed :w! would write it anyways, it didn't. So again I try to chmod the file, then ultimately etc. After that I was no longer able to use sudo. My question doesn't involve how to fix where I'm at. I'm just curious how exactly do you get things done when everything is locked up, seeing how I'm obviously doing something wrong. Thanks in advance.

---

### Post by foxylad on 2006-10-30
You need to read a bit about the [unix permission system]("http://en.wikipedia.org/wiki/Unix_permissions"). It is pretty simple, but pay particular attention to x on directorys. Once you have your head around this, your problems will make sense.

I guess you have come from the PC world, where you are the only user and it seems sensible to give that user rights to everything. But as soon as you plug that PC into the internet, there are potentially millions of users of the PC. The appauling security record of Windows is mostly due to this issue.

UNIX, on the other hand, started as a multi-user system and catered limited permissions from the ground up. One day when you get a malicious user on your server, you will be praising the permissions system.

---

