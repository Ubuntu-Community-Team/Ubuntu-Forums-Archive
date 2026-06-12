---
title: "Lost Ubuntu Server 9.04 password"
date: 2010-07-15
forum: Server Platforms
---

### Post by Davidslv on 2010-07-15
Hi everyone,

It's a shame that my first post is about a lost password.

I have a ubuntu home server with a website (wish i really need the files), but i have a huge problem, since i "never" use the computer i forgot the password and i can't find the paper with the info.

I have the computer right by my side, i have a liveCD, i tried what is in this post [http://ubuntuforums.org/showthread.php?t=1530980&highlight=chroot&page=2](http://ubuntuforums.org/showthread.php?t=1530980&highlight=chroot&page=2)   by Penguin Guy, but no success, i think when i done this installation I encrypted the HDD, can't remember.

So, when i try to use the chroot command, it says :"chroot cannot run command bin bash' no such file or directory" 

I'm totally lost, if there is any way to recover the files i really appreciate your knowledge and help.

Thank you

---

### Post by gencha on 2010-07-15
Seems like you're missing the bin folder on your mounted partition. Maybe it's on a different partition. What does an ls produce in your chroot?

---

### Post by Davidslv on 2010-07-15
I'm sorry, what do you mean about the command ls and chroot?

---

### Post by sisco311 on 2010-07-15
Did you try to reset the password from the recovery mode?
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by gencha on 2010-07-15
> **Davidslv said:**
> I'm sorry, what do you mean about the command ls and chroot?

I ment, what is the actual content of the device that you mounted (and chrooted).

---

### Post by Davidslv on 2010-07-15
Thank you all,

sisco311, yes i just had done that.

Thank you for your help.

---

