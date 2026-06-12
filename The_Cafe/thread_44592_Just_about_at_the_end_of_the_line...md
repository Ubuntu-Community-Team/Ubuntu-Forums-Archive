---
title: "Just about at the end of the line.."
date: 2005-06-26
forum: The Cafe
---

### Post by Quest-Master on 2005-06-26
.. in the bad way. :( 

I've tried countless times to get either VMware and/or Qemu working. I still haven't gotten them to work at all, as you can see in their respected HOWTO threads. Why do I need them? A few pieces of software which won't build on Ubuntu, but build on other Linux distros. like Gentoo, and obviously, Windows. They are namely ika and Sphere, at Sourceforge.

They came from the Verge and RPG creation community, one I am closely linked to. They've finally matured to the point where I am going to start programming with them, simply to find they don't compile.

I've also begun to learn how to play guitar, and we're lacking a PowerTab and/or a Guitar Pro 4, or something that can open files generated with them. This is where VMware or QEmu would come in handy as well if they worked.

I've been so frustrated with these problems lately, I'm almost at the end of my sanity. Soon, I must be able to either fix these problems, or move on.. to something like the likes of Gentoo or SUSE. :(

There have been numerous times I've come under pressure like this, but the issue usually gets resolved within at the maximum a few days. This has now been going on for a few months now (though, VMware did work with Warty perfectly).

Yeah.. just sort of wanted to let it all out to you guys. I'd really hate to leave what has become such a loving and helpful community though since I joined when Ubuntu first came around on the scene.

---

### Post by mrtaber on 2005-06-26
What is happening with VMWare?  I got version 5 of VM Ware workstation working just fine on Ubuntu Hoary.  You'll need to download the headers for your kernel, and install the basic compilers (build-essential) ala the Unofficial Ubuntu Starter Guide.

Mark :)

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=Quest-Master] Soon, I must be able to either fix these problems, or move on.. to something like the likes of Gentoo or SUSE. :([/QUOTE]


Whew...as long as you didn't say Windows!!!

Just joking....use what works for you...no love lost from this crowd. We will always be waiting to crack up with you...


See you after Breezy maybe?

---

### Post by bored2k on 2005-06-27
I'll miss the horny Mario avatar ..

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=bored2k]I'll miss the horny Mario avatar ..[/QUOTE]

Me 2.

Have you tried a reinstall for the VMware thing?

---

### Post by kassetra on 2005-06-27
[QUOTE=Quest-Master]This has now been going on for a few months now (though, VMware did work with Warty perfectly).[/QUOTE]

Ok, I have vmware 5 running just fine in a fresh Hoary install...  You absolutely have to have the linux-headers-KERNEL_VERSION_YOU_ARE_RUNNING and build-essential installed from synaptic...

With those two items installed, vmware 5 installs with:
 ```
sudo vmware-install.pl
``` 
And then just press enter until it's installed... (you might have to press a "y" at some point.)

As long as you've installed the headers for the current kernel you're running and build-essential, vmware should install just fine... and then you can configure a virtual machine and install a guest OS.

The *only* sticking point might be sound.

---

### Post by Quest-Master on 2005-06-27
> See you after Breezy maybe?

No! Don't speak of such blasphemy! I must get through this and stick with Ubuntu. :)

> Have you tried a reinstall for the VMware thing?

Yes, numerous times.

> 
And then just press enter until it's installed... (you might have to press a "y" at some point.)

Just to make sure, I've downloaded ALL of the available headers and sources from the Ubuntu repos. I continuously get the error that it can't find "linux", "asm", and "net", when it asks me to link to the directory with the sources in them. :x

**HOWEVER.**

I have noticed that the I have linux-headers-2.6.10-5 and my kernel is 2.6.10-4. There is no linux-headers-2.6.10-4 though. Might this have anything to do with it?

---

### Post by Quest-Master on 2005-06-27
Sorry about the bump, hehe..

Just found out my kernel wasn't upgraded for some reason when I moved to Hoary from Warty. So, I upgrade it, and X is dead. Read here more about the problem.. [http://www.ubuntuforums.org/showthread.php?p=230917](http://www.ubuntuforums.org/showthread.php?p=230917)

---

### Post by kassetra on 2005-06-27
[QUOTE=Quest-Master]
I have noticed that the I have linux-headers-2.6.10-5 and my kernel is 2.6.10-4. There is no linux-headers-2.6.10-4 though. Might this have anything to do with it?[/QUOTE]

That's a GIANT problem.  You have to have a matching header for your image, otherwise vmware pukes.

Where did you get your kernel?  Warty?  If you got it from Warty, you'll need to add a Warty repository and pull the matching header that way.  Also, make sure you remove all the other headers, they can cause a mess of confusion.

---

### Post by Quest-Master on 2005-06-29
I'm pretty sure now I can get vmware and QEmu working, as soon as my X.Org starts working again.

If anyone is willing to help out a poor dude who's been without Ubuntu for a few days now, and stuck on Windows.. [http://ubuntuforums.org/showthread.php?t=44748](http://ubuntuforums.org/showthread.php?t=44748) :(

---

