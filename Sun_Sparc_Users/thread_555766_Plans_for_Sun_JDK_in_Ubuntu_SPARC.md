---
title: "Plans for Sun JDK in Ubuntu SPARC"
date: 2007-09-20
forum: Sun Sparc Users
---

### Post by calenti on 2007-09-20
Hi there...I know there have been a few discussions about JDK support (or lack thereof) on some of the forum posts but those threads that turned up on my search are pretty old. 

I have a Sun Ultra 5 with Feisty SPARC running on it, and I'd really really really like to use it for Seam/JBoss 5 development as part of an open source push to our higher powers. The problem is that there's no JDK 5 or 6 for the SPARC implementation. 

Couple of questions:

1. Isn't it kind of odd that the SPARC port of Ubuntu wouldn't include a JDK? I know that the OS guys and language guys are not as one but it would seem that anyone who'd be doing a port would include some apps like Java to verify their OS build?

2. Are there any plans to include a JDK/JRE in future Ubuntu builds? I know, Blackdown, but Blackdown and gcj are dead and out of date. They were great for their role but we need a going-forward JVM that keeps pace with Sun's current offerings now.

3. Who would develop this port? Is there a mailing list or user group? I am just a corporate bit pusher so I take myself out of the running to port a JVM to SPARC, but someone should be capable of doing it and I'd happy to be a tester. How would I contact such people?

I know - this is free, people are volunteering, why don't I just go buy Microsoft if I want my hand held, RTFM RTFM etc. I am not demanding anything, just asking. Thanks for any non-snippy RTFM-reply help.

---

### Post by netztier on 2007-09-20
> **calenti said:**
>  I have a Sun Ultra 5 with Feisty SPARC running on it, and I'd really really really like to use it for Seam/JBoss 5 development as part of an open source push to our higher powers. The problem is that there's no JDK 5 or 6 for the SPARC implementation. 


I'm not a developper or anything - but I'm kind of fond of the SPARC machines and have a few of my own.

I've also been wondering how long it'd take a Linux/SPARC version of Sun's JRE/JDK to appear, now that Sun is opensourcing Java. I don't know for sure but it might be that not all needed parts of Java are available under GPL.

I think that if ever it is going to come, a sun-java6-bin package will most probably come from "upstream", in extenso from Debian. A superficial Goolge search in that direction didn't yield any promising results, though.

Given the cooperation of Sun that brought forth the support for Ubuntu on the Niagara processors, it might be that Ubuntu might be the first distro to have it - but this is just pure speculation. 

In a nutshell: I don't know any more than you do :-)

best regards

Marc

---

### Post by calenti on 2007-09-25
Thanks for the response, Netzier. I would think there would be a lot more interest in this subject but I guess we're it.

Seems like there's a good argument for converting the old Sun hardware lying around, the stuff that they won't backport Solaris 10 + for, that would benefit from Ubuntu and a standardized, Sun-owned JDK would be a big part of that. But maybe now that it's open-source they're hoping for the community to step up.

I have a dev machine, now all I need is a copy of "Porting JVMs for hackers with delusions of grandeur"...

---

### Post by psychicist on 2007-09-27
First of all I am not a (K)Ubuntu user, even though I have installed it for numerous people. I have Slackware 12.0 running on x86, MIPS and SPARC and run into the same problem that the JDK for Linux/SPARC is stuck at Blackdown's 1.4.1 release. But nowadays most of the code has been released under the GPL v2 license except for some binary plugs that cannot be released because of third party licensed code. If you are a developer you can subscribe to the mailing lists at [http://openjdk.java.net](http://openjdk.java.net), particularly the hotspot-dev list.

If you take a look at the hotspot code you will see that there are directories for os, cpu and os_cpu. Since Solaris and Linux are very much alike the only thing that has to be done is copying the solaris_sparc directory to linux_sparc and making some necessary changes. When you read the mailing list you can see that I have asked for help getting support for Linux/MIPS (which is almost finished by another company) and Linux/SPARC. Sun developers have reacted saying they would like to have Solaris and Linux support consolidated to a unix directory with only the differences in separate directories.

This would make it a lot easier to build up to date JDKs for Linux/SPARC but won't happen very soon. There is a Red Hat initiated project to replace the binary plugs with alternative implementations and stubs that you can find at [http://icedtea.classpath.org](http://icedtea.classpath.org).

---

