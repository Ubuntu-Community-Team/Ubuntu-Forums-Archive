---
title: "Windows 7 (64 bit) needs 64 Gig Partition?"
date: 2010-06-03
forum: The Cafe
---

### Post by neu5eeCh on 2010-06-03
And how does 64 Bit Linux only need *really* need 4 to 8 gigs? I'm not looking to trash Microsoft. I'm genuinely curious... Why does Windows 7 need so much more space? I can't see that it does anything Linux doesn't?

---

### Post by cap10Ibraim on 2010-06-03
~ 20 GB mine , 64 Gig partition !!?

---

### Post by Wiebelhaus on 2010-06-03
Sorry but I've never heard this and I do this stuff for a living , can you please provide reference?

---

### Post by nrs on 2010-06-03
> **VTPoet said:**
> And how does 64 Bit Linux only need *really* need 4 to 8 gigs? I'm not looking to trash Microsoft. I'm genuinely curious... Why does Windows 7 need so much more space? I can't see that it does anything Linux doesn't?
Doesn't it only require a 20GB partition?  I've installed on a 32GB drive before, and I've gone lower. 

That's still quite a lot compared to my usual 6GB /. Totally pulling something out of my *** but  I'm guessing compatibility libraries + windows update eat up a hefty % of used space. I'm actually completely ignorant of windows, but doesn't it also keep backup copies of the OS?

Edit: just checked default install on my forgotten desktop. 9.62GB used.

---

### Post by pwnst*r on 2010-06-03
News to me. Mine's around 15GB with a bunch of programs/games.

---

### Post by FuturePilot on 2010-06-03
I installed it on a 70GB partition with plenty of room to spare. It only took about 10-15GB of space. Not sure where you heard it needs 64GB.

---

### Post by lostinxlation on 2010-06-03
[http://www.microsoft.com/windows/windows-7/get/system-requirements.aspx](http://www.microsoft.com/windows/windows-7/get/system-requirements.aspx)

---

### Post by kamaboko on 2010-06-03
Errrr...maybe you were thinking each bit took a gigabyte? :-)

---

### Post by PsychoDevon on 2010-06-03
It says this:

> 16 GB available hard disk space (32-bit) or 20 GB (64-bit)

Were you confused by it saying this? It only requires 20 GB for 64-bit (which is still a little hefty in my opinion, but then again, Windows is Windows...)

---

### Post by mickie.kext on 2010-06-03
When I once installed 64-bit W7 ultimate on my rig, it took about 27 gigs for just windows, no programs added. Then I find out that it made 8Gb pagefile.sys because I have 8 gigs of ram. And hibernate file also took some space.

On other comps. it takes about 15-16gb.

---

### Post by ajgreeny on 2010-06-03
Perhaps you are trying to shrink an existing windows installation with its own disk management system.

That tends to ensure that huge amounts of space are reserved for the OS and will not let you shrink it as far as you might want.  As an example, on a machine with an unused Vista OS which was defragged three times, I could not shrink it with its own disk management system to smaller than 80GB.  This is absolutely ridiculous, of course, but I could not afford to get rid of the windows partition while it was in warranty, had no DVDs for the recovery of the system, so lived with it.  The next time I update the Ubuntu OS, windows OS will just be wiped out.

There is nothing on the vista except the OS and whatever came with it, I couldn't be bothered to run it properly to find out, just had to get it going to do the partition shrinking, but 80GB is just totally unbelievable.  Perhaps windows 7 is similarly a disk hog.

---

### Post by SunnyRabbiera on 2010-06-03
Never heard this, though windows is a major space hog compared to linux

---

### Post by itreius on 2010-06-03
Yeah and Ubuntu requires 2 terabytes of hard drive space.

---

### Post by McRat on 2010-06-03
On a new HP Win7 Pro 64 computer:

14 GB compressed content on recovery partition.

Roughly 75 GB for "as delivered" installation area, includes crapware.

4 DVD-R to create "recovery disc", or about 16 GB.

---

