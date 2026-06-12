---
title: "Ever removed the HDD from a running system?"
date: 2009-12-18
forum: The Cafe
---

### Post by alphaniner on 2009-12-18
I just did.  I have several machines on a rack, set up so I can easily swap out the HDD.  I thought the machine was off, but when I pulled out the HDD I got a taste of angular momentum.  Oops.  Surprisingly, it seems there was no damage to the system.

---

### Post by NoaHall on 2009-12-18
Yes. I've done this on a system running Vista at the time, it worked for about 2 seconds and then crashed.

If you had something like DSL, you should be able to keep running it until something is needed from the hard drive.

---

### Post by fromthehill on 2009-12-18
dit this to a ubuntu and vista system
the effects are the same when you force chm0d 777 on the entire filesystem:
everything slowly disappears

---

### Post by BrokenKingpin on 2009-12-18
Many times actually. I work for a company that develops ATM software, so we have about 60 ATMs in our lab that are constantly being imaged and all that stuff. There have been many times where I though the machine was off before removing the hard drive. Most of the time there is no issue and the drive works fine after, but once in a while it will kill the drive. No big deal though as have enough of them to go around.

---

### Post by xir_ on 2009-12-18
> **BrokenKingpin said:**
> Many times actually. I work for a company that develops ATM software, so we have about 60 ATMs in our lab that are constantly being imaged and all that stuff. There have been many times where I though the machine was off before removing the hard drive. Most of the time there is no issue and the drive works fine after, but once in a while it will kill the drive. No big deal though as have enough of them to go around.


good luck with that job then :-p hope your boss doesn't read these forums

---

### Post by JayKay3000 on 2009-12-18
I have one really rubbish sata cable that comes out now and again. How do I tell? The comp just crashes/re-boots without showing the hdd. 

Should be ok as long as your not mooving stuff at the time.

---

### Post by mmix on 2009-12-18
In diskless system like slitaz, except that in boot time, there is no need HDD/USB.

---

### Post by juancarlospaco on 2009-12-18
Yes, HotSwap Disks...

---

### Post by Shibblet on 2009-12-18
I tried, but the system was just too fast.

Seriously though, why would you do this?

---

### Post by s3a on 2009-12-18
Isn't one of the advantages of using LVM being able to do that without problems? I use LVM on one of my computers but don't fully understand it which is why my school laptop has regular partitions.

---

### Post by alphaniner on 2009-12-18
> **Shibblet said:**
> Seriously though, why would you do this?

If that was directed at me, I did it by accident.

---

### Post by BrokenKingpin on 2009-12-18
> **xir_ said:**
> good luck with that job then :-p hope your boss doesn't read these forums
nah, it's built into the budget. With the amount we are swapping drives we go through them rather quickly regardless of people doing stupid things with them. My company should look into solid state drives, they can take a lot more abuse.

---

### Post by Shibblet on 2009-12-18
> **alphaniner said:**
> If that was directed at me, I did it by accident.

It was.  I am still trying to figure out how it happened on accident.  

You were going downstairs in the middle of the night to get a glass of water for your girlfriend, who only likes cold water in the middle of the night.  Then you heard a noise outside, dropped the glass of water, slipped on the spill, fell face first into your computer denting the side of it, so you pulled the side off to see how much damage was done, in the process pulling the case apart, you accidentally turned it on and it booted into Ubuntu, which launches a VirtualBox running Knoppix automatically.  Then when you looked inside to see if any damage was done, you had to use a flashlight to see because it was dark, and your girlfriend shouts "Where's my water?" but she's standing directly behind you, and irritated that you're up, and futzing around with the computer at 3 in the morning, but it startled you in the process causing your arm to twitch enough to flip the flashlight up and yank the SATA cable out of the hard drive.

Am I close?

---

### Post by red_Marvin on 2009-12-18
> **s3a said:**
> Isn't one of the advantages of using LVM being able to do that without problems? I use LVM on one of my computers but don't fully understand it which is why my school laptop has regular partitions.

