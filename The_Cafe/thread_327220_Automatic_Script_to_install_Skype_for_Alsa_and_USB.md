---
title: "Automatic Script to install Skype for Alsa and USB devices"
date: 2006-12-28
forum: The Cafe
---

### Post by patrick295767 on 2006-12-28
****Hi, 

I made again an automatic script. This one for Skype for ALSA & USB installation for difficulties with Skype & Alsa.
  
The howto is there : [http://forums.debian.net/viewtopic.php?p=44096#44096](http://forums.debian.net/viewtopic.php?p=44096#44096)
 The code to start the graphical installation is there:
  
```
cd /tmp
wget http://patrick295767.sitesled.com/patatixinstallations/patatix_skype0256.sh
sudo su                ##   to start installing as root, depending on your distro.  wget will be made a users !
su                        ##   to start installing as root, depending on your distro.  wget will be made a users !
bash /tmp/patatix_skype0256.sh
```
[B]
[COLOR="Red"]unsure if it works for you & very very risky[/COLOR][/B]

Best Regards, 

Patrick
  
===
(Alsaconf / alsactl are used)
==
Updated vers. 2.0

---

