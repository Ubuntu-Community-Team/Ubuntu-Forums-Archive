---
title: "Harm in using Live - CD"
date: 2010-04-24
forum: The Cafe
---

### Post by anantshri on 2010-04-24
Hi all,

after collecting all the inputs on [innovative usage of Live CD's here]("http://ubuntuforums.org/showthread.php?t=1449209") I also started thinking in the alternate direction.

we are collecting all the positive aspects of Live CD.

But how Live CD could be dangerous.

I have few idea's in mind which i would like to refine and then present to all.

in the mean time again i am asking my fellow friends to help me with this study too.

Please share your thoughts how live CD could be dangerous.

---

### Post by Swagman on 2010-04-24
Live CD isn't dangerous.. Gparted can be though (Partition Manager)

---

### Post by Ewingo401 on 2010-04-24
The only thing I can think of is the extra wear and tear on the CD drive.  Other than that, running from a live CD is one of the safest things you can do.

---

### Post by cariboo on 2010-04-24
Using a Live CD gives you full access to the system, and using the Ubuntu Live CD also gives you root access, allowing you to do pretty much anything you want.

If the drive is encrypted, it is pretty easy to repartition and format the hard drive.

---

### Post by Lightstar on 2010-04-24
I'm not sure this is a good idea for a thread, might give some people some bad ideas.

As others have said, gparted and other partition editors can be dangerous.  Accessing private files is not very nice either.

---

### Post by tica vun on 2010-04-24
No harm in specifically using liveCDs. Anything you can screw up with a liveCD, you can screw up with a normal installation.

---

### Post by arashiko28 on 2010-04-24
AS long as you don't play with gparted on a live CD session, I doubt you can actually harm your computer, and for the usage of the CD/DVD rom, I think it's the same as playing a game or a DVD movie, no??? Actually, once loaded, the drive rests until you do something that needs refreshing, at least it happens like this for me :P

---

### Post by undecim on 2010-04-24
Two things I can think of:

1: It doesn't have all the security updates. That's a lot less dangerous on a live CD though, nothing is saved, so getting for example, a trojan from, a PDF file due to a vulnerability in the viewer isn't permanent unless it installs itself to the hard drive.

2: You don't need a password most of the time to get root access, which makes it easier to mess up your computer and for hackers, trojans, etc to get root access. Again, this isn't necessarily permanent though.

---

### Post by Ebere on 2010-04-24
> **anantshri said:**
> Please share your thoughts how live CD could be dangerous.

Make a saw kerf in the end of a broom handle.

Break the live cd in such a way as to get a spear point out of it.

Stick your new spear point in the saw kerf on the broom handle, and duct tape in place. (Pointy end, pointing out.) (Careful not to put the duct tape over the pointy end !)

Now go huntin for wabbit.

---

### Post by Directive 4 on 2010-04-24
wheels on death moon buggy

---

### Post by MCVenom on 2010-04-24
I once got rather angry and deleted someone's Windows System32 folder from a LiveCD, I'm not very proud of that. :|

They say physical access is root access, a LiveCD can be a nightmare in the wrong hands.

---

### Post by square_root on 2010-04-24
Make a hat using the liveCD for a brim and who cares what else for the body of the hat. Knock on Mr Goldfinger's door and ask for Oddjob. Give Oddjob a special hat gift for whatever reason. Go and stand in Mr Goldfinger's garden and pretend to be statue. Wait.

What the heck do I know eh

---

### Post by cascade9 on 2010-04-24
I *think* it could be possible to damage some hardware with a liveCD, if the hardware is new enough and the liveCD old enough. 

> **BlackOtaku said:**
> I once got rather angry and deleted someone's Windows System32 folder from a LiveCD, I'm not very proud of that. :|

They say physical access is root access, a LiveCD can be a nightmare in the wrong hands.

Yes, physical access pretty much = root access. You dont need a liveCD to do damamge to windows, cracking the password is very easy.

---

### Post by Directive 4 on 2010-04-24
put 10,000 in a box and drop out of flying machine,

---

### Post by nerdopolis on 2010-04-24
yes. it IS possible for a rouge live cd to exist and do bad things to installed systems. Its pretty easy for a live cd to detect your os with os-prober, the command GRUB uses to find oses, and chroot into it with a script. 

In fact I make a live cd that allows you to control your Ubuntu system 'offline' for the case that it becomes unbootable or unusable, which detects your system, so it can give you GUI tools to get it booted again, so its very possible for some one else to use the same methods of detecting the system and mounting it to do bad things, automatically upon boot. (FYI: Mine does NOT do bad things automatically)

----------------------------------------------
Also a normal live cd can also be used to do bad things to your system. some people might think that since they are in a live cd environment where every thing disappears,  they might think its a good time to try out that command that writes all zeros to the hard disk or something, to see what happens, and take out the live cd thinking everything will go back. of course thats wrong. (so no one try it please) 

I brainstormed about the idea that people might use a live cd to experimentally run bad commands thinking they are safe, when they are not here: [http://brainstorm.ubuntu.com/idea/21545/](http://brainstorm.ubuntu.com/idea/21545/) a while back, but it seemed to have slipped under the radar.

----------------------------------------------
or someone could use a live cd to sneak in some rouge actions while your away from your system. as they say physical access is total access, but if you are now worried about that, you could password protect your bios from allowing a CD boot...

---

### Post by Directive 4 on 2010-04-24
cut into ninja star shape and throw at commuters on train

---

### Post by dearingj on 2010-04-24
My school protects their computers using [DeepFreeze]("http://www.faronics.com/html/deepfreeze.asp"), which prevents us students from making any permanent writes to the hard drive while running Windows. Booting a computer from a Live CD allows me to bypass DeepFreeze's protection.

---

### Post by Georgia boy on 2010-04-24
But, don't everyone say to use a Live CD to try out Ubuntu before installing? At this rate then a person could royally screw up their system without being aware of it and then shut down and have a system that don't work? If so then a big ouch.

Tom

---

### Post by red_Marvin on 2010-04-24
> **Georgia boy said:**
> But, don't everyone say to use a Live CD to try out Ubuntu before installing? At this rate then a person could royally screw up their system without being aware of it and then shut down and have a system that don't work? If so then a big ouch.

Tom

There is a difference between trying out the system, and format c:\ and wonder where all the files went.

---

### Post by Georgia boy on 2010-04-24
Oh so true, but who would do that? Never mind, even though I'm not that great on computers etc I'd never think of doing so but guess that there are some who would do so without even thinking of it. Would be a big blunder at that. You could tell from some of the questions I've asked in the past and probably in the future I wouldn't do something like that on my own.
Can't see why someone would do something like that but there are all types aren't there?

Tom

---

### Post by dragos240 on 2010-04-24
Sharpen the edges of the livecd and throw it.

---

### Post by arashiko28 on 2010-04-24
> **Georgia boy said:**
> Oh so true, but who would do that? Never mind, even though I'm not that great on computers etc I'd never think of doing so but guess that there are some who would do so without even thinking of it. Would be a big blunder at that. You could tell from some of the questions I've asked in the past and probably in the future I wouldn't do something like that on my own.
Can't see why someone would do something like that but there are all types aren't there?

Tom

Even then, if you realize soon enough, something can be done, I myself messed up pretty badly last year when I deleted the wrong partition, while on live CD and even though, I crossed my fingers, canceled installation and click every back button I found and voilà, no harm done...

I did get to the verge of a heart attack, though...

---

### Post by swoll1980 on 2010-04-24
> **tica vun said:**
> No harm in specifically using liveCDs. Anything you can screw up with a liveCD, you can screw up with a normal installation.

Sure there is. When we use our live cds at school we have root access to files that we shouldn't. The IT staff hasn't realized the live CDs have ntfs read/write capabilities. Back in the day Linux couldn't do this.

---

### Post by renkinjutsu on 2010-04-24
> **red_Marvin said:**
> There is a difference between trying out the system, and format c:\ and wonder where all the files went.

I would think formatting "/dev/sda1" is different from formatting "C:\" .. it's PERFECTLY safe :confused:

---

### Post by red_Marvin on 2010-04-25
'Formatting' *anything* should hopefully ring a couple bells for anyone trying out the live cd, enough bells to at least make them double check what they are formatting.

I can't play the piano and not everyone is cut out to be a sysadmin. It is not the piano's fault that I can't play it.

---

### Post by nerdopolis on 2010-05-07
> **red_Marvin said:**
> 'Formatting' *anything* should hopefully ring a couple bells for anyone trying out the live cd, enough bells to at least make them double check what they are formatting.

I can't play the piano and not everyone is cut out to be a sysadmin. It is not the piano's fault that I can't play it.

It won't for the people that don't know what the word 'formatting' means. At that point its not the fault of the live cd, but someone might try it on a live cd thinking that once they eject the Live CD, everything goes back to the way it was...

---

### Post by wilee-nilee on 2010-05-07
Just stay away from hirens, unless you want to really get wild.

---

