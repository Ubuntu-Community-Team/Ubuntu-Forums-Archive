---
title: "Server's been hacked -- how to investigate and recover?"
date: 2008-01-09
forum: Server Platforms
---

### Post by xingmu on 2008-01-09
Uh...sorry, I jumped gun.  Moderators, please delete this thread.

---

### Post by Miademora on 2008-01-09
You will have to reinstall the whole server again to make sure its clean. 

Did you have ssh-password authentication enabled by any chance or keys only? Did you have a password with a word that might be inside a dictionary or a proper one with numbers etc.? 

Id suggest you make an image from the hdd and mount the image read only for further investigation. Make sure you take the box offline for incoming and outgoing traffic to the internet.

Just google for more since investigating these things can be a pretty complex process if it goes as far as rootkits.

---

### Post by xingmu on 2008-01-09
Thanks for the advice.  I actually just figured out in the last couple minutes that I had some broken packages related to sendmail which caused all the weird messages in the syslog.

---

### Post by Sef on 2008-01-09
Locked.  The problem was not what the OP believed.  No need to have others post here.  The OP can start a new thread with the actual problem.

---

