---
title: "Your Swap partition size vs RAM?"
date: 2011-05-28
forum: The Cafe
---

### Post by Bart_D on 2011-05-28
How big do you set your swap partition to be, in comparison to your RAM?

I heard that, in Linux, the Swap must be TWICE as large as the amount of RAM you have installed.

Is there a disadvantage to having a swap partition that is smaller than the amount of RAM installed?

---

### Post by Zenrex on 2011-05-28
I don't know, but in my opinion 1:1 ratio or more is fine.

---

### Post by blueridgedog on 2011-05-28
It depends.  Take a look:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by LowSky on 2011-05-28
1:1 is crazy if you have over 4GB of RAM.

My system rarely if ever uses SWAP with its 12GB of RAM, I set SWAP to 4GB and I know it is overkill.

Realistically you don't really need SWAP unless you like to use Suspend.

---

### Post by nzjethro on 2011-05-28
I go 2GB swap with 2GB of RAM, and have had no problems. I imagine I could even get away with less, but decided that I had no shortage of disk space.But no, nothing wrong with less than 2:1.

---

### Post by aysiu on 2011-05-28
My swap doesn't exist, because I prefer sleep and shutdown to hibernate.

---

### Post by VanR on 2011-05-28
When I installed Zorin  OS 4 it set up 2 swap partitions one 4 GB and one 4.9 GB. I have 4 GB's of RAM in my machine. Weird.

---

### Post by wolfen69 on 2011-05-29
> **LowSky said:**
> 
Realistically you don't really need SWAP unless you like to use Suspend.

Exactly. I don't use suspend, so I thought having 1gb of swap was too much when I have 8gb ram. I don't recall ever using any swap.

---

### Post by aysiu on 2011-05-29
If you suspend to RAM, you don't need swap. It's necessary only if you suspend to disk (hibernate).

---

### Post by wolfen69 on 2011-05-29
> **aysiu said:**
> If you suspend to RAM, you don't need swap. It's necessary only if you suspend to disk (hibernate).

To be honest, I've never once in my life used sleep, suspend, hibernate, or anything else. My desktop stays on 24/7 and has for years, and the rare times I use my laptop, I just shut it off when not in use. I don't even know the difference between all those "unconscious states".

---

### Post by kerry_s on 2011-05-29
2gb ram, no swap

---

### Post by aysiu on 2011-05-29
> **wolfen69 said:**
> To be honest, I've never once in my life used sleep, suspend, hibernate, or anything else. My desktop stays on 24/7 and has for years, and the rare times I use my laptop, I just shut it off when not in use. I don't even know the difference between all those "unconscious states".
I don't have a desktop. I can assure you sleep is very handy for laptops and netbooks.

---

### Post by Bart_D on 2011-05-29
Thanks.

Like wolfen69, I too have NEVER used ANY of those options. When my laptop is on, it's ON. It's ALWAYS p[lugged into an AC power outlet and I never run it on battery power.

I just noticed that ubuntu wiki link earlier in the post....that's actually the reason why I started this thread.

When you install to empty space, the installer creates the partitions and I see an ext4 partition but no swap partition(I checked with gparted)........which got me very nervous. Problem is I've been doing this for years with Ubuntu.....never ONCE have I paid attention to how much "swap" the installer set up for me. I just took what it gave me and that was the end of that.

That Ubuntu wiki article is really misleading. If you're not setting up partitions manually, how will you know what is the size of your swap partition?

---

### Post by Macskeeball on 2011-05-29
> **wolfen69 said:**
> To be honest, I've never once in my life used sleep, suspend, hibernate, or anything else. My desktop stays on 24/7 and has for years, and the rare times I use my laptop, I just shut it off when not in use. I don't even know the difference between all those "unconscious states".

Sleep/suspend/standby are different names for the same thing: a very low power state in which many components are turned off. The point being that it's faster to wake from sleep than to boot up the computer from an off state. The downside is that battery power is still being used and will decrease, albeit at a relatively slow rate.

Hibernate copies the contents of RAM to the hard disk and then shuts completely off. Upon rebooting the machine the save state is copied from the hard disk back to RAM. This takes much longer than waking from sleep because the computer has to boot from an off state and copy data from the slow HD to RAM. Once finished, however, the computer will pick up where you left off. According to posters in this thread, the swap partition is used by the hibernate mode to store the data copied from RAM.

When my laptop is about to run completely out of battery, whether it's on fully or asleep, it automatically goes into hibernate mode. That way, I don't lose any unsaved work and I can pick up where I left off once I plug in and boot.

---

### Post by wolfen69 on 2011-05-29
> **Macskeeball said:**
> Sleep/suspend/standby are different names for the same thing: a very low power state in which many components are turned off. The point being that it's faster to wake from sleep than to boot up the computer from an off state. The downside is that battery power is still being used and will decrease, albeit at a relatively slow rate.

Hibernate copies the contents of RAM to the hard disk and then shuts completely off. Upon rebooting the machine the save state is copied from the hard disk back to RAM. This takes much longer than waking from sleep because the computer has to boot from an off state and copy data from the slow HD to RAM. Once finished, however, the computer will pick up where you left off. According to posters in this thread, the swap partition is used by the hibernate mode to store the data copied from RAM.

When my laptop is about to run completely out battery, whether it's on 100% or asleep, it automatically goes into hibernate mode. That way, I don't lose any unsaved work and I can pick up where I left off once I plug in and boot.

You know what's really funny? I fix and sell pc's for a living, but not once has that information been important on the job. "Fix it, and fix it now!" That's what I do. But anyways, thanks for the info I won't remember. :)

