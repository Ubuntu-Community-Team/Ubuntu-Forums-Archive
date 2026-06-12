---
title: "5400 vs 7200 RPM and Virtualization"
date: 2009-07-29
forum: System76 Support
---

### Post by samalex on 2009-07-29
I posted this as a reply to another thread about Virtualization, but someone suggested I post a new thread so it wasn't so buried... so here it is.  

For you guys who use VirtualBox on the Pangolin laptop, do you have a 5400 rpm drive or 7200 rpm drive?  I plan on running Win XP through VirtualBox, and given the PC image is on the hard drive I wasn't sure if this would affect performance.  Also the laptop I've spec'ed has the P8700 2.53 GHz processor and 4 Gigs/Ram.  The hard drive speed is the only variable I'm unsure about.

My main reason to run Win XP is to use the AppDev training videos which use a proprietary codec with DRM that only works on Windows :evil:.  Also being a DBA in a Microsoft shop it would be nice to have the MS SQL Server tools installed.  I'm not a gamer though, so that's not a concern.

I tried hitting Google with this question, but I didn't see much regarding the drive speed and virtualization.  Also sorry for so many questions lately to the forum, but I hope to put in my laptop order today or tomorrow and I want to cover all my bases.

Thanks for any feedback you guys have.  

Sam

---

### Post by 3Miro on 2009-07-29
Linux in has an excellent cashing strategy when it comes to the HD. If you get a 4GB RAM machine and running Ubuntu + XP, they would feel very comfortable with 1GB of RAM (half a gig for each one is plenty). This leaves 3GB of RAM to be used as Cash for the HD (approximately of course). Other than for initial boot, I don't think 7200 would make much of a difference compared to 5400. Compared to the shorted battery life for the 7200, I think for a laptop 5400 is the way to go.

I am using 5400 and I am happy with it, however, I have not made any real tests to compare it to 7200.

---

### Post by jocampo on 2009-07-29
> **samalex said:**
> I posted this as a reply to another thread about Virtualization, but someone suggested I post a new thread so it wasn't so buried... so here it is.  

For you guys who use VirtualBox on the Pangolin laptop, do you have a 5400 rpm drive or 7200 rpm drive?  I plan on running Win XP through VirtualBox, and given the PC image is on the hard drive I wasn't sure if this would affect performance.  Also the laptop I've spec'ed has the P8700 2.53 GHz processor and 4 Gigs/Ram.  The hard drive speed is the only variable I'm unsure about.

My main reason to run Win XP is to use the AppDev training videos which use a proprietary codec with DRM that only works on Windows :evil:.  Also being a DBA in a Microsoft shop it would be nice to have the MS SQL Server tools installed.  I'm not a gamer though, so that's not a concern.

I tried hitting Google with this question, but I didn't see much regarding the drive speed and virtualization.  Also sorry for so many questions lately to the forum, but I hope to put in my laptop order today or tomorrow and I want to cover all my bases.

Thanks for any feedback you guys have.  

Sam

1st, don't be sorry about asking questions, be sorry about NOT learning :-) ... asking and reading is the only way to learn and be proficient on anything on this life.

Like I said before, I always recommend and use 7200rpm or higher on any Linux/Windows system which is going to be used as Virtual Lab (Vmware, VirtualBox, etc) Slowest hardware on a system  is Hard Disk, so, the faster the better.

With 4GB or RAM you are doing well, but if your motherboard and budget allow more, like 8Gb, go for it. Virtual machines LOVES memory, so, the more the better.

Finally, please setup /home or whatever partition you are gonna use in a separate place than root. That way, you can protect your data in case or any system crash. I would also suggest assign 1gb for swap.

Have fun!

PS: if you have enough hard drive space and are using VirtualBox, please use fixed drive assignment when creating your virtual machine; performance will be a bit better

---

