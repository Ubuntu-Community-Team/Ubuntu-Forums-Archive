---
title: "Installing programs"
date: 2010-11-13
forum: Wine
---

### Post by veestunna on 2010-11-13
Hi.
So this is my first time using ubuntu but i cant figure out how to install stuff in a way that will work
I got Wine but it seems to be useless, files are blocked, I did manage to install Orbit but
it just didnt turn on, it looks like its loading the program but nothing happens.

i really need help ubuntu looks and feels to good to go back on windows
i need to install my sound card driver program orbit downloader win rar or 7 zip
and daemon tools, and later on some big programs and ive all ready checked if in wineHQ
database and it seems they suppose to work

---

### Post by cgroza on 2010-11-13
Check for alternatives in Ubuntu Software Centre, there are many and they cover the part with winrar and daemon tools. I don't know about hte others. Also, to launch them with wine you need to give them executable rights in the propreties menu.

---

### Post by veestunna on 2010-11-13
> **cgroza said:**
> Check for alternatives in Ubuntu Software Centre, there are many and they cover the part with winrar and daemon tools. I don't know about hte others. Also, to launch them with wine you need to give them executable rights in the propreties menu.

what can replace daemon tools and winrar ?
BTW forgot to ask what can replace an mp3 player
and how can i download mp3 files

---

### Post by matt_symes on 2010-11-13
Hi

Daemon tools for mounting iso's
[http://linuxtree.blogspot.com/2010/02/daemon-tools-for-ubuntu-acetone.html](http://linuxtree.blogspot.com/2010/02/daemon-tools-for-ubuntu-acetone.html)
[http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html](http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html)

Or just mount them as a loopback device.

Rar files
[http://blog.sudobits.com/2010/05/30/how-to-open-rar-file-in-ubuntu-10-04/](http://blog.sudobits.com/2010/05/30/how-to-open-rar-file-in-ubuntu-10-04/)

for mp3 open a terminal and type
sudo apt-get install ubuntu-restricted-extras
Then enter you password to get the mp3 codecs. Then use any music player

Download mp3 files the same way you did under windows or mac.

---

