---
title: "Before I install 12.2 ... anything I should know about grubs and boots?"
date: 2009-01-02
forum: Slackware and derivatives
---

### Post by xarte on 2009-01-02
My ISO has neeeearrrly finished downloading. At last. 

I'm just a teensy bit anxious about it because I see quite a few posts from people going "how do I boot.." and well, so far in linux, I boot by pressing the 'on' button.

I have some live CDs so I can rescue things but I'd rather not completely bugger it up in the first five minutes.

My existing partition is a 4 gig swap  at the start of the drive, an 8 gig (I think?) root partition and the remainder for /home.  Doing that seemed to give me a speed increase from my previous "just format the whole disk" setup (or is it my imagination?)

SO. 
[I][B]
Is there anything I should know before I pop the disk in the hard drive and attempt to 'follow the bouncing ball'? [/B][/I]

(If you've got a link to an idiot-proof guide, that'd be grand. The slack site is talking about a boot floppy... I haven't owned a floppy drive for several years!)

[http://www.slackware.com/install/rootdisk.php](http://www.slackware.com/install/rootdisk.php)

Yes, yes, I know if I'm THIS much of a noobie I should probably stick with nice safe Ubuntu, but this is much more fun ... press buttons, see what happens. Take things apart, put them back together, wonder where those extra nuts and bolts belonged.....

---

### Post by saulgoode on 2009-01-02
There will be an [Installation HOW-TO file]("ftp://ftp.slackware.com/pub/slackware/slackware-12.2/Slackware-HOWTO") on your DVD. You may also find helpful information [in this thread on LQo]("http://www.linuxquestions.org/questions/slackware-14/so-you-want-to-be-a-slacker-what-do-i-do-next-644746/").

Your partitioning layout seems OK (this aspect is always somewhat subjective). Personally I'd do things slightly different. I typically place my root partition first, mainly for consistency across all of my computers (if a rescue disk/CD is needed, I know where to find /). 

8G is a good size for your root directory.

Your swap partition is quite large, but if you don't mind losing the disk space it shouldn't cause any problems -- and might be useful if you intend to use 'suspend to disk'. A large swap might also be useful if you intend to mount /tmp on a tmpfs (tmpfs is like an on-demand RAM disk). If you aren't doing either of these things, you might consider reducing your swap to about 512Mb or maybe 1G.

Depending on the size of your harddrive, you might want to take some of the space from /home and create a fourth partition of about 4-8Gb. This makes it very simple to install a different distro (or a different version of SW) later on. It also provides some flexibility if you later decide to do anything with LFS or software RAID.

I would recommend sticking with LILO initially, unless you have a particular reason for wanting GRUB. GRUB will probably work just fine, but you will need to take some extra steps to install it; this is not handled automatically by the 'setup' program.

---

### Post by Antman on 2009-01-02
It would be best to do a test install in virtualbox first. This way you can become familiar with the install process and not be as anxious. :wink:

Cheers...

---

### Post by xarte on 2009-01-02
ah, cool. Good ideas. Yeah I wasn't sure if I was going to be upgrading the ram so went for 4 gig on the "twice ram" basis. One will probably be heaps. Great idea to chuck in another partition for playing with other distros on - it's only a small HD but since I don't plan on storing images on it, should have enough space.

I tried Virtualbox and even then there were a few things it was asking for where I had to guess what to set it to, and then opensolaris hung, and so I thought, oh to hell with it I'll just install the dang thing.

Well here goes. Sheesh lucky I'm not a brain surgeon isn't it....

---

### Post by Antman on 2009-01-02
> **xarte said:**
> 
Well here goes. Sheesh lucky I'm not a brain surgeon isn't it....
LOL... I'm sure you'll be fine.

Cheers

---

