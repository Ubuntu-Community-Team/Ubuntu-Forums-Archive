---
title: "Backport: bittornado 0.3.10-3"
date: 2005-04-08
forum: Ubuntu Backports
---

### Post by jdong on 2005-04-08
The current Hoary Bittornado doesn't work. I though we should try a newer version from Sid.

Rev 115

---

### Post by poofyhairguy on 2005-04-11
[QUOTE=jdong]The current Hoary Bittornado doesn't work. I though we should try a newer version from Sid.

Rev 115[/QUOTE]

Thanks Jdong. I'll try this out tonight and tell you how it goes.

---

### Post by jdong on 2005-04-11
ok, I've downloaded Kanotix and Hoary through this client, and it works quite well. If you come back with good things, I'll mark it stable. :)

---

### Post by poofyhairguy on 2005-04-12
Hey this works really good. Thanks a bunch. Mark it stable.

Heck, offer it to the MOU.

Thanks again, BitTornado is the reason I abondoned Fedora for Ubuntu (stupid reason then, but it worked out).

---

### Post by poofyhairguy on 2005-04-12
Ok. This might seem weird. But thanks again jdong. I used it again, and it works better than Warty's for me. 

You are my hero. Even though my broadband provider might think otherwise....

---

### Post by PeteG on 2005-04-15
Hi,

I'd really love to use Bittornado on my linux box however i can't get it to install. It just tells me that package can't be found however i've added the backports to the sources list. I sudo apt-get install bittornado and it just says the package cannot be found. Something i'm doing wrong here?

Pete.

---

### Post by poofyhairguy on 2005-04-15
[QUOTE=PeteG]Hi,

I'd really love to use Bittornado on my linux box however i can't get it to install. It just tells me that package can't be found however i've added the backports to the sources list. I sudo apt-get install bittornado and it just says the package cannot be found. Something i'm doing wrong here?

Pete.[/QUOTE]

its in staging now. 

hoary-backports-staging

---

### Post by PeteG on 2005-04-15
So i'd just add staging to the sources list. e.g. deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted staging?

While i was waiting i actually downloaded the .deb files for it (i'm pretty sure i found them), but when installing the GUI it wanted to libwxgtk2.4-python package. I apt-get install libwxgtk2.4-python and it says it isn't available. Sorry if these questions are really newb, i'm really new to linux.

Pete.

---

### Post by poofyhairguy on 2005-04-15
[QUOTE=PeteG]So i'd just add staging to the sources list. e.g. deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted staging?

While i was waiting i actually downloaded the .deb files for it (i'm pretty sure i found them), but when installing the GUI it wanted to libwxgtk2.4-python package. I apt-get install libwxgtk2.4-python and it says it isn't available. Sorry if these questions are really newb, i'm really new to linux.

Pete.[/QUOTE]


No, the line would be:

[http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports-staging main universe multiverse restricted


add it after backports. No big deal. It worth a few questions to get it right.

---

### Post by jdong on 2005-04-15
Just in case poofyhairguy didn't make it clear enough, -staging is a complimentary branch to hoary-backports. Some stuff won't work if you don't have hoary-backports enabled at the minimum.

Also, you need Hoary's "universe" repositories enabled.

---

