---
title: "I convinced 2 to switch in one day"
date: 2006-12-28
forum: Testimonials &amp; Experiences
---

### Post by Praxicoide on 2006-12-28
Nearly 2 months ago, my computer got a nasty case of virus. I was quite fed up with windows at that point, so instead of reinstalling it, I opted for trying out Linux. At that time I knew next to nothing about it, except that it was open source and that you could "use a terminal for a lot of stuff", but I went ahead blindly.

Ubuntu installed beautifully on my Dell Inspiron, except for the screen configuration, looking to fix this I stumbled on this forum which has been my salvation for this and any other problem or question I could possibly have.

Anyways, now I can't believe it took me so long to switch from an OS I was constantly unhappy about.

Unfortunately, the computer at work still has XP, though I've installed Firefox and OOo. Today I was working as usuall when the keyboard stopped responding. I started whining about it to my coworker, saying how hard it was for me to work with Windows.

"Well, perhaps we should invent something better," he joked.

I proceeded to tell them that there was already something better, and indeed how I was already using it. I told him a bit about how Linux works (I know a tiny bit, now, I like to read), and he asked me if I could install it on his computer.

All this was in about 5 minutes (the computer hadn't even finished rebooting). I told him I would come back with the installation CD after lunch and give him a dual boot.

Well, he had to go, but after work I went to see a friend of mine, and after we had some dinner she asked me about the CD I was carrying. I explained it to her, and she begged me to please install it for her because her computer is slow as molasses.

So there you have it, tomorrow I'm going to do two installations (with codecs, and wine, of course). I'm kind of nervous because I really don't know much about computers, but it has worked great for me, so why shouldn't I share it with others. 

I'm crossing my fingers.

---

### Post by some_random_noob on 2006-12-28
>  but I went ahead blindly.
Cool, I went ahead blindly too :D ... good thing I chose not to fiddle with things that could possibly blow up hardware!

>  "Well, perhaps we should invent something better," he joked.
I would laugh at that because its so dumb but its almost midnight and I feel like I'm going to die. Careful with the dual-boot thingie. Free space doesn't count, he needs a spare partition. Don't do anything you're not sure about, or otherwise you'll screw something up. It scares me that you're dealing with Linux and you "don't know much about computers". Don't go too far...

>  after work I went to see a friend of mine, and after we had some dinner she asked me about the CD I was carrying. I explained it to her, and she begged me to please install it for her because her computer is slow as molasses.
Its... its every mans dream :D I wish there were smart people in New Zealand. I haven't got anyone to change to Linux yet.

Anyway good luck. Make sure you're not responsible for any damage, including hardware damage.

---

### Post by sultanoswing on 2006-12-28
> **some_random_noob said:**
> I wish there were smart people in New Zealand. I haven't got anyone to change to Linux yet.


You just haven't met the right people...I've got a few of my friends and relatives over to Linux in the past year.

---

### Post by lyceum on 2006-12-28
Linux is like the telephone game. I told a friend, who told a friend, who told a friend. As the pyramid grows, we slowly take over the world! (just kidding!) But that is cool. Just be there for them, as they will have questions. If they feel abandoned and can't help themselves you will turn into a zealot in their minds. Be sure to tell them about the forum too. That will help you out a lot. I have run into a few people that were "stuck" with an OS that they knew nothing about and no $$'s to get MS back on their machine, so good idea dual booting!

---

### Post by Jeroen Vernooij on 2006-12-29
Don't resize their NTFS-partitions while installing Ubuntu !!!

There is a critical bug in ubuntu (all releases) that destroys your partition table when resizing NTFS-partitions (for example to make space for a ext3-partition):
[https://bugs.launchpad.net/distros/ubuntu/+source/gparted/+bug/48229](https://bugs.launchpad.net/distros/ubuntu/+source/gparted/+bug/48229)

I already lost all of my data on my computer because of this.

As much as I love Ubuntu, I hate how Canonical dares to ship with this bug, I think this is absolutely unacceptable because many ARE resizing their NTFS's to install Ubuntu.

---

### Post by Praxicoide on 2006-12-29
:o 

Too late! I was without Internet yesterday:( 

I'm looking at the laptop right now, it's about 50 percent done. I can't believe this kind of bug would exist without warning us in big bold letters in the installation guide.

Well, maybe I got lucky and it will boot fine. We'll see in a minute.

---

### Post by Praxicoide on 2006-12-29
The installation finished. I've rebooted and Grub shows Ubuntu, Windows XP, and Windows NT (?).

Ubuntu loads fine, Widows XP......it showed me a blue screen, which checked the NTSF, after that it rebooted and now its started, but slooooooow as hell.

I'm trying to check OE to see if the e-mails are still, there (I backed them up, fortunately). I'm looking at the splash screen.

OK, now its stating up, and everything is there.....pheew.

This thing is way too slow, to the point that it can't be really used. It was slow before, but man...

It's a Compaq Presario. AMD Sempron, 256MB.


EDIT:

Everything is fine (sort of) Already used to Ubuntu, I forgot that windows will take forever to load and act like it's got a hangover for some minutes. 

So, why does it have Windows NT?

---

### Post by lyceum on 2006-12-29
> **Praxicoide said:**
> The installation finished. I've rebooted and Grub shows Ubuntu, Windows XP, and Windows NT (?).

Ubuntu loads fine, Widows XP......it showed me a blue screen, which checked the NTSF, after that it rebooted and now its started, but slooooooow as hell.

I'm trying to check OE to see if the e-mails are still, there (I backed them up, fortunately). I'm looking at the splash screen.

OK, now its stating up, and everything is there.....pheew.

This thing is way too slow, to the point that it can't be really used. It was slow before, but man...

It's a Compaq Presario. AMD Sempron, 256MB.


EDIT:

Everything is fine (sort of) Already used to Ubuntu, I forgot that windows will take forever to load and act like it's got a hangover for some minutes. 

So, why does it have Windows NT?

If you can, double the memory. That might speed it up. Ubuntu runs on 256, but is a bit slow. Also, too much stuff on the hard drive slows things down. As for the NT, was the XP an upgrade??? or could be an XP thing, if it is an older model? I have no clue on that one.

:-k 

Also, I have dual booted 2 PCs, on with XP Pro & Ubuntu and one with Vista & Ubuntu. I did the same as what you are describing here with no probs. I had no idea there was a bug.

---

### Post by Praxicoide on 2006-12-29
This computer is supposed to be new, so I have no idea, really.

Now I can't get the ethernet to work. ](*,) 

It has a realtek which is supposed to be autodetected, but nothing. The plug lights up, but the network connection still says its disconected.

I tried configuring it, even giving it a static IP :confused: It works fine in Widows, argh!

EDIT:

I'm looking at the device manager and it's there. I still don't know why it doesn't connect.

EDIT2:

Ha! got it to connect. Now, on to the wi-fi (dum-dum-duum).

---

### Post by lyceum on 2006-12-30
good luck with the wifi! :) 

Once you find out what kind it is there are lots of great how-to's to get things working.

---

### Post by Praxicoide on 2006-12-31
> **lyceum said:**
> good luck with the wifi! :) 

Once you find out what kind it is there are lots of great how-to's to get things working.


It's a Broadcom 43xx, I can't remember which, and I don't have the computer with me right now.

My boss asked me what I was doing with the laptop, I told him and he didn't seem pleased.

After he saw the computer running smoothly, He asked me to install it in our work computers:) 

