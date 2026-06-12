---
title: "Wine PPA Karmic 64-bit"
date: 2009-12-17
forum: Wine
---

### Post by darkhammer8108 on 2009-12-17
I have been searching for a while and i cant seem to find anything about this. I have a karmic 64-bit installation and i installed the Wine PPA. when i go to mark wine it tells me that i have a dependency missing and says
Wine1.2:
and then its just blank after that. its been like this for a long while now and i was wondering if the problem might be on my end or if there is a way to get the latest wine for karmic 64-bit installed from the wine PPA

---

### Post by beastrace91 on 2009-12-17
I'd like to know this as well. The new PPA system seems to be a bit messy in regards to Wine since they have added the "wine1.2" package into the default 9.10 repos.

For now I have just installed Wine from source on my Karmic 64bit system.

Regards,
~Jeff

---

### Post by darkhammer8108 on 2009-12-17
i suppose i can always run 1.0.1 that ships with karmic. but this build has been like this for a very long time. it would be nice to get 1.1.34 (1.2) from the ppa though

---

### Post by Soulcage on 2009-12-18
sudo apt-get install wine1.2 into a terminal after adding ppa:ubuntu-wine/ppa to software sources' "Other Software" tab.

---

### Post by beastrace91 on 2009-12-18
> **Soulcage said:**
> sudo apt-get install wine1.2 into a terminal after adding ppa:ubuntu-wine/ppa to software sources' "Other Software" tab.

I'll give that a go... For now I just compiled it from source.

~Jeff

---

### Post by YokoZar on 2009-12-19
> **darkhammer8108 said:**
> I have been searching for a while and i cant seem to find anything about this. I have a karmic 64-bit installation and i installed the Wine PPA. when i go to mark wine it tells me that i have a dependency missing and says
Wine1.2:
and then its just blank after that. its been like this for a long while now and i was wondering if the problem might be on my end or if there is a way to get the latest wine for karmic 64-bit installed from the wine PPA
Are you marking Wine inside Software Center?

Try marking the other one: Wine (Beta Release)

This is a bit confusing as there's a bug in software center that gives them both the same icon.

Alternatively checking the "wine1.2" package in Synaptic should work.

I'm pretty sure this only happens if you install the (default Karmic) wine 1.0.1 package and then add the PPA.

---

