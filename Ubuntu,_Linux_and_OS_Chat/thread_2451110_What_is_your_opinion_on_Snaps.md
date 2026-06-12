---
title: "What is your opinion on Snaps?"
date: 2020-09-27
forum: Ubuntu, Linux and OS Chat
---

### Post by aaronrv2008 on 2020-09-27
What is your opinion on Snaps? Some people hate it, some people like it.

As for me, I like the idea for snaps. Having one app store for (almost) all Linux distros is actually a good idea.

I use snaps in distros like Solus where software is limited.

Plus, can't snap be open source?

---

### Post by TheFu on 2020-09-27
There was a long thread about this a few months ago. Please check that out.

---

### Post by oldfred on 2020-09-27
More info here:

boot time cut in half by removing snap, they since have improved boot somewhat
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

---

### Post by VMC on 2020-09-27
Don't use Snaps. Never will.

---

### Post by exploder on 2020-09-28
You will get very mixed answers on this. I personally like snaps but then I do not have many installed. I also have reasonably fast machines with SSD's too so I don't have issue with load times. Canonical has given me a great operating system, they have invested time and money in snaps and I refuse to bash them after them giving me so much. Snaps, flatpack and appimage all have their pros and cons. I appreciate the concept and think they will continue to get better over time.

---

### Post by poorguy on 2020-09-28
I like the concept of Snaps all dependencies and everything else you need rolled up into one software package.

Snaps are new so give them a chance to mature and developers a chance to get them tweaked to work better and perhaps they will be alright.

I've given some Snaps a try and OK they are slow to load and open although once loaded and opened  they work OK.

I'm  not using the most powerful computer so that could be why Snaps are slow to load and open.

---

### Post by mastablasta on 2020-09-29
> **poorguy said:**
> I like the concept of Snaps all dependencies and everything else you need rolled up into one software package.

wouldn't that also be possible with packing binaries and libraries together? like Linux portable applications. for example Tux Cart does it like that. you just unpack and run.

---

### Post by guiverc on 2020-09-29
I like the idea & concept of snaps. They make it easier for *devs* to provide later software, and if you're happy on an older LTS system, they allow you to easily access later software (without upgrade hassles of PPA & like solutions) etc.

I try and use *deb* based software though in preference, as 

- my primary box is a 2009 dell desktop, I don't have a lot of resources to spare!
- I'm also on the *development* cycle, so my software is pretty much the latest anyway

---

### Post by mastablasta on 2020-09-29
> **oldfred said:**
> 
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)


snaps start faster in Kubuntu? :D

---

### Post by Shibblet on 2020-09-29
> **mastablasta said:**
> snaps start faster in Kubuntu? :D

Do they?  I have always found that the Snap version of (insert software here) doesn't run as fast as just installing it from the Software Repos.

I don't really mind Snaps.  I actually like the idea quite a bit.  A non-distro-specific version of software that runs in it's own container, is a great idea.  The problem I have at this point, is that they seem to have some issues with functionality, and they run slow.

MakeMKV's Snap, for example, will not allow me to access mounted drives.  The Ubuntu PPA version works just fine, and loads up faster.

---

### Post by mikewhatever on 2020-09-29
> **Shibblet said:**
> Do they?  I have always found that the Snap version of (insert software here) doesn't run as fast as just installing it from the Software Repos.

I don't really mind Snaps.  I actually like the idea quite a bit.  A non-distro-specific version of software that runs in it's own container, is a great idea.  The problem I have at this point, is that they seem to have some issues with functionality, and they run slow.

MakeMKV's Snap, for example, will not allow me to access mounted drives.  The Ubuntu PPA version works just fine, and loads up faster.

This is because snaps are containerized. I thought you said it was a great idea.

---

### Post by kurt18947 on 2020-09-29
In certain applications snaps are quite useful. SWMBO would be beyond upset if she lost the use of Shutter. Shutter is available in 18.04 repos, it is not available in 20.04 repos. I've tried alternatives but she has her work flow down with shutter so not an easy switch - AT ALL. She will stay on 18.04 for the foreseeable future but eventually she's going to have to upgrade, probably to 22.04. Shutter as a snap will do what she needs to do.

---

### Post by CatKiller on 2020-09-29
> **Shibblet said:**
> MakeMKV's Snap, for example, will not allow me to access mounted drives.

You need to set the [removable-media permission]("https://snapcraft.io/docs/removable-media-interface") to allow the snap access to removable media. You can do it in the Snap Store or with the *snap* command. Already covered in the previously-linked thread.

---

### Post by Shibblet on 2020-09-30
> **mikewhatever said:**
> This is because snaps are containerized. I thought you said it was a great idea.

Well, it is a great "idea."  At this point in the Snap's "life-cycle" it's just not implemented very well.

> **CatKiller said:**
> You need to set the [removable-media permission]("https://snapcraft.io/docs/removable-media-interface") to allow the snap access to removable media. You can do it in the Snap Store or with the *snap* command. Already covered in the previously-linked thread.

Oh.  That's good to know.  Got any tricks to speed them up?  :p
I've been pretty lucky so far.  All of the software that I use is in the Repos, or has a PPA.  So, it's ***really*** not an issue for me, per se.

---

### Post by monkeybrain20122 on 2020-10-01
> **mastablasta said:**
> wouldn't that also be possible with packing binaries and libraries together? like Linux portable applications. for example Tux Cart does it like that. you just unpack and run.

Or blender

---

### Post by monkeybrain20122 on 2020-10-01
> **kurt18947 said:**
> In certain applications snaps are quite useful. SWMBO would be beyond upset if she lost the use of Shutter. Shutter is available in 18.04 repos, it is not available in 20.04 repos. I've tried alternatives but she has her work flow down with shutter so not an easy switch - AT ALL. She will stay on 18.04 for the foreseeable future but eventually she's going to have to upgrade, probably to 22.04. Shutter as a snap will do what she needs to do.

For focal you can get shutter form this [ppa]("https://launchpad.net/~linuxuprising/+archive/ubuntu/shutter").

---

### Post by monkeybrain20122 on 2020-10-01
I prefer flatpak to snap, seems cleaner in that you don't have to mount a bunch of volumes and you can control access to file systems for all flatpak apps with a unified, simple to use interface (flatseal)

---

### Post by Shibblet on 2020-10-02
> **monkeybrain20122 said:**
> I prefer flatpak to snap, seems cleaner in that you don't have to mount a bunch of volumes and you can control access to file systems for all flatpak apps with a unified, simple to use interface (flatseal)

I have heard a lot of good things about Flatpak's, but have not really needed to use any yet.

What I am hoping doesn't happen, is "exclusivity."  Kind of like platform specific titles on video game consoles.  You know... you can't play Halo on a Playstation...  Currently, some Snap Software exists that is not available anywhere else than the Snap store.  Now, this could be due to the author not wanting to have too many different ways for people to get the software (PPA's, GitHub, etc.)  But it could cause exclusivity... i.e. You can't run (insert software here) as a Snap, it's only available in Flatpak (or vice-versa.)

---

### Post by exploder on 2020-10-02
I watched a video not long ago, anyone can create a snap, flatpack or appimage.

---

### Post by CelticWarrior on 2020-10-02
> **exploder said:**
> I watched a video not long ago, anyone can create a snap, flatpack or appimage.

And anyone can create a DEB file.
What's your point?

---

