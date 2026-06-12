---
title: "Help with Windows 7 x64 Virtualbox"
date: 2015-09-19
forum: Virtualisation
---

### Post by james139 on 2015-09-19
I'm trying to install WIn7 on a virtual box, and I'm getting the error in the screen capture below. It's my first attempt and I don't really know what I'm doing! Is it a problem with my CPU not being compatible with virtualbox?

[IMG][[IMG]http://i46.photobucket.com/albums/f112/Forkbeard78/virtualbox_zps1vqyosap.png[/IMG]]("http://s46.photobucket.com/user/Forkbeard78/media/virtualbox_zps1vqyosap.png.html")[/IMG]

---

### Post by james139 on 2015-09-19
OK, I enabled virtualization in BIOS and now I'm getting a different error message: 

[IMG][[IMG]http://i46.photobucket.com/albums/f112/Forkbeard78/Screenshot-1_zpsxpcqlcx9.png[/IMG]]("http://s46.photobucket.com/user/Forkbeard78/media/Screenshot-1_zpsxpcqlcx9.png.html")[/IMG]

---

### Post by james139 on 2015-09-19
OK, solved. It appears I was a bit trigger happy in posting. That'll teach me :)

For anyone else who might have the problem, change the chipset settings in Virtualbox to ICH9, and enable IO APIC.

---

