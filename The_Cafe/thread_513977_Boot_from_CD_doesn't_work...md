---
title: "Boot from CD doesn't work.."
date: 2007-07-31
forum: The Cafe
---

### Post by dupa on 2007-07-31
I have an old pc.
On its bios there is the option Boot From CD but though i set it, it doesn't work.
So, everytime i need to install an operating system on that PC i become mad, since the boot from cd option is very useful and almost required for all modern operating systems.

Is there any way to create a "floppy boot disk" that will just "forward" the boot to the Cd-Rom?

For example.. i have a installation cd of Ubuntu.. or a installation cd of WinXp.

I insert the floppy and the installation cd in the computer.
The bios automatically boot fro the floppy.. and the floppy just "forward" the boot to the Cd-Rom.. so in this way i hope to get a working Cd Boot.

Some people told me to use Grub. Do you think it can do this? and have you any link to tutorial about creating this kind of floppy?

Thank you very much.

---

### Post by swoll1980 on 2007-07-31
Can you hit f12 befor the boot and select the drive you want to boot from?

---

### Post by dupa on 2007-07-31
> **swoll1980 said:**
> Can you hit f12 befor the boot and select the drive you want to boot from?

I can select "boot from Cd" from the bios, but Doesn't work!
the cd-rom works correctly when the system is UP... but during the boot process the "boot from cd" doesn't work though i can select that option in the BIOS menu.

---

### Post by Beamerboy on 2007-07-31
> **dupa said:**
> I have an old pc.
On its bios there is the option Boot From CD but though i set it, it doesn't work.
So, everytime i need to install an operating system on that PC i become mad, since the boot from cd option is very useful and almost required for all modern operating systems.

Is there any way to create a "floppy boot disk" that will just "forward" the boot to the Cd-Rom?

For example.. i have a installation cd of Ubuntu.. or a installation cd of WinXp.

I insert the floppy and the installation cd in the computer.
The bios automatically boot fro the floppy.. and the floppy just "forward" the boot to the Cd-Rom.. so in this way i hope to get a working Cd Boot.

Some people told me to use Grub. Do you think it can do this? and have you any link to tutorial about creating this kind of floppy?

Thank you very much.

Hey you might want to check this out:

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by dupa on 2007-07-31
> **Beamerboy said:**
> Hey you might want to check this out:

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

thanks for the link.
is "Smart Boot Manager" indipendent from the OS i need to install.
I mean.. with that floppy disk, can I boot up from Linux Cd, or BSD Cd.. or Windows CD ?

---

### Post by logos34 on 2007-07-31
> is "Smart Boot Manager" indipendent from the OS i need to install.
I mean.. with that floppy disk, can I boot up from Linux Cd, or BSD Cd.. or Windows CD ?

yes, it works with any bootable cd

---

### Post by dupa on 2007-07-31
unluckily it seems to not work.
i downloaded the binary sbminst
i executed the command and i created the boot disk on /dev/fd0

I boot the pc with the floppy inserted in.
it appears the SBM menu.. but if I choose "cdrom" and press "enter", it shows me an error message (error 0xAA) or something like that.

Of course i put in the cd-rom player a bootable cdrom (the Xp instllation cd)

I'm doing this first test on a machine on  which the boot from cd from the BIOS works correctly.

Have you any idea?
thanks

---

### Post by logos34 on 2007-07-31
I get the red error message too, but I just hit 'enter' again more firmly (as opposed to tapping the key) and it works.  Or try making it 'active' (F4 or F6 key, can't remember), then save with F2, then try selecting cdrom again.

---

### Post by dupa on 2007-07-31
> **logos34 said:**
> I get the red error message too, but I just hit 'enter' again more firmly (as opposed to tapping the key) and it works.  Or try making it 'active' (F4 or F6 key, can't remember), then save with F2, then try selecting cdrom again.

hitting enter more firmly? are you kidding me?

---

### Post by dupa on 2007-07-31
in the SBM menu there is an option
Set CDROM I/O ports
how can i get know which ports are correct?

---

### Post by Tyggna on 2007-07-31
You may want to try and flash you bios.  Chances are that the manufacturer has a new driver for it that will fix the boot from CD problem--along with other things.  You just download what they tell you, and they should provide instructions.  If that doesn't work, then I'd take a command-line bootable floppy, and edit the windows boot.ini file to look at the CD-ROM drive instead of the harddrive (backing up the file first, of course).  Once you're done booting from the CD-ROM, then switch it back.

---

### Post by dupa on 2007-07-31
> **Tyggna said:**
> You may want to try and flash you bios.  Chances are that the manufacturer has a new driver for it that will fix the boot from CD problem--along with other things.  You just download what they tell you, and they should provide instructions.  If that doesn't work, then I'd take a command-line bootable floppy, and edit the windows boot.ini file to look at the CD-ROM drive instead of the harddrive (backing up the file first, of course).  Once you're done booting from the CD-ROM, then switch it back.

i already check it.. but the mobo producer is very crappy and also with the last (of the few) bios updtes... it still doesnt' work

now i'm looking for a way to know the I/O port associated to my cdrom

if i look into
/proc/ioports
I can see some stuff associated with ide0 and ide1

My cdrom is connected on primary slave (/dev/hdb)
Someone knows a way to know the io port associated to /dev/hdb

THANKS!

---

### Post by dupa on 2007-07-31
the exact error i get is:

"disk error! 0xaa"

---

### Post by init1 on 2007-07-31
Try GRUB. 
[http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#GRUB](http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#GRUB)

---

### Post by logos34 on 2007-07-31
> hitting enter more firmly? are you kidding me?
> 
"disk error! 0xaa"

I kid you not...I get the exact same message if I quickly tap the enter key, I have to hold it down a split second longer and/or press the key 2-3 times to get it to boot up the cd...I have no idea why.  I use it all the time (I have it integrated into Grub so I don't have to change the bios to boot cds).  You say you dl'd the 'sbminst' (~40 KB executable?)...All I can suggest is to try it with the sbm.bin (~1.5 MB) file on the Ubuntu CD ('/install' folder).  That works for me.

---

