---
title: "Why is Wubi being stopped?"
date: 2013-04-25
forum: Ubuntu, Linux and OS Chat
---

### Post by riahc3 on 2013-04-25
Hello

I think Wubi was one of the greatest things out of the Ubuntu community. It let users set up Ubuntu quickly without partions, dealing with GRUB, etc............

And now they remove it?!? Why? It makes absolutly no sense.
¡
Yes, development has stopped on it but like all open source projects it can be picked up by someone else.

---

### Post by mörgæs on 2013-04-25
There are plenty of pages explaining why, like these:
[http://www.techweez.com/2013/04/02/ubuntu-13-04-to-exclude-wubi-windows-installer/](http://www.techweez.com/2013/04/02/ubuntu-13-04-to-exclude-wubi-windows-installer/)
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)

---

### Post by deadflowr on 2013-04-25
Wubi isn't really a great program.
A wonderful concept, sure.

---

### Post by Mark Phelps on 2013-04-25
The introduction of UEFI and secure-boot have both made life for Wubi very hard.  I don't actually know why they decided to kill it off -- but I can understand the Wubi developers getting fed up with MS's constantly making their lives difficult by introducing new and harder problems to solve with each new version of Windows.

---

### Post by riahc3 on 2013-04-25
> **mörgæs said:**
> There are plenty of pages explaining why, like these:
[http://www.techweez.com/2013/04/02/ubuntu-13-04-to-exclude-wubi-windows-installer/](http://www.techweez.com/2013/04/02/ubuntu-13-04-to-exclude-wubi-windows-installer/)
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)
Bugs are not a good reason why something should be just abandonded. IMAGINE, just IMAGINE, if every software that had a bug, was stopped from being furthered developed.....

> **deadflowr said:**
> Wubi isn't really a great program.
A wonderful concept, sure.
Then a great program using that wonderful concept should be made.

> **Mark Phelps said:**
> The introduction of UEFI and secure-boot have both made life for Wubi very hard.  I don't actually know why they decided to kill it off -- but I can understand the Wubi developers getting fed up with MS's constantly making their lives difficult by introducing new and harder problems to solve with each new version of Windows.
You actually have given a better explaination than Ubuntu's devs!

I really hope someone repicks the project up, else one less Ubuntu installation here (I only installed it because it was very easy to install besides Windows)

---

### Post by lykwydchykyn on 2013-04-25
I'm sure for some people WUBI was a perfect solution, but the fact is that both dual booting has become easier, and virtualion technology has improved dramatically in the years since it was introduced.  Any computer made in the last 5 years should be able to handle virtualizing Ubuntu without difficulty; any computer than can't would probably perform much better with a dual-boot anyway.  I know that's painting with a broad brush, but my point is, the people for whom WUBI is really the *best* solution is a shrinking population.

Anyone who's been a regular here for a while can tell you that WUBI creates more problems than it solves.

---

### Post by QIII on 2013-04-25
Someone made a cost/benefit decision.  The cost of keeping it up with developments like UEFI/secure boot outweighed the benefit of doing it.

---

### Post by Zill on 2013-04-25
> **riahc3 said:**
> ...Yes, development has stopped on it but like all open source projects it can be picked up by someone else.
...and, of course, *you* are free to do so!

FOSS is community driven and relies on *all* of us to drive a project forward.  Many developers are unpaid volunteers and free to work on whatever they wish and so none of us, as humble users, can demand that they work on a project that *we* want.

---

### Post by monkeybrain2012 on 2013-04-25
> **riahc3 said:**
> 

I really hope someone repicks the project up, else one less Ubuntu installation here (I only installed it because it was very easy to install besides Windows)

BTW, WUBI is not installing beside Windows, it is installed** inside** Windows. Installing beside Windows means giving Ubuntu its own partition. That's why WUBI is limiting and buggy. If you would only use Ubuntu in the form of WUBI then you will never really use Ubuntu anyway.There  is no "one less Ubuntu installation", since you have never had a Ubuntu installation.

That's one of my issues with WUBI,  it gives the wrong impression that it is a real install while it is only meant to be a "try it out", a demo for Windows users, it is never meant to be a replacement for a real install. Real Ubuntu install doesn't need Windows to work.

---

### Post by mastablasta on 2013-04-26
1. having a painless option to install and give OS a spin is good.

2. cheap USB sticks and persistence offer much the same thing. so do we really need wubi like install option?

3. virtualisation offers many options. a good one is Linux liveUBS option with portable virtual box and virtualise this key. it could be simpler thatn that. problem with virtualisaiton option is that it doesn't do 3D acceleration. so you might boot into various fallback options.

 anyway i think as trial of the OS - the live USB with some persistence added is best way.

---

### Post by Warren Hill on 2013-04-26
Modern computers with Windows 8 installed use GPT drives and have secure boot.  Wubi does not work with secure boot.

If you want to try the OS either use a USB stick or virtualisation software such as Virtualbox.

If you want Ubuntu to keep install it in its own partition.  Or like me go Windows free.

---

### Post by 3rdalbum on 2013-04-26
As Wubi required Windows to be present at all times, it actually hindered people from removing Windows and going all-Ubuntu.

From a support point of view, Wubi was a bit of a nightmare.

1. It often threw up error messages that nobody could help the victim to solve.

2. Newbs would ask "How do I access my Windows partition?" and the helpers here would tell them that if the partition wasn't in the sidebar then they would have to add it to their fstab... and finally on page 3 they'd realise the OP had used Wubi.

3. It was never communicated properly that Wubi was really only to try out Ubuntu before a proper install. Newbs would use Wubi, get everything set up the way they liked it, start installing programs and copying over files, and then bump up against the 16 gig limit and complain that Ubuntu was out of space even though there was a hundred gigs free on the hard disk.

4. "I installed Ubuntu with Wubi and I got it just how I like it, now how do I remove Windows?"

5. "My Windows stopped working and now I can't get into Ubuntu either?"

A nightmare to support, I'm glad Wubi is gone. I would only support its return if it created an actual partitioned dual-boot.

---

### Post by cariboo on 2013-04-26
Actually wubi isn't being dropped, our resident wubi expert bcbc has come up with some patches, that will keep wubi working with Windows 7, it's the combination of Windows 8 and UEFI, that are causing problems, but bcbc has vowed to continue working on the problem.

---

### Post by M Star on 2013-04-27
> **Mark Phelps said:**
> The introduction of UEFI and secure-boot have both made life for Wubi very hard.  I don't actually know why they decided to kill it off -- but I can understand the Wubi developers getting fed up with MS's constantly making their lives difficult by introducing new and harder problems to solve with each new version of Windows.

So maybe the developers could at least continue making WUBI for up to win7. So you don't have to deal with > The introduction of UEFI and secure-boot, but still providing support for the users who does not require > The introduction of UEFI and secure-boot. :)

---

### Post by sudodus on 2013-04-27
I think wubi will be around during the long time support of Ubuntu 12.04, until April 2017. So you can run 12.04 LTS with wubi.

---

