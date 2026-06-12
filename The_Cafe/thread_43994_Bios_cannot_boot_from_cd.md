---
title: "Bios cannot boot from cd"
date: 2005-06-24
forum: The Cafe
---

### Post by champ_rock on 2005-06-24
Bios cannot boot from cd... hey guys my motherboard is an oldie and an antique pece which cant boot from cd..... what should i do to install ubuntu..........

also whether dos boot disk will be sufficient

---

### Post by eskaypey on 2005-06-24
netbootinstall? or even install debian via floppy and upgrade to ubuntu.

---

### Post by champ_rock on 2005-06-24
sorry i was not able to understand what u meant by "netbootinstall?"....also i am using LINUX for the first time so it would be really kind of u to please tell me the steps so that i can proceed further......

---

### Post by somuchfortheafter on 2005-06-24
not to offend but what are the specs on this machine, i mean if it doenst support booting from a cdrom drive chances are that it will not support all the features of ubuntu either...

---

### Post by UbuWu on 2005-06-24
The easiest way is to use a smartbootmanager floppy. For instructions look here:
[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

---

### Post by jdong on 2005-06-24
[QUOTE=somuchfortheafter]not to offend but what are the specs on this machine, i mean if it doenst support booting from a cdrom drive chances are that it will not support all the features of ubuntu either...[/QUOTE]

That doesn't mean you should give up on installing Ubuntu...

I have a 75MHz system running Ubuntu, and that still does well if you know what software to install.

---

### Post by Brunellus on 2005-06-24
[QUOTE=jdong]That doesn't mean you should give up on installing Ubuntu...

I have a 75MHz system running Ubuntu, and that still does well if you know what software to install.[/QUOTE]

OK, I'm *very* interested.  How did you get Ubuntu running happily on what must be a 486DX?

---

### Post by jdong on 2005-06-24
I had a PCMCIA NIC. Installed Ubuntu on my desktop (ubuntu-base only, like the 'server' install), booted the laptop with a floppy distro, then scp'd over the base system :)

It amazingly runs X.org with fluxbox, abiword, dillo as web browser, and many other goodies, too. It runs as a competent X terminal to my desktop, too, which is what I use it for the most.

---

### Post by sonny on 2005-06-24
[QUOTE=champ_rock]Bios cannot boot from cd... hey guys my motherboard is an oldie and an antique pece which cant boot from cd..... what should i do to install ubuntu..........

also whether dos boot disk will be sufficient[/QUOTE]
With a windows 98 boot floppy... First put the ubuntu cd inside, then put the win98 floppy in; rebbot and make a floppy boot, when the floppy ask you about cd-rom support then say yes, and that should be all... the specifics I can't tell cuz I'ven't done it for a long time, but I maganed to get Win2000 to some old pc's with that technique...  :grin: Hope you manage to figured out the specifics of the process.

---

### Post by jdong on 2005-06-24
[QUOTE=sonny]With a windows 98 boot floppy... First put the ubuntu cd inside, then put the win98 floppy in; rebbot and make a floppy boot, when the floppy ask you about cd-rom support then say yes, and that should be all... the specifics I can't tell cuz I'ven't done it for a long time, but I maganed to get Win2000 to some old pc's with that technique...  :grin: Hope you manage to figured out the specifics of the process.[/QUOTE]
This will NOT work, because the Ubuntu installer requires a LINUX kernel to be loaded.

---

### Post by sonny on 2005-06-24
[QUOTE=jdong]This will NOT work, because the Ubuntu installer requires a LINUX kernel to be loaded.[/QUOTE]
Then he has to look for a Bios-update, or buy a new mobo... cuz it's his/her first time with linux and network boot is not for a linux newbie...

---

### Post by UbuWu on 2005-06-24
[QUOTE=sonny]Then he has to look for a Bios-update, or buy a new mobo... cuz it's his/her first time with linux and network boot is not for a linux newbie...[/QUOTE]

No he doesn't, just follow the instructions on [https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

This will give you a floppy from which you can boot and this boots the cd-rom, even if that is not supported by the bios.

---

### Post by benplaut on 2005-06-24
[QUOTE=jdong]That doesn't mean you should give up on installing Ubuntu...

I have a 75MHz system running Ubuntu, and that still does well if you know what software to install.[/QUOTE]

specs... give me specs...

i need something to do with my 75MHz 701C  ](*,)

---

### Post by sonny on 2005-06-24
[QUOTE=UbuWu]No he doesn't, just follow the instructions on [https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

This will give you a floppy from which you can boot and this boots the cd-rom, even if that is not supported by the bios.[/QUOTE]
Nice... I had never heard of it... why?... it's super cool... just added to my boot floppy collection... does it make every Linux installation to work, or just Ubuntu?.. I want ot presume that ALL distros... right??

---

### Post by jdong on 2005-06-24
It's an El Torito bootable CD-ROM stub... Works well for BIOS-recognized IDE CD-ROMS, not awesome for the retarded laptop CD-ROMs.

---

### Post by champ_rock on 2005-06-25
thnaks for the smart boot manager tip .......  but i tried rawrite to write the smartboot manager on a floppy....problem is that rawrite writes only .img files whereas the smartbootmanager is a .dsk file....what should i do

---

### Post by UbuWu on 2005-06-25
On linux it is as easy as typing:
dd if=image of=/dev/fd0       (where image is the image filename)

On windows... I think renaming it to .img would do? Otherwise try one of the programs from this page: [http://www.fdos.org/ripcord/rawrite/#windows](http://www.fdos.org/ripcord/rawrite/#windows)

---

### Post by CospeFogo on 2005-06-25
Try this:

[http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm](http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm)

EDIT: Oops... didn't notice you had already tried.

---

### Post by champ_rock on 2005-06-25
the thing is this rawrite writes only *.img files and this smart boot manager is a *.dsk file.......................................... if i change the name of smartboot manager to *.img then it writes but the floppy disk is empty ....nothing is in it????????????????? is it a normal thing....that maybe the files r hiden or something

---

### Post by UbuWu on 2005-06-25
[QUOTE=champ_rock]is it a normal thing....that maybe the files r hiden or something[/QUOTE]

Don't know, never used it myself... have you tried if it works?

---

### Post by andlinux21 on 2005-06-27
on rawwrite click the drop down arrow where it says *.img and select *.* or all files and then pick the smartboot image it should work i just used it.

---

### Post by champ_rock on 2005-06-28
thanks it runs just perfect..............

---

### Post by andlinux21 on 2005-07-22
I used SBM and got the CD to load and install but when it asks to remove the CD and reboot it wont load Ubuntu anyone have this problem???? ](*,)

---

### Post by andlinux21 on 2005-07-23
after a bit of googling I found out that the BIOS wont handle that 10G hard drive so I will have to try a smaller hard drive....

---

