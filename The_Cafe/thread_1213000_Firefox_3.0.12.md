---
title: "Firefox 3.0.12"
date: 2009-07-14
forum: The Cafe
---

### Post by ThisEndlessFall on 2009-07-14
When will Canonical ship this?

---

### Post by steveneddy on 2009-07-14
Patience young padiwan.

Have you tried FF 3.5? It's a lot faster and easier to use.

The Ubuntu version is always a little behind what the mfr has currently released.

---

### Post by ThisEndlessFall on 2009-07-14
> **steveneddy said:**
> Patience young padiwan.

Have you tried FF 3.5? It's a lot faster and easier to use.

The Ubuntu version is always a little behind what the mfr has currently released.

Padiwan?

Anyway I was trying to add 3.5 from a PPA, but ended up with 3.0.12 instead. It's seems considerably faster than 3.0.11. And as how we won't be receiving 3.5 until Karmic, this would be a good stopgap until then.

---

### Post by vinutux on 2009-07-14
install from [**[COLOR="DarkGreen"]this[/COLOR]**]("https://launchpad.net/~fta/+ppa-packages") repo But FF called that shiretoko (codename of FF 3.5)

no prob....working everything fine 4 me....

.

---

### Post by andrewabc on 2009-07-14
sometimes takes a week for them to get to ubuntu. So better off waiting a week and get it as normal update.

---

### Post by Tibuda on 2009-07-14
> **ThisEndlessFall said:**
> Padiwan?

Anyway I was trying to add 3.5 from a PPA, but ended up with 3.0.12 instead. It's seems considerably faster than 3.0.11. And as how we won't be receiving 3.5 until Karmic, this would be a good stopgap until then.
You should read this thread: [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)
You don't even need a PPA anymore to install the 3.5, but it is on a different package ([firefox-3.5]("apt:firefox-3.5")). It's going to be called Shiretoko, the Mozilla beta codename, but it is not beta. [Canonical chose to keep the name]("http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html") for people that keep both browsers.

---

### Post by steveneddy on 2009-07-14
> **ThisEndlessFall said:**
> Padiwan?

Anyway I was trying to add 3.5 from a PPA, but ended up with 3.0.12 instead. It's seems considerably faster than 3.0.11. And as how we won't be receiving 3.5 until Karmic, this would be a good stopgap until then.

Try looking at applications --> internet --> shiretoko

---

### Post by vinutux on 2009-07-15
Shiretoko is fine...FF with diffrent name ...no probe but sites give information about not support this browser and informs to change to FF or chrome....no matter they don't understood shiretoko is the same FF .

---

### Post by Tibuda on 2009-07-15
> **vinutux said:**
> Shiretoko is fine...FF with diffrent name ...no probe but sites give information about not support this browser and informs to change to FF or chrome....no matter they don't understood shiretoko is the same FF .

That's a known issue with the user agent. To fix it, open about:config, and search for general.useragent.extra.firefox and replace Shiretoko for Firefox.

---

### Post by RATM_Owns on 2009-07-15
Ubuntu still has 3.0.11 by default?

I got 3.5 the day it came out from my `pacman -Syu`.

---

### Post by Tibuda on 2009-07-15
> **RATM_Owns said:**
> Ubuntu still has 3.0.11 by default?

I got 3.5 the day it came out from my `pacman -Syu`.

Jaunty yes, and it will not change. Ubuntu is not rolling as Arch.

---

### Post by ramnarayan on 2009-07-15
> **ThisEndlessFall said:**
> When will Canonical ship this?

as others have said why not move to 3.5 - FF 

just download the package

unarchive it and rename it firefox35 (or whatever) and copy the folder to
/home/foo_user/.mozilla/

in this diretory (hidden) you will find the default firefox folder

enter the firefox35 folder and find a file called firefox - click this and say run app (or run in terminal) this will launch firefox 3.5

However if you press the default firefox icon it will revert to the already installed firefox

so what i have done is made shortcuts to the new firefox (icon and all) and replaced it everywhere (desktop and top menu panel) and now this runs well

ram


To see hidden folders press ctrl+h in your home folder and all the . folders and files will become visible

---

### Post by vinutux on 2009-07-15
> **danielrmt said:**
> That's a known issue with the user agent. To fix it, open about:config, and search for general.useragent.extra.firefox and replace Shiretoko for Firefox.

Thanks....

---

### Post by binbash on 2009-07-15
> **RATM_Owns said:**
> Ubuntu still has 3.0.11 by default?

I got 3.5 the day it came out from my `pacman -Syu`.

Yes and it was on gentoo portage hours ago before arch linux.WTF? these arch users are killing me.

---

### Post by vinutux on 2009-07-15
> **binbash said:**
> Yes and it was on gentoo portage hours ago before arch linux.WTF? these arch users are killing me.


ubuntu ppa have it ...as soon as come out ...but called shiretoko instead FF

---

### Post by ThisEndlessFall on 2009-07-15
> **steveneddy said:**
> Try looking at applications --> internet --> shiretoko

I have tried Shiretoko, but I am somewhat of a perfectionist. I want the Firefox branding with the browser. 

Sad but true.

---

### Post by suresnjain on 2009-07-15
> **danielrmt said:**
> That's a known issue with the user agent. To fix it, open about:config, and search for general.useragent.extra.firefox and replace Shiretoko for Firefox.

my shiretoko works fine but two or three  irritants.(1)-daily update and hence daily new build-today I have build 20090714162348.(2)All extensions/add-ons work, but once something downloaded,and you try to view the same by directly clicking on the same in the download list,it would not open,for the simple reason that the default browser is firefox 3.1, while this one is Shiretoko.So, you are forced to go the folder concerned and open it with firefox 3.1.  my question is -would changin the user agnet in Shiretoko to firefox 3.5,would solve this?,

---

### Post by vinutux on 2009-07-15
> **suresnjain said:**
> my shiretoko works fine but two or three  irritants.(1)-daily update and hence daily new build-today I have build 20090714162348.(2)All extensions/add-ons work, but once something downloaded,and you try to view the same by directly clicking on the same in the download list,it would not open,for the simple reason that the default browser is firefox 3.1, while this one is Shiretoko.So, you are forced to go the folder concerned and open it with firefox 3.1.  my question is -would changin the user agnet in Shiretoko to firefox 3.5,would solve this?,

No user agent tells to web which browser are u using....

U can fix it easily 
[B][COLOR="DarkGreen"]
System->preferences->Preferred Applications[/COLOR][/B]

set we browser **custom** adn in command paste this value **[COLOR="Red"]firefox-3.5 %u[/COLOR]**

.

---

