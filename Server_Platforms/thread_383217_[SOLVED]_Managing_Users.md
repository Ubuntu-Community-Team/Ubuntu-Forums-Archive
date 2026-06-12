---
title: "[SOLVED] Managing Users"
date: 2007-03-13
forum: Server Platforms
---

### Post by victorbrca on 2007-03-13
Hi all,


  I installed a Edgy server this weekend to use as a SSH server for many different tunneling over the Internet.

  I would like to set up a user with very restricted access (like not even access to /, only his folder ).

  Can someone direct me to a link where I can find a REALLY COMPLETE info on user management? I've already spent some time looking but could not find anything on it!!

  Thanks a lot!!


Vic.

---

### Post by kokiri on 2007-03-13
I would set this user up in a chroot jail , meaning that he's locked into his directory.

He sees / but in reality / is /home/user on the real /

[http://www.ffnn.nl/pages/articles/linux/setting-up-a-chroot-jail-for-cvs.php]("http://www.ffnn.nl/pages/articles/linux/setting-up-a-chroot-jail-for-cvs.php")
That link takes you through how to set up a chroot jail for cvs but you could easily adapt it for your needs as it's the basic stock stuff and they get into setting special users that are chrooted

---

### Post by Mr. C. on 2007-03-13
For a simpler solution:

man bash

Search for RESTRCTED SHELL

MrC

---

### Post by victorbrca on 2007-03-13
Thanks a lot guys....  After knowing the proper term (chroot) I did a search and found a walk through... It's all set now!! :)

[http://ubuntuforums.org/showthread.php?t=248724&highlight=chroot](http://ubuntuforums.org/showthread.php?t=248724&highlight=chroot)

:KS :KS :KS 



Vic.

---

