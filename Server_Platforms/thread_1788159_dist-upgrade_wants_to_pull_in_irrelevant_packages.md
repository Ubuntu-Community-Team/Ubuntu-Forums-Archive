---
title: "dist-upgrade wants to pull in irrelevant packages"
date: 2011-06-22
forum: Server Platforms
---

### Post by georgek on 2011-06-22
I've been running an overnight cron job for months on my servers which tells me what apt-get dist-upgrade wants to do.

This morning I was faced with it wanting to install 115 new packages including many (if not all - I can't face checking, e.g. firefox) which are entirely pointless on a server with no gui.

apt-get upgrade wants to do the sensible (in my mind) thing.

To save anyone asking, I've been using dist-upgrade because upgrade wouldn't report on pending kernel upgrades and, until I spotted that, I was due kernel upgrades for quite a while before I realised.

I presume this is caused by an over-enthusiastic depends or recommends somewhere but does anyone actually know?

Off to work now but I'll look further this evening so any pointers before then gratefully received.

All ok again now, the bug with language pack dependencies has been fixed - [https://bugs.launchpad.net/bugs/800857]("https://bugs.launchpad.net/bugs/800857")

---

### Post by Alfafa on 2011-06-22
Hi

I had the same problem. It seems it is language-pack-en-base which have a recommend on firefox-locale-en which depends on firefox

I cannot find a reasonable reverse dependencie on either language-pack-en-base or language-pack-en

So I don't know why these packages is installed at all on my machine, but removing them helps :)

---

### Post by Alfafa on 2011-06-22
and then run locale-gen or I got problems when running perl about falling back to the C locale

---

### Post by mistamidget on 2011-06-22
I think language-pack-en-base might be installed by squirrelmail.
Do you have squirrelmail installed?
Removing language-pack-en-base fixes the problem as Alfafa suggests and doesn't break squirrelmail.
Has anyone installed all of the selected packages to see what, if any, of a mess it makes?

---

### Post by ttusi on 2011-06-23
Thank you, I had some problem and solved.
Can you tell me, how you found it? 
When apt upgrade want install the full X server, which package depends it?
Thanks again.

---

### Post by mistamidget on 2011-06-23
Alfafa found it. As he mentioned it is because "language-pack-en-base which have a recommend on firefox-locale-en which depends on firefox" and to install firefox the xserver is required.
Looking at one of my servers just now the problem seems to be fixed as it is not exhibiting the same problem trying to load firefox when checking for updates in aptitude.

---

