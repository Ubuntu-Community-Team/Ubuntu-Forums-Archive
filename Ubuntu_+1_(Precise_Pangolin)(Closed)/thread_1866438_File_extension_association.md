---
title: "File extension association"
date: 2011-10-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2011-10-21
Wonder where/how to set exe file be associated with wine. When i open the "open with" dialog box , wine which is installed is not listed there, and searching for it also fails; worst it propose to remove wine1.3 to install wine1.2 :(

---

### Post by mc4man on 2011-10-21
Then just put it in ~/.local/share/applications/mimeapps.list under - 

[Default Applications]
application/x-ms-dos-executable=wine.desktop

If you're on wine-1.3 then I'd just let it use wine.desktop (Wine Windows Program Loader), which doesn't use the cautious-launcher like wine-1.2 does.
(unless you want the c-l involved for some reason

---

### Post by seeker5528 on 2011-10-21
> **dino99 said:**
> Wonder where/how to set exe file be associated with wine. When i open the "open with" dialog box , wine which is installed is not listed there, and searching for it also fails; worst it propose to remove wine1.3 to install wine1.2 :(

Don't know if messing with mime stuff will get you what you want, before messing with it I would try:

```
sudo apt-get install binfmt-support
```

What mc4man suggests does seem like a likely suspect, if the binfmt-support thing doesn't work.

Later, Seeker

---

### Post by mc4man on 2011-10-21
binfmt-support  should be installed as a dep of wine - maybe try re-installing

Here there is no issue - Wine Windows Program Loader shows up in the context menu with out any 'help'

The other thing to check - for the most part - 
  .desktop's _can_ fail to show in the context menu's '_list_' if the Exec= line doesn't end with a <space>%<letter> (mainly properties list iirc 

Most commonly that would be %f or %U 
wine.desktop should end with %f

What usually works if all else doesn't is to copy a .desktop to ~/.local/share/applications/ & log out/in

---

### Post by dino99 on 2011-10-22
> **mc4man said:**
> 

The other thing to check - for the most part - 
  .desktop's _can_ fail to show in the context menu's '_list_' if the Exec= line doesn't end with a <space>%<letter> (mainly properties list iirc 

Most commonly that would be %f or %U 
wine.desktop should end with %f



Thanks for your answer, but i dont find those Exec= %f ; where are they ?

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/879500](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/879500)

---

### Post by mc4man on 2011-10-22
> **dino99 said:**
> Thanks for your answer, but i dont find those Exec= %f ; where are they ?

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/879500](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/879500)
Dino - sorry, been a bit since I needed to adjust this -  The deal with the %<whatever> only affects the _properties_ of a filetype, not the _open with_

( 2 examples of that would be gdebi & clementine. Both are seen on the r. click > open with, but not on the r. click > properties > open with list.
To fix either of them one would open the desktop & add to the Exec= line
Ex. gdebi
gksudo gedit /usr/share/applications/gdebi.desktop

and make the Exec= line to this
Exec=gdebi-gtk %f
}
So  - adding wine.desktop to mimeapps.list didn't change anything?

---

### Post by dino99 on 2011-10-22
> **mc4man said:**
> 
So  - adding wine.desktop to mimeapps.list didn't change anything?

Nope, is your install a fresh one ? Mine is a Oneiric dist-upgrade, and i'm thinking about a fresh install again, as nothing i've tried works.

---

### Post by mc4man on 2011-10-23
> **dino99 said:**
> Nope, is your install a fresh one ? Mine is a Oneiric dist-upgrade, and i'm thinking about a fresh install again, as nothing i've tried works.

fresh release 11.10 updated plus unity from proposed, then switched to PP.
Wine (1.3) shows immediately  in the context & properties menus (Wine window Program Loader

---

