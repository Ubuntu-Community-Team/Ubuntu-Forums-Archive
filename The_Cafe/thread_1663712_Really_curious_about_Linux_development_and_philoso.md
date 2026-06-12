---
title: "Really curious about Linux development and philosophy"
date: 2011-01-10
forum: The Cafe
---

### Post by asifnaz on 2011-01-10
I am relatively new Linux user (1 year ) . I am amazed by development of Linux . I just want to understand ...

1)Why would one  give his hard work for free 

2)Is there driver for almost all hardware in Linux kernel or "one fits many" method is used .

3)why one would learn how to develop for Linux as there is no monetarily gain involved   .

thank you

---

### Post by Idefix82 on 2011-01-10
I find this question really strange. How is Linux development so different from many other activities that people do without a monetary gain? Do I interpret your question correctly as asking essentially "why would someone spend considerable time and effort on anything that doesn't promise monetary gains"?

If my interpretation of your question is correct, then the answer is "for 1001 reasons". Because it's fun, because it feels good to do something good for others, because it feels good to do something that you believe to be "the right thing", to fight for a just cause, as it were, because it can advance one's career, e.g. it's a great CV booster to be able to point to a successful open source project of yours, for networking, etc., etc. By the way, have I mentioned fun?

If you have never done something for any other reason than to earn money, then it is likely impossible for you to understand why others would. But if you have (which is much more likely), then thinking about **your** reasons for doing it will probably, at least partially, clear up the mystery for you.

---

### Post by asifnaz on 2011-01-10
> **Idefix82 said:**
> I find this question really strange. How is Linux development so different from many other activities that people do without a monetary gain? Do I interpret your question correctly as asking essentially "why would someone spend considerable time and effort on anything that doesn't promise monetary gains"?

If my interpretation of your question is correct, then the answer is "for 1001 reasons". Because it's fun, because it feels good to do something good for others, because it feels good to do something that you believe to be "the right thing", to fight for a just cause, as it were, because it can advance one's career, e.g. it's a great CV booster to be able to point to a successful open source project of yours, for networking, etc., etc. By the way, have I mentioned fun?

If you have never done something for any other reason than to earn money, then it is likely impossible for you to understand why others would. But if you have (which is much more likely), then thinking about **your** reasons for doing it will probably, at least partially, clear up the mystery for you.

Your interpretation is right . I really appreciate the people behind this wonderful project . But I am stunned by the sheer perfection which is required to have an outcome like gnu/Linux .

I do many things for fun and for society as well ( I volunteer for a social service ) but giving your 100s of 1000s lines of codes for free is a big deal

---

### Post by Idefix82 on 2011-01-10
I agree with you that it's a big deal and that those who do it are simply awesome. As to why they do it, I am sure that each one of them has his reasons, which can be a combination of the aforementioned and more.

---

### Post by piquat on 2011-01-10
> **asifnaz said:**
> 3)why one would learn how to develop for Linux as there is no monetarily gain involved .
 
thank you
 
Not sure about developing per se but where I used to work only the desktops were windows, everything else behind the scense was RHEL.  Knowing Linux surely brought "monetary gain" to the techs servicing that equipment.

---

### Post by asifnaz on 2011-01-10
I will appreciate if somebody could answer :

*is there driver for almost all hardware in Linux kernel or "one fits many" method is used*

---

### Post by Paqman on 2011-01-10
> **asifnaz said:**
> 
1)Why would one  give his hard work for free 


Mostly, they don't. The vast majority of work on the core systems are done by paid developers working for one of the big companies that have a stake in the server business (Intel, Red Hat, etc) where Linux is very important. 

A lot of the apps you might use on the desktop are developed substantially by volunteers, but under the hood is developed by the pros.

Generally people create apps because they see a need and want to contribute. The old cliché that devs create the apps they want to use themselves has a certain amount of truth to it.

---

### Post by ssam on 2011-01-10
some people enjoy programming :-)

> **asifnaz said:**
> 
2)Is there driver for almost all hardware in Linux kernel or "one fits 

some things have generic drivers. all USB pen drives follow a standard, so only one driver is needed for them. but each network card would need its own driver.

linux does have the advantage that it can share code among drivers. for example there is lots things that every wireless network card needs to do. they all share this code [http://wireless.kernel.org/en/developers/Documentation/mac80211](http://wireless.kernel.org/en/developers/Documentation/mac80211)

you can see all the drivers in the source code at
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers;h=2a307e81f2bf2b439f084c3875d19361afbe522b;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers;h=2a307e81f2bf2b439f084c3875d19361afbe522b;hb=HEAD)
and a list of the new drivers in linux 2.6.37
[http://kernelnewbies.org/Linux_2_6_37-DriversArch](http://kernelnewbies.org/Linux_2_6_37-DriversArch)

---

### Post by asifnaz on 2011-01-10
> **Paqman said:**
> Mostly, they don't. The vast majority of work on the core systems are done by paid developers working for one of the big companies that have a stake in the server business (Intel, Red Hat, etc) where Linux is very important. 

A lot of the apps you might use on the desktop are developed substantially by volunteers, but under the hood is developed by the pros.

Generally people create apps because they see a need and want to contribute. The old cliché that devs create the apps they want to use themselves has a certain amount of truth to it.

Your answer is quite opposite to what other have said . But you seem right . Hobey devs cant handle sheer amount of work required for a working kernel . 

At some point pros and co.s must be involved .

---

### Post by Spice Weasel on 2011-01-10
> **asifnaz said:**
> Your answer is quite opposite to what other have said . But you seem right . Hobey devs cant handle sheer amount of work required for a working kernel . 

At some point pros and co.s must be involved .

It has been done. ;)

