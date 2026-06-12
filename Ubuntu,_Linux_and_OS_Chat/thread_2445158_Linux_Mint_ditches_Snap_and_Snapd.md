---
title: "Linux Mint ditches Snap and Snapd"
date: 2020-06-10
forum: Ubuntu, Linux and OS Chat
---

### Post by webaake on 2020-06-10
Linux Mint removes Snap and Snapd from auto install at installation. ```
A year later, in the Ubuntu 20.04 package base, the Chromium package is indeed empty and acting, without your consent, as a backdoor by connecting your computer to the Ubuntu Store. Applications in this store cannot be patched, or pinned. You can’t audit them, hold them, modify them or even point snap to a different store. You’ve as much empowerment with this as if you were using proprietary software, i.e. none. This is in effect similar to a commercial proprietary solution, but with two major differences: It runs as root, and it installs itself without asking you.

First, I’m happy to confirm that Linux Mint 20, like previous Mint releases will not ship with any snaps or snapd installed.
``` 

Source: [https://blog.linuxmint.com/?p=3906](https://blog.linuxmint.com/?p=3906)

---

### Post by mastablasta on 2020-06-10
and Cannonical already replied why they did it like that. they don't have resources to maintain the browser for the all different versions of OS (14.04 Extendend support, 16.04, 18.04, 20.04 and any active releases in between) x multiple versions of architecture (i686, ARM...). so they packaged it in snap which enables them to just create different architecture versions for each update, while snap can be the same for all OS versions.

i think majority of applications will eventually really go into snap or flatpack. they do make sense for developers. however i also think they should improve the performance, so that apps don't take a performance hit/reduction.

---

### Post by kevdog on 2020-06-10
Is Mint turning to Flatpack?  I thought the major driving force for Mint to ditch snap was because Canonical is the sole source for the packages.  It's essentially a closed system.

---

### Post by CatKiller on 2020-06-10
The driving force behind it is that Mint is losing users to Pop or Manjaro, but ranting and raving about snaps means that people write articles about them and remind people that they exist.

It's not a closed system.

---

### Post by &amp;KyT$0P# on 2020-06-10
From that blog link -
>     In Linux Mint 20, APT will forbid snapd from getting installed.

You’ll still be able to install it yourself and we’ll document this in the release notes, but by default APT won’t allow repository packages from doing this on your behalf.

How are they going to achieve this?

---

### Post by jeremy31 on 2020-06-10
This is nothing new, Mint 19 didn't have snap installed by default and had flatpack software available in the Software Manager

---

### Post by webaake on 2020-06-11
Well, the article I referenced is from 1 of june and no one mentioned it here, on this forum. So I thought it could be of general interest for all Ubuntu users.

---

### Post by mastablasta on 2020-06-11
though, i am not sure why OS devs don't help with snap development rather than just being bothered by it. i mean it does have benefits and if they could remove the minuses in a way it could be a very good thing.

---

### Post by kevindoor77 on 2020-06-14
Can someone help a stupid person like me to understand this topic about snaps? Because for me it seems that Ubuntu is favoring convenience for the developers over security and freedom of the users, or am I wrong?

thx in advance

---

### Post by CatKiller on 2020-06-14
> **kevindoor77 said:**
> am I wrong?

Yes, you're wrong. 

This has already been [ discussed before](https://ubuntuforums.org/showthread.php?t=2442097&p=13960355#post13960355).

---

### Post by kevindoor77 on 2020-06-16
> **CatKiller said:**
> Yes, you're wrong. 

This has already been [ discussed before]("https://ubuntuforums.org/showthread.php?t=2442097&p=13960355#post13960355").

But what about some points I hear about...like:

1) closed source infrastructure, proprietary store
2) centralised instead of decentralised
3) forced autoupdating
4) can&#8217;t opt out of the non-FOSS packages
5) no option to audit things
6) deceiving: secretly installing snaps instead of debs
7) "flatpaks tell you upfront what permissions they need to operate when you install them but snaps don't"
8) to the point of favoring convenience for the developers over the freedom of the users....I hear then something like this on forums: "this is indeed less interesting for the end user but devs that i talk to are most of the time really thrilled by the ease of packaging a snap.".....i think this guy "ogra", who said that, even works at Canonical......

Again, I'm a noob who doesn't even use the terminal (much), but it seems to me that Ubuntu is more an more moving away from open source, in which I do ask myself, why don't I just go back to Windows then.

---

### Post by mastablasta on 2020-06-16
> **kevindoor77 said:**
> But what about some points I hear about...like:

1) closed source infrastructure, proprietary store
2) centralised instead of decentralised
3) forced autoupdating
4) can’t opt out of the non-FOSS packages
5) no option to audit things

huh? it's a package that has all the needed components. think portable apps files on windows.
> 
6) deceiving: secretly installing snaps instead of debs

it's not deceiving, if it is published in release notes.

> 
7) "flatpaks tell you upfront what permissions they need to operate when you install them but snaps don't"
8) to the point of favoring convenience for the developers over the freedom of the users....I hear then something like this on forums: "this is indeed less interesting for the end user but devs that i talk to are most of the time really thrilled by the ease of packaging a snap.".....i think this guy "ogra", who said that, even works at Canonical......

