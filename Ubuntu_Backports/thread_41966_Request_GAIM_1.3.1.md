---
title: "Request GAIM 1.3.1"
date: 2005-06-15
forum: Ubuntu Backports
---

### Post by Kyral on 2005-06-15
I don't know if its elligible for backporting, but if it is could you backport Gaim 1.3.1? Thanks :D

---

### Post by man.life on 2005-06-15
Already backported, but still in staging.  ;-)

---

### Post by Kyral on 2005-06-15
Oh lol, what do I have to add to my sources.list for Staging?

(I'm not afraid of bleeding edge, I was the kinda guy that set ~x86 in Gentoo :P)

---

### Post by christooss on 2005-06-15
[QUOTE=Kyral]Oh lol, what do I have to add to my sources.list for Staging?

(I'm not afraid of bleeding edge, I was the kinda guy that set ~x86 in Gentoo :P)[/QUOTE]
 I think this is enough

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

But my gaim is still 1.3.0

---

### Post by Kyral on 2005-06-15
added that line, updated APT, still no GAIM 1.3.1   :???:

---

### Post by christooss on 2005-06-15
[QUOTE=Kyral]added that line, updated APT, still no GAIM 1.3.1   :???:[/QUOTE]
 I sad that i don't have 1.3.1 gaim jet. I don't know maybe line is not right

---

### Post by Kyral on 2005-06-15
Got it working

You added the Extras Staging, its in the Backports Staging :P Just replace "extras" with "backports"

Oyah, the package works fine! Thanks Backports Team!!!

---

### Post by christooss on 2005-06-15
[QUOTE=Kyral]Got it working

You added the Extras Staging, its in the Backports Staging :P Just replace "extras" with "backports"

Oyah, the package works fine! Thanks Backports Team!!![/QUOTE]
 OK that works perfectly

---

### Post by dlpfmVfH on 2005-06-15
using gaim 1.31 without a problem...even got the event-blinking in taskbar working...
guification also working...so I think it can be promoted....

so everybody can enjoy it. this is my backport sources list:
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports-staging main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras-staging main universe multiverse restricted

hope it helps..

---

### Post by ah.heng on 2005-06-26
sorry but how exactly do you install gaim 1.3.1?

i tried apt-get but it didn't download or install anything, my gaim is still 1.1.4

i downloaded the deb package and tried to dpkg it and got this

```
dpkg: dependency problems prevent configuration of gaim:
 gaim depends on gaim-data (= 1:1.3.1-1~5.04ubp1); however:
  Version of gaim-data on system is 1:1.3.1~5.04ubp1.
dpkg: error processing gaim (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
``` 


or do i already have 1.3.1 just that the version number (from the help button in gaim) did not update?

---

### Post by christooss on 2005-06-26
You have to have this inyour /etc/apt/sources.list

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted

Than

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by virgule on 2005-06-26
my apt-get warned me that packages from this site couldnt not be authenticated.
Why?

---

### Post by CAE on 2005-06-27
[QUOTE=virgule]my apt-get warned me that packages from this site couldnt not be authenticated.
Why?[/QUOTE]

Because the packages are not officially signed. They should be soon, however, with backports becoming an official Ubuntu project. Still, you don't have anything to be worried about.

---

