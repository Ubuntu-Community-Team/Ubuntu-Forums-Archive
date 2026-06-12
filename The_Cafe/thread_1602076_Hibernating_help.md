---
title: "Hibernating help"
date: 2010-10-21
forum: The Cafe
---

### Post by shibui on 2010-10-21
I cannot hibernate. I came to _[this thread](http://ubuntuforums.org/showthread.php?t=1599039)_ via a Google search (since Ubuntu now litters almost all searches for anything linux related), hoping to figure out why I cannot hibernate. It mentions having a largeish swap. Since I have 8 gigs of memory, having swap would be nothing more than a waste of disk space.

So, I ask of you this: Why is swap necessary for hibernate? I'm not hibernating every 5 minutes, so I should not be forced to permanently sacrifice 16 gigs of my partition (the thread recommends twice as much swap as ram). I've attempted file based swap, but it will not boot, so that's out of the question. Figure this is the best place to ask since Ubuntu recently replaced Gentoo on my laptop, and FreeBSD on my desktop. (Those with a little experience will know why.)

---

### Post by cariboo on 2010-10-21
I think you are getting suspend and hibernate confused, Suspend to ram is what happens when you choose suspend from the menu. Hibernate writes an image to the hard drive in the swap partition, if you don't have a swap partition, hibernation isn't going work. The advice about needing twice the ram for swap is no longer valid, Have a look [here]("https://help.ubuntu.com/community/SwapFaq") for more info on why a swap partition is needed in order to hibernate and how to create one.

---

### Post by Khakilang on 2010-10-21
I got a screen shot of the power management preference to see whether this is what you are looking for. Its in the System > Preference > Power Management Preference.

[ATTACH]173008[/ATTACH]

---

### Post by shibui on 2010-10-21
I am not confusing hibernate and suspend. Suspend is what you do when you aren't using your laptop for a brief period. Hibernate is what you do when you unplug your desktop to move it to another room. I have 8 gigs of memory. I do not need swap. It's a waste of disk space that becomes permanent, unless I want to repartition the few times I hibernate. That takes up way more time than just booting and restarting all my software, rendering hibernate pointless. The link you provided does not explain why this poor decision was made, only that it was made.

---

### Post by Cuddles McKitten on 2010-10-21
I don't know the answer to your question, but you can use a file for swap avoiding the whole partition annoyance.  Just create a file with dd of the desired size, use mkswap on the file, and finish with a swapon

You could script it so that this process would be done before hibernation and delete the swap file afterwards.

---

### Post by shibui on 2010-10-21
> **Cuddles McKitten said:**
> I don't know the answer to your question, but you can use a file for swap avoiding the whole partition annoyance.  Just create a file with dd of the desired size, use mkswap on the file, and finish with a swapon

You could script it so that this process would be done before hibernation and delete the swap file afterwards.

The Ubuntu hibernation system doesn't support file backed swap.

---

### Post by Cuddles McKitten on 2010-10-21
> **shibui said:**
> The Ubuntu hibernation system doesn't support file backed swap.

I stand corrected.  That makes me agree with your point even more.  

One point though is that you only need enough swap space to cover the RAM you're using.  For example, I use about 1 GB of RAM for my usual computing activities; if I have more swap space than that, I can hibernate.  I have 4 GB of RAM total, but I don't need 8 GB of swap.  That 2x-your-RAM is an outdated rule of thumb -- much like the old "change your oil every 3,000 miles."

Yet another edit: I should probably go to sleep.  I missed this point as well: you can't just dump all the information into your RAM, because everything in your RAM goes poof when the computer goes off.  It has to have electricity to keep functioning.  The point of going on to your swap space is that your hard drive won't disappear after it powers down.  Why it doesn't support more temporary options on the HD, I don't know.

---

### Post by uRock on 2010-10-21
You don't need 8 gigs of swap. 2 gigs is plenty for Hybernating.

This is just how Linux works.

---

### Post by shibui on 2010-10-21
> **uRock said:**
> You don't need 8 gigs of swap. 2 gigs is plenty for Hybernating.

This is just how Linux works.

Having double was mentioned in the thread I was dejected from. I only went along with it. Don't have much experience in the linux hibernation department, but surely, there's got to be a better way than forcing a swap partition, even if not yet available on Ubuntu? 

(_[This Debian wiki page](http://wiki.debian.org/Hibernation/Hibernate_Without_Swap_Partition)_ indicates it should be possible to use a swapfile)

---

### Post by Ctrl-Alt-F1 on 2010-10-21
Opinion
> **shibui said:**
> The link you provided does not explain why this poor decision was made, only that it was made.
/Opinion

Hard drive space is CHEAP, and Ubuntu strives for ease of use.  If you want that much control over your OS maybe you should stick with Gentoo.

---

### Post by uRock on 2010-10-21
> **shibui said:**
> Having double was mentioned in the thread I was dejected from. I only went along with it. Don't have much experience in the linux hibernation department, but surely, there's got to be a better way than forcing a swap partition, even if not yet available on Ubuntu? 

(_[This Debian wiki page]("http://wiki.debian.org/Hibernation/Hibernate_Without_Swap_Partition")_ indicates it should be possible to use a swapfile)
Personally, I never use hibernation, because as you said, it takes to long to restart. If I am going to be away from my system for long, then I just shut it down. I do however use the swap when running because I only have 2gigs of RAM and I do a lot of network monitoring while running pen tools and such, which loads every packet into RAM and the Swap once the RAM is full. Even with 8gigs I would have a small swap to prevent a crash. As soon as the system slows, I pause the testing and clear TCPdump from the cache.

---

### Post by shibui on 2010-10-21
> **Ctrl-Alt-F1 said:**
> Opinion

/Opinion

Hard drive space is CHEAP, and Ubuntu strives for ease of use.  If you want that much control over your OS maybe you should stick with Gentoo.

...or windows. I was using Gentoo. For about 3 years. I switched for the update system (Gentoo has nothing to indicate which ports are vulnerable), the packages (don't need to wait 8 hours for compiles which fail quite a bit), and the support by companies like Google (seriously, try to find a company that offers Gentoo/OpenBSD port downloads).

---

### Post by CharlesA on 2010-10-21
This thread has run it's course.

Closed.

---

### Post by CharlesA on 2010-10-22
Thread reopened after speaking with the OP.

---

### Post by blueturtl on 2010-10-22
Maybe if the OP feels badly about permanently sacrificing the HDD space, he could use a memory stick for swap? With that much RAM it would rarely be written to except when hibernating. An 8 gig memory stick is cheap.

---

### Post by shibui on 2010-10-22
> **blueturtl said:**
> Maybe if the OP feels badly about permanently sacrificing the HDD space, he could use a memory stick for swap? With that much RAM it would rarely be written to except when hibernating. An 8 gig memory stick is cheap.

Never try to swap on a memory stick. You'll end up crying yourself to sleep. That's what I do with my servers when I move 'em about or upgrade the power circuits, etc. I use an external SAS as temporary swap. That's a business expense I can justify. However, a usb stick, even with swapiness at 0, will still suffer constant reads/writes as swap. The plus side to that is that it does make for a good marshmallow toasting device.

Another problem to fs backed swap for hibernation is that people add memory over time. Adding memory is trivial. Adjusting partition sizes to accommodate a larger swap, however, is not.

I can create temporary swap on an external hard drive. I can make a file backed hibernate. However, I'm willing to bet less than half of the userbase can claim the same. I'm not going to walk the less experienced through partition shifting. If something screws up, it's my fault. I'm not going to walk them through setting up a temporary swap or swapfile, because I don't know their setup. The next best thing is to make it an option in the system itself.

---

### Post by cariboo on 2010-10-22
I really don't understand your reluctance to create a 2Gb swap file just for hibernation. The idea of twice the ram for a swap partition is outmoded. The page I linked to in the second post says:

> Example Scenarios

Low RAM and low disk space With 512 MB RAM and 30 GB hard disk, use 512 MB for swap since RAM is very low.

Low RAM and high disk space With 512 MB RAM and 100 GB hard disk, use 1 GB for swap since RAM is very low and hard disk space is in plenty.

High RAM and low disk space With 2 GB RAM and 30 GB hard disk, use 1 GB for swap since hard disk space is very low.

High RAM and high disk space With 2 GB RAM and 100 GB hard disk, use 2 GB for swap since hard disk space is plentiful. 

If disk space is that precious, what do you do about the 5% allocated to root?

---

### Post by Sporkman on 2010-10-22
> **Ctrl-Alt-F1 said:**
> Opinion

/Opinion

Hard drive space is CHEAP, and Ubuntu strives for ease of use.  If you want that much control over your OS maybe you should stick with Gentoo.

Uh oh, he dropped da G bomb!!

---

### Post by blueturtl on 2010-10-22
> **shibui said:**
> Never try to swap on a memory stick. You'll end up crying yourself to sleep. That's what I do with my servers when I move 'em about or upgrade the power circuits, etc. **I use an external SAS as temporary swap. That's a business expense I can justify.** However, a usb stick, even with swapiness at 0, will still suffer constant reads/writes as swap. The plus side to that is that it does make for a good marshmallow toasting device.

Another problem to fs backed swap for hibernation is that people add memory over time. Adding memory is trivial. Adjusting partition sizes to accommodate a larger swap, however, is not.

I can create temporary swap on an external hard drive. I can make a file backed hibernate. However, I'm willing to bet less than half of the userbase can claim the same. I'm not going to walk the less experienced through partition shifting. If something screws up, it's my fault. I'm not going to walk them through setting up a temporary swap or swapfile, because I don't know their setup. The next best thing is to make it an option in the system itself.

You can afford an external dedicated swap drive, but can't afford to use 2-8 gigs of space for swap from the primary drive?

edit: emphasis added

---

### Post by shibui on 2010-10-22
My company can afford an SAS. I am not my company. I'm not even a director.

Anyway, there seems to be a communication problem on my part, it seems. I already have an 8 gig file backed swap which is temporary for hibernation. Try walking a fresh linux user through doing the same. I'm not asking how. I'm asking why. Why is it not a gui option?

---

### Post by cariboo on 2010-10-22
Ubiquity is designed to make it easy  for a new user to set up Ubuntu, if they use automatic partitioning, there is no need to fool with the swap partition. Even if extra ram is added, there is not need to increase the size of the swap partition.
 
Remember the Ubuntu install process is primarily designed for someone who has never installed an operating system before. Those of us that have been using a Linux variant for years, know how to work around the some of the restrictions put in place because of this ease of use.

There are very few reasons to increase or decrease the size of a swap partition, or any other partition for that matter, but there are some pretty easy to use gui tools for that sort of operation.

---

