---
title: "WoW - Unhide Files command not working."
date: 2010-11-24
forum: Wine
---

### Post by pockets08 on 2010-11-24
Alright, everyone and their mother seems to be having this issue.

Installing WoW by disc - the computer hides all the files BUT Installer.exe. 

So to unhide them, CTRL +H. Not work.

To unhide them, going into desktop/gnome/file_view - and so on to permenantly change the unhide settings. Does not work.

Going into the Terminal and typing 
```
 sudo umount dev/cdrom 
``` - 
Will properly unmount the disc - however, when remounting i come across an issue.

```
 sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/ 
```

That obviously doesnt work. because cdrom0 isnt the name at the end...I THOUGHT I place the name of the disc, which woudl be wow3.2.0...that is false also. Now - if i remove the cdrom, and just make it mount to /media/ - the disk drives start up and goes, but i get an error saying false string or bad something. so - what goes into cdrom0? - because that doesnt exist on my computer - and idk how to find the name of what its looking for - when nothing is there.

---

### Post by Soulcage on 2010-11-25
/dev/sr0 maybe? idk

---

### Post by Hairy_Palms on 2010-11-25
> but i get an error saying false string or bad something
post the error, makes it lots easier

---

