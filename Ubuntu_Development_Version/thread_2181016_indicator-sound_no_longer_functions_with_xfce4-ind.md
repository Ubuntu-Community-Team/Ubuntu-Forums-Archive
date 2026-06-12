---
title: "indicator-sound no longer functions with xfce4-indicator-plugin (Launchpad 1208204)"
date: 2013-10-15
forum: Ubuntu Development Version
---

### Post by hhWnd8K on 2013-10-15
I am trying to apply this fix for 13.10 Xubuntu

"Thanks, Sean
 For those looking for a temporary workaround, look at /usr/share/dbus-1/services/indicator-sound.service and change the Exec line

 Exec=/usr/lib/indicator-sound-gtk2/indicator-sound-service"

But I can't edit the file without root access? How do I get root access? I know there is way to do it via a gui with mouse pad or leafpad, but when I type gksudo is says it's not found. Do I install it? What commands do I use? 
Thanks

---

### Post by Toz on 2013-10-15
Hello and welcome to the forums.

gksudo [isn't installed by default]("http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-13-04") any more, but it can be installed via:
```
sudo apt-get install gksu
```

[pkexec]("http://manpages.ubuntu.com/manpages/raring/man1/pkexec.1.html") is supposed to be the replacement for gksudo, but its [not configured out of the box for running X applications]("http://askubuntu.com/questions/313828/why-is-pkexec-preferred-over-gksudo-for-graphical-applications"). 

Apparently, you can also use "sudo -i" to run graphical applications as root".

---

### Post by pqwoerituytrueiwoq on 2013-10-15
There is a more versatile workaround in this comment
[https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204/comments/41](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204/comments/41) 
you can use nano
```
sudo nano /usr/share/dbus-1/services/indicator-sound.service
```

---

### Post by hhWnd8K on 2013-10-15
[SIZE=2]**Thanks for th[B]e welcome**

*I assume the only text I change is the Exec line?:*[/B][/SIZE]

Exec=/bin/sh -c 'if [ -n "$(ps -U $USER | grep xfce4-panel)" ]; then /usr/lib/indicator-sound-gtk2/indicator-sound-service;else /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service;fi'





> **pqwoerituytrueiwoq said:**
> There is a more versatile workaround in this comment
[https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204/comments/41](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204/comments/41) 
you can use nano
```
sudo nano /usr/share/dbus-1/services/indicator-sound.service
```

---

### Post by hhWnd8K on 2013-10-15
I don't know how to use this program "sudo nano" it won't allow me to save a file. I don't know how to type out ^O to write out the file or any of the commands or what they do. Can it be done with  a GUI interface that allows me to click file then save.

---

### Post by Toz on 2013-10-15
> **hhWnd8K said:**
> I don't know how to use this program "sudo nano" it won't allow me to save a file. I don't know how to type out ^O to write out the file or any of the commands or what they do. Can it be done with  a GUI interface that allows me to click file then save.

You can either:

1. Install gksu:
```
sudo apt-get install gksu
```
...and use gksudo to startup mousepad in root mode:
```
gksudo mousepad /usr/share/dbus-1/services/indicator-sound.service
```

2. Or if you don't want to install gksu, you can:
```
sudo -i mousepad /usr/share/dbus-1/services/indicator-sound.service
```

---

### Post by hhWnd8K on 2013-10-15
TOZ, Thanks works perfect now.

---

### Post by Elfy on 2013-10-16
> **hhWnd8K said:**
> I don't know how to use this program "sudo nano" it won't allow me to save a file. I don't know how to type out ^O to write out the file or any of the commands or what they do. Can it be done with  a GUI interface that allows me to click file then save.

Just a couple of notes - to save and exit in nano Ctrl+O, Ctrl+X

I'd try to get the hang of it - if you get issues where you need to work with files at the recovery root menu then you'll thank yourself.

Secondly, be aware that while that fix works - if changes to the file come through you'll possibly need to redo the change.

---

### Post by pqwoerituytrueiwoq on 2013-10-16
> **hhWnd8K said:**
> [SIZE=2]**Thanks for th[B]e welcome**

*I assume the only text I change is the Exec line?:*[/B][/SIZE]

```
Exec=/bin/sh -c 'if [ -n "$(ps -U $USER | grep xfce4-panel)" ]; then /usr/lib/indicator-sound-gtk2/indicator-sound-service;else /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service;fi'
```
yes, that is a replacement 'Exec' line

---