But I did know they were power saving states.

---

### Post by doorknob60 on 2011-05-29
I have 4 GB of RAM and 2 GB of swap. I probably don't need the swap, but oh well, it's already there, don't need it for anything else :P

---

### Post by Nyromith on 2011-05-29
0

I never create a swap partition for Linux, and always disable the swap file in Windows. Never had a problem with that.

---

### Post by meborc on 2011-05-29
SWAP is also used when you are running programs which need more RAM than you have. then the swap space is used as virtual RAM automatically by your operating system. This is SLOOOOOW because swap is essentially just a hard drive partition.

So, unless you are using very heavy programs with low RAM or love hibernation, you really have no use for SWAP

I personally just use whatever the default value is in Ubuntu installer as hard drive space is not important for me :)

---

### Post by ssam on 2011-05-29
unless you have far more RAM then you're programs will ever use then it probably worth having some swap.

suppose you have 1-2GB of RAM and have a few large programs open such that most of your RAM is used. now you want to open another large program.

with no swap you may not be able to open the new program. or maybe you will run out of memory (OOM) while it is running. when you hit OOM then the kernel has to kill programs. suppose you are right at the limit of your memory and a new email arrives, your email program asks for some more memory which pushes you over the limit. in this case its possible that the email program will get killed and cause data loss.

with swap the kernel just shuffles stuff around. this will be slow, but everything will keep running.

---

### Post by Paqman on 2011-05-29
> **wolfen69 said:**
> My desktop stays on 24/7 and has for years

If you set it to sleep when it was idle after an hour or so, you'd save yourself a lot of money. Power use while suspended on my desktop is only about 1W more than when it's off, so it's quite a big drop. Leaving a desktop on overnight is a real waste of electricity unless it's doing something useful IMO.

Just a thought.

---

### Post by weasel fierce on 2011-05-29
With 4 gigs of RAM, my swap is virtually untouched.

---

### Post by LowSky on 2011-05-29
> **Paqman said:**
> If you set it to sleep when it was idle after an hour or so, you'd save yourself a lot of money. Power use while suspended on my desktop is only about 1W more than when it's off, so it's quite a big drop. Leaving a desktop on overnight is a real waste of electricity unless it's doing something useful IMO.

Just a thought.

Try running sleep with proprietary drivers... I try to put my PC to sleep and guess what it fails to wake because some developer never thought a person might like his graphics card to work. Also sleep doesn't shut down the fans so its still pulling more power than it really should in a low power state.

So since I like it on 24/7 it runs MythTV and Folding@Home just so I feel it is doing something.

---

### Post by TheJackal12 on 2011-05-29
```
andrew@thinkpad-x200t:/$ free -m
             total       used       free     shared    buffers     cached
Mem:          3860       3764         95          0       1198       1805
-/+ buffers/cache:        760       3100
Swap:            0          0          0
```

Hmmm I don't really see the need for swap if you have >4GB and don't use your computer for intensive stuff.

---

### Post by Allavona on 2011-05-29
Sleep - What I do...sometimes!
Hibernate - What bears do.
Suspend - The results of getting in trouble at school!

Turn-off - What my computer does. 6 seconds from turn on until Grub, then 8 seconds till a fully operational desktop. In other words I can shut down and restart faster than I can wake up from sleep/hibernate/suspend. 

I don't use swap, but like a lot of replies here, I'm not hurting for space, so I leave it alone.

---

### Post by Artemis3 on 2011-05-29
I don't have any swap partitions or files.

---

### Post by wolfen69 on 2011-05-29
> **Paqman said:**
> Leaving a desktop on overnight is a real waste of electricity unless it's doing something useful IMO.

I turn off the monitor at night and seed iso's for the benefit of everyone. Is that useful?

---

### Post by Gremlinzzz on 2011-05-29
Back in the old days when I had to set up my own partition it was double the ram.that was 6 years ago!:D
just checked ubuntu,s set up it equalled the ram!

