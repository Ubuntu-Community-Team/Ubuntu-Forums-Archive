---
title: "Were/what is  Ubuntu Studio?"
date: 2009-10-28
forum: Ubuntu Studio
---

### Post by quimkaos on 2009-10-28
Were/what is  Ubuntu Studio?

it seams i can't find any info on the main Ubuntu site? can anyone enlighten me?

---

### Post by Bucky Ball on 2009-10-28
[http://au.altavista.com/web/results?itag=ody&q=ubuntu+studio&kgs=0&kls=0](http://au.altavista.com/web/results?itag=ody&q=ubuntu+studio&kgs=0&kls=0)

Why limit yourself to the Ubuntu site? Always do a full search. Studio has a site of its own.

---

### Post by quimkaos on 2009-10-28
i didn't limited myself to the ubuntu site but since it was supposedly a ubuntu project/flavor i thought that it was supposed to have a link from the main site.

still i'm i would like to ear what studio is (not that is just a collection of programs) and if it is installable in an normal ubuntu system...

---

### Post by Jammy4041 on 2009-10-28
It's basically an ubuntu remix with things for media professionals. Because of this I'm sure you can update it using APT. What ubuntu system are you running exactly?

---

### Post by quimkaos on 2009-10-28
Ubuntu 9.10

And since i work with webdesign and multimedia i could use some of the studio features...
i'm already using gimp, inkscape and synfig.

---

### Post by Jammy4041 on 2009-10-28
The Ubuntu studio wiki page is here: [https://help.ubuntu.com/community/UbuntuStudio/Installation](https://help.ubuntu.com/community/UbuntuStudio/Installation)
 
I cannot find any info about Juanty specific features, but try typing
 
```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
``` into a terminal to update via apt.

---

### Post by Jammy4041 on 2009-10-28
If you only need Studio applications and things,  there is this page here: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
 
It seems that Ubuntu Studio prefers 8.04?

---

### Post by vinutux on 2009-10-28
ubuntu with a lot additional multimedia apps pre-loaded , U can even turn your current ubuntu installation to studio......., it usually come with dvd image [coz of a lot apps pre-insatlled]

---

### Post by quimkaos on 2009-10-28
> **Jammy4041 said:**
> The Ubuntu studio wiki page is here: [https://help.ubuntu.com/community/UbuntuStudio/Installation](https://help.ubuntu.com/community/UbuntuStudio/Installation)
 
I cannot find any info about Juanty specific features, but try typing
 
```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
``` into a terminal to update via apt.

FAIL!

i'll be looking into those last 2 links soon

---

### Post by Jammy4041 on 2009-10-28
[http://ubuntuforums.org/showthread.php?t=1252957](http://ubuntuforums.org/showthread.php?t=1252957)
 
[http://ubuntuforums.org/showthread.php?t=682337](http://ubuntuforums.org/showthread.php?t=682337)

---

### Post by Jammy4041 on 2009-10-28
Try splitting the commands up.
 
Open a terminal and type
 
```
sudo apt-get update
```
 
and then:
 
```
sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```
 
EDIT: you could alweays use synaptic to install the packages.

---

