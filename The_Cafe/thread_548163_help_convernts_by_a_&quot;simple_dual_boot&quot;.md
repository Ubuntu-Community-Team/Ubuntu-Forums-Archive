---
title: "help convernts by a &quot;simple dual boot&quot;"
date: 2007-09-10
forum: The Cafe
---

### Post by ant2ne on 2007-09-10
I propose a "simple dual boot installation" method that would  help those who would like to try out ubuntu, but are afraid of abandoning windows. During the Live CD installtion, when it gets to the partitioning and mounting part there should be a radio button for "Simple Dual Boot". Programmers can make this automatically resize the partition, make another primary partition for ubuntu and install it as a dual boot. 

I think this would help convince a lot of fence sitters to try out linux. And maybe some will stay, maybe they wont. Maybe they'll have a new respect and insight to the whole idea.

---

### Post by FuturePilot on 2007-09-10
Doesn't it currently do this? You should have the option to resize the current partition and set up a dual boot. I don't think it would be possible to make it automatically resize it to a certain size, since everyone's hard drive is a different size.

---

### Post by ant2ne on 2007-09-11
Yes you can resize it, but the newb user is gonna get scared by that. It shouldn't be hard to design the installer to resize 3 or 4 gigs (if free) and make it a primary partition and then install ubuntu on it.

---

### Post by kagashe on 2007-09-11
[Wubi]("http://wubi-installer.org/") is best solution for newb who is scared of partioning.

From [wubi Faq]("http://wubi-installer.org/faq.php"):
> Is Wubi officially supported by Ubuntu?

Not at the moment, Wubi is an independent project, but there are plans to make Wubi an official installer for Ubuntu 7.10.

kagashe

---

### Post by purdy hate machine on 2007-09-11
The ultimate in simplicity already exists for the potential new user, the live cd. 
Easy to try and 100% commitment free.

---

### Post by Warren Watts on 2007-09-11
> **purdy hate machine said:**
> The ultimate in simplicity already exists for the potential new user, the live cd. 
Easy to try and 100% commitment free.

My only issue with Live CD's is that they tend to run S-L-O-W-L-Y because they are entirely RAM based.  I think a Ubuntu/Linux newbie could easily misinterpret the slow speed as being the way the OS ALWAYS runs.

Other than the speed issue, I agree; a live CD is an excellent way to "test drive" an OS.  It gives the user an idea of the "look and feel", as well as allowing them to verify all their hardware/software is going to operate as expected.  The user just needs to be aware/made aware that an actual install won't suffer from the speed issues that a RAM based Live CD creates.

---

### Post by ant2ne on 2007-09-11
> **purdy hate machine said:**
> The ultimate in simplicity already exists for the potential new user, the live cd. 
Easy to try and 100% commitment free.Right but when it comes to the actual install they get scared off.

---

### Post by igknighted on 2007-09-11
> **Warren Watts said:**
> My only issue with Live CD's is that they tend to run S-L-O-W-L-Y because they are entirely RAM based.  I think a Ubuntu/Linux newbie could easily misinterpret the slow speed as being the way the OS ALWAYS runs.

Other than the speed issue, I agree; a live CD is an excellent way to "test drive" an OS.  It gives the user an idea of the "look and feel", as well as allowing them to verify all their hardware/software is going to operate as expected.  The user just needs to be aware/made aware that an actual install won't suffer from the speed issues that a RAM based Live CD creates.

Actually it is slow because it has to read off the CD.  Find a live CD (PCLOS is one I think) that can load 100% into ram and it is actually very fast.  You do need at least a gig of ram to do this though.  RAM access is the quickest memory for the computer to access, much faster than even reading off the HD.  The other issue the liveCD has is that everything is compressed, so it needs to decompress any file it needs before it can use it.

---

### Post by the_darkside_986 on 2007-09-11
No offense to the developers, but I would certainly never trust the Ubuntu installer to safely resize an NTFS partition without botching the Windows installation and personal user files. 

I have used both GParted and Ubuntu's install disk to resize my NTFS, not concerned about the results (they both failed). Of course, I backed up my data and was apathetic to whether or not Windows would survive since I kinda wanted it gone anyway to make more room for Linux.

I hate to admit it, but the openSUSE 10.1 installer safely resized my NTFS drive, but that might be because I defragged it about 5 times prior to that. But openSUSE is terrible, IMO, and I replaced it with Ubuntu.

---

### Post by Warren Watts on 2007-09-12
> **igknighted said:**
> Actually it is slow because it has to read off the CD.  Find a live CD (PCLOS is one I think) that can load 100% into ram and it is actually very fast.  You do need at least a gig of ram to do this though.  RAM access is the quickest memory for the computer to access, much faster than even reading off the HD.  The other issue the liveCD has is that everything is compressed, so it needs to decompress any file it needs before it can use it.

:oops: You are correct. I don't know what I was thinking. :oops:
Obviously if it is entirely RAM based it would be** faster **not slower...Duh..

---

### Post by kagashe on 2007-09-14
I think only Puppy Linux is a Live CD which is entirely RAM based because you can take it out after the desktop is loaded. Moreover it requires only 128 MB RAM for this and even less if you have a Linux SWAP partition.

kagashe

---

### Post by Naz624 on 2007-09-15
> **ant2ne said:**
> Right but when it comes to the actual install they get scared off.

He is right, im a newbie to this forum aswell as any OS apart from Windows. I'm am scared about installing Ubuntu simply because i've used Windows since i've started using computers.

Going back to the first post, your saying that i will get an option to keep my windows OS when installing Ubuntu? This is what i want, i would like to install Ubuntu and keep my current OS.

Can somebody help me do this?

---

### Post by ArtF10 on 2007-09-15
I tried Wubi with 2 GB RAM and AMD K7 1Ghz.  Too slow for my liking.  Booting was particularly slow.

---

### Post by hessiess on 2007-09-15
most new comps already have 3 or 4 primary partitions, so an 100% auto option wouldent work that well

---

### Post by DarkDancer on 2007-09-15
> **kagashe said:**
> I think only Puppy Linux is a Live CD which is entirely RAM based because you can take it out after the desktop is loaded. Moreover it requires only 128 MB RAM for this and even less if you have a Linux SWAP partition.

kagashe

DSL (Damn Small Linux) and DSL-N (Damn Small Linux - Not) will both do this and they are tiny. It's an option at boot (dsl toram if I remember correctly).

---

### Post by Naz624 on 2007-09-15
this is all gibberish to me!!

---

### Post by ant2ne on 2007-09-15
> **Naz624 said:**
> He is right, im a newbie ... I'm am scared about installing Ubuntu simply because i've...:-\"

---

### Post by kagashe on 2007-09-16
> **DarkDancer said:**
> DSL (Damn Small Linux) and DSL-N (Damn Small Linux - Not) will both do this and they are tiny. It's an option at boot (dsl toram if I remember correctly).
Yes. You are right. I forgot about toram boot option in DSL. Personally I prefer Puppy over DSL because 2.6 series kernel. Yes I know that DSL-N is having 2.6 kernel but it is still under development.

kagashe

---

