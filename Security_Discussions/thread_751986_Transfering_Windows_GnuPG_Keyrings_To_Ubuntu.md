---
title: "Transfering Windows GnuPG Keyrings To Ubuntu"
date: 2008-04-11
forum: Security Discussions
---

### Post by Johnnny on 2008-04-11
Hope I posted this in the right place. Anyway I need little help.....I use GnuPG/Thunderbird/Enigmail in windows xp but now I'm dual-booting with Ubuntu and I want to know if there is a way to transfer my keyrings(private/public keys and revocation cert.) from windows to Ubuntu?

If so where can I store my keys in ubuntu?

I have just got done setting up Thunderbird and Enigmail. I have noticed that GnuPG was installed by default in Ubuntu and it's currently in version 1.4.6(hope it's not outdated). Only thing now is I want to transfer my keys from Windows to Ubuntu, but not sure how. Thanks for your time.

gnight :)=

---

### Post by hyper_ch on 2008-04-11
they keys in ubuntu are stored in ~/.gnupg

not sure how windows stores them but you should be able to copy them over (and chown/chmod accordingly)

---

### Post by Johnnny on 2008-04-11
Hi,

Thanks for that I got it solved. Now I'm looking to update my version of GnuPG. It is currently in version 1.4.6 and looking at the official page the newest version is at 1.4.9. Is there a way that I can update it by way of Synaptic or in Add/remove?
```
http://gnupg.org/download/index.en.html
```

---

### Post by hyper_ch on 2008-04-11
upgrade your ubuntu installation.... is there anything that 1.4.9 offers which is not offered by 1.4.6?

---

### Post by Johnnny on 2008-04-11
Upgrade Ubuntu installation....,I'm using latest version 7.10 and by default GnuPG is installed at 1.4.6. I did in fact checked for updates in the Update Manager, but nothing was found. As for your question, I have no idea what 1.4.9 offers, all I know is that it's the latest version and I'm behind. 

How are applications/softwares updates handled in Ubuntu?

Does the Update Manager check for "All" application/softwares pre-installed for updates? In this case for example, gnupg, firefox, etc....Or do I have to manually update them myself?

---

### Post by hyper_ch on 2008-04-12
> **Johnnny said:**
> How are applications/softwares updates handled in Ubuntu?

See, that's the whole issue here

Ubuntu has a release cycle of 6 months and upon each release the software "number" will be frozen. Only bug fixes and security fixes will be released.

whatever you install from the repos will be auto-updated for bug fixes and security issues.. all the stuff you install manually you'll have to update manually.

But tell me, if you have no clue what changed from 6 to 9, why do you want to update?

---

### Post by Johnnny on 2008-04-12
> whatever you install from the repos will be auto-updated for bug fixes and security issues.. all the stuff you install manually you'll have to update manually.
Hmm, that's good to know. I didn't install GnuPG from the repos, it came with my version of Ubuntu by default. I tried to check for updates in the update manager but there was none, so I'm guessing it's safe to say that updating my current version is not necessary. But I'll look more into it and see where it goes. 

This is off topic but.....I recently heard from Enigmail that Ubuntu reconfigured and installed there own version of GnuPG and Enigmail, that's why I see a few people having minor errors and problems with encryption and decryption. The installation folders and readme files were all in different directories and they did not match the official installations. That's just what I heard.
> But tell me, if you have no clue what changed from 6 to 9, why do you want to update?
I feel the need to stay updated. Usually newer versions have new stuff and fixes. I assume that it includes minor bug fix and possible security patches. I haven't yet really looked through the changes between 6 and 9, but as usual staying up to date is most important, just hope there's no draw backs to it.

---

### Post by hyper_ch on 2008-04-12
> **Johnnny said:**
> Hmm, that's good to know. I didn't install GnuPG from the repos, it came with my version of Ubuntu by default.
that's the same as installing from the repos :)

And bugfixes/security fixes will be provided for your version through the normal update service through apt (synaptic, apt-get, adept, aptitude...)

---

