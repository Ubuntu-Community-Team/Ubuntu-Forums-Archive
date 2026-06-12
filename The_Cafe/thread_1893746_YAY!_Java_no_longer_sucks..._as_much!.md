---
title: "YAY! Java no longer sucks... as much!"
date: 2011-12-11
forum: The Cafe
---

### Post by Primefalcon on 2011-12-11
Since Java is no longer included in the Ubuntu repo's due to the change is Java's licence and I needed the latest version and had to manually install anyhow, I took the opportunity to install the latest V7 release.

And finally I don't don't to use the pulseaudio wrapper for it.... it uses pulse audio by default now! YAY!!!!!

---

### Post by FuturePilot on 2011-12-11
I've never had an issue with PulseAudio and Java. ***shrug***

---

### Post by Primefalcon on 2011-12-11
> **FuturePilot said:**
> I've never had an issue with PulseAudio and Java. ***shrug***
ever played a heavy java game like runescape?

---

### Post by FuturePilot on 2011-12-11
> **Primefalcon said:**
> ever played a heavy java game like runescape?

Minecraft. Never had an issue with sound.

---

### Post by kostkon on 2011-12-11
OpenJDK works fine with PulseAudio, Sun Java didn't or still doesn't, I am not sure.

---

### Post by Primefalcon on 2011-12-11
OpenJDK tends to be overly laggy for me, were as Sun Java isn't so... I honestly would prefer to use OpenJDK since I loathe Oracle... however I love Runescape too much....

Sun Java 6 (current stable) does not work with Pulseaudio 
Sun Java 7 (beta) does work perfectly with Pulseaudio

You can use the pulseaudip wrapper or padp make anything go through pulseaudio however it is kind of a hack....  Actually for reference I'll just explain it for the people who don't know how to do it....

Since you locate for example where the Java Executable is (easier if you manually installed it since well it's wherever you extracted it to....)and basically rename it to say... java.bin instead of java

and then create another executable text file there called java and simply have the following

```

#!/bin/bash
padp "/location/to/java/executable" "$@"

```

However once version 7 is released proper this hack will no longer be necessary, however Wine still needs it :-(

---

### Post by Dragonbite on 2011-12-12
Isn't Oracle trying to force people to use (and improve where it lacks) OpenJDK instead of their Java?

---

### Post by Kimm on 2011-12-12
> **Primefalcon said:**
> However once version 7 is released proper this hack will no longer be necessary, however Wine still needs it :-(

Usually its not necessary for wine either! if you install pulseaudio-esound-compat (PulseAudio ESD compatibility layer) and configure wine to use ESD instead of Alsa, wine will use PulseAudio.

---

### Post by BrokenKingpin on 2011-12-12
hmmm, can't remember the last time I used a Java application. Not that I have anything against Java or avoid Java applications, I guess I just haven't come across one lately that I need to use.

---

### Post by Roasted on 2011-12-12
> **Dragonbite said:**
> Isn't Oracle trying to force people to use (and improve where it lacks) OpenJDK instead of their Java?

Really? Why would they do that? Are they wanting to get people on OpenJDK to someday offload Java??

---

### Post by Dragonbite on 2011-12-13
> **Roasted said:**
> Really? Why would they do that? Are they wanting to get people on OpenJDK to someday offload Java??

Ok, I may have misread the article: [_Oracle retires licence for distributing its Java with Linux_]("http://www.h-online.com/open/news/item/Oracle-retires-licence-for-distributing-its-Java-with-Linux-1332835.html").

> Ledru noted that some packages are hardwired to depend on the Oracle binary release and that there are still some issues with fonts, applets and support from other software developers for OpenJDK; he asked that users report OpenJDK-only problems so that they can be fixed upstream and bring the OpenJDK packages up to the quality of the Oracle JDK. 

I think I first read that differently.  Sorry for the confusion.

---

### Post by craig10x on 2011-12-13
They are right about that...i have a program in fact that works perfectly in Oracle java 6 (the licensed version) and does NOT work properly in Oracle Open JDK 6 or 7 for that matter...

So they are not identical at this point as some java programs will not work in the open version..They really do need to get it on par with the license version...especially now that ubuntu is no longer offering the licensed version in their repos...

And if you want to get it from Oracle's site it's a pain in the neck...no deb file...has to be installed manually...

---

### Post by Primefalcon on 2011-12-13
> **craig10x said:**
> And if you want to get it from Oracle's site it's a pain in the neck...no deb file...has to be installed manually...
On the plus side there are a lot of easy walkthroughs around that will do it.

I'd advise though that if you do a manual install, set it up in a version independent folder name such as java_custom rather than 1.7 or 1.6.29 so that to update in the future all you have to do is extract the files to there.... saves a lot of future hassle.

BTW does the licence  change mean that no one can provide a deb file?

---

### Post by Roasted on 2011-12-13
Sigh. Oracle just really needs to stop.

---

### Post by BrokenKingpin on 2011-12-13
> **craig10x said:**
> They are right about that...i have a program in fact that works perfectly in Oracle java 6 (the licensed version) and does NOT work properly in Oracle Open JDK 6 or 7 for that matter...

Have you investigates why? Is this an application you are developing? If so maybe you can update it to workaround the issue so it works with both SDKs.

---

### Post by BrokenKingpin on 2011-12-13
> **craig10x said:**
> They are right about that...i have a program in fact that works perfectly in Oracle java 6 (the licensed version) and does NOT work properly in Oracle Open JDK 6 or 7 for that matter...

Have you investigates why? Is this an application you are developing? If so maybe you can update it to workaround the issue so it works with both SDKs. At this point it is probably better to just try and get it working with the open SDK, instead of waiting for it to "catch up".

At the very least open a bug with the open SDK to get the issue resolved.

---

### Post by Primefalcon on 2011-12-13
> **BrokenKingpin said:**
> Have you investigates why? Is this an application you are developing? If so maybe you can update it to workaround the issue so it works with both SDKs. At this point it is probably better to just try and get it working with the open SDK, instead of waiting for it to "catch up".

At the very least open a bug with the open SDK to get the issue resolved.
The openJDK will probably get updated somewhat faster now, what I am wondering though myself is if the oracle licence prohibits a 3rd party from making a .deb file of the oracle java for others to use....

---

