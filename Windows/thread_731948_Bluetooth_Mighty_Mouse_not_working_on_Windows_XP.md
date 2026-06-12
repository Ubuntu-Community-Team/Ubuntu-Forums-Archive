---
title: "Bluetooth Mighty Mouse not working on Windows XP"
date: 2008-03-22
forum: Windows
---

### Post by marcikic on 2008-03-22
Hi,

I'm pretty new in Ubuntu business and my title probably seems to be for a windows forum but let me tell my story and you'll see.

Ok, I installed Ubuntu on my laptop using Wubi on a different partition disk from the one where is my XP (please do not ask why do I need Ubuntu if I already have XP, it is another question). Everything worked nicely on Ubuntu 7.04 except my Mighty Mouse. I decided to upgrade to 7.10. Small inconvenience was the "Failed to initialized HAL" message which I managed to resolve using solution found on this forum (well correct me if I'm wrong there are 18 reasons for this error massage (according to the same source) and the one which worked for me was a simple line command "sudo /usr/lib/hal/hald-generate-fdi-cache" found on this thread [http://ubuntuforums.org/showthread.php?t=583940](http://ubuntuforums.org/showthread.php?t=583940) , I thank vnovea so much for this).

Now everything works nicely on Ubuntu, except me i.e. for anything I want to install I need 2-3 hours looking and finding solutions on the web. But this is not Ubuntu's problem, it's mine. 

Anyway, here's my problem, once I returned to XP my previously perfectly working Mighty Mouse can not be connected. My machine can find him, can even lunch usual Logitech driver to instal him, and even it tells me it is installed and it was for less then a second but then it is disconnected. So my question is (I suppose far from being simple) how a OS installed on another disk (at least I hope everything is decoupled) can influence my XP? I would be grateful if someone has a start of idea what to do (for example disabling and enabling my bluetooth did not work, I didn't try to reinstall driver, I might).

Thanks in advance.

---

### Post by corvi42 on 2008-04-09
I have been having the same issue myself. I dual-boot 7.10 and winXP. I can get the Mighty Mouse successfully paired and working in either OS, and if I reboot back into the same OS everything is fine. However, if I boot into the other, it is no longer able to use the mouse. I have to delete the mouse profile and recreate it before it will work. In windows I do this by just deleting and rescanning the devide. In Ubunto i need to delete /var/lib/bluetooth/* and then /etc/init.d/bluetooth restart and then hidd --search.

This is quite annoying really. I think it is probably due to the fact that there is some machine identifying info which is communicated to the mouse from the OS. The bluetooth ids of the adapter on my box & the mouse are obviously the same, so there must be some system-identifier that the mouse is caching. Not knowing much about bluetooth internals I'm not sure what this is. Any suggestions would be helpful. I'll post again if I come up with any solutions.

---

