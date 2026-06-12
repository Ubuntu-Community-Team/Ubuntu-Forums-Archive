---
title: "home folder icon replaced?"
date: 2013-03-27
forum: Ubuntu Development Version
---

### Post by Jacobonbuntu on 2013-03-27
Hi people, 

I noticed in 13.04, the home folder icon (/usr/share/applications/nautilus-home.desktop) is replaced by the "Files" icon (//usr/share/applications/nautilus-folder-handler.desktop). Just curiousity, but does anyone know why that is?

---

### Post by rrnbtter on 2013-03-27
Greetings,
This is just a knee jerk guess but it could be that the new icon was deemed more appropriate for Nautilus ((//usr/share/applications/**nautilus**-folder-handler.deskto). I'm ok with it.

---

### Post by dino99 on 2013-03-27
Thats all the gnome team fun: the first time i've clicked on Home and was expecting to see nautilus opening the folders tree, i got baobab instead; very annoying. Now i'm used with the Files icon.

---

### Post by grahammechanical on 2013-03-27
Canonical hired someone to redesign various icons. And some labels have been changed. The Dash label now says Search your computer and online sources. This has been around for a couple of weeks. Just wait until you get Unity 7 with its 100 scopes on 1st April.

[http://www.omgubuntu.co.uk/2013/03/ubuntu-13-04-updates-nautilus-update-tool-icons](http://www.omgubuntu.co.uk/2013/03/ubuntu-13-04-updates-nautilus-update-tool-icons)

Regards.

---

### Post by mc4man on 2013-03-27
> **grahammechanical said:**
>  Just wait until you get Unity 7 with its 100 scopes on 1st April.

Maybe they can fix it enough in the next 4 days to the extent they're ready to dump it on users, atm can't see how.
> The goal is to have everything ready by April 1st. Until then, a ppa
  will be updated everyday for testing the feature by a group of 5 people
  (the ppa will be: [https://launchpad.net/~ubuntu-unity/+archive](https://launchpad.net/~ubuntu-unity/+archive)
  /experimental-certified). Existing tests will be run as per of the daily
  release process. That + the manual testing, we'll have a good pick on
  the quality status before flipping the switch.
  
I'm obviously not one of those 5 but currently the "quality status" is unacceptable

---

### Post by Jacobonbuntu on 2013-03-27
Thanks! 
Not that is that important, but I still wonder why they did it. If it's just an icon, they could have easily just replaced that?
let's see what happens.

---

### Post by Frogs Hair on 2013-03-27
Here is a post about the icons. [http://www.omgubuntu.co.uk/2012/11/ubuntu-updates-software-center-update-manager-icons-in-13-04](http://www.omgubuntu.co.uk/2012/11/ubuntu-updates-software-center-update-manager-icons-in-13-04)

---

### Post by Jacobonbuntu on 2013-03-27
I definitely like the new icons. however, it is not the icon that is changed, but the desktop file representing nautilus in the launcher. the icon of /usr/share/applications/nautilus-home.desktop is still the old folder icon (almost)

---

### Post by rrnbtter on 2013-03-27
Greetings,

> **Jacobonbuntu said:**
> Hi people, 

I noticed in 13.04, the home folder icon (/usr/share/applications/nautilus-home.desktop) is replaced by the "Files" icon (//usr/share/applications/nautilus-folder-handler.desktop). Just curiousity, but does anyone know why that is?

 The new format allows the desktop file to call the **default** file manager and not just nautilus.

---

### Post by mc4man on 2013-03-27
Ubuntu(unity) is now using nautilus.desktop, not the other 2  (the prev. nautilus-home.desktop &  nautilus-open-folder.desktop which is just there for upgrades
Just ck. the default gsetting for the unity launcher > favorites

---

### Post by Jacobonbuntu on 2013-03-28
> **rrnbtter said:**
> Greetings,



 The new format allows the desktop file to call the **default** file manager and not just nautilus.

AHA, that makes sense I guess

---

### Post by ping-wu on 2013-03-28
I also like the new file manager icon.  Very intuitive!

---

### Post by Jacobonbuntu on 2013-03-28
> **mc4man said:**
> Ubuntu(unity) is now using nautilus.desktop, not the other 2  (the prev. nautilus-home.desktop &  nautilus-open-folder.desktop which is just there for upgrades
Just ck. the default gsetting for the unity launcher > favorites

you're right! 
what do you mean by just for upgrades?

---

### Post by mc4man on 2013-03-28
> **Jacobonbuntu said:**
> 
what do you mean by just for upgrades?

nautilus-folder-handler.desktop was added back via this report i had in 11.10 for 11.10 & later
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788)

whether they've found any other current use don't know, nor see. If not then it can go at some point in near future
(assuming down the road nautilus is still used...

---

