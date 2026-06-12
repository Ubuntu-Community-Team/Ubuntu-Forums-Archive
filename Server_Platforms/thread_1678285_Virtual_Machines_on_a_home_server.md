---
title: "Virtual Machines on a home server"
date: 2011-01-30
forum: Server Platforms
---

### Post by Twizzle on 2011-01-30
Hi

I have a home server that I have been running for some years and am constantly tweaking / playing with it resulting in numerous reinstalls (and upsetting the wife!).

It does nothing critical but I use it mainly for:
 
backing up my laptop files
XBMC
ZoneMinder

Due to the number of times that I manage to break it, I have now thought about setting it up as a base system but with virtual machines looking after the seperate 'components'.

The machine is an AMD Athlon 64 X2 4200+ with 2Gb RAM.

First of all do you think it is powerful enough to run XBMC and ZM in seperate virtual machines? - I appreciate the more RAM the better but at the moment I am sticking to 2Gb.

I was also wondering what sort of issues may arise for the audio and video areas I will be using. XBMC currently outputs through an HDMI cable to the TV and ZM recieves video signals through a seperate video card. ( I have had my concerns in the past that there have been conflicts in the way I have set things up!).

I have read a number of guides about setting a system up with virtual machines but not really found any articles about the practicalities of using such a set up at home.

I just thought a bit of guidance may help before I commit and spend a week pulling my hair out trying to get it all to work!

Thanks

---

### Post by ryannathans on 2011-01-30
Check if the processor supports visualization first before trying anything.

If so have a look and 'play' with [VMWare]("http://www.vmware.com") or [VirtualBox]("http://www.virtualbox.org/") it wouldn't take much to set up and mess around with, if your machine doesn't have the 'grunt' you can just as easily delete the VM. It is usually best to try first hand and see the performance for your self, oh and make sure you aren't using a GUI, they tend to chew up alot of valuable resources.

-ryannathans

---

### Post by doogy2004 on 2011-01-31
> **ryannathans said:**
> Check if the processor supports visualization first before trying anything.

Verifying that the processor supports hardware virtualization is not required for most virtualization...However if you want to virtualize 64-bit machines then you will need CPU that supports hardware virtualization.

I have a 330Mhz P2 that runs Ubuntu with VMware Server just fine with 32-bit VMs.  I also have a Dell PowerEdge 1850 that is running ESXi, it runs 32-bit VMs great, but it does not support hardware virtualization so no 64-bit VMs for me.

---

### Post by Thirtysixway on 2011-01-31
Yes ram is an issue, but if you're setting up server versions that don't use GUI then you should get some moderate performance.  I have vmware running on an ubuntu 8.04 machine, running a win2000 system.  It worked but like you said RAM tends to be the first thing that gets in the way.

---

### Post by Hedgehog1 on 2011-01-31
I have been running VMware player images of Ubuntu on my Ubuntu system at home.

In fact - for the same reason.  I was trying some large changes for some research I am doing, and did not want to destroy my main installation of Ubuntu.

The vmware player is free: [http://www.vmware.com/products/player/]("http://www.vmware.com/products/player/")

You can install Ubuntu using an ISO on your hard drive, or a CD.

I ran both 32 bit and 64 bit Ubuntu allotting only 512 megs of ram for the sessions, and the speed was quite good.

Your 2 gigs of RAM should work fine for at least one VMware Player session, and possibly run 2 at the same time.  Linux need much less memory than windows.  If you were to run a windows VM image, you would find yourself running slow.  But Ubuntu on Ubuntu does quite well.

Also:  After building the VMware inmage - save a copy.  Then copy back over the damaged WMware image after you screw it up.  That way you can start over with your tests without having to reinstall Ubuntu again.

This has saved me a ton of time!

---

