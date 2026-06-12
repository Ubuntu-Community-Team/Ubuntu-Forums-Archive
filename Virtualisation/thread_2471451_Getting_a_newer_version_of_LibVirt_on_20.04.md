---
title: "Getting a newer version of LibVirt on 20.04"
date: 2022-01-30
forum: Virtualisation
---

### Post by cschalk on 2022-01-30
I've upgraded all of my servers and desktops to 20.04 and kept them up to date with the latest LTS versions. I realize that 22.04 will be coming out in a couple of months that *will* have the version I need, but I want it now!

So, I've installed KVM/QEMU and Libvirt on my servers, but 20.04 only includes Libvirt 6.0.0. I want to use a parameter that was added in Libvirt 6.10, and Libvirt was updated to 8.0.0 two weeks ago. Does ubuntu have a repository I can use to install a later version than 6.0.0 on my servers, or am I stuck with a 2-year-old version of libvirt until 22.04 is released in April?

Thanks

---

### Post by Tadaen_Sylvermane on 2022-01-30
Build it yourself. I skip the rmadison part myself. Just add the deb-src line for wherever it is in the 22.04 repositories then apt source it and try to build. You may have to backport more but I don't know. It's worth a shot if there is no reliable ppa already out there. Not super complicated either.

[https://wiki.debian.org/SimpleBackportCreation](https://wiki.debian.org/SimpleBackportCreation)

While I personally haven't done this myself I'd guess it's also possible to modify the makefile or build rules file (can't recall which is used) and make it install where you want, change the prefix. Would need to be done before the build step.

---

### Post by cschalk on 2022-01-31
I decided to install Jammy before April. It's technically still on a development branch and I'll probably have to re-run the installer in April when Jammy goes live, but it gave me the version of libvirt I needed. Thanks.

---

### Post by MAFoElffen on 2022-01-31
LOL. 

I've been testing 22.04 since Day One of Dev. Mostly for testing KVM. It should be fine. It's only less than 3 months from release now, and most of the other current work to be done (changes), is not server related...

You didn't mention what new QEMU/KVM feature you were looking to use(?) Just curious. There are a few of us here that have been testing current KVM... (I know of one other here, besides myself).

Both of us were mostly testing VirGL and some other graphics enhancements.

---

### Post by TheFu on 2022-01-31
Find a PPA built with the newer version
or
build it yourself
or
live without the new version until June/July.

I'm assuming this is a production system with production data.
If it is just a toy system, then run the pre-Alpha 22.04 and have fun!

I am feeling the desire to bleed a bit on a seldom used laptop (Core i5/8GB RAM). Perhaps putting the pre-alpha 22.04 on it would be fun?
It is just 1 more thing on my list of stuff to do in life.

---

