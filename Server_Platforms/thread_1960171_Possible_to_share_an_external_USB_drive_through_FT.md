---
title: "Possible to share an external USB drive through FTP?"
date: 2012-04-16
forum: Server Platforms
---

### Post by JD32 on 2012-04-16
I got an old desktop i want to put to use as file server. I'm pretty familiar with FTP and all but i could never figure out how to get an external drive to share. I have a 1TB external drive id like to use instead of buying a new drive. The external drive has an eSATA and a 2.0 USB hook up. Is it possible for me to share this drive as an external drive over VSFTP as a usb hook up? or should i just get an eSATA to IDE converter and just run it as my main drive?

Any opinions would be nice. I know somebodies gonna say "why not use samba?" well i want to be able to access it over the internet through my domain

---

### Post by bubylou on 2012-04-17
Let me first start by saying i would not recommend using ftp. I would recommend that you use a much more secure file sharing service (SFTP) via openssh. You most likely have already installed it to use ssh. From there you could simply allow your users access to wherever your drive is mounted. (/media/"drive") Have you accessed the drive locally before?

---

### Post by JD32 on 2012-04-17
yeah i know but i wasn't to worried about security since its all just movies, music and if they want to steal my homework lol... i havent been able to get the drive to share even locally through FTP no

---

### Post by JD32 on 2012-04-17
i guess it wouldn't hurt to use SFTP though, is the setup any similar to FTP, easy to configure?

---

### Post by bubylou on 2012-04-17
SFTP requires almost no configuration. Really depends on how much security you want and how you want to implements it. If you already have openssh install  and working the way you want then there isn't really much else that needs to be done.

---

### Post by JD32 on 2012-04-17
well i dont have openshh installed and running yet, will be my first venture into SSH, will i be able to share my external drive through SSH?

---

### Post by bubylou on 2012-04-17
Yes and you can use it to remotely administer your server.

---

### Post by JD32 on 2012-04-17
ic, any good how to's on this you know about?

---

### Post by memilanuk on 2012-04-18
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

