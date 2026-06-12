---
title: "Choosing a distro for a crappy latop"
date: 2009-12-21
forum: The Cafe
---

### Post by SnoringFrog on 2009-12-21
My friend recently gave me an old laptop they didn't have any use for, so now I'm trying out what distro to put on there. 

CPU Type: Pentium (R) III
CPU Speed: 700MHz
RAM: 96mb

The only small type of Linux I've used before is DSL. I'll go back to that if I can't find a better alternative, but I'd prefer to try something new (and preferably with a little more polish and functionality). So far I've looked at Xubuntu, Arch, and Tinycore, and I tried looking up some info about Firefly but didn't have much luck. 

Anyone have any suggestions for a good distro to try for this?

---

### Post by NoaHall on 2009-12-21
DSL, Puppy, TinyCore, Arch, Debian, SliTaz, Slax, Ubuntu Minimal install, there, I've done everyone's answers for you. Oh, and some would have said MacPup. Oh, and earthpigg would have said  [this]("http://ubuntuforums.org/showthread.php?t=1248322")


Why, only after I have done this, does everyone come up with different distros?
</thread>

---

### Post by Grenage on 2009-12-21
Puppy is supposed to be good for machines with low resources, but I have never used it myself.  If your Internet connection is of decent speed, I'd just download a few and see what 'floats your boat'.

Edit: Beaten to it, and he was more helpful!

---

### Post by snowpine on 2009-12-21
DSL is the only one I've personally tried that will work well with 96mb of ram.

If you can get more ram, it opens up options like Puppy, SliTaz, etc. 

I am currently running Sidux Xfce edition on a 500mhz Pentium 3 with 256mb of ram. It can be done!

LOL at NoaHall's answer. :)

---

### Post by smo0th on 2009-12-21
vectorlinux is good for old computers

---

### Post by &#32 Greg on 2009-12-21
> **NoaHall said:**
> DSL, Puppy, TinyCore, Arch, Debian, Ubuntu Minimal install, there, I've done everyone's answers for you. Oh, and some would have said MacPup. Oh, and earthpigg would have said  [this]("http://ubuntuforums.org/showthread.php?t=1248322")


Why, only after I have done this, does everyone come up with different distros?
</thread>

SliTaz, also the source based.

---

### Post by Simon17 on 2009-12-21
DSL is dead.
Puppy is nice, TinyCore is cool if you like minimalism and have some idea of what you're doing, but my highest recommendation is Slax.
Though all three of them suffer from either a lack of packages or many outdated or broken packages.

---

### Post by snowpine on 2009-12-21
> **  Greg said:**
> SliTaz, also the source based.

I love SliTaz too, but:

> SliTaz GNU/Linux supports all machines based on i486 or x86 Intel compatible processors. A minimum 256MB of memory is recommended to use the main LiveCD. 64MB is needed for the "slitaz-loram" flavor and 16MB for the "slitaz-loram-cdrom" flavor.

With the slitaz-loram flavor, the system is less responsive, but allows you to graphically install SliTaz on very old machines. Once installed, SliTaz works well with a minimum of 16MB memory, but forget about using Firefox to surf the web - you'll have to use the text based 'links' for example.

DSL may be "dead" but as it uses a very old kernel, Firefox 1.0, etc. it should be fully functional with only 96mb of ram. I would recommend 256mb minimum for any "non-dead" distro. :)

---

### Post by alexfish on 2009-12-21
Puppy

---

### Post by &#32 Greg on 2009-12-21
> **snowpine said:**
> I love SliTaz too, but:



DSL may be "dead" but as it uses a very old kernel, Firefox 1.0, etc. it should be fully functional with only 96mb of ram. I would recommend 256mb minimum for any "non-dead" distro. :)

As it says, the 256 threshold is only for LiveCD. And Midori is a solid replacement for FF, as an example.

---

