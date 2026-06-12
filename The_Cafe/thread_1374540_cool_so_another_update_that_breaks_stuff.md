---
title: "cool so another update that breaks stuff"
date: 2010-01-06
forum: The Cafe
---

### Post by eponymous on 2010-01-06
Just updated the kernel through automatic update and now I've got no sound and can't mount my 2nd local drive. Posting this here cause I just wanted to bitch don't want anybody to actually expend effort on me. I'll probably just hack away until everything works again, like usual.

I'm a little frustrated but really it's more embarrassing than anything. Ubuntu is the #1 "alternative" operating system and yet a couple times a year an update gets pushed out that forces me to spend hours googling for solutions and mucking about in the terminal to get basic things fixed. *Le sigh.*

---

### Post by eponymous on 2010-01-06
That being said, I'm not going anywhere.

---

### Post by earthpigg on 2010-01-06
have you tried using the old kernel listed in the grub menu?

---

### Post by eponymous on 2010-01-06
that was going to be step 3. i commented the filesystem out of fstab, then put it back in and ran mount -a and that worked. no clue why but that's easy enough for now.

---

### Post by Lambertus on 2010-01-06
For the record:

The upgrade loaded two days ago, ruined the connections for the wbar in the 9.10 setup. This is the error:

***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_free_image();

    With the parameter:

    image

    being NULL. Please fix your program.
/usr/share/wbar/font/10 -> Couldn't load font.

Considering the recent tinkering in the command line and such needed to get the bar going, and now having to tinker more for what looks like a trifle of an app is discouraging. 

It changed setting to default in Evolution.
The upgrade will not be loaded on my other machines.

---

### Post by cariboo on 2010-01-06
> **Lambertus said:**
> For the record:

The upgrade loaded two days ago, ruined the connections for the wbar in the 9.10 setup. This is the error:

***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_free_image();

    With the parameter:

    image

    being NULL. Please fix your program.
/usr/share/wbar/font/10 -> Couldn't load font.

Considering the recent tinkering in the command line and such needed to get the bar going, and now having to tinker more for what looks like a trifle of an app is discouraging. 

It changed setting to default in Evolution.
The upgrade will not be loaded on my other machines.

Are you asking for help?

---

### Post by Nerd King on 2010-01-07
I've not tried it yet as I'm on 32.2 myself. I can highly recommend it. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/) for those who are interested, combine with xorg-edgers ppa if you're an ATI user and you get open source 3d thrown in free.

---

### Post by Icehuck on 2010-01-07
> **eponymous said:**
> Just updated the kernel through automatic update and now I've got no sound and can't mount my 2nd local drive. Posting this here cause I just wanted to bitch don't want anybody to actually expend effort on me. I'll probably just hack away until everything works again, like usual.

I'm a little frustrated but really it's more embarrassing than anything. Ubuntu is the #1 "alternative" operating system and yet a couple times a year an update gets pushed out that forces me to spend hours googling for solutions and mucking about in the terminal to get basic things fixed. *Le sigh.*

This is the world of Linux on the desktop. Your machine works today but tomorrow it might not.

---

### Post by magmon on 2010-01-07
> **Nerd King said:**
> I've not tried it yet as I'm on 32.2 myself. I can highly recommend it. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/) for those who are interested, combine with xorg-edgers ppa if you're an ATI user and you get open source 3d thrown in free.

If I could acquire a tutorial, you would be my new hero.

---

### Post by Warpnow on 2010-01-07
> **Icehuck said:**
> This is the world of Linux on the desktop. Your machine works today but tomorrow it might not.

Not the world of linux on the desktop, just the world of ubuntu and other often-updated distributions

Go install debian stable. The distribution will stay solid for a long time, but you won't have the shiniest things.

---

### Post by Icehuck on 2010-01-07
> **Warpnow said:**
> Not the world of linux on the desktop, just the world of ubuntu and other often-updated distributions

