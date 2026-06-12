---
title: "NAS &amp; Apache"
date: 2011-10-15
forum: Server Platforms
---

### Post by jaksu on 2011-10-15
Hi, I want to view my images from D-link dns-323 through apache web server. My problem is that when I try to open image file, image does not open and my browser complains that image contains errors and I doubt it (images works fine when I open them in windows). I have mounted my dns drive to /mnt/nas and I have symbolic link from my apache root dir to that nas folder. Does anybody know how I can access my images in nas correctly through apache?

---

### Post by CharlesA on 2011-10-15
Do you have a page you are using to view the images, or are you accessing them directly?

---

### Post by jaksu on 2011-10-15
I have tried it both ways. I have tried to use normal html and php file in my nas folder and pictures does not appear. When I open my index.php through web and look the source code, everything is looks normal but images does not appear. When I try to access them directly then my browser complains that pictures contains errors.

I´m trying to do image gallery with php and javascript and I want that my images is in my nas. My other test images works fine when they are in my web server.

---

### Post by CharlesA on 2011-10-15
Permission issue maybe?

---

### Post by Dangertux on 2011-10-15
Do you have FollowSymLinks in your apache virtual host configuration?

---

### Post by jaksu on 2011-10-15
Maybe. Do you know how to fix permission problems like that? I have mounted my nas with that instruction [http://forums.dlink.com/index.php?topic=7848.0](http://forums.dlink.com/index.php?topic=7848.0)

My version of mount

mount -t cifs //192.168.0.102/Volume_1 /mnt/nas -o guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777

---

### Post by CharlesA on 2011-10-15
> **Dangertux said:**
> Do you have FollowSymLinks in your apache virtual host configuration?

That might be it.

> **jaksu said:**
> Maybe. Do you know how to fix permission problems like that? I have mounted my nas with that instruction [http://forums.dlink.com/index.php?topic=7848.0](http://forums.dlink.com/index.php?topic=7848.0)

My version of mount

mount -t cifs //192.168.0.102/Volume_1 /mnt/nas -o guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777

Permissions look fine, 777 is read/write to all.

---

### Post by jaksu on 2011-10-15
> **Dangertux said:**
> Do you have FollowSymLinks in your apache virtual host configuration?

Yes I have. I tried to restart my apache but got some errors ;) I have a small confession :) I use gentoo linux and apache update and another package is now installing and it will take some time..

---

### Post by CharlesA on 2011-10-15
What errors did you get?

---

### Post by jaksu on 2011-10-16
Long battle but I manage to fix apache start problem. (Note to yourself. Do not update/edit system when you are drunk :D). Restart didn´t remove my original problem.

---

### Post by CharlesA on 2011-10-16
Hmm, is it serving files as expected now?

---

### Post by jaksu on 2011-12-08
No solution yet. Does anyone have new ideas?

---

### Post by CharlesA on 2011-12-08
So Apache is starting up ok now, right?

I don't know what the problem is with it serving files.

Are you able to test it by putting an image in the /var/www/ folder and trying to access it from there?

---

