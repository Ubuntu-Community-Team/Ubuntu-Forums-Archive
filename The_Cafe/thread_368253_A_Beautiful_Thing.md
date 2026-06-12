---
title: "A Beautiful Thing:"
date: 2007-02-23
forum: The Cafe
---

### Post by TheMono on 2007-02-23
"Your computer will be faster and more reliable with Windows XP Professional"...

---

### Post by Tomosaur on 2007-02-23
Haha, nice one. Let us know when you get your first BSOD :)

---

### Post by Jimmy_r on 2007-02-23
[http://www.ubuntuforums.org/showthread.php?t=313661](http://www.ubuntuforums.org/showthread.php?t=313661)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=20650&d=1165423401[/IMG]

---

### Post by TheMono on 2007-02-23
I actually did get a BSOD when it tried to restart after installing, however, I think I can write that off as a quirk of running in a vm lol.

---

### Post by steven8 on 2007-02-23
I am curious about the virtual machine idea.  You can install vmWare from automatix.  Is it easy to set up?

---

### Post by Jimmy_r on 2007-02-23
> **steven8 said:**
> I am curious about the virtual machine idea.  You can install vmWare from automatix.  Is it easy to set up?

I do not know about vmware server, but I installed vmware player from the repos.
I followed the guide here:[http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html](http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html)

This guide is for having windows as the host, so some things needs to be adapted, for example ```
qemu-img.exe create -f vmdk Windows...
``` needs to be changed to
```
qemu-img create -f vmdk Windows...
```

---

### Post by steven8 on 2007-02-23
Hmm.  I think I'll give that a go this weekend.  Thanks!

---

### Post by TheMono on 2007-02-23
If you have a relatively recent processor that supports hardware VT - Intel Core 2's for example - then wait till feisty comes out and use KVM... The screenshot at the start is using KVM on feisty. Works a treat.

That is, feisty works a treat, not Windows lol. Using Windows Update again is trying my patience after my time with synaptic!

---

### Post by Jimmy_r on 2007-02-23
Too bad my athlon64 does not support KVM :(

---

### Post by maniacmusician on 2007-02-23
> **steven8 said:**
> Hmm.  I think I'll give that a go this weekend.  Thanks!
I would use VirtualBox instead of VMWare ([http://virtualbox.org](http://virtualbox.org) ), it's more "free" and most people find that it is much faster than VMWare for them.

As TheMono said, if your processor supports hardware VT, your virtual machine experience will be **much** faster.

---

### Post by floke on 2007-02-23
I especially liked the '27 minutes' left to go bit - when the blue bar showed it was already 1/3 of the way through!

---

### Post by H.E. Pennypacker on 2007-02-23
I don't get the joke?

What's the window manager you're using?

---

### Post by FuturePilot on 2007-02-23
If your idea of fast is being able to take a coffee break when booting, then yeah, it's fast:lolflag:

---

### Post by maniacmusician on 2007-02-23
> **FuturePilot said:**
> If your idea of fast is being able to take a coffee break when booting, then yeah, it's fast:lolflag:
You laugh, but in all fairness, Windows XP was a fairly quick booter, if I remember correctly. And it shutdown pretty fast too. Must give credit where credit is due. XP does have that going for it, even though it is a POS otherwise.

---

### Post by Tomosaur on 2007-02-23
Windows is slower to boot for me, and I have to wait for like an extra 40 seconds once I hit the desktop before I can even use it.

---

### Post by maniacmusician on 2007-02-23
> **Tomosaur said:**
> Windows is slower to boot for me, and I have to wait for like an extra 40 seconds once I hit the desktop before I can even use it.
Ah yeah, if you have programs that start up with XP, it's a pain to wait for it to be usable.

But, I just installed a dual-boot system with XP and Kubuntu on it for my mother. It was an old IBM NetVista PIII, I believe, and Windows booted quite snappily on it.

---

### Post by TheMono on 2007-02-23
The window manager is just plain old metacity... My Beryl is broke lol.

As far as booting XP is concerned, it has always been very fast for me. Having said that, feisty flies as well, with bootchart reporting 22 seconds. This is the first time that Ubuntu has booted faster than XP though.

---

### Post by shareMenaPeace on 2007-02-23
Hi,
i used vmware and must say the boot process from a fresh xp install is pretty fast.
XP boots faster with vmware it seems to me, but well never used xp yet - just have no need :)
I tried to update my XP with the automatic feature which took so much time that i quiet that.
If i actualy would use xp with vmware i would update manual. You can download updates and more here [http://winboard.org/](http://winboard.org/)

So i think i going to install fluxbox next, specialy if it is more faster. But maybe i dont because no need for xp.

Well i got soon a beta game i will be playing which is not yet planed to be support for linux!
mythos.com - but for this case i will use a dual boot desktop computer ....


Cheeers

---

### Post by Lux Perpetua on 2007-02-23
> **maniacmusician said:**
> You laugh, but in all fairness, Windows XP was a fairly quick booter, if I remember correctly. And it shutdown pretty fast too. Must give credit where credit is due. XP does have that going for it, even though it is a POS otherwise.I used to say that, but now Dapper boots as fast as or faster than Windows XP ever did on this computer. (That is, when it doesn't decide to check my filesystem. :-P)

---

### Post by esaym on 2007-02-23
> **maniacmusician said:**
> You laugh, but in all fairness, Windows XP was a fairly quick booter, if I remember correctly. And it shutdown pretty fast too. Must give credit where credit is due. XP does have that going for it, even though it is a POS otherwise.

Yes  this is true for most people.  But don't forget the average user that doesn't know what they are doing and has 50mb worth of printer drivers running, 30mb of webcam drivers running, 60mb of anti virus software services running.  Thats minimum!  There are plenty of people that on top of that they have pda software and services installed, all kinds of tool bars, "internet enhancers" and anything else they like to click on and install while browsing the web.  Don't forget maybe some p2p software running in the background plus the preloader services in ram for adobe acrobat, MS office, Java, some sound card software and PLENTY of other programs and services that I forgot or don't care to remember.  And we must factor in the usual slowing down that adds up naturally every month until  after 1.5 - 2 years windows won't boot at all without blue screening!

Yes for us advanced users we can keep our boot times down.  But go tell my grandma or my mom that windows is a fast booter.  Or for that matter tell 90% of college students.  You will get kicked in the balls for sure!

---