Go install debian stable. The distribution will stay solid for a long time, but you won't have the shiniest things.

Yep, until I apt-get install and get a bunch of junk dependencies that weren't dependencies. Debian? Been there done that, no thanks.

---

### Post by Hallvor on 2010-01-07
> **Icehuck said:**
> Yep, until I apt-get install and get a bunch of junk dependencies that weren't dependencies. Debian? Been there done that, no thanks.

You have to expect a little instability if you use a bleeding edge distro. Ubuntu is essentially a fork of Debian Sid, so you can`t expect them to iron out all the bugs in a very short time.

---

### Post by Icehuck on 2010-01-07
> **Hallvor said:**
> You have to expect a little instability if you use a bleeding edge distro. Ubuntu is essentially a fork of Debian Sid, so you can`t expect them to iron out all the bugs in a very short time.

This isn't my first rodeo. I've used Debian, Slackware, Gentoo, LFS, Ubuntu, Arch, OpenSUSE, CentOS, DSL, Puppy, wolvix, Crux, and a bunch of others I can't remember. Everyone one of them will work today, maybe not tomorrow. Two days after installing debian lenny I had a new kernel ready to be downloaded.

---

### Post by Hallvor on 2010-01-07
> **Icehuck said:**
> Two days after installing debian lenny I had a new kernel ready to be downloaded.

And it broke your system?

---

### Post by Nerd King on 2010-01-07
I did one elsewhere on a thread about ATI coming of age.. 

[http://ubuntuforums.org/showpost.php?p=8448508&postcount=101](http://ubuntuforums.org/showpost.php?p=8448508&postcount=101)

Change [http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/) to [http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.2/](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.2/) to get the latest and greatest.

---

### Post by Techsnap on 2010-01-07
> You have to expect a little instability if you use a bleeding edge distro. Ubuntu is essentially a fork of Debian Sid, so you can`t expect them to iron out all the bugs in a very short time.

Ubuntu isn't as cutting edge as other distros which manage to hold it together. 

> Ubuntu is the #1 "alternative" operating system and yet a couple times a year an update gets pushed out that forces me to spend hours googling for solutions and mucking about in the terminal to get basic things fixed. Le sigh.

Exactly, this is what annoys me the most. A lot of people push Ubuntu as "THE" Linux distro (hahahaha) yet when something breaks like this it's either your fault, your lack of understanding or because you're running a "Cutting Edge Distro". I understand why you are angry, it makes sense.

---

### Post by Hallvor on 2010-01-07
> **Techsnap said:**
> Ubuntu isn't as cutting edge as other distros which manage to hold it together. 


Well I have to agree that it isn`t the best compromise between stability and bleeding edge out there.

---

### Post by ~sHyLoCk~ on 2010-01-07
Edited.

---

### Post by Xbehave on 2010-01-07
Choosing a different entry isn't exactly the end of the world (it's one reboot and then you just wait till a new kernel pops along) and unless you've done something strange your old kernels will still be there. 

> **Icehuck said:**
> This isn't my first rodeo. I've used Debian, Slackware, Gentoo, LFS, Ubuntu, Arch, OpenSUSE, CentOS, DSL, Puppy, wolvix, Crux, and a bunch of others I can't remember. Everyone one of them will work today, maybe not tomorrow.It sounds like you switch distros instead of fix problems, if you couldn't get a stable Debian/slackware/centOS install, you either used them years ago or do some real damage to your setups. 

> Two days after installing debian lenny I had a new kernel ready to be downloaded.Did you install lenny when it was debian stable? I ran it for months and all i got were security updates, no breakages nothing

---

### Post by mutex023 on 2010-01-07
Why is everyone so anxious to install updates ?
In my opinion, updates are overhyped.
I've till now never updated any ubuntu I installed, I always close the update manager when it pops up (annoying).
As a rule, update only if you have some problem. If you don't have any, why create problems by installing updates.

---

### Post by Techsnap on 2010-01-07
> As a rule, update only if you have some problem. If you don't have any, why create problems by installing updates.

