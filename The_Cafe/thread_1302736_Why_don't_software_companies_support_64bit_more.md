---
title: "Why don't software companies support 64bit more?"
date: 2009-10-27
forum: The Cafe
---

### Post by dj-toonz on 2009-10-27
Hi all, it's got me puzzled this as me & a friend were going on about it all over the weekend & still puzzled. Take Renoise for example (a 32bit application) not x64, Yes I know you can force install it by using the 32bit libs, but then the VST plugins don't work :( as there x64. you email the companys to ask why they don't support linux x64 over x32 (not worth it) bull when they can make the same software for windows x64 lol (just might aswell stick with x32 & a server kernel to get over the ram limit) is it just me who feels that x64 should be supported more in software ?

---

### Post by Icehuck on 2009-10-27
Why write two versions of software when you can write 32 bit software and it will run on both?

---

### Post by dj-toonz on 2009-10-27
As I said you can by force installing it to use the 32bit Libs in Linux but then the Native plugins for example won't work as there x64bit, but the companys make the same software under windows a 32bit version & a x64 bit version for xp x64 vista x64 & now windows 7 x64 so why not Linux x64 so everything plays ball. what I mean by that. if you want to run a program under Ubuntu x64, some programs you have to do a force install of them by using lib32 libs,that's why I can't use Renoise under Ubuntu because of the problem (but I can under windows xp x64 because it's got a x64 bit version of the software, that's what's getting to me :(

---

### Post by Tibuda on 2009-10-27
> **Icehuck said:**
> Why write two versions of software when you can write 32 bit software and it will run on both?

Actually you only write one version, but compile it twice. And there are good reasons for it: better performance and the [2038 year problem]("http://en.wikipedia.org/wiki/Year_2038_problem").

---

### Post by sanderj on 2009-10-27
<Disclaimer: I don't know renoise nor VST. I'm just a 64-bit Ubuntu user.>


Yes, more 64-bit would be great. However, a company has to assign it's resources on it's highest prio cases.

Information on your specific remarks:
[http://www.renoise.com/board/index.php?showtopic=15213&st=0](http://www.renoise.com/board/index.php?showtopic=15213&st=0) seems to have useful info for you:
- 32-bit renoise should run on 64-bit Linux. VST plugins are not mentioned, but if that does not work (and it should), I think you can get support in that forum. And/or do you know [http://www.breakfastquay.com/dssi-vst/](http://www.breakfastquay.com/dssi-vst/) stating "dssi-vst can also be used to run 32-bit Windows VST plugins in a 64-bit Linux host."
- a 64-bit renoise version is going to be made

FWIW: [http://www.renoise.com/download/requirements/](http://www.renoise.com/download/requirements/) does NOT show a 64-bit Windows version.

FWIW2: the real solution is Open Source Software. With OSS, you're not dependent on software companies not willing or able to write 64-bit software at the moment you want it. So you could look for an OSS variant of renoise if the above information does not work for you.

HTH

---

### Post by coldReactive on 2009-10-27
> **Icehuck said:**
> Why write two versions of software when you can write 32 bit software and it will run on both?

32-bit deb packages don't even install on 64-bit debian/ubuntu

---

