---
title: "Any idea why Ubuntu says https://quality.mozilla.org is unsafe?"
date: 2012-01-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kevpan815 on 2012-01-16
This issue is not new to Ubuntu 12.04 Long Term Support Alpha 1, it has existed in previous versions of Ubuntu for a while now when ever using the Integrated Version of Mozilla Firefox that comes with the Operating System! Just for your information.

---

### Post by kevpan815 on 2012-01-16
> **kevpan815 said:**
> This issue is not new to Ubuntu 12.04 Long Term Support Alpha 1, it has existed in previous versions of Ubuntu for a while now when ever using the Integrated Version of Mozilla Firefox that comes with the Operating System! Just for your information.

Post Script:  I forgot to mention that this issue does not occur in Microsoft Windows or Apple Mac OS X Lion! Only Ubuntu is affected.

---

### Post by cariboo on 2012-01-16
What browser are you using? I just tried the url using chromium-browser, and it works as expected.

---

### Post by kevpan815 on 2012-01-16
> **cariboo907 said:**
> What browser are you using? I just tried the url using chromium-browser, and it works as expected.

As I previously said: It happens when I go there with the Integrated Web Browser that comes with Ubuntu, which in Alpha 1 with no Updates Installed is: Mozilla Firefox 9.0.

I go to that website on a regular basis to re-download the latest Nightly Build of Mozilla Firefox anytime after signing out of the Guest Account.

I currently have no Anti-Virus software installed since Avast for Linux Home Edition only works on X86 Linux and I am using X64 Ubuntu since X86 Ubuntu does not work on my Dell Inspiron 1012 Mini Netbook due to a BIOS Incompatibility Problem (which I  read about on the Ubuntu Wiki).

As a result I have decided to use only the Guest Account when logging in.

---

### Post by cariboo on 2012-01-16
We are at Firefox v10.0 now, so you are a bit behind. so we can't really give you an answer to your question. In the future specify what version of a program you are using, as we have progressed quite a bit since the release of Alpha 1.

I'd really suggest you find a place to download the daily iso, then you won't use up all your bandwidth just to keep up-to-date.

---

### Post by kevpan815 on 2012-01-17
> **cariboo907 said:**
> We are at Firefox v10.0 now, so you are a bit behind. so we can't really give you an answer to your question. In the future specify what version of a program you are using, as we have progressed quite a bit since the release of Alpha 1.

I'd really suggest you find a place to download the daily iso, then you won't use up all your bandwidth just to keep up-to-date.

I have one more problem than just the Bandwidth Issue: Usually whenever the Ubuntu Nightly CD's are Over Sized (like they are right now) they do not work at all on my 2 Dell Computers, even though I always use DVD's instead of CD's, due to the fact that CD's never work on my systems, the DVD's never work when the Disk Images are Over Sized.

By the way, I do not drive anymore, due to my Mental Disorder, it's a long walk to the closest McDonald's, where they recently put up a No Loitering Sign: 30 minute time limit to consume all food and use their free Wifi.

It's an even longer walk to the closest Starbucks where they have no time limit to sit there and use their Wifi as long as you buy their Coffee of the Day for about just over $2.50 when buying their Venti Size, which is a lot more expensive than McDonald's $1 Large Coffee (I am on limited income from Public Assistance).

---

### Post by ranch hand on 2012-01-17
Use zsync and it will only upgrade the parts of the iso image that needs changing.  If you are working with an A1 image this will take a while the first time.  After that you probably could do it at home.

If disks don't work you will need to upgrade what you have.  Do not use Update Mangler.  You have way to much to upgrade for it to handle.  Use apt-get or aptitude.  Synaptic would be the gui choice.

---

### Post by xyzzyman on 2012-01-17
Sorry if you've already researched the option, but a place I'd forgotten about is public libraries. I was in a middle of nowhere town (It did have mcdonalds and a walmart) this past summer walking/hitchhiking from Philadelphia to Syracuse, and the library looked like a converted house, but they had free wifi and air conditioning. They also usually aren't as speed limited as commercial establishments.

Also have you taken a look at using thumb drives to install as opposed to burning? 4GB drives are on sale retail for $10 all the time nowadays, and would just have to skip a few starbucks drinks. (Personally I prefer to use SD cards. You could just always leave it in the media reader slot on your laptop so it's handy as a rescue disk.) 

Otherwise you may want to look at sticking with 12.04 once it's released. 12.10 won't be an LTS so it'll be back to things breaking alot more as opposed to now which has been relatively easy as it's tweaks and optimizations for 12.04. I'll admit that I have a 12.04 installation but I'm in 11.10 90% of the time.

---

### Post by paul_in_london on 2012-01-17
Just tried it on FF nightly (12.0a1 (2012-01-16)) and it's fine.

---

### Post by MacUntu on 2012-01-17
Guess what you are seeing is the warning about unencrypted elements on the site:

[ATTACH]211003[/ATTACH]

That's not an issue with Firefox or Ubuntu.

---

