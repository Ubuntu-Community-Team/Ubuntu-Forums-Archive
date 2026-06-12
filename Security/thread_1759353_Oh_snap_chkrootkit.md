---
title: "Oh snap chkrootkit"
date: 2011-05-15
forum: Security
---

### Post by ubunnut on 2011-05-15
Hallo Forum,

i wanted to doenload ia32libs from packaes.ubuntu.com but i was in hurry and typed packages.ubunut.com. I download and installed the package and did a chkrootkit scan.
The page looks exactly like the original!!!!


It sayes that i have a LKM trojan installed.

Be carefull !!!!!!!!!!!!!!!!!!!

with kind regards 
ubunut

---

### Post by uRock on 2011-05-15
There's no such site.

---

### Post by Joe of loath on 2011-05-15
chrootkit occasionally comes up with false positives. It's meant for servers that are rarely updated, not regularly updated desktops.

---

### Post by Thewhistlingwind on 2011-05-15
> **Joe of loath said:**
> chrootkit occasionally comes up with false positives.

More like always, CHrootkit is infamous for it's level of "If it moves it's hostile.".

> **uRock said:**
> There's no such site.

+1 I got a search results page.

---

### Post by ubunnut on 2011-05-15
The page name is packages.ubunut.com but it seems to be in the same subnet like packages.ubuntu.com. 

I started with the live DVD 10.10 Desktop 64 bit.

I just downloades ia32lib packages and avira antivir and i got a lkm torjan detection. Then I did a reboot and booted into the live dvd again, installed chkrootkit and no trojan was found.

strange thing.

---

### Post by CandidMan on 2011-05-15
Am able to reach this site here [http://packages.ubunut.com/](http://packages.ubunut.com/)

---

### Post by tgm4883 on 2011-05-15
> **ubunnut said:**
> The page name is packages.ubunut.com but it seems to be in the same subnet like packages.ubuntu.com. 

I started with the live DVD 10.10 Desktop 64 bit.

I just downloades ia32lib packages and avira antivir and i got a lkm torjan detection. Then I did a reboot and booted into the live dvd again, installed chkrootkit and no trojan was found.

strange thing.

So registration says it's owned by the same guy that owns Ubuntu.com. Out of curiosity, I downloaded the package that you say is malicious and checked the md5sum on it. The package is identical to the one at packages.ubuntu.com.

I recommend changing the title of this thread, as it seems to be completely false/FUD.

---

### Post by Dave_L on 2011-05-15
packages.ubunut.com seems to have the same IP address (91.189.94.219) as packages.ubuntu.com

---

### Post by ubunnut on 2011-05-15
Okay, thanks for help. Seems that i got a false positive from chkrootkit. 
 I ran the live DVD ubuntu 10.10. 64 bit. I installed only the ia32lib package, avira antivir and chkrootkit. Then i got the false chkrootkit result.
After a reboot, booting into the dvd, no trojan was there anymore.

with kind regards
ubunut

---

### Post by uRock on 2011-05-15
Changed the title & marked as solved. 

This is one of the reason I gave up on using chkrootkit. It shows too many false positives.

I am glad it is the same IP as the Ubuntu Package site and that there was no harm to your system. :P

Cheers & Beers,
uRock

---