### Post by Xianath on 2010-06-03
I run it (Windows 7 Enterprise 64-bit) in a virtualbox instance that has a 20GB virtual disk. With Windows, Office 2007 Ultimate, Visio and Project installed, it's  taking just under 10GB. More than Ubuntu, but certainly less than you claim.

Keep in mind that Windows 7 keeps a copy of every single version of every single DLL ever used, so that programs can use whatever they work best with. It also keeps compatibility layers for several earlier versions of Windows. There's also sample music and video, help files, and all sorts of other tiny bits that add to the polish and take up space. It probably can be trimmed down a few gig but would likely still take more than Ubuntu, though still a magnitude less than what you describe.

---

### Post by neu5eeCh on 2010-06-03
> **Wiebelhaus said:**
> Sorry but I've never heard this and I do this stuff for a living , can you please provide reference?

Here's a user who recommends 100g (others recommend less). However, the average seems to be around 40 to 60.

[http://www.sevenforums.com/hardware-devices/31341-recommended-partition-size.html](http://www.sevenforums.com/hardware-devices/31341-recommended-partition-size.html)

The 64 Gig (for a 64 bit system) was recommended on the Windows 7 forum (as well), but I no longer have the link. I've since partitioned my computer and gave Windows 7 all of 64 Gigs. It uses 44 Gig of that 64 - and I'm not a gamer. All I have are three browsers, WordPerfect, Nero, Paint Shop Pro and sundry little pieces of freeware. Let's be absurdly generous and say third party software accounts for 5 Gigs. Why is my Windows installation pigging out on 39 Gigs?

---

### Post by neu5eeCh on 2010-06-03
> **ajgreeny said:**
> Perhaps you are trying to shrink an existing windows installation with its own disk management system.

That tends to ensure that huge amounts of space are reserved for the OS and will not let you shrink it as far as you might want. 

Yes, my situation was very similar to yours. I was resizing an existing Windows partition.

But why does Windows need so much more real estate than Linux?

---

### Post by neu5eeCh on 2010-06-03
> **Xianath said:**
> Keep in mind that Windows 7 keeps a copy of every single version of every single DLL ever used, so that programs can use whatever they work best with. It also keeps compatibility layers for several earlier versions of Windows.

Thatnks Xianath. So far, you're the only respondent who has actually gone some way toward answering the question. :-)

---

### Post by Shining Arcanine on 2010-06-03
> **VTPoet said:**
> And how does 64 Bit Linux only need *really* need 4 to 8 gigs? I'm not looking to trash Microsoft. I'm genuinely curious... Why does Windows 7 need so much more space? I can't see that it does anything Linux doesn't?

I can install Gentoo Linux on a 2GB partition without issue, although the 2GB will not leave much room for source files, binary packages or a compiler cache, not to mention assorted programs. Right now my Gentoo Linux system is using about 40GB, but less than 2GB of that is in use by the core OS.

---

### Post by FuturePilot on 2010-06-03
> **VTPoet said:**
> Here's a user who recommends 100g (others recommend less). However, the average seems to be around 40 to 60.

[http://www.sevenforums.com/hardware-devices/31341-recommended-partition-size.html](http://www.sevenforums.com/hardware-devices/31341-recommended-partition-size.html)

The 64 Gig (for a 64 bit system) was recommended on the Windows 7 forum (as well), but I no longer have the link. 

A recommendation from some random person on a forum != official requirements.

---

### Post by neu5eeCh on 2010-06-03
> **FuturePilot said:**
> A recommendation from some random person on a forum != official requirements.

Who ever said it was an "official requirement"?

Here's my question:

"Why does Windows 7 need so much more space? I can't see that it does  anything Linux doesn't?"

Instead of make uselessly snarky comments, why not try answering the question?

---

### Post by FuturePilot on 2010-06-03
> **VTPoet said:**
> Who ever said it was an "official requirement"?

Here's my question:

"Why does Windows 7 need so much more space? I can't see that it does  anything Linux doesn't?"

Instead of make uselessly snarky comments, why not try answering the question?

The original question was "Windows 7 (64bit) needs 64GB Partition?" unless I misunderstood.

---

### Post by neu5eeCh on 2010-06-03
> **FuturePilot said:**
> The original question was "Windows 7 (64bit) needs 64GB Partition?" unless I misunderstood.

Yes. It was a question. Hence, the question mark. I never wrote anything about "official requirements". There are a wide variety of recommended partition sizes by users with more experience than me.

Fact is, Windows requires more space than Linux. I was wondering why, and still am.

---

### Post by pwnst*r on 2010-06-03
> **VTPoet said:**
> Yes. It was a question. Hence, the question mark. I never wrote anything about "official requirements". There are a wide variety of recommended partition sizes by users with more experience than me.

Fact is, Windows requires more space than Linux. I was wondering why, and still am.

No, the fact is you were saying it needs a 64GB partition.  Where did you come up with that rubbish?

---

### Post by CharlesA on 2010-06-03
It's Windows. >.>

More **** comes preinstalled.

I've got 32-bit Win7 running with around 10ish gigs used, but then I removed most of the crap I won't use with nlite.

---

### Post by Xianath on 2010-06-04
> **VTPoet said:**
> Thatnks Xianath. So far, you're the only respondent who has actually gone some way toward answering the question. :-)

Forgot to add the fact that it also maintains completely separate 32 and 64 bit environments (for example, Internet Explorer comes in both 32- and 64-bit variants) plus an entire virtual machine hosting a stripped-down XP (so-called XP mode), DirectX, .NET, a large help subsystem, accessibility features and whatnot... Basically, it's bloated because it has to cover 95% of the market, and that's the 95% of the users who don't know or don't care enough about computers to tweak for months until they get it "just right".

---

### Post by siimo on 2010-06-04
Most of it is these HUGE printer drivers and rubbish for every printer in existence.

---

### Post by jrothwell97 on 2010-06-04
> **siimo said:**
> Most of it is these HUGE printer drivers and rubbish for every printer in existence.

But do the printers *work*? :roll:

---

### Post by philinux on 2010-06-04
[http://www.microsoft.com/windows/windows-7/get/system-requirements.aspx](http://www.microsoft.com/windows/windows-7/get/system-requirements.aspx)

Like they say 20gig available hard drive space. So obviously you are going to need a larger partition than 20gig to run it.

---

### Post by pwnst*r on 2010-06-04
> **jrothwell97 said:**
> But do the printers *work*? :roll:

Um. Yes? 

> **philinux said:**
> [http://www.microsoft.com/windows/windows-7/get/system-requirements.aspx](http://www.microsoft.com/windows/windows-7/get/system-requirements.aspx)

Like they say 20gig available hard drive space. So obviously you are going to need a larger partition than 20gig to run it.

The point is, you don't need 64GB as the OP claims or dreams.

---

### Post by philinux on 2010-06-04
> **pwnst*r said:**
> 
The point is, you don't need 64GB as the OP claims or dreams.

Precisely.

---

### Post by Frogs Hair on 2010-06-04
Disc space usage in W7

[http://blogs.msdn.com/b/e7/archive/2008/11/19/disk-space.aspx](http://blogs.msdn.com/b/e7/archive/2008/11/19/disk-space.aspx)

---

### Post by neu5eeCh on 2010-06-04
> **pwnst*r said:**
> No, the fact is you were saying it needs a 64GB partition.

A.) Show me where I said that. 

> **pwnst*r said:**
> Where did you come up with that rubbish?

B.) I found this advice on Windows 7 Forum.

C.) Get a life.

---

### Post by neu5eeCh on 2010-06-04
> **pwnst*r said:**
> The point is, you don't need 64GB as the OP claims or dreams.

No. The point is to read my original post. I didn't make any such assertion (as you claim or dream).

I've found this advice at other locations.

And more thanks to Xianath, Charles, Slimo and others who actually have tried to answer my question.

The rest of you can kiss my...

---

### Post by pwnst*r on 2010-06-04
U mad?

---

