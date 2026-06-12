---
title: "[Whine] Stop updating Hardy! I need to work!"
date: 2008-06-19
forum: Testimonials &amp; Experiences
---

### Post by stormbolter on 2008-06-19
Look, I understand that updates usually fix security errors, and because of that are important. But, please, I cannot restore everything it doesn't work after an update because I NEED TO WORK!

Example 1:
After the last kernel update, I wasn't able to start VirtualBox. Seems that someone forgot to add the necessary modules. That, and because I have a bleeding-beeping-edge video card, everytime I update the kernel I need to recompile the drivers. It happened so often the past month I made a pre-generated xorg.conf to accelerate the process.

Example 2:
Last update broke my premounted windows partitions, again with the "you need to be root to mount /media/winsys".

Let me tell you that, because I do not code for fun, I DO NOT ENJOY GOING 
THROUGHT THE COMMAND LINE EVERYTIME YOU UPDATE SOMETHING AND BREAK THE REST!

Arf, arf...

Thanks. I feel much better.

Now seriously. What is happening with Hoary? It is by far the worst, less stable Ubuntu distro I've ever tested (granted, I'm only here since 6.10 but...), and everything that's supposed to be revolutionary (like pulseAudio) simply doesn't work in my configuration. Yeah, I probably could make it work, but as stated above, I do not have time to play.

Guys, this is the LTS, it is supposed to be stable and a bit conservative, and right now I'm thinking of downgrading to 7.10 and sitting until 8.10 is ready.

---

### Post by dasunst3r on 2008-06-19
If you don't like to update, you really don't have to.  To disable update notification:
[list=1]
[*]Go to System -> Preferences -> Sessions
[*]Under startup programs, uncheck *Update Notifier*
[*]Close out of *Sessions Preferences*
[*]Go to System -> Administration -> Software Sources
[*]Under *Updates*, uncheck *Check for Updates* under the *Automatic updates* section.
[*]Close out of *Software Sources*, and you're finished.
[/list]

Example 1: I've had VirtualBox break because of a kernel update.  You can fix that by typing in the terminal *sudo dpkg-reconfigure virtualbox*.  Also, if your "bleeding edge video card" is an nVidia card, you should install the package *nvidia-glx-new-envy*.  This will insert the module in the DKMS, which will recompile the module for you every time you update kernels.

Example 2: How are you mounting this /media/winsys?  What filesystem is it?

By the way, Linux and open-source software is not necessarily coded by people who do it just for fun.  There are people who do this full-time and get a salary for it.

---

### Post by tgrimley on 2008-06-19
I know how you feel.. I was gone for a week and I came back to 78 updates :)

---

### Post by jrusso2 on 2008-06-19
Still using Gutsy and its great.  But I still get some updates.

---

### Post by wolfen69 on 2008-06-19
why didnt you stay with gutsy until 8.04.1 came out? there will be fewer updates after that. it is like this with every release. early adopters always get alot of updates. complaining about it will not change this.  as dasunst3r said, you can always turn them off. no one is forcing you to do the updates.

---

### Post by stormbolter on 2008-06-19
to Dasunst3r

Thank you for your kind response. I did not know about the envy drivers until you mentioned it, and I will try as soon as I have an opportunity.

And I did know how to disable updates, but also I understand that updates are important. I know it isn't what it seem when I writed, but understand that it was a "whine" - my point was that, at least on my system, updates seem to break things more often than fix. It is something that did not happen in the previous incarnations of Ubuntu I tried (6.04, 7.04 and 7.10) unless I did something really bold (like a distro update or compiling a patch for my laptop -poor, poor tc1100-), so it broke (sometimes) when I expected to break.

VirtualBox: on each kernel update, there is a virtualbox-module package that has the same number, just that the last kernel doesn't have its accompanying virtualbox-module. Of course it was my surprise when it didn't start. I don't thing is a case of reconfiguring a package. The package didn't broke, it simply doesn't have the modules for the current kernel.

As for the winsys partition. For playing and applications that need 3D acceleration and Windows (Games, 3DStudio, Games, Rhinoceros, Games... Did I mentioned Games? :D), I dual-boot with Windows XP, of wich there are two big NTFS partitions (DataVault and WinSys -- forgive me for my lack of originality).

I don't know what has been updated, but before the update I could access as User to these partitions, and finally I decided to perma-mount (via fstab) them. Now it ask me to be root in order to mount these partitions.

--returning to illustrating my point, I feel that the upgrades something feel rushed and that this is a LTS. I prefer to be "in Danger" for a couple more days than to download twice a patch, the first to correct the vulnerability, and the second to fix everything the first patch broke.

And... excuse me if something sounds angry or else. English is not my native language and sometimes it can be misinterpreted (this is text, it doesn't convey very well emotions). I tried to raise my point trough a bit of humor, a bit of Irony, and a bit of Real Examples.

In any moment I never implied the people behind Ubuntu only code for fun. Ubuntu is the first distribution that made ME sense, and I respect both the professional and the user community although I never had much chance to collaborate (except spreading the word).

Again, thanks for the assistance. I will try some of the changes as soon I have an opportunity.

---

### Post by damis648 on 2008-06-19
I think you mean Hardy. But just use the propreietary drivers Ubuntu offers in System>Administration>Hardware Drivers.

---

### Post by Keyper7 on 2008-06-19
EDIT: The last reply from the OP, posted above almost simultaneously, made my post useless.

---

### Post by dje on 2008-06-19
LTS = Long Term Support not Long Term Stability, it does not necessarily mean stable it means it is supported for longer ;)