[http://www.menuetos.net/](http://www.menuetos.net/)

---

### Post by disabledaccount on 2011-01-10
Linux drivers are mostly developed for chipsets - this makes sometimes huge difference to windows, where drivers are often written for vendors. This also makes people think that linux uses some kind of "universal" drivers, while the truth is that many devices uses identical HW - 3G/GSM modems, wireless, bluetooth devices, sound cards, etc.
USB is special case - most of devices (like HID, Mass Storage) are included in USB standard and uses universal drivers under all OSes.

---

### Post by Paqman on 2011-01-10
> **asifnaz said:**
> Your answer is quite opposite to what other have said . But you seem right .

People get confused by the licence. They assume that because volunteers CAN inspect the code and write patches, that's how it all happens.

As far as the kernel is concerned it works out as [18% community, 75% corporate, and 7% unknown]("http://apcmag.com/linux-now-75-corporate.htm"). 18% is still a figure to be proud of though, it's equivalent to about US$250 Million of R&D time if it were done commercially. All donated by generous individuals.

---

### Post by 3Miro on 2011-01-10
People that write software for Linux (kernel or otherwise), do this because they want to the have a good working piece of software for themselves (to use for whatever). A single programmer can only do so much, a group of programmers can do a lot. In order to form a community, they have to share their work.

Corporations that write code work much in the same way. It is a huge expense for a corporation to do everything from scratch, so they use the existing programs and simply modify them for their own use. In order to do that, they have to share like everyone else.

For more details, look up Free Software Foundation.

As for the kernel drivers, Linux uses whatever works. Sometimes one driver is used for several devices (if they are similar enough), sometimes the drivers are written with a single specific device in mind.

---

### Post by asifnaz on 2011-01-10
> **3Miro said:**
> People that write software for Linux (kernel or otherwise), do this because they want to the have a good working piece of software for themselves (to use for whatever). A single programmer can only do so much, a group of programmers can do a lot. In order to form a community, they have to share their work.



I am afraid i may not agree . This might be the reason for developing a FOSS in early and mid 90s . But now so many solutions are available other than making/customizing your own software .

I think now people develop for FOSS for fun , personal proud , feel the part of philosophy and community etc

---

### Post by ErikNJ on 2011-01-10
> **asifnaz said:**
> I am afraid i may not agree . This might be the reason for developing a FOSS in early and mid 90s . But now so many solutions are available other than making/customizing your own software .

I think now people develop for FOSS for fun , personal proud , feel the part of philosophy and community etc

I don't know about that.  Google is one of the recent success stories and they've built quite a bit upon FOSS.

---

### Post by juancarlospaco on 2011-01-10
1)Its Free but not Free, its Free, but theres a lot of money involved.
2)Modules are loaded On-Demand into the Kernel.
3)Because theres a lot of money involved.

---

### Post by Chronon on 2011-01-10
OP, I think there's a finer structure to things than you appreciate.  You talk about Linux development but it seems that this really applies to development of free software, not necessarily Linux.

I have found that a certain amount of free software is written because it fulfills a need.  Someone finds that software doesn't exist that does what they want or what exists doesn't do the job adequately.  So, they do some work and write some code to allow them to do what they want.  If they release it under a free software license then not only can other people share the fruits of their labor but they can also sometimes attract help in improving the software.

Many small software projects are purely volunteer efforts and the people who work on them have other day jobs.  People find spare time to improve the code because in some way they find it fulfilling or interesting.

The free software ecosystem has many small projects like this.  Large projects often have corporate backing and programmers can be paid to work on the code.  In this case, the corporate body has a vested interest in making the code work better.

---

### Post by Chronon on 2011-01-10
> **asifnaz said:**
> I am afraid i may not agree . This might be the reason for developing a FOSS in early and mid 90s . But now so many solutions are available other than making/customizing your own software .

I think now people develop for FOSS for fun , personal proud , feel the part of philosophy and community etc

Yes, but if the code is free then you actually have a way to ensure that the software will gain features that you find important.  I.e. you can actually write the code for the new feature yourself.

The fact is that with free software people can write a patch to extend its functionality to do what they want.  If a patch produces a beneficial change in how the software works then why not contribute it back so that other people can share?

---

