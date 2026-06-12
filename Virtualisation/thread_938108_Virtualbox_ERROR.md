---
title: "Virtualbox ERROR"
date: 2008-10-04
forum: Virtualisation
---

### Post by Tex786 on 2008-10-04
Help!!

I wanted to use virtualbox but some way i screwed things up. here is the error I am getting when i launch virtualbox.

"Could not load the settings file '/home/home/.VirtualBox/VirtualBox.xml'.

Element '{http://www.innotek.de/VirtualBox-settings}VirtualDiskImage', attribute 'filePath': [facet 'pattern'] The value '**_ubuntubetafile:///home/home/Desktop/ubuntu-8.10-beta-desktop-i386.iso_**

.vdi' is not accepted by the pattern '.+'.

Element '{http://www.innotek.de/VirtualBox-settings}VirtualDiskImage', attribute 'filePath': 'ubuntubetafile:///home/home/Desktop/ubuntu-8.10-beta-desktop-i386.iso

.vdi' is not a valid value of the atomic type '{http://www.innotek.de/VirtualBox-settings}TLocalFile'.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
VirtualBox
Interface: 
IVirtualBox {557a07bc-e6ae-4520-a361-4a8493199137}
"

what can i do to wipe anything related to virtualbox? I want a fresh start as i was starting out with virtualbox in the past 2 hours.

Can I wipe things out in terminal with some sort of comand?

Thanks

---

### Post by squaregoldfish on 2008-10-04
Try moving the .VirtualBox directory out of the way - VirtualBox should then create a whole new configuration from scratch.

The following should do it from the command line (make sure you've quit VirtualBox before you do it):

```
cd
mv .VirtualBox .VirtualBox.old

```

The above code will move you to your home directory and rename the .VirtualBox directory without deleting it, so you can get it back if you need to.

Once you've done this, start VirtualBox, and it should behave just like a new installation.

Steve.

PS I know there's (rightly) a lot of warnings about destructive code being posted on these forums, but the above is non-destructive - it won't delete any files.

---

### Post by Tex786 on 2008-10-04
command line or terminal? I am new to linux. what should i do?

thanks

---

### Post by Tex786 on 2008-10-04
> **squaregoldfish said:**
> 
```

cd
mv .VirtualBox .VirtualBox.old

```


```

home@home-desktop:~$ cd
home@home-desktop:~$ mv .VirtualBox .VirtualBox.old
mv: cannot stat `.VirtualBox': No such file or directory
home@home-desktop:~$ 

```:confused:

Anymore ideas???

---

### Post by Tex786 on 2008-10-04
that seems to have done the job. Nevermind :)

thanks

---

### Post by alaneyue on 2010-03-14
The "mv" solution works.  Just experienced the same problem, and this solution did the trick.

---