I guess that means no more windows for me.

---

### Post by 3rdalbum on 2006-12-31
> **Praxicoide said:**
> 

This thing is way too slow, to the point that it can't be really used. It was slow before, but man...

It's a Compaq Presario. AMD Sempron, 256MB.

EDIT:

Everything is fine (sort of) Already used to Ubuntu, I forgot that windows will take forever to load and act like it's got a hangover for some minutes. 

I feel its owner's pain. A friend's friend's sister asked me to see if I could speed up her computer a little while back. It was a Compaq Presario laptop with 256MB of RAM and a Sempron M processor, with a full Internet security suite... I got an extra hour of pay just waiting for that thing to boot up each time.

---

### Post by lyceum on 2007-01-01
> **Praxicoide said:**
> It's a Broadcom 43xx, I can't remember which, and I don't have the computer with me right now.

My boss asked me what I was doing with the laptop, I told him and he didn't seem pleased.

After he saw the computer running smoothly, He asked me to install it in our work computers:) 

I guess that means no more windows for me.

Good luck. Broadcom 43xx and Linux do not seem to mix well :mad: . Here are some how-to's that might help though:

[http://www.ubuntuforums.org/showthread.php?t=285809&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=285809&highlight=broadcom)

[http://www.ubuntuforums.org/showthread.php?t=319227&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=319227&highlight=broadcom)

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)

---

### Post by Praxicoide on 2007-01-02
Thank you for pointing me to those threads. I will be sure to try them as soon as the computer arrives.

---

