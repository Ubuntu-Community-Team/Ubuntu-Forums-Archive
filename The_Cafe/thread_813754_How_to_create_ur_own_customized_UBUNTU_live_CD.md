---
title: "How to create ur own customized UBUNTU live CD?"
date: 2008-05-31
forum: The Cafe
---

### Post by d.kusummmanth@gmail.com on 2008-05-31
I'm using Ubuntu since nearly 4 months. I wanna customise Ubuntu and create my own live CD. I basically want to change the entire look of OS an d the packages installed, to suit my own needs. 

Can anyone guide me by informing me of the steps to be followed to create  my own customized UBUNTU live CD?

---

### Post by altariel on 2008-05-31
well, probably the easiest way is by remastersys ... 
but take the newest version!
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

i.e. add 
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/
to your /etc/apt/sources.list 

some advice (found out "the hard way")
* check and doublecheck that the password and groupfiles are in sync with each other and the shadow versions 
(sudo pwck, sudo grpck, sudo vipw -s and sudo vigr -s are useful commands as are sudo pwconv and sudo grpconv)

* NEVER start the system with a -386-kernel when intending to build the CD/DVD - you won't get a bootable system

* check and doublecheck that the links in / to your vmlinuz and initrd.img also DO NOT point to any -386-version in your /boot ... 

* you need at least the discspace to hold your ENTIRE SYSTEM AND the CD/DVD to build it

* keep everything under about 9 GB (i.e. the whole system and in case of the backup-option your whole /home) - if the compressed filesystem grows over 4 GB you won't get a bootable DVD either :( - and the remastersys-script will NOT finish properly (well, one CAN manually create the ISO-file but with a squashfs bigger than 4 GB the DVD won't boot any way) 

* the remastersys nowadays reverts your login manager back to systems default - there are ways around this (pm me in case you want instructions) since many people seemingly have screwed up the kdm/gdm/whatever so the remastersys maintainer decided to rather revert to default

---

