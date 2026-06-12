---
title: "Anti-Virus IS the virus?"
date: 2010-05-16
forum: The Cafe
---

### Post by McRat on 2010-05-16
[http://www.wilderssecurity.com/showthread.php?t=271968&highlight=matousec](http://www.wilderssecurity.com/showthread.php?t=271968&highlight=matousec)

Apparently most all AV products hook the Win OS services to detect attempts to make changes.  And apparently that leaves a hole for malware writers to exploit with multi-core or multi-CPU machines.

It seems 64bit versions of Win are immune though. 

I'll admit I've always been suspicious of AV software doing more harm than good.  The McAfee meltdown recently just reinforced that belief.

---

### Post by KiwiNZ on 2010-05-16
A link to another Forum proves what ?

---

### Post by 3rdalbum on 2010-05-16
I posted about this in the Cafe a few days ago.

The flaw allows viruses to evade detection when they are already running. It isn't like the viruses wouldn't work unless you had anti-virus.

One thing that amuses me is that when a Windows user finds their computer running slowly, they assume it's a virus causing the slowdown, and it never is. Viruses always try to evade detection and run silently underneath the surface of your computer, so they use as little CPU power as they can.

---

### Post by McRat on 2010-05-16
> **KiwiNZ said:**
> A link to another Forum proves what ?

Seems that thread had links explaining both sides, while many others have been one-sided.

Here's the Register article:

[http://www.theregister.co.uk/2010/05/07/argument_switch_av_bypass/](http://www.theregister.co.uk/2010/05/07/argument_switch_av_bypass/)

Most desktop computers in the world are running AV software containing this flaw. It seemed an interesting story.

Feel free to delete it if it's inappropriate.

---

### Post by wilee-nilee on 2010-05-16
Using Mcafee is a foolish thing to do anyway, it is a well known AV, and the crackers who write the nasty-ware if they are astute have it written to disable all the major vendors anyway. There are many free more robust AV programs, but the user is the first in line for protection.

---

### Post by MichealH on 2010-05-16
You could try avast! Antivirus 
1. It supports Linux
2. It is free
3. Is not well known so it will find a virus immediately ( No one has programmed a virus for the mis-detection of avast!. It finds every virus :D Also if this page had a virus it would block it and tell me no further action is needed.

---

### Post by NightwishFan on 2010-05-16
I agree with the thread title, but I have no proof. So I will go based on my knowledge of system security, theory and gut feeling.

---

### Post by Khakilang on 2010-05-16
And when you download Adobe flash or Reader you have to download McAfee as well. What are those Windows users in for?

---

### Post by madjr on 2010-05-16
> **McRat said:**
> [http://www.wilderssecurity.com/showthread.php?t=271968&highlight=matousec](http://www.wilderssecurity.com/showthread.php?t=271968&highlight=matousec)

Apparently most all AV products hook the Win OS services to detect attempts to make changes.  And apparently that leaves a hole for malware writers to exploit with multi-core or multi-CPU machines.

It seems 64bit versions of Win are immune though. 

I'll admit I've always been suspicious of AV software doing more harm than good.  The McAfee meltdown recently just reinforced that belief.

totally agree with you

not only that but i bet my home that AV companies sponsor almost all the virus/malware dev offshore, creating the disease and selling you the cure (oldest trick in the book). Yea an awesome business

is a billion dollar industry (so anything and everything happens)

i wouldn't be surprised if Msft also kept their OS unsecured on purpose too, they earn millions by selling these extra security products and expensive enterprise support contracts.

I do not trust any of these companies, the bigger they're the worse.

---

### Post by Timmer1240 on 2010-05-16
The best Antivirus Ive found is called Karmic Koala 9.10 Its working very nicely so far!Im sick of fixing windows all the time so Its Ubuntu for me the battles over I won!

---

### Post by madjr on 2010-05-16
> **timmer1240 said:**
> the best antivirus ive found is called karmic koala 9.10 its working very nicely so far!im sick of fixing windows all the time so its ubuntu for me the battles over i won!

+1

---

### Post by wilee-nilee on 2010-05-16
> **MichealH said:**
> You could try avast! Antivirus 
1. It supports Linux
2. It is free
3. Is not well known so it will find a virus immediately ( No one has programmed a virus for the mis-detection of avast!. It finds every virus :D Also if this page had a virus it would block it and tell me no further action is needed.

Avast is a very good AV, but I don't use it for Linux. It does not get every possible virus/rootkit/malware...etc in a windows environment, there are others that don't run continuously like superantispyware which is excellent, and malwarebytes. All of these are free, you can buy a version, but the free versions work quite well.

---

### Post by MooPi on 2010-05-16
> **Koh Kook Loon said:**
> And when you download Adobe flash or Reader you have to download McAfee as well. What are those Windows users in for?
That is not a required download and you can opt out with a simple check. But is always a good idea to steer clear of McAfee products.

---

### Post by screaminj3sus on 2010-05-16
I haven't used a/v for windows in years :p

---

### Post by NightwishFan on 2010-05-16
Fedora with SELinux alerts me any time I step my OWN toe out of line. :)

---

### Post by Crunchy the Headcrab on 2010-05-16
> **Koh Kook Loon said:**
> And when you download Adobe flash or Reader you have to download McAfee as well. What are those Windows users in for?
No you don't.

---

### Post by NightwishFan on 2010-05-16
> **Crunchy the Headcrab said:**
> No you don't.

A lot of stuff used to be like that back in the day. Toolbars and Apple stuff does that now.

---

### Post by cariboo on 2010-05-16
I've been recommending Microsoft Security Essentials lately, because **so far** it is finding malware that all the others miss, and it doesn't ask to install any annoying extras, like most of the rest of the free av-scanners.

---

### Post by screaminj3sus on 2010-05-16
Yeah MSE is pretty good, I've recently changed to recommending that from avast.

---

### Post by perlluver on 2010-05-16
Also using Microsoft Security Essentials, and it is very decent, being from Microsoft and all.

---

### Post by jetsam on 2010-05-16
It's just more monopoly play, though...  :/

---

### Post by McRat on 2010-05-17
A word about Windows Defender and MS Security Essentials:

There is still a bug in both products that is 3 years old or older.

If you try and start a Win Computer and it doesn't want to run, go CNTL-ALT-DEL and pull up the Task Manager, and look at Processes.  Sort by CPU.  If the CPU on MSMPENG.EXE is over 50%, you found the reason.  Not sure why it happens, nor does MS seem to care.  If you ask, they will say it's another processes fault, so stop all non-MS processes.  And if that doesn't work?  Shut off Windows Defender or MSSE.

Not saying they are bad products, but just be aware.  It's pretty common.  Some computers will report 100% of CPU.  Now I KNOW MS knows how to control CPU access, so it would be a very simple "kludge" for them to cap it at 30% CPU.

---

### Post by jerenept on 2010-05-21
No, Windows is not a virus. Here's what viruses do:

1. They replicate quickly. ... Okay, Windows does that.

2. Viruses use up valuable system resources, slowing down the system as they do so. ... Okay, Windows does that.

3. Viruses will, from time to time, trash your hard disk. ... Okay, Windows does that too.

4. Viruses are usually carried, unknown to the user, along with valuable programs and systems. ... Sigh.. Windows does that, too.

5. Viruses will occasionally make the user suspect their system is too slow (see 2) and the user will buy new hardware. ... Yup, Windows does that, too.

Until now it seems Windows is a virus but there are fundamental differences: Viruses are well supported by their authors, are running on most systems, their program code is fast, compact and efficient and they tend to become more sophisticated as they mature.

So Windows is not a virus. ... It's a bug.

BTW... Please don't take this too seriously

---

### Post by jetsam on 2010-05-21
What do I have to give you to get you to allow me to take that seriously?

---

### Post by Rasa1111 on 2010-05-21
> **jerenept said:**
> No, Windows is not a virus. Here's what viruses do:

1. They replicate quickly. ... Okay, Windows does that.

2. Viruses use up valuable system resources, slowing down the system as they do so. ... Okay, Windows does that.

3. Viruses will, from time to time, trash your hard disk. ... Okay, Windows does that too.

4. Viruses are usually carried, unknown to the user, along with valuable programs and systems. ... Sigh.. Windows does that, too.

5. Viruses will occasionally make the user suspect their system is too slow (see 2) and the user will buy new hardware. ... Yup, Windows does that, too.

Until now it seems Windows is a virus but there are fundamental differences: Viruses are well supported by their authors, are running on most systems, their program code is fast, compact and efficient and they tend to become more sophisticated as they mature.

So Windows is not a virus. ... It's a bug.

BTW... Please don't take this too seriously


 haha, excellent ! :KS

do i have permission to use that elsewhere,  credit to jerenept? lol  :D
not too seriously...
but its so very true. lol
well done. *

---

### Post by Ebere on 2010-05-21
> **jetsam said:**
> What do I have to give you to get you to allow me to take that seriously?

What do I have to give you to get you to allow me to make that my tagline ?

---

### Post by TheNessus on 2010-05-21
On my windows 7 is do not have an AV.

I simply fortify my Firefox with every possible defense add-on such as no-script, adblock plus, and others as well; and stay clear of conspicious websites. (it's for academic work mostly, when I use it). I have yet to catch a virus or anything else of the sort. 

BUt yeah, using Linux prevents all that and it's my main :)

---

