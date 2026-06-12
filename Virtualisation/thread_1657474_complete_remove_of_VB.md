---
title: "complete remove of VB"
date: 2011-01-01
forum: Virtualisation
---

### Post by surati on 2011-01-01
Hi 

I removed VB from my computer (sudo apt-get remove virtualbox) and would like to remove all other vb-rests too.
  I was searching for VB rests on my computer and found 30 more VB-files, cann i simply delete them?
 

 On the list are for ex.
 -Virtualbox-ose         /etc/init.d
 - k-20 virtualbox-ose         /etc/rc6.d
 - virtualbox-3.2.....ubuntu_maveric_i386.deb           /var/cache/apt/archives
  -virtualbox-ose.....dkms....all.deb            /var/cache/apt/archives
 - virtualbox-3.2.list          var/lib/dpkg/info
  - download.virtualbox.org.......maveric.release     /var/lib/apt/list
 etc.
 

 Can i just delete them? How can i find out if more rests are in my computer?
 (I would like to do later a new clean install of the latest VB. maybe in this way i can prevent my VM-Errors ).
thanks
S.
**[COLOR=DarkRed]EDIT[/COLOR]**
[COLOR=DarkRed]I was just  trying to delete some files but it did´nt function (no rights). I have 9 files in the /etc folder, can someone be so kind and tell me how i can delete them?? [/COLOR]

---

### Post by surati on 2011-01-01
[SIZE=2][COLOR=Black]The problem is solved with these 2 comands: 
sudo apt-get remove --purge virtualbox-ose
 dpkg -l | grep ^rc | awk '{print $2}' | xargs sudo dpkg --purge  
The rest 2 files i deleted with nautilus.
):P[/COLOR][/SIZE]

---

