---
title: "Having issues installing Vista for dualboot with ubuntu"
date: 2008-06-22
forum: Windows
---

### Post by Kronie on 2008-06-22
Hi, i am currently single booting ubuntu, and i want to install Vista to dualboot for games and all that stuff.. when i get to the partition choosing window i choose 40 gig partition formatted as "Primary" NTFS in gparted, i click next and it gives me an eeror saying

> Windows is unable to find a system volume that meets its criteria for installation

i tried to delete the partition using windows' partition manager, and then create it again but i kept on getting the same error..

i googled it and i didnt find any decent answers.. before i had ubuntu i was dual booting xp and vista, and everything was fine. ma i getting dis error because i have ubuntu installed?

i have 
Dell Dimension E510
with
WD Caviar SE SATA 250GB hard drive.

---

### Post by niyonk on 2008-06-22
found [this]("http://support.microsoft.com/kb/933925") and [this]("http://support.microsoft.com/kb/927520")
Did you take a look at those two? 
There seem to be a solution on those pages.

Hope it helps ;-)

---

### Post by Kronie on 2008-06-22
thanx.. 1st liink looks like a way out but THIS EFFIN BLOWS! T_T i spent couple weeks to configure ubuntu, and now i have to format it all... life sux >_<

---

### Post by niyonk on 2008-06-22
Sorry, dude.
Maybe next time u might want to write in small txt files of some of ur configuration files and a list of programs u have for quick install next time.
Good luck! O:)

---

### Post by rockface on 2008-06-23
This behaviour is Microsofts modus operandi in action.

They make it almost impossible to install a Windows operating system on a machine with a rival operating system.

Almost all operating systems (does Apple do this?) go out of there way to accommodate Microsoft's crapware. But Microsoft, for their part, try and make their OS the one and only 'true' OS.

I would recommend backing up your settings, format then install Windows. Then and only then (after making sure Windows works ok) install the Linux distro of your choice.

It should not be this way, but this is 'The Microsoft Way!' that their fanbois wet themselves and drool over so much.

---

### Post by ComputerGeek31618 on 2008-06-24
I said it somewhere else, but Windows is not a dual-boot intended OS, and Linux (whether it is "intended" or not, per se), is dual boot minded.  The non dual-boot OS comes first, so it can handle being there.  And the other won't mind.  Sorry that you'll have to reformat for Windows.

---

### Post by Kronie on 2008-06-24
well i used to dualboot xp and vista with no problem.. 
guys is there some software that backups all packagaes and then makes some sort of installer? i have so many stuff installed, and configured and i dont want to get rid of it(and do it all over again..took me about a week or 2) and i really need vista.. 

or can i just grab the whole ubuntu system, put it on external hard drive for backup, then format my primary HD, install windows, then make partition for ubuntu, put all the files in its place,and then make a grub entry? o_0 or i need to do full install? T_T

---

### Post by pelle.k on 2008-06-25
Use a livecd (with partimage) to back up one (or more) image(s) to your external HD.
```
partimage -z1 -b -d save /dev/<DRIVE> /mnt/<external_drive>/<imagename>
```

then, install vista or whatever, recreate ext3 (?) partitions with livecd, and put that imagefile back where it (they?) belong.
```
partimage -b restore /dev/<DRIVE> /mnt/<external_drive>/<imagename>
```

**IMPORTANT;**
Since the partitions have a new "location", on the HD, (i assume?) you need to do these steps as well.
The only modification you have to do to to ubuntu, is to update /etc/fstab so that the partitions point to the new location (eg. /dev/sda2 instead of sda1 etc) and /boot/grub/menu.lst so that the entries it points to the new root and so forth.

Final step is to install grub, from live-cd. run "grub" at a root prompt.
set the root (ubuntu root);
```
root (hd0,**X**)
```
install it (to MBR);
```
setup (hd0)
```
exit grub;
```
quit
```

**Learn this once, it'll make you life easier. I even have linux installed to my external HD to do these backups automatically, if needed.**

---

### Post by Kronie on 2008-06-25
pelle.k
yes! i was just talking to friend whos sysadmin, and he told me to do same thing. to make image of current ubuntu part. but i didnt know how to do it, and here u are :D thanx, ill try that right away..gotta clean up some space on external HD frist tho.. 0_o

---

### Post by pelle.k on 2008-06-26
Do update us on your progress :)
It can be a little bit overwhelming if it's your first time.

btw, partimage does "sparse" imaging, i.e. if your /home is 200GB, but you are only using 5GB, the image will be approx 5GB (or less with compression).
Also, note that grub drive names start from "0" not "1". Let me illustrate;
hd0 = sda (MBR)
hd0,0 = sda1 (fist drive, first partition)
hd1,0 = sdb1 (second drive, first partition)

You'll get the hang of it :)

---

