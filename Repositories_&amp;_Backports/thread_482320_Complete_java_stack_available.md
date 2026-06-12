---
title: "Complete java stack available ?"
date: 2007-06-23
forum: Repositories &amp; Backports
---

### Post by jnorthr on 2007-06-23
This link : [http://linuxplanet.com/linuxplanet/newss/6380/1/](http://linuxplanet.com/linuxplanet/newss/6380/1/) [http://linuxplanet.com/linuxplanet/newss/6380/1/]("http://linuxplanet.com/linuxplanet/newss/6380/1/") made me think there may be a complete stack of java apps in a respository somewhere but i can't find it. Anyone  know where it is ?
ta

---

### Post by GNUtoo on 2007-09-03
themain ubuntu java stack's name is GCJ(GNU compiler for java)
for instance if you install eclipse-sdk you'll see that it use that.

basicaly you have several implementations of java(don't knoz wich ones are in ubuntu but GCJ is and iced isn't):
->openjdk -> 4% non free
->classpath/GCJ ->100%free
->blackdown ->comming with source code but not free
->icedtea ->100% free but sun has forgetten to add the gpl on several files so unless it is resolved you will have to build it yourself and it won't be included in ubuntu

what's icedtea? simply it's openjdk with code from classpath/GCJ to fill the gaps of the 4%


by the way i mean free as in freedom

---

### Post by jamesstansell on 2007-09-08
The article referenced by the original post was referring to the multiverse repository in ubuntu 7.04 (feisty fawn.)  The package names of interest are glassfish and netbeans5.5.  (Note that the netbeans package has special instructions in the description.)

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) is one of several instructions for enabling the multiverse repository.

Regarding open-source java the future is a little murky right now.  Experimental icedtea packages are available, but will not be included in 7.10 (gutsy gibbon.)  Personally at this point I wouldn't bet on inclusion even in 8.04 (hardy heron.)  Java 7 is still very much in flux.  Sun is planning to release an open-source version of Java 6, which could conceivably come out before Java 7 is released.  But unless they make use of the icedtea work it won't be fully usable.  (Note: I'm not talking about the multiverse sun-java6 package - that's fully sun blessed, but not open source.  I'm talking about a sun java 6 package that could ship in main or universe.)

The blackdown project shut down recently.  I'd just like to take a few extra keystrokes to thank them for leading the way to Java on Linux.

That leaves the classpath-based projects like kaffe, gcj, jamvm, cacao and sablevm.  These packages are available in the main and universe repositories and generally work very well, although there are issue with some applications.  (And of course they don't carry Sun's stamp of approval at all.)

I asked recently in #ubuntu-java IRC freenode and was told to keep an eye on the debian bug tracking system in order to know what would be happening with java in ubuntu.

Regards,

-james.

---

