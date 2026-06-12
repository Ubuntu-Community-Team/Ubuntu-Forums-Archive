---
title: "Installing desktops in 13.04"
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by JLeon85 on 2013-03-23
I'm running Lubuntu 13.04 and I'm trying to install the other desktop environments. Using "[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install xubuntu-desktop"[/FONT][/COLOR]Gets me the following error: [COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Does anyone know what I'm doing wrong? Thanks in advance.

---

### Post by ibjsb4 on 2013-03-23
Is another process using it?

Do you have another package manager open like maybe the software center?  Only one can be open at a time.

---

### Post by Virtuality314 on 2013-03-23
Try this in terminal IF ibjsb4 's suggestion does not work: 

sudo rm -r /var/lib/dpkg/lock

This will remove the lock. However, only do this if you do not have something like synaptic already open, or something like aptitude running.

---

### Post by JLeon85 on 2013-03-24
Thanks guys! There must have been something else running, because a reboot was all it took. I'll keep that unlock method in mind though.

---

### Post by zika on 2013-03-24
> **JLeon85 said:**
> Thanks guys! There must have been something else running, because a reboot was all it took. I'll keep that unlock method in mind though.Bigger hammer (reboot) is always available... We prefer working with the smallest that is effective... ;)

---

### Post by arpanaut on 2013-03-24
> Bigger hammer (reboot) is always available... We prefer working with the smallest that is effective... 

LOL  Much appreciated!

---

