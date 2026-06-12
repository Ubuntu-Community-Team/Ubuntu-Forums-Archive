---
title: "Best way to run Windows Apps on Ubuntu 7.10"
date: 2008-01-18
forum: Windows
---

### Post by obdata on 2008-01-18
Hello,

I'm somewhat new to Ubuntu, I'd like to switch to using Ubuntu 7.10 Gutsy Gibbon, and I'm wondering how I could run Windows apps on Ubuntu, and if I can run all, most, or only a few apps successfully. Or should I just dual-boot XP Pro and Ubuntu?

Also, if I dual-boot, I probably still need antivirus etc. for Windows? What if I only use Windows once in a great while for a few apps, and use Ubuntu for all browsing, emailing, etc?

Thanks,

Jason

---

### Post by logos34 on 2008-01-18
[http://www.winehq.org/](http://www.winehq.org/)
[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)
($)

You might not need to install windows at all.  If you decide to dual-boot, I'd run AV even if you never go online. (linux could potentially pass something to it. like through a shared file)

---

### Post by obdata on 2008-01-18
Thanks,

The main programs that I want to run are AutoCad 2008, Filemaker Pro 8-9, and Quickbooks 2006. I checked out Filemaker, it MIGHT run on WINE, but even if it does it would probably be somewhat limited (things like network sharing etc). I have XP, so I can dual-boot, I just thought that if I could run everything inside Ubuntu it would all the better. It sure would be nice if there were some way to run everything or nearly everything on Ubuntu, alot of people would start using Linux then because there would be no point in having Windows.:)

Jason

---

### Post by SunnyRabbiera on 2008-01-19
a dual boot might be desired though if you rely on windows for things like gaming...
but you can try a virtualmachine too

---

### Post by angryfirelord on 2008-01-20
If you don't need any 3D acceleration, then I would go for a virtual machine. I've used VirtualBox without any problems. Wine would be faster and give you 3D, but some apps still don't work properly. Personally, I prefer a dual-boot setup because I need the 3D for games and such.

---

### Post by RebounD11 on 2008-01-20
+1 for the VirtualBox virtual machine for Windows... faster and safer than dual boot (and more comfortable). The apps you listed all run fine in VirtualBox.

For Games I use Cedega and Wine (some ork better with one some with the other).

My advice: give up Windows - it's slow, unsecure and bloated without having anything useful or usable after a fresh install, and it doesn't play nice with other OSes (try installing Windows after Linux and see if it dual boots :( ) - that's unless you need it out of obligation for work or school :|

---

### Post by obdata on 2008-01-21
Thanks for the help,

What about QEMU?

I want something that runs at very nearly native speeds for most of the things that I'd be doing in Windows, so I was thinking of a virtual machine for most smaller Windows stuff, then just reboot in Windows when I absolutely need it.

---

### Post by phrostbyte on 2008-01-23
VirtualBox is very fast, nearly native. The only thing is you need a decent amount of RAM because you are basically running two operating systems at the same time. But there is almost no performance loss as a result of virtualization, the code usually gets executed on the processor as if it was running outside of the VM. Video has to go through a layer or two though, so some very visual things might be a little jerky.

---

### Post by obdata on 2008-01-28
Thanks all, I've installed VirtualBox on XP, just to have a look at it, it looks very useful.:)

Now, what if I install Mint or Ubuntu as a VM on Windows (I was thinking this would be a way to try them out more than I can on a LiveCD) can I easily remove them?

---

### Post by Infinity-al on 2008-01-29
> **obdata said:**
> Thanks all, I've installed VirtualBox on XP, just to have a look at it, it looks very useful.:)

Now, what if I install Mint or Ubuntu as a VM on Windows (I was thinking this would be a way to try them out more than I can on a LiveCD) can I easily remove them?
yeah... sure... you just have to delete a couple of files...

---

### Post by Battie on 2008-01-30
Just a note:

If you choose to run Windows in a VM, run an antivirus program anyway.  You will still be wide open to the internet that way.  I recommend Grisoft's [Free AVG]("http://free.grisoft.com/"). It's free and works great.

When dual-booting, it would be very hard for Linux to give your Windows system a virus unless you specifically enable NTFS write support.  Windows won't see ext3 partitions without a third-party driver, and Linux (unless things have changed very recently) doesn't write to NTFS by default.

---

