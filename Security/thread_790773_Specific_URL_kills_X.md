---
title: "Specific URL kills X"
date: 2008-05-11
forum: Security
---

### Post by jsgarvin on 2008-05-11
I have no idea what's causing this, but when I try to go to a specific URL in FireFox, X restarts (just as if I'd hit CTRL-ALT-Backspace).  All I can guess is that there's something on the page that's causing FireFox to panic and the problem is bubbling all the way up to Gnome. Here's the Details

OS: Ubuntu 8.04 (clean install a couple weeks ago and all updates applied)

Browser String: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5

URL: [http://whynotwiki.com/Rails](http://whynotwiki.com/Rails)  <-- [COLOR="Red"]_**** DO NOT CLICK UNLESS YOU'RE PREPARED FOR THE CONSEQUENCES DESCRIBED ABOVE! ****_[/COLOR]

Anybody care to volunteer to try and confirm if this is just me or if it happens to you too?

---

### Post by brian_p on 2008-05-11
> **jsgarvin said:**
> I have no idea what's causing this, but when I try to go to a specific URL in FireFox, X restarts (just as if I'd hit CTRL-ALT-Backspace).  All I can guess is that there's something on the page that's causing FireFox to panic and the problem is bubbling all the way up to Gnome. Here's the Details

OS: Ubuntu 8.04 (clean install a couple weeks ago and all updates applied)

Browser String: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5

URL: [http://whynotwiki.com/Rails](http://whynotwiki.com/Rails)  <-- [COLOR="Red"]_**** DO NOT CLICK UNLESS YOU'RE PREPARED FOR THE CONSEQUENCES DESCRIBED ABOVE! ****_[/COLOR]

Anybody care to volunteer to try and confirm if this is just me or if it happens to you too?

Doesn't happen to me with iceweasel.

---

### Post by Patb on 2008-05-11
It opens okay in Firefox 2.0.0.14 but it sends my cpu up to 100%.  It seems to automatically start a program called whiptail which then continues and hogs the cpu, even after I kill Firefox (PS: only did this the first time I opened it).  

Also opens okay in Opera 9.25 but hogs the cpu for about 30 seconds.  

Several forum sites occasionally and temporarily hog my cpu, include certain pages on Ubuntu Forums.  I don't know why.  It is less of a problem in Opera.  Does anyone have suggestions?  

Cheers, Pat.

PS: To answer Tyler, I have Adblock Plus 0.7.5.3 running.  Disabling it does not reduce temporary hogging of the cpu.

---

### Post by tylermoody on 2008-05-11
This isn't doing anything for me either, I'm running Firefox beta 3, 8.04, on a macbook. I'm not getting any CPU hogging, either.  

Do you have any FF addons installed? Have you looked at other Mediawiki pages without this happening?

---

### Post by Dr Small on 2008-05-11
It ran my CPU usage up, but only breifly and locked up firefox like normal big pages do. I am running Arch Linux (2.6.24 Kernel).

---

### Post by jsgarvin on 2008-05-12
> **tylermoody said:**
> Do you have any FF addons installed? Have you looked at other Mediawiki pages without this happening?

I do have several addons, and should have thought earlier that one of them might be the culprit. However, after disabling all of them (including the Ubuntu Modifications one) the same thing still happens.  I also had the idea to disable Compiz and see if that had any effect (it didn't).

Yes, other mediawiki pages work fine for me, and I've never had any issue with unusually large pages before either.

---

### Post by Oldsoldier2003 on 2008-05-12
no isses at all with ff3B5. the page took a moment to load but nothing ununusal.

---

### Post by yomaoni on 2008-05-15
I tried it on my system (8.04 with FF 3.0b5) no problems cpu doesn't go over 5% overall.  I also have compiz enabled with an nvidia card.  Hope this helps.

---

### Post by yussri on 2008-05-15
nothing unusual (ubuntu 8.4 firefox 3.0 b5 ) here too , it only  takes sometime to load , I suggest you run firefox from terminal and see what you get .


I had have some issues similar to that before but then it was a flash problem

---

### Post by BlueSkyNIS on 2008-05-15
Nothing unusual here either (8.04 ff 3.0b5), it took ages to load though. CPU usage was small.

EDIT: It looks like this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/212648]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/212648")

Others experience:
[http://ubuntuforums.org/showthread.php?t=746777]("http://ubuntuforums.org/showthread.php?t=746777")

Are you using nvidia graphics?

---

### Post by jsgarvin on 2008-05-15
> **BlueSkyNIS said:**
> EDIT: It looks like this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/212648]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/212648")

Others experience:
[http://ubuntuforums.org/showthread.php?t=746777]("http://ubuntuforums.org/showthread.php?t=746777")

Are you using nvidia graphics?


Bullseye!  Yup, that's me, too.  Thanks.  Good to know it's on the radar. Thanks for hunting that down.

---