### Post by snowpine on 2009-12-21
> **  Greg said:**
> As it says, the 256 threshold is only for LiveCD. And Midori is a solid replacement for FF, as an example.

Correct. If you have 256mb+, the filesystem is uncompressed to RAM and SliTaz is very fast. If you have to use the Loram flavor, it cannot run uncompressed from RAM and is much slower. Therefore I recommend 256mb minimum for the optimum SliTaz "experience". 

Of course, there is the awesome Tazlito tool you can use to create your own "flavor" (for example replace Firefox with Midori) but I do not think that will reduce RAM usage by 160mb, do you?

---

### Post by lykwydchykyn on 2009-12-21
I've been messing with tinycore lately, it's pretty impressive for a 10 MB distro.  Way better than DSL in many respects.

---

### Post by &#32 Greg on 2009-12-21
> **snowpine said:**
> Correct. If you have 256mb+, the filesystem is uncompressed to RAM and SliTaz is very fast. If you have to use the Loram flavor, it cannot run uncompressed from RAM and is much slower. Therefore I recommend 256mb minimum for the optimum SliTaz "experience". 

Of course, there is the awesome Tazlito tool you can use to create your own "flavor" (for example replace Firefox with Midori) but I do not think that will reduce RAM usage by 160mb, do you?

Of course not, but it's definitely there and usable. 

You can always pull a kmandla- SliTaz console :P

---

### Post by snowpine on 2009-12-21
> **  Greg said:**
> Of course not, but it's definitely there and usable. 

You can always pull a kmandla- SliTaz console :P

Agreed. :)

I am glad you mentioned the name kmandla actually... SnoringFrog (great name), here is a blog that has some great info on older computers: [http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)

---

### Post by SnoringFrog on 2009-12-23
Ok, I installed Slitaz (the 64mb RAM one). LiveCD booted fine, and the install seemed to work fine as well, but when I tried to reboot it freezes up. I get past the Gateway logo screen and get stuck on a black screen with blinking cursor. 

I'm going to try to install it again and see if that fixes anything. Assuming it doesn't, what could the problem be? Could it be a problem with the Grub installaton or athe Grub file (forgot what it's called)? I'm still new to all this Linux stuff so I'm really not to sure what to look for.

EDIT: Also, during the install, the installer failed to find...argh, I forgot what it was called. Think it had cdrom in it, the first time. When I tried again the installer ran fine though. Not sure if that would affect anything.

---

### Post by snowpine on 2009-12-23
> **SnoringFrog said:**
> Ok, I installed Slitaz (the 64mb RAM one). LiveCD booted fine, and the install seemed to work fine as well, but when I tried to reboot it freezes up. I get past the Gateway logo screen and get stuck on a black screen with blinking cursor. 

I'm going to try to install it again and see if that fixes anything. Assuming it doesn't, what could the problem be? Could it be a problem with the Grub installaton or athe Grub file (forgot what it's called)? I'm still new to all this Linux stuff so I'm really not to sure what to look for.

The SliTaz installer gives you the option to install GRUB. Did you say "Yes"?

As mentioned above, I recommend 256mb minimum RAM for Slitaz and have no personal experience using it with only 96mb.

---

### Post by SnoringFrog on 2009-12-23
> **snowpine said:**
> The SliTaz installer gives you the option to install GRUB. Did you say "Yes"?

As mentioned above, I recommend 256mb minimum RAM for Slitaz and have no personal experience using it with only 96mb.

Yeah, I installed Grub when it did that.

EDIT: I don't know what was wrong, but I got it working. I partitioned the drive myself (all that entailed was deleting the one partition on it and recreating it with an ex3 filesystem) then ran the installer. Opted out of formatting the hardrive as ex3, and said yes to Grub (again). Hit reboot, and it worked! So I don't know what was up with it before.

Thanks for all the distro suggestions, I've got alot of them saved to try on other comps I have. Might try dual/triple/etc. booting some of them on a bigger machine considering they're all small distros.

---

