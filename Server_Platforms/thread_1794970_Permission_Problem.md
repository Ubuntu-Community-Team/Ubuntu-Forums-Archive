---
title: "Permission Problem"
date: 2011-07-01
forum: Server Platforms
---

### Post by silveringking on 2011-07-01
Hi, here is my problem, my permissions are all correct, in winscp I can create dirs anywhere, but for some reason in filezilla I cannot move files or make dir it always gives me the error saying that my permissions are 550, what can I do?
My ubuntu is the 10.04, and the kernel is all updated, as far as I know this appeared out of nothing, but I had a server crash a few days ago, so must be it! Can you help me?

---

### Post by doas777 on 2011-07-01
if you console into the box with ssh, what is the output of 
```
umask
```?

the default umask should be 0022, which means that newly created files will automatically be assigned 755.

there is some discussion on client settings for winscp umask here:
[http://winscp.net/forum/viewtopic.php?t=436](http://winscp.net/forum/viewtopic.php?t=436)

---

### Post by silveringking on 2011-07-01
Hi, the code is 0022 yes, but in filezilla I cannot do it, also I cannot do it in my plataform which is "Plesk 10" from parallels. Is not better to reset the setting, how can I do it?

---

### Post by doas777 on 2011-07-01
for filezilla, this may help
[http://serverfault.com/questions/283492/how-to-specify-file-permission-when-putting-a-file-using-openssh-sftp-command](http://serverfault.com/questions/283492/how-to-specify-file-permission-when-putting-a-file-using-openssh-sftp-command)

---

### Post by silveringking on 2011-07-01
Sorry doas77 I cannot understand the instructions actually. I am a very young user I have my server since May and I have so much to learn!
What can be the causes for the problem? If you can't give me solutions give me causes and maybe I can research for myself! ;)

---

