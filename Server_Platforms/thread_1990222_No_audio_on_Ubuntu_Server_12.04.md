---
title: "No audio on Ubuntu Server 12.04"
date: 2012-05-29
forum: Server Platforms
---

### Post by alelinuxbsd on 2012-05-29
sudo apt-get install alsa alsa-tools
sudo adduser myusername audio
logout
alsamixer
Master 100
PCM 100
I make an attempt on youtube but there is no sound.

---

### Post by Orion8 on 2012-05-29
Is the sound physically switched on? I ask not to be insulting, but because I have struggled with this very issue only to find I had a switch turned off!

---

### Post by alelinuxbsd on 2012-05-29
Yes is on.

Now i put even an image taken from alsamixer just in case.

---

### Post by spynappels on 2012-05-29
Please give more information on what your setup is and what you are trying to achieve.

Do you have a desktop environment installed? If so, which one?

Are you trying to watch a YouTube video, or stream one to another device? If you are trying to watch one, are you doing it from the console/desktop in a browser or through a remote connection such as through SSH tunnelling or vpn?

---

### Post by alelinuxbsd on 2012-05-30
> **spynappels said:**
> 
Do you have a desktop environment installed? 

No i'm using the windows manager Icewm.
Anyway a desktop environment isn't strict necessary so it isn't a problem.

> **spynappels said:**
> 
Are you trying to watch a YouTube video
Yes.

Note:
I'm installed different OS on this computer included the old Ubuntu 10.04 LTS so i'm sure there aren't compatibility hardware problems.

---

### Post by alelinuxbsd on 2012-06-07
Was sufficient activate the front.

Note:
Linuxquestions help me to resolve this issue.

---