Well if that works for you then great, however that's a really flawed logic.

---

### Post by Nerd King on 2010-01-07
> **mutex023 said:**
> Why is everyone so anxious to install updates ?
In my opinion, updates are overhyped.
I've till now never updated any ubuntu I installed, I always close the update manager when it pops up (annoying).
As a rule, update only if you have some problem. If you don't have any, why create problems by installing updates.
Security. Even linux needs security patches.

---

### Post by speedwell68 on 2010-01-07
If you want to enjoy 100% stability then run 8.04 LTS and upgrade at the next LTS.  If you do mind having to tweak and play then run the latest 9.10.  I choose to run the latest and TBH I enjoy 100% stability.

---

### Post by CharlesA on 2010-01-07
> **Nerd King said:**
> Security. Even linux needs security patches.

This.

> **speedwell68 said:**
> If you want to enjoy 100% stability then run 8.04 LTS and upgrade at the next LTS.  If you do mind having to tweak and play then run the latest 9.10.  I choose to run the latest and TBH I enjoy 100% stability.

Same here. Altho, every time there is a kernel upgrade, the drivers for my RAID array "break." Simple fix, since all I need to do is reinstall them.

---

### Post by markp1989 on 2010-01-07
> **Hallvor said:**
> You have to expect a little instability if you use a bleeding edge distro. Ubuntu is essentially a fork of Debian Sid, so you can`t expect them to iron out all the bugs in a very short time.

ubuntu isnt bleeding edge, i consider it a stable distro most of the time, i have never had an update break my ubuntu install i have for arch though  , which is why i multiboot arch and ubuntu, using ubuntu as backup

---

### Post by MasterNetra on 2010-01-07
lol Just installed Kubuntu 9.10 replacing Ubuntu. Kubuntu was breaking on me a bit frequently up until I got the updates installed. Now she ok.

---

### Post by kostkon on 2010-01-07
> **eponymous said:**
> Just updated the kernel through automatic update and now I've got no sound and can't mount my 2nd local drive. Posting this here cause I just wanted to bitch don't want anybody to actually expend effort on me. I'll probably just hack away until everything works again, like usual.

I'm a little frustrated but really it's more embarrassing than anything. Ubuntu is the #1 "alternative" operating system and yet a couple times a year an update gets pushed out that forces me to spend hours googling for solutions and mucking about in the terminal to get basic things fixed. *Le sigh.*
Sorry, but I would like to ask the obvious: which update and from where?

---

### Post by RiceMonster on 2010-01-07
> **Hallvor said:**
> You have to expect a little instability if you use a bleeding edge distro. Ubuntu is essentially a fork of Debian Sid, so you can`t expect them to iron out all the bugs in a very short time.

But for a distro who's updates are only supposed to be security fixes, updates really shouldn't be breaking things.

Ubuntu IS NOT bleeding edge, people. 

> **mutex023 said:**
> Why is everyone so anxious to install updates ?
In my opinion, updates are overhyped.
I've till now never updated any ubuntu I installed, I always close the update manager when it pops up (annoying).
As a rule, update only if you have some problem. If you don't have any, why create problems by installing updates.

You don't want security updates? Really?

---

### Post by Hallvor on 2010-01-07
> **markp1989 said:**
> ubuntu isnt bleeding edge, i consider it a stable distro most of the time, i have never had an update break my ubuntu install i have for arch though  , which is why i multiboot arch and ubuntu, using ubuntu as backup

It depends what you are used to, I guess. I run Debian most of the time. Ubuntu being a fork of Debian Sid, yes, I think the new releases of Ubuntu are bleeding edge.

---

### Post by Xbehave on 2010-01-07
> **RiceMonster said:**
> But for a distro who's updates are only supposed to be security fixes, updates really shouldn't be breaking things.

Ubuntu IS NOT bleeding edge, people. 



