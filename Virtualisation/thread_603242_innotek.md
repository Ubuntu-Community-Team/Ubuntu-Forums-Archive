---
title: "innotek"
date: 2007-11-04
forum: Virtualisation
---

### Post by j d on 2007-11-04
innotek sreen no bootable media found system failure
run ubuntu 7.04
j d

---

### Post by Delvien on 2007-11-05
Please add more information to your question, what are you trying to do? What are you trying to install.

Questions that are bare will remain un-answered.

---

### Post by j d on 2007-11-05
when i insert a dvd or cd or floppy using virtualbox
i am getting no bootable media found system failure on the vm screen
everthing is ticked of by the setting used the wizard to install it all
using ubuntu 7.04
j d

---

### Post by arthurginspain on 2007-11-05
i had this problem - issue seems to be that virtual box is looking in the wrong area.....


the cd drives in virtual box are hard coded as /dev/cdrom

but in ubuntu the cd drives are /media/cdrom0 & /media/cdrom1

so you need to do at a terminal prompt

sudo ln -fs /media/cdrom0 /dev/cdrom

worked for me 

this info is on virtual box forums - just do a search for /media/cdrom0

good luck):P

---

### Post by caligula2 on 2007-12-11
i tried that and now i don't even have a /dev/cdrom. how do i get it back?

---