Again, I'm a noob who doesn't even use the terminal (much), but it seems to me that Ubuntu is more an more moving away from open source, in which I do ask myself, why don't I just go back to Windows then.

i can't comment on 7, but to me the idea of portable package in linux seems a good one. i am not sure what freedom of user is mentioned here. you can install it or not. you can install older version on new OS or new version of app on old OS. seems like freedom to me. and the package as i understand is containerised and you can still see the source, right? so what is this huge difference? because they are all in snapstore? well how well did it work out when there was no central repo in android? even now that is centralized malware still creeps in.

---

### Post by webaake on 2020-06-16
> think portable apps files on windows

No, I don't want to think Windows! At all. Ever.

More centralization leads to less freedom and more closed sorce.

One way of getting around this is to compile the apps you need yourself. I've already started this with some apps.

Another way is to avoid distros with snap and go to distros like PCLinuxOS or Mint.

PCLinuxOS doesn't even have systemd. Great!

---

### Post by CatKiller on 2020-06-16
> **kevindoor77 said:**
> But what about

Yes, that was all covered in the other thread.

---

### Post by grahammechanical on 2020-06-16
>  but it seems to me that Ubuntu is more an more moving away from open  source, 

You are entitled to your opinion. Of course you are. I do not see any evidence for this accusation. But then again I have only been using Ubuntu for more than a decade. What do I know?

Using a FOSS distribution does not take away our freedom to use an OS or application for which a licence has to be purchased. Are you saying we should be denied the right to use proprietary software? I do not own a smartphone but it is not because I joined some kind of cult where buying a closed source OS as part of the purchase price is forbidden. 

> in which I do ask myself, why don't I just go back to Windows  then.

You have the freedom to do that. If you did it would not trouble me one little bit.

Regards.

---

### Post by Shibblet on 2020-06-16
Here are my questions:

**1. Have we given Snaps enough time to mature?**
I have a couple of Snaps installed, and they don't run as quickly as other packages.  Some Snaps that I have installed, do not have the same functionality as regular packages also.  MakeMKV will not allow me to select a different place to save my rips, whereas the regular package does.

**2. Why have multiple forms of this?**
Snaps, Flatpak, Docker, AppImage, etc...  Is this another way of separating distributions like .RPM and .DEB did?

---

### Post by grahammechanical on 2020-06-16
> **2. Why have multiple forms of this?**
Snaps, Flatpak, Docker, AppImage, etc...  Is this another way of separating distributions like .RPM and .DEB did? 				

That is what is most likely to happen but it is not intentional. There are some distributions that are commercial enterprises. Whether the people running those commercial organizations have a master plan to rule the world, I cannot say. Free & Open Source Software allows and often encourages diversity. One way to prevent it happening is to take out the competition. I can think of a couple of corporations (non-FOSS) that have been very good at doing that over the decades. 

As long as the source code continues to be licensed under an open source licence then there will be those who will set themselves the goal of keeping Linux free & open source with the benefits and disadvantages that come with it.

Regards

---

### Post by CatKiller on 2020-06-16
> **Shibblet said:**
> I have a couple of Snaps installed, and they don't run as quickly as other packages. 

You'll probably find that they *run* fine, but take a long time to start up. The filesystem is squashfs, and all of the environment stuff that the application's expecting need to be faked because it's sandboxed. That takes time. Second run is generally a lot quicker, since that stuff's already set up.

> MakeMKV will not allow me to select a different place to save my rips, whereas the regular package does.

Snap applications are sandboxed. You need to give them permission (removable-media) to be able to access files that aren't in your Home folder. You can do it in the Snap Store, or make the connection with the snap command.

> Snaps, Flatpak, Docker, AppImage, etc...

Snaps, like Unity and Mir, were created for the Ubuntu Phone, since the technologies available at the time (AppImage, Gnome, X11) weren't up to the task. Flatpak came later.

Docker is most of the way to a VM rather than just distributing single applications.

---

### Post by mastablasta on 2020-06-17
> **Shibblet said:**
> Here are my questions:

**1. Have we given Snaps enough time to mature?**
I have a couple of Snaps installed, and they don't run as quickly as other packages.  Some Snaps that I have installed, do not have the same functionality as regular packages also.  MakeMKV will not allow me to select a different place to save my rips, whereas the regular package does.


probably not. the idea is young and from Ubuntu point it just came to LTS users ("stable OS lovers"). Over the next few years we could expect more scrutiny and hopefully bug reports from the users that hop from LTS to LTS. it is only then that issues will get triaged and then hopefully addressed. bug changes and implementing inovation takes time. the more people use the software the more refined it gets. since 10.04 the only time i went with non LTS was when i installed 11.10 as it supposedly resolved my sound issue. partially it was true. but then 12.04, 14.04 and now 18.04 (yes i skipped the 16.04 due to upgrade bug). i plan to upgrade to 20.04 next year or maybe i will stay on 18.04. i am still deciding.

---

### Post by aaronrv2008 on 2020-08-09
True. In my opinion, I like snaps. Having one app store for all distros sounds good. I don't care about it being closed source :D

---

