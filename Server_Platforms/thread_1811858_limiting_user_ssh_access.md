---
title: "limiting user ssh access"
date: 2011-07-25
forum: Server Platforms
---

### Post by callasabra on 2011-07-25
I want to grant a certain user access to /srv/www/folder1
but I don't want the user to access anything in /srv/ or /srv/www/

all access is via ssh

how do I do this?  
Thanks in advance to the gurus!!!!

---

### Post by ubudog on 2011-07-25
Hi, I'm not sure about limiting access to directories, but this might help you:
[http://ubuntuforums.org/showthread.php?t=875164](http://ubuntuforums.org/showthread.php?t=875164)

Best of luck!  ;-)

---

### Post by ubudog on 2011-07-25
Actually, I do know something you can do.  

You can change the home directory of the user to /srv/www/folder1, and then limit the ssh access for that user to its home directory.  Here are some links that may help you.  :-)

Change home directory: [http://www.spiration.co.uk/post/1294/Unix-/-Linux-change-a-user's-home-directory---usermod](http://www.spiration.co.uk/post/1294/Unix-/-Linux-change-a-user's-home-directory---usermod)

(SSH) Limit to home directory: [http://ubuntuforums.org/showthread.php?t=1081119](http://ubuntuforums.org/showthread.php?t=1081119)

Enjoy!

---

