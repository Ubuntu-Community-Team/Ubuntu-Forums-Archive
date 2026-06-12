---
title: "Home folder surviving reinstalls?"
date: 2006-06-01
forum: The Cafe
---

### Post by Mr. Picklesworth on 2006-06-01
I'll figure out how to submit feature suggestions eventually, but I think it's best to see what other people think about it before I complicate something else.
Besides, I don't like calling things feature suggestions... we'll call this a discussion of user-friendliness in installers.

I think a handy addition to Ubuntu would be for the installer to detect past installations and transfer the home folder to the new installation. (Thus keeping intact old documents).
This could be a very user-friendly addition, and I'm sure it would be worthwhile!

That, of course, could be a bit tricky to do, since the old partition would theoretically be gone by the point that the new home folder is created... so another possibility would be for the installer to have an option for immeadiately dumping the Home folder into its own special partition which could persist throughout installations of Ubuntu.

Any thoughts or loud exclamations of "Picklesworth, you idiot!" are welcome :)



Edit:
Nah, I didn't forget to back up my home folder
...I just didn't bother to do it then later realized that I had, in fact, done some stuff in Ubuntu which I never backed up.
(So it wasn't a mistake... I never make mistakes :P)

---

### Post by qalimas on 2006-06-01
Well, you could just use /home in a partition of it's own all the time :P

---

### Post by ComplexNumber on 2006-06-01
>  Any thoughts or loud exclamations of "Picklesworth, you idiot!"
Picklesworth, you......!!! only joking :D. 

now seriously, i agree with galimas. one thing that you can learn from this experience of yours is to always put your home folder in a separate partition. it really is useful inbetween install. your home partition can act as a permanant storage depot in addition to keeping your settings intact.
the whole puropose of making mistakes is to learn from them ;)

---

### Post by briancurtin on 2006-06-01
what you suggested is nice, but the answer will always be "make a separate /home" partition.

that way you can use whatever distro you want and always have your files

---

### Post by cvcaelen on 2006-06-02
My personal experience:

on my testbox I had breezy installed, some pictures, set the themes to my liking,
had to manualy configure the soundcard(aztech eisa)and set the screensaver to BSOD
via apt-move I'd installed some extra programs like gkrellm, numlockx,...

downloaded the dapper iso yesterday

put the dapper cd in the testbox
got a message i could update

took about an hour of replacing files

after a restart:

login screen was changed 
still had the old themes
screensaver settings were gone, had to set the settings again, lost the BSOD(pitty!!!)
rest of the home was unchanged:still had the extra programs, soundcard still working :)

hope this helps

Christiaan

---

### Post by bonzodog on 2006-06-02
The thing with this is, that they were *supposed* to make sure that the installer created a /home partition if it wasn't already there. It was supposed to be one of the changes made to the dapper installer, and I am fairly sure there is a bug lodged in Launchpad about it.

---

### Post by asimon on 2006-06-02
[QUOTE=cvcaelen]lost the BSOD(pitty!!!)
[/QUOTE]
It seems that screensaver is now part of the package xscreensaver-data-extra from universe.

---

### Post by cvcaelen on 2006-06-02
Oh :)

thanks for the info

Christiaan

---

