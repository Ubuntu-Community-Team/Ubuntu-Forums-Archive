---
title: "after kernel updates Windows vms in virtualbox crash and restart"
date: 2022-09-07
forum: Virtualisation
---

### Post by hanscees on 2022-09-07
Hi,

running ubuntu VERSION="22.04.1 LTS (Jammy Jellyfish)" 


My vm's in virtualbox crash and restart. Virtualbox forums say I should update to a newer virtualbox, becuase of a newer kernel. 
My virtualbox is  [COLOR=#000000]Version 6.1.34_Ubuntu r150636

[/COLOR]Apparently I should update to a newer version. But to do that I should do so by hand. I prefer to use apt-get so ubuntu decides what updates get onto my host. 

Questions:
[LIST=1]
[*]Is there a reason ubuntu package manager do not upgrade the current virtualbox version on their platform?
[*]According to some forum I should upgrade by doing dpkg -i since
[https://download.virtualbox.org/virtual ... _amd64.deb]("https://download.virtualbox.org/virtualbox/6.1.38/virtualbox-6.1_6.1.38-153438~Ubuntu~jammy_amd64.deb")
[/LIST]

but if I upgrade by hand wont that inter-fear with later upgrades?

---

### Post by SeijiSensei on 2022-09-08
The best solution is to add the Oracle repository to your "sources" and let the normal package manager handle everything.

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by hanscees on 2022-09-08
thank you! That works. 
after that install extentionpack like so 
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

and doubleclick it or install via preferences

---

### Post by hanscees on 2022-09-08
thank you! That works. 
after that install extentionpack like so 
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

and doubleclick it or install via preferences


when getting ro errors that block starting up vm's:
 after that get rid of old modules by doing this 
[https://forums.virtualbox.org/viewtopic.php?f=1&t=106582](https://forums.virtualbox.org/viewtopic.php?f=1&t=106582)

in my case:
lsmod | grep vbox
modinfo vboxnetadp
rmmod vboxnetadp
sudo rm /lib/modules/5.15.0-47-generic/updates/dkms/vboxnetadp.ko

and that for 3 ko modules










and reinstalling new ko by doing 
sudo /sbin/vboxconfig

---

