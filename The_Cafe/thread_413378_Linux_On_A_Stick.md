---
title: "Linux On A Stick"
date: 2007-04-19
forum: The Cafe
---

### Post by myxiplx on 2007-04-19
Hey folks,

Had an idea and needed to brainstorm with a few folks who know linux better than I.

There are a lot of Live CD's out there, Babel Linux is the latest I've heard of with a nice little twist - centralised storage for all your work ([http://www.babeldisk.com/)](http://www.babeldisk.com/)).

Now Live CD's will boot on a lot of hardware, but there are bound to be problems from time to time, either with hardware drivers, or internet / network settings.  And if you're dealing with non technical users, getting them to go into the BIOS to enable booting from CD-ROM or USB sticks could be a pain.

So what I'm thinking is this.  Can we combine a Live CD with a VMware image on a single 2GB memory stick, and get the best of both worlds?  If you can boot straight off the memory stick, great!  Plug it in, switch on and you're away.  If you're not sure however, just boot the normal OS, and then plug the memory stick in.  VMware will use your existing internet connection (even dial up!), and it'll work on Linux or Windows.

So, questions and problems:

1.  Does Linux support autorun?  Bear with me please, Linux is still pretty new to me :)

2.  Is it possible to put a FAT partition as the boot partition on one of these memory sticks?  I'm hoping you can get Linux booting from the FAT partition as you could also store the Linux and Windows VMware players on there.  

3.  Can the VMware player run without installation on Windows and Linux?

If all 3 are possible, Linux On A Stick sounds like something I might put together for my mum :D

Combine the simplicity of booting from that with centralised storage and backup like Babel would be great.  I'd give it my mum to use as her home PC.  At home I'd configure it to just boot off the USB drive, but when she goes to visit family she can take her photos, e-mail and everything just by putting the memory stick on her keyring.  At my aunties there's no need for her to reboot or change BIOS settings (both of which would scare her), she just plugs it in & it runs, with all her settings.

Myx

---

### Post by Robin Hood on 2007-04-19
Whilst I don't know about the Linux side of things if all you mom wants is to be able to run a browser, a email client and a media player just check out [http://www.portableapps.com](http://www.portableapps.com). There are loads of programs that run from a memory stick. Another bonus is that many of them also run in Ubuntu using wine.... Hope this helps.

Martin

---

### Post by beniwtv on 2007-04-19
> **myxiplx said:**
> Hey folks,
1.  Does Linux support autorun?  Bear with me please, Linux is still pretty new to me :)


Yes, see [http://standards.freedesktop.org/autostart-spec/autostart-spec-0.5.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-0.5.html)

> **myxiplx said:**
> 
2.  Is it possible to put a FAT partition as the boot partition on one of these memory sticks?  I'm hoping you can get Linux booting from the FAT partition as you could also store the Linux and Windows VMware players on there.  

This is more tricky, since FAT32 doesn't have permissions. But I heard Klinux could do it some time ago. 

> **myxiplx said:**
> 
3.  Can the VMware player run without installation on Windows and Linux?


Vmware can, but it costs money. Not sure of Vmware Player though.

---

### Post by badactress on 2007-04-19
I have the Qemu version of Puppy Linux on my stick, which does exactly this! If you plug stick in & turn computer on it boots directly into Linux, if you boot into Windows first, there's a puppy.exe file you double-click & hey! You have Puppy linux running under emulation in Windows.. It uses Qemu rather than VMPlayer but works perfectly.. Network was auto detected so you're straight on the net without any setting up at all.

Damn Small Linux can do the same.. just setting it up & saving your settings is slightly more complicated..

Linux has no problem booting from FAT16 or FAT32 partition.. Just make sure you format the sick under windows not Linux.. Other people may have had success, but a group of us spent ages figuring it out & eventually decided that there's something about formatting FAT partitions under Linux that Windows doesn't like!

[http://www.puppylinux.org/](http://www.puppylinux.org/)      Click downloads & look under specialised puppy's by enthusiasts..

---

### Post by myxiplx on 2007-04-19
No, I'm not thinking of just having a browser.  In the example above, my aunt would already have one, from my mum's point of view, why would she want to go through all that hassle just to use a different one?  

What I'm thinking is the Babel people have central storage of everything - photo albums, documents, music, etc.  If my mum has taken some pictures and saved them to 'her' computer, being able to just take that USB disk anywhere and be able to load up 'her' computer makes it much easier to show anyone the photos & things.  Wherever she goes she gets the same interface and software she's used to.  This is about bringing technology to the masses in the simplest way possible.  

I have a feeling the VMware player will need installing to use the virtual machine, which is a bit of a pain at the moment, but can probably be worked around.

Regarding the FAT32 permissions thing, I'm not talking about installing Linux on that partition, just having the boot loader there.  I'm thinking FAT as everything can read it and it only needs to be a small partition.  It just gives a common place to start from whether booting the PC, or just plugging it into Linux or Windows.

---

