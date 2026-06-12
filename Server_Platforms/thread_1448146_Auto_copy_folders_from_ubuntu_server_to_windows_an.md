---
title: "Auto copy folders from ubuntu server to windows and vice versa"
date: 2010-04-06
forum: Server Platforms
---

### Post by savin on 2010-04-06
Hi can any one help me in this... Many Thanks in advance...



1. I need a script(like a scheduled cron job) which should perform Automatic copy (backup) of a directory from ubuntu server to windows and vice versa....


i tried every thing like samba mounting,ftp,etc..
with samba its possible to map the network drive of an ubuntu directory in windows..
but if the ubuntu server is not available then i cant access the network share..

Exactly this situation is happening for me while backing up tmp directory of ubuntu server ...

so in this case i need a permanent backup of tmp directory of ubuntu server in windows rather than a network share.



2. Also any ideas or scripts regarding automatic ftp (while doing a backup) from ubuntu server to windows... which can easily solve the above issue...

---

### Post by lmontrieux on 2010-04-06
Have you tried unison ?

---

### Post by savin on 2010-04-07
not yet...
am not aware of unison...
can u brief tat ......

---

### Post by lmontrieux on 2010-04-07
Sure: [http://lmgtfy.com/?q=unison+file+copy](http://lmgtfy.com/?q=unison+file+copy)

---

### Post by savin on 2010-04-08
Thanks Bro Let me check on tis

---

### Post by kewlrichie on 2010-04-08
Are you trying to keep the folders synced, between both ubuntu and windows box??

---

### Post by savin on 2010-04-12
ya am trying to snyc the linux and window..s  so tat instead of network share tat backup should b avialable even if linux box s powered off...

---

### Post by kewlrichie on 2010-04-13
Seems Like rsync is what your looking for on linux and there is a rsync for windows called Deltacopy Check that out and see how that works for you. I guess you could also use rysnc on one side to check the windows share if there's updates and I guess you can use sync toy on windows to check a samba share also. I think the rsync/deltacopy method would be the better choice

---

### Post by savin on 2010-04-20
Yup let me check out bro

---