You don't want security updates? Really?
It's not bleeding edge, but it's also not stable, it's somewhere in between so some breakage is acceptable. If you want a more stable OS then ubuntu isn't for you (if you want a more bleeding edge OS then it's not for you either). Personally, while running released versions of ubuntu, security updates have only caused problems when i had prop drivers and once a system is setup it is pretty rock solid (that said once set up any non-rolling release distro has been rock solid for me, fedora/ubuntu/debian), but OP claims that all linux distros have caused him problems so obviously I'm just special.

> **Hallvor said:**
> It depends what you are used to, I guess. I run Debian most of the time. Ubuntu being a fork of Debian Sid, yes, I think the new releases of Ubuntu are bleeding edge.
In fairness debian users aren't aware it's even the 21st century yet :P

---

### Post by felious_fadger on 2010-01-07
it took out my wired connection >.>

that is like the third time that has happened in a year. do they ever do testing before releasing?

---

### Post by arrancaru on 2010-01-07
What I don't like is updating libnoonecares.1.2.3 to version 1.2.4 in the default update rules, must untick recommended setting in update manager.

---

### Post by Techsnap on 2010-01-07
> that is like the third time that has happened in a year. do they ever do testing before releasing?

Being a stable distro you'd expect so. If anyone says well you should use the LTS they're still wrong. As I said, I use more cutting edge distros (heck my Slackware -current install is more current than Ubuntu 9.10) and I've never experienced any breakage bar a few expected instances. 

Stable Distros should NOT get breakage.

---

### Post by eponymous on 2010-01-07
> **kostkon said:**
> Sorry, but I would like to ask the obvious: which update and from where?

sorry it was the last kernel update, running ubuntu 9.10

---

### Post by fatcrab on 2010-01-07
Is there a truly stable distro?

---

### Post by Skripka on 2010-01-07
> **Techsnap said:**
> Being a stable distro you'd expect so. If anyone says well you should use the LTS they're still wrong. As I said, I use more cutting edge distros (heck my Slackware -current install is more current than Ubuntu 9.10) and I've never experienced any breakage bar a few expected instances. 

Stable Distros should NOT get breakage.

Whatever the word "stable" actually means....

---

### Post by Skripka on 2010-01-07
> **eponymous said:**
> sorry it was the last kernel update, running ubuntu 9.10

Would that be to 2.6.31 ?  Wierd.  Shoot the packager.  If you like 2.6.31 you'll LOVE 2.6.32, especially if you are using the FOSS drivers.

---

### Post by chessnerd on 2010-01-07
Yeah, I just had two issues:

1. Wireless took 4 minutes to connect
2. Started Rhythmbox as the only open window, played some Journey, minimized and... CRASH!

I have never had a Linux crash before. The screen, even mouse, froze up and vibrated ever so slightly while one second of Stone in Love looped endlessly. 

Oh, and thank you to the Ubuntu dev who came up with the idea to remove Ctrl-Alt-Backspace. I forgot about the fact that it was gone and didn't think to put it back. Needed to hard reboot. Hopefully I'll remember to restore it for subsequent installs. Either way, it's back now.

Into the previous kernel, which was acting a bit funny as well. So I went back to the new one and it seems to be working okay for now. 

Since my other kernel was acting up too, maybe it wasn't the kernel update. Maybe it was one of the other updates that got installed at the same time. I don't know.

---

### Post by Techsnap on 2010-01-07
> Whatever the word "stable" actually means.

Well of a distro with bug #1 beat Windows marketshare, Ubuntu should not be at the stage where updates break stuff.

---

### Post by Skripka on 2010-01-07
> **Techsnap said:**
> Well of a distro with bug #1 beat Windows marketshare, Ubuntu should not be at the stage where updates break stuff.

Windows updates break things from time to time.  Updates to MacOS have broken things from time to time.  Such is life-and they are centralized monolithic corps that develop things, not herds of cats.

And no one really knows what "stable" is nor how we get to being "stable" from where we are now.

---

