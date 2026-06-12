---
title: "Firefox &quot;Stable&quot; -- not so stable"
date: 2010-04-18
forum: Ubuntuzilla
---

### Post by fermulator on 2010-04-18
So the default firefox supplied in the repositories for Ubuntu 9.04 was too old (3.0.X if I recall).  Some applications on the Internet were not working properly, and they required a later version of Firefox.

At this point, I set out on which PPA I should use to acquire the latest STABLE version of Firefox.  I cam across these instructions, and followed them: [http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa.html](http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa.html).

For a while, this worked great.  However, last week (give or take), there was another update in this PPA.  Considering it was the "firefox-stable" branch, I didn't think twice about applying the update.

As it turns out, it did NOT install a stable version -- instead it installed version 3.6.4pre.  It's not even named Firefox anymore (the icon and  names changed in Ubuntu to "Namoroka Web Browser", which is the code name for this next Firefox release.  This version is NOT stable ... crashes going to youtube, going to ubuntu geek website, sometimes on facebook.  Just terrible.

What the heck is the deal with this.  Which PPA are people supposed to use to acquire the latest STABLE version of Firefox?

**_The Big Question:_**  Which PPA are people supposed to use in order to get th latest stable version of firefox, without being fed this "pre release" junk?

NOTE:  Ubuntuzilla might be an option, but I need to run the older version of Thunderbird (2.X) still, so that's why I've been holding off.

---

### Post by nanotube on 2010-04-18
Hi,

If your issue is with the firefox-stable repository, suggest you post a question to the general section, rather than the ubuntuzilla subforum.

As to ubuntuzilla - you don't have to upgrade thunderbird if you don't want to. you can pick and choose which applications you install from ubuntuzilla. Since all packages are named '$package-mozilla-build', you don't get forced upgrades of everything, when you add the ubuntuzilla repo, only what you choose to install and follow.

(And yes, if you're on 32bit, i do think ubuntuzilla a good option. But i may be biased :) )

---

### Post by fermulator on 2010-04-18
Thanks! -- yep -- well, I just switched to using the ubuntuzilla installation for Firefox, and it's version 3.6.3, is stable.

---

### Post by nanotube on 2010-04-19
> **fermulator said:**
> Thanks! -- yep -- well, I just switched to using the ubuntuzilla installation for Firefox, and it's version 3.6.3, is stable.

nice :)

---

### Post by blue_bullet on 2010-04-19
Same problem here.  All the antics caused me to switch over to try Opera.  It seems equivalent to firefox w/o all the junk and confusion.:)

---

### Post by nanotube on 2010-04-19
> **blue_bullet said:**
> Same problem here.  All the antics caused me to switch over to try Opera.  It seems equivalent to firefox w/o all the junk and confusion.:)

well, if you just stick with the official mozilla releases (either manually, or through the ubuntuzilla repository), you shouldn't have such problems... that said, if opera makes you happy, go for it. :)

---

### Post by fermulator on 2010-04-20
Whoops!  Well I discovered my problem.  Was a user mis-understanding.

As it turns out, I did have the mozilla-daily PPA in my apt-sources list files, but I just didn't realize it:

```
sources.list.d/thunderbird.list:1:deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
sources.list.d/thunderbird.list:2:deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
```

As you can see, it was my intention to try out the latest release of thunderbird3, and to do this, I added the above source-list file.  What is clear now, but not clear then, was that this would also force the updating of my Firefox installation.

There is discussion in the IRC channel on splitting the TB and FF PPAs in the future to avoid this sort of problem and mis-understanding.

---

### Post by fermulator on 2010-04-24
I'm running 3.6.3, this appears to be the current stable release (as of 2010-04-24).

---