### Post by MorphWVUtuba on 2009-07-29
My Serval Pro has a 7200RPM drive, and my VMs run great.  I don't really feel comfortable comparing it to my 5400RPM drive on my previous machine, because it was PATA instead of SATA, Core Duo 2.10 instead of Core 2 Duo 2.53, etc.  Not an apples to apples test.

---

### Post by samalex on 2009-07-29
MorphWVUtuba,

This is totally off topic, but I couldn't help but notice your nick and icon...  I'm a euphonium player, or used to be rather, haven't played in years though I'd love to join the local community band whenever time allows.

I played Tuba while in college, but that was years ago.  

Do you keep up with DCI?  Just curious...

Sam

---

### Post by HotShotDJ on 2009-07-29
> **jocampo said:**
> With 4GB or RAM you are doing well, but if your motherboard and budget allow more, like 8Gb, go for it. Virtual machines LOVES memory, so, the more the better.Generally, this is a true statement.  All things being equal, the more RAM, the better.  However, all things are NOT equal.  As of today, 4G RAM is a $50 upgrade on the Pangolin, for a cost of $25 per Gig (50/2).  However, 6G RAM is a $299 upgrade, for a cost of $74.75 per Gig (299/4) and 8G RAM is a $499 upgrade, for a cost of $83.17 per Gig (499/6). Although, even $83 is dirt cheap compared to the bad old days where 16 Meg RAM was a $300 upgrade that "power users" were happy to pay.

As with most things, increasing RAM reaches a point of diminishing returns.  Where that point is depends on how you will be using your machine.  In your case (as in mine), 4G RAM should be plenty to allow you to run a virtualized WinXP session along with your regular apps under Ubuntu.  Of course, 6 or 8 Gigs might be better, but probably not $299 or $499 worth of better.  I guess what I'm saying is that the difference between 2G and 4G will be significant, but not so significant between 4G and 6G, and probably not even noticeable between 6G and 8G.  However, if your planning on running multiple VM's and/or some RAM intensive native apps, you may very well find significant benefits from the 6 or 8 G RAM upgrade.

---

### Post by samalex on 2009-07-29
[QUOTE="HotShotDJ"]Generally, this is a true statement. All things being equal, the more RAM, the better. However, all things are NOT equal. As of today, 4G RAM is a $50 upgrade on the Pangolin, for a cost of $25 per Gig (50/2). However, 6G RAM is a $299 upgrade, for a cost of $74.75 per Gig (299/4) and 8G RAM is a $499 upgrade, for a cost of $83.17 per Gig (499/6). Although, even $83 is dirt cheap compared to the bad old days where 16 Meg RAM was a $300 upgrade that "power users" were happy to pay.[/QUOTE]

My budget is only about $1100 max, so 4 Gigs is the most I can do right now.  Maybe down the road I can hit Crucial and add more to the box, but not today.

But it looks like I'm faced with the same ol' conundrum of speed vs battery life.  Probably 95% of what I do will be in Linux which should work well using a 5400 rpm drive, but in the off chance I do start depending on Windows for a few things and if VirtualBox is lagging, I can always setup a dual-boot system and run it that way.  It's not ideal, but for now I think battery life wins between the two.

Sam

---

### Post by jocampo on 2009-07-29
> **HotShotDJ said:**
> the difference between 2G and 4G will be significant, but not so significant between 4G and 6G, and probably not even noticeable between 6G and 8G. 

Good point HotShot. In my case, I use VMs intensively, several VMs opened at the same time and some time using Oracle and/or MS-SQL. RAM is a must for me. But general speaking, 4GB should be enough. 

Samalex:
If you are going to buy a laptop and get the 7200rpm disk, I would not be concerned about battery life if you are not planning to use VirtualBox all the time. 

You can also tweak hd spins using hdparm command. It could help a bit in reducing your power comsuption. Everything that spins or has fans inside a PC, usually use a lot of power. So, decreasing the spins, reduce the power consumption too. But again, I should not be very worried about it if you will get a 7200rpm and won't use VirtualBox all day or all the time.

---