I'm not so sure about PATA disks, I don't think they are designed to be hot swappable down on the electrical level. SATA drives on the other hand should be removable at "any" time given that they are not mounted (AFAIR).

---

### Post by alphaniner on 2009-12-18
> **Shibblet said:**
> Am I close?

Not so much, no.

---

### Post by handy on 2009-12-18
I mount/umount SATA & PATA drives to remove or swap, no problem at all providing you umount/mount them.  

It's the same as mounting & unmounting a NAS (or any other kind of) device I think.

I know that the OP removed the drive whilst is was mounted, which is a bit of a lottery, if data is being written or is still in cache & hasn't been written you would have data loss.

---

### Post by Shibblet on 2009-12-18
> **alphaniner said:**
> Not so much, no.

Well, we all mess up like that some times.

---

### Post by markp1989 on 2009-12-18
i  have done a similar thing, i power down the system, then moved the drive, and i felt (and heard) it still spining, just held it very still till it finished spining down.

---

### Post by blur xc on 2009-12-18
> **Shibblet said:**
> It was.  I am still trying to figure out how it happened on accident.  

You were going downstairs in the middle of the night to get a glass of water for your girlfriend, who only likes cold water in the middle of the night.  Then you heard a noise outside, dropped the glass of water, slipped on the spill, fell face first into your computer denting the side of it, so you pulled the side off to see how much damage was done, in the process pulling the case apart, you accidentally turned it on and it booted into Ubuntu, which launches a VirtualBox running Knoppix automatically.  Then when you looked inside to see if any damage was done, you had to use a flashlight to see because it was dark, and your girlfriend shouts "Where's my water?" but she's standing directly behind you, and irritated that you're up, and futzing around with the computer at 3 in the morning, but it startled you in the process causing your arm to twitch enough to flip the flashlight up and yank the SATA cable out of the hard drive.

Am I close?

Did you read his post?  He has several machines on a rack, forgot/didn't notice that one was still on.  I can easily see how that could happen.

Yeah, on my desktop computer w/ one internal hdd, it'd be hard to pull off on accident...

BM

---

### Post by Cam42 on 2009-12-18
> **Shibblet said:**
> I tried, but the system was just too fast.



[IMG]http://www.instructables.com/files/deriv/F9P/004A/FJ7PNJZ9/F9P004AFJ7PNJZ9.MEDIUM.jpg[/IMG]

---

### Post by The Real Dave on 2009-12-18
Nope, burned out a CD drive doing it though. Molex connectors seem....sparky :)

---

### Post by Shibblet on 2009-12-18
> **blur xc said:**
> Did you read his post?  He has several machines on a rack, forgot/didn't notice that one was still on.  I can easily see how that could happen.

Yeah, on my desktop computer w/ one internal hdd, it'd be hard to pull off on accident...

BM

I did read the post, but then I couldn't have elaborated as much as I did.  BTW, I have nothing but respect for your girlfriend, and her cold water.  ;)

---

### Post by dragos240 on 2009-12-18
I did this with a system booting off a flash drive. I had archlinux on it. Worked for ages. I browsed the web for about 2 hours. I went to open a folder. And nothing happened. So after that I opened up firefox again, and it stopped working. Interesting.

---

### Post by Zoot7 on 2009-12-18
I did it with a desktop I put together about 6 years ago running XP, it ran for a second or two then I got greeted by a humble BSOD. I'm curious what the effect with a Linux distro would be.

---

### Post by alphaniner on 2009-12-18
> **Zoot7 said:**
> I'm curious what the effect with a Linux distro would be.

Allow me to alleviate your curiosity.  By the time I realized what happened and switched to the machine in question through the KVM, the wallpaper and all the stuff on my panels had disappeared.  Shortly thereafter the icons on the desktop turned to what looked like a piece of paper with an upturned corner (the 'missing icon' icon).  Then a dialogue popped up with a bunch of ?s instead of text.  Then I held the power button to shut the thing down.

I reconnected the HDD and booted up, it was like nothing happened.  No forced fsck or anything, it just booted normally all the way to desktop.