---

### Post by Paqman on 2011-05-30
> **LowSky said:**
> Try running sleep with proprietary drivers...


I've not had any problem with Nvidia and suspend for a few years now, but I don't use the absolute latest cards (you generally can't get them in fanless versions). AMD might be a different story I guess, but I wouldn't touch them with a barge pole.

> Also sleep doesn't shut down the fans so its still pulling more power than it really should in a low power state.

Yikes. Have you filed a bug? That's a bit of a howler.

> 
So since I like it on 24/7 it runs MythTV and Folding@Home just so I feel it is doing something.

Yeah, distributed computing is the main thing I was thinking of when alluding to it doing something useful overnight. I set my machine to switch to BOINC when it's idle, but I still shut it down overnight. Modern desktops are getting pretty ridiculous for power use. Any electronic device sucking over 100W continuously is a bit inexcusable IMO. I have an ARM powered NAS that I leave running for (amongst other things) torrents, but that maxes out at about 22W, which I can live with.

---

### Post by NMFTM on 2011-05-30
I currently have about 10GB of swap space (+2GB more than my amount of RAM) just out of paranoia. My main drive is two 1TB drives fake RAID0'd together. I don't have to worry about conserving space.

Also, if you're on Windows make sure that you go into your pagefile options and set the minimum pagefile size option to whatever the maximum is as soon as you install the OS. This will increase speeds as the pagefile won't get fragmented due to the "accordion effect" of it shrinking when not in use.
> **Bart_D said:**
> If you're not setting up partitions manually, how will you know what is the size of your swap partition?
Going into your partition manager.
> **meborc said:**
> SWAP is also used when you are running programs which need more RAM than you have. then the swap space is used as virtual RAM automatically by your operating system.
Back when I had a "measly" 4GB of RAM, when copying large amounts (hundreds of GB) of data between hard drives I would use up to 2GB of swap space IIRC. But now that I have 8GB I can't recall ever seeing the system use any.

---

### Post by oldos2er on 2011-05-30
I have a 512MB swap file, ala [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq). Never use it, and when I had a swap partition of 2GB or less, I never used that either. I have 4GB RAM, and I guess I just don't stress my system to the point where it would need to swap. Plus I turn the swappiness way down for every install, the default is too high, in my opinion.

---

### Post by earthpigg on 2011-05-30
```
[chris: ~]$ f
             total       used       free     shared    buffers     cached
Mem:          6034       2207       3826          0        233       1123
-/+ buffers/cache:        850       5184
Swap:            0          0          0
[chris: ~]$ 

```

None, for obvious reasons.

The old 'rules of thumb' for a set swap-size-to-RAM ratio aren't really applicable if you have 1gb of RAM or more.

---

### Post by Thewhistlingwind on 2011-05-30
> **weasel fierce said:**
> With 4 gigs of RAM, my swap is virtually untouched.

I have 800MB and my swap is virtually untouched, lol.

---

### Post by Dry Lips on 2011-05-30
So I guess 8GB of swap is overkill with 4GB of RAM?
(Imagine, I followed the RAM*2 formula in my utter ignorance...)

---

### Post by Bandit on 2011-05-30
I am glad this question was brought up. 
I havent used swap space on any system with 2GB or more of RAM. 
I still have one setup, this time 10GB for some reason I cant remember, but its at 0% all the time and I have 4GB RAM.

Guess if I put it to hibernate it might get used, but then its a pain sometimes to get everything woke back up without locking the system up.

---

### Post by mike_f on 2011-05-31
I prefer hibernate mode. 
My 4GB current desktop system wakes up from it about twice as fast as regular booting. For reasons previously stated I don't trust or can't use sleep mode.

Therefore, I use swapfile size = RAM size.

BTW what's even worse than poorly implemented computer sleep modes are the brain dead cable set top boxes (on 24/7) that have NO power saving modes. The 'power' button usually doesn't do anything except control the aux power outlet. :mad:

---

### Post by Artemis3 on 2011-05-31
Back to unplugging or use the magic powerbar switch... Weren't they forbidding "standby" in common devices in the UK or somewhere?

Hibernate... just the thought of waiting for 8g to flush into the swap file... I'd rather turn it off, Xubuntu starts fast anyway and Firefox, umplayer and others save sessions (Of course it didn't help that suspend didn't work with sandy bridge).

---

### Post by Bandit on 2011-05-31
Seems VBox uses SWAP a small bit. Using 17.5MB of 10GB.. lol

---

### Post by blueridgedog on 2011-06-01
> **Dry Lips said:**
> So I guess 8GB of swap is overkill with 4GB of RAM?
(Imagine, I followed the RAM*2 formula in my utter ignorance...)

Yes, but not really an issue.

---