---

### Post by stormbolter on 2008-06-19
To Keyper: But I liked your post (in a fun way)! Mind you if I quote your choice of distro when writing my weekly post? :)

And, for commenting a bit of what you posted that seemed a bit serious. You can choose what not to update, but you can't ignore it. For example, in Windows XP, if I don't want to install certain patch, I can (how it was... nck, unc, ah, yes) UnCheck it, and then Windows Update asks me if I want it not notify me anymore of this patch. Of course I can go to the website and recheck for update manually, but it doesn't appear anymore (well, except this pesky Windows Genuine Advantage: is that, or the gun in the head, like your HHTE).

To Dje:
I installed last LTS on computers my customers wanted to use for light work (there were old P3 computers). I wanted them to be safe from viruses and I couldn't support them (they lived far from where I live) if they had a problem.

For me, LTS has been a synonim of stability. Well, until now :D

---

### Post by senorian on 2008-06-19
<LTS does not necessarily mean stable it means it is supported for longer >

This comment has been made by a number of posters in the past few months.
It sounds reasonable at first glance 
; but actually  it is not reasonable. This can be seen if we assume, for example,that there exists a Linux OS (not, of course Ubuntu) that offers a LTS version in which the updates are sloppy, incorrect, haphazard, break things that were previously working, ( you can supply more defects like these)
Is there any benefit in using a OS that promises long term support but is completely unstable?
The OS would be a disaster and nobody, NOBODY, would download it unless they were very masochistic 
So, A LTS system HAS to work.( be stable)

---

### Post by dje on 2008-06-19
> **senorian said:**
> <LTS does not necessarily mean stable it means it is supported for longer >

This comment has been made by a number of posters in the past few months.
It sounds reasonable at first glance 
; but actually  it is not reasonable. This can be seen if we assume, for example,that there exists a Linux OS (not, of course Ubuntu) that offers a LTS version in which the updates are sloppy, incorrect, haphazard, break things that were previously working, ( you can supply more defects like these)
Is there any benefit in using a OS that promises long term support but is completely unstable?
The OS would be a disaster and nobody, NOBODY, would download it unless they were very masochistic 
So, A LTS system HAS to work.( be stable)

It is a matter of opinion, personally, on my hardware, hardy heron is very stable and i like it very much

---

### Post by karellen on 2008-06-19
if a Linux distro works on a certain piece of hardware and another doesn't, there's no excuse for the latter

---

### Post by Keyper7 on 2008-06-19
> **stormbolter said:**
> To Keyper: But I liked your post (in a fun way)! Mind you if I quote your choice of distro when writing my weekly post? :)

You mean Ubuntu TE? (let's just leave people who didn't saw my original post speculate on what that means =P). Fine, but I own the copyright and will have a piece of any profit you might get from it. ;)

> **stormbolter said:**
> And, for commenting a bit of what you posted that seemed a bit serious. You can choose what not to update, but you can't ignore it. For example, in Windows XP, if I don't want to install certain patch, I can (how it was... nck, unc, ah, yes) UnCheck it, and then Windows Update asks me if I want it not notify me anymore of this patch. Of course I can go to the website and recheck for update manually, but it doesn't appear anymore (well, except this pesky Windows Genuine Advantage: is that, or the gun in the head, like your HHTE).

Synaptic has an option to put packages on hold. I believe the update notification will leave you alone if you do that. I'm not sure of how to do that, though, because I never tried it. :)

---

### Post by stchman on 2008-06-19
> **stormbolter said:**
> Look, I understand that updates usually fix security errors, and because of that are important. But, please, I cannot restore everything it doesn't work after an update because I NEED TO WORK!

Example 1:
After the last kernel update, I wasn't able to start VirtualBox. Seems that someone forgot to add the necessary modules. That, and because I have a bleeding-beeping-edge video card, everytime I update the kernel I need to recompile the drivers. It happened so often the past month I made a pre-generated xorg.conf to accelerate the process.

Example 2:
Last update broke my premounted windows partitions, again with the "you need to be root to mount /media/winsys".

Let me tell you that, because I do not code for fun, I DO NOT ENJOY GOING 
THROUGHT THE COMMAND LINE EVERYTIME YOU UPDATE SOMETHING AND BREAK THE REST!

Arf, arf...

Thanks. I feel much better.

Now seriously. What is happening with Hoary? It is by far the worst, less stable Ubuntu distro I've ever tested (granted, I'm only here since 6.10 but...), and everything that's supposed to be revolutionary (like pulseAudio) simply doesn't work in my configuration. Yeah, I probably could make it work, but as stated above, I do not have time to play.

Guys, this is the LTS, it is supposed to be stable and a bit conservative, and right now I'm thinking of downgrading to 7.10 and sitting until 8.10 is ready.

If a current state of Ubuntu works for you then by all means disable updates.  You do not have to install them.

---

