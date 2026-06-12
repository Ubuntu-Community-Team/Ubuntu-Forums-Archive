---
title: "Woohoo my Karmic woes are over!"
date: 2009-11-30
forum: The Cafe
---

### Post by Nerd King on 2009-11-30
So before, any heavy downloading over wireless on my atheros crapthing would lock the system. Just installed the .30 kernel and I'm all good. And it was so easy to do too! It's nice to be able to use Karmic on ALL my machines :)

---

### Post by sandyd on 2009-11-30
nice to see everything worked out!
/rant
isnt there ANY ubuntu release that isnt going to be a bit less buggy?
karmic = driver issues, somebody mainstream/upstream decided to change package names resulting in adobe flash installagion problems.
jaunty = pulseaudio
hardy.. (cant remember)
/rant

---

### Post by witeshark17 on 2009-11-30
Very glad to see that! :popcorn:

---

### Post by Psumi on 2009-11-30
> **carlee said:**
> karmic = driver issues, somebody mainstream/upstream decided to change package names resulting in adobe flash installagion problems.

karmic also has a broken gnome metapackage:

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/451266](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/451266)

---

### Post by Nerd King on 2009-12-01
I spoke too soon. .30 kernel also has the issue it seems. I'm now trying to get the .28 kernel (as found in Jaunty) to work though flgrx isn't too keen on it. We'll see what happens (downloading flgrx 9.11 to see if that helps).

---

### Post by michaelzap on 2009-12-01
Try the latest Lucid RC kernel instead, which you can get here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I run it in Karmic and it's made the difference between a completely unstable and broken system and one that works rather well.

---

### Post by Nerd King on 2009-12-01
.32 RC8 you mean? I'm just downloading it now to see what happens.

---

### Post by michaelzap on 2009-12-01
> **Nerd King said:**
> .32 RC8 you mean? I'm just downloading it now to see what happens.

That's what I'm running, yes. I started with RC6 and my problems went away immediately. Later I updated to RC7 and then RC8, but I haven't noticed anything different since then.

---

### Post by Nerd King on 2009-12-02
Sadly 32 wouldn't play nice with my ati driver (got a nice fail message when building the kernel module thingy) which ruins that plan :(

---

### Post by Sin@Sin-Sacrifice on 2009-12-02
My heart goes out to you all having trouble with Karmic. I have had my keyboard slamming sessions over slax installations and know what you're going through. Just so you know, though, when/if you get Karmic running it's amazing. It just worked on this system (even pulseaudio...) and everything is immaculate. Hope you get there too.

---

### Post by michaelzap on 2009-12-02
> **Nerd King said:**
> Sadly 32 wouldn't play nice with my ati driver (got a nice fail message when building the kernel module thingy) which ruins that plan :(

Building the kernel module thingy? What do you mean by that? Did you install from the mainline deb files or try to compile your own kernel?

It's possible that these mainline kernels are missing some specific drivers, so you might look for a repo that has non-mainline Ubuntu versions of the later kernel.

---

### Post by Nerd King on 2009-12-02
I grabbed the mainline kernels but at the stage where it's doing the modules (ie virtualbox, flgrx, etc) it oks everything except flgrx which means that the kernel module for the ATI proprietary driver is no good. I booted into it to see and it was slow as molasses as a result. Back to 31, pull out 32 and I'm good again.

No doubt Karmic is good, and I'm using it for most things, but it's annoying not to be able to use my wireless. I'm keeping a spare Jaunty partition for dire wireless-needing emergencies! Literally EVERYTHING is perfect bar this one pig of a problem. Still, I'm learning a bit more about kernels this way (spending a lot of time reading terminal output!) so maybe it's time to compile my own and see what happens!

---