> **Shibblet said:**
> ...but then I couldn't have elaborated as much as I did.

Paradox much?

---

### Post by Exodist on 2009-12-18
> **red_Marvin said:**
> I'm not so sure about PATA disks, I don't think they are designed to be hot swappable down on the electrical level. SATA drives on the other hand should be removable at "any" time given that they are not mounted (AFAIR).
yea PATAs will fry the ribbon cable if the molex power cable is removed. Pin1 gets very hot.
Although I have not tested it, SATA like Marvin mentioned should be easily hot swappable if your running RAID1 or 5 or a LVM setup.

---

### Post by alphaniner on 2009-12-18
> **Exodist said:**
> SATA like Marvin mentioned should be easily hot swappable if your running RAID1 or 5 or a LVM setup.

AFAIK, the SATA controller has to support hot swapping.  But I guess you can at least remove drives without blowing anything up.

---

### Post by Shibblet on 2009-12-18
> **alphaniner said:**
> Paradox much?

I don't know how a couple of medical professionals have anything to do with this.

---

### Post by handy on 2009-12-18
> **Exodist said:**
> yea PATAs will fry the ribbon cable if the molex power cable is removed. Pin1 gets very hot.
Although I have not tested it, SATA like Marvin mentioned should be easily hot swappable if your running RAID1 or 5 or a LVM setup.

> **alphaniner said:**
> AFAIK, the SATA controller has to support hot swapping.  But I guess you can at least remove drives without blowing anything up.

I've been using cheap plastic drive drawers on my own machines & others for maybe 15 years now.  They have only had any SATA drives in them inside of the last year. I use an adapter to connect the SATA drives to the drawer's internal IDE cable.

The only problem I ever had was when the PSU blew up (spectacularly whilst the machine wasn't turned on, capacitor I think, still haven't looked inside the PSU), it damaged the circuitry of one of the drive drawers, fortunately that was the only other damage to the system; there was a 1TB SATA drive in that particular drawer, I initially thought that I may have lost the drive, it surely was a relief when I swapped into a another drawer & it worked.

If the PATA drives truly don't handle hot swapping, then the tiny simple circuit in the drawer must provide protection, the ones I use have power switches that also function as a mechanical lock that ensures the drive is located properly before it gets power, & the power is off, before the drive can be removed. I guess that the protection for PATA drives may be as simple as that?

---

### Post by alphaniner on 2009-12-18
> **Shibblet said:**
> I don't know how a couple of medical professionals have anything to do with this.

Yeah, Nip/Tuck is a good show, but not really relevant to the issue at hand.

---

### Post by orlox on 2009-12-18
Once they broke into my house, and some of the things they stole, were my mouse, and a ram (512mb, the only one I had) from my desktop PC...quite strange things to steal if you ask me. When I got home, my computer was desperately beeping for help!

I've never experienced a hard drive removal though...only a hard drive frying due to a malfunctioning power cable on top of it...

---

### Post by tom66 on 2009-12-19
I did it on Ubuntu - 7 seconds it lasted, I could keep typing in OpenOffice.org but then it just kernel panic'd.

---

### Post by Shibblet on 2009-12-21
> **alphaniner said:**
> Yeah, Nip/Tuck is a good show, but not really relevant to the issue at hand.

Well, you're the one who said "Pair-of-Docs."

This is really the pinnacle of bad jokes for me.

---

### Post by alphaniner on 2009-12-21
> **Shibblet said:**
> Well, you're the one who said "Pair-of-Docs."

This is really the pinnacle of bad jokes for me.

I actually hadn't gotten that.  I thought you were just being completely obtuse. :oops:

---

### Post by Shibblet on 2009-12-21
> **alphaniner said:**
> I actually hadn't gotten that.  I thought you were just being completely obtuse. :oops:

A bit.

[IMG]http://d1.ac-videos.myspacecdn.com/videos02/208/thumb1_41f684e0ec6f44169a6ee9d1f4f10f38.jpg[/IMG]

---

