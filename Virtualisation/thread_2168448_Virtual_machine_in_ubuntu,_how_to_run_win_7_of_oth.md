---
title: "Virtual machine in ubuntu, how to run win 7 of other device?"
date: 2013-08-17
forum: Virtualisation
---

### Post by Artur_Indio on 2013-08-17
Hi,

i'm decide use ubuntu as SO primary, but still needs some softwares in other SO/Windows. I known apps to use virtual machines in ubuntu, but i would want know if exist the possibility of run in ubuntu session a virtuality session of windows 7, it is already installed on a hd. 

thanks in advanced

---

### Post by 3rdalbum on 2013-08-17
I believe it is possible to have your existing Windows, that is installed on your hard disk, run inside as virtual machine on Ubuntu.

I don't know how to do it though. Somebody else will have to tell you.

There are various Ubuntu help forums in different languages, you might be able to find help in your native language on a different website.

---

### Post by Artur_Indio on 2013-08-17
Ok, thanks! I'm trying in other forums, google, etc also.

---

### Post by squakie on 2013-08-24
I know it was possible with XP - and I suspect with Windows 7 as well, but here's the voice of experience speaking - DON'T.  The virtualization software virtualizes the devices, so Windows comes up with new devices - and sometimes suspects you are on different hardware than where installed, so you have to re-validate it.  Not so terrible UNTIL you decide to go back and use the same Windows installation stand-alone again.  This causes an amazing number of headaches - in my experience anyway.  I actually "lost" my existing Windows installation doing this and had to completely reinstall.

So, if virtualbox still allows it (you used to do it via the command line with something like vboxmanage or some such thing, DON'T DO IT.  Either ALWAYS use as stand-alone Windows or ALWAYS use in a virtual machine - DON'T try to mix both!!!

---

### Post by TheFu on 2013-08-26
If it is possible, it is non-trivial.  There are tools to convert physical installs into VMs .... google for "p2v" to find those. I know that Windows Ultimate has a way to boot the VHD files that their VM stuff makes directly OR inside a VM ... but you'd have to use the MS-VM tools.

Basically it comes down to whether the real hardware in a system can be cloned inside a virtual environment - we're talking chipsets, HDD controllers, NICs ... plus these things need to appear to be installed in the same virtual PCI, PCIe and PCIx slots inside the VM.  it doesn't take much to realize that is almost impossible.  I've never heard of anyone being success from a reputable, trusted source. That doesn&#8217;t mean it hasn't happened, just that I don't believe it.

Plus, make certain that you don't violate the SW license for the Windows install. Not all of them allow running inside a VM, that is a different license. I understand that MS will happily sell you one of those, but you need to request it.

---

### Post by squakie on 2013-08-28
> **TheFu said:**
> If it is possible, it is non-trivial....

Actually, at least back then, it was actually fairly simple to do, but as I said before and you have reiterated, PLEASE, NOBODY DO THIS!!   I can't begin to emphasize enough the headaches this caused me, and I would not wish it on even my worst enemy.

As far as licensing, back then at least, Microsoft wouldn't even talk to you if you were running one of their OS's in a virtual machine, and especially if the host of that virtual machine was not Windows based.  I have no clue if they have modified this or not, but back then it was a terrible experience.  I had Windows ME in a VM.  Windows ME had a BAD memory leak, and I called them on it.  They wouldn't look at it at all.  I ended up providing many dumps and trace backs so they could see it was the OS at the time (hey, I'm not bashing Microsoft, just saying the experiences I had ;) ).  They finally replied and said they would send me a free copy of the next OS (XP Pro), which they did.  Oh the old days....

But back to the thread - anyone reading this and considering it - plain and simple - DON'T!

---

