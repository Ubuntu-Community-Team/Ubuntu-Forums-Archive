---
title: "Converting Parallels to KVM, and onto an LVM?"
date: 2013-06-20
forum: Virtualisation
---

### Post by 1clue on 2013-06-20
Hi,

I'm converting a Parallels (mac) VM of Windows to KVM.  I've figured the kvm-img command and it's about 12% done right now, but I'm wondering how to get that image (if it works) into an LVM volume?

And what's the ideal format for KVM?  I'm using qcow2 right now, but can convert to something else instead.

Thanks.

---

### Post by TheFu on 2013-06-20
Can't really answer your question specifically, I don't use Apple products, however,  migration from one VM tool to another is just a few steps.
* Remove any proprietary extensions from Tool-A that run inside Client-1.  VMware Guest Additions and similar.
* Determine the current virtual hardware and the "future" virtual hardware supported by each VM tool.  For example, ESXi defaults to LSI HDD controllers, but KVM doesn't support those (last time I checked).  An unsupported disk controller is hard to recover from after the fact.
* virtual HDDs have many different formats. Each has pros and cons.  Without knowing your specific needs, we can't really suggest a good choice for you.  If you care about performance, a fully allocated, non-sparse file is usually the best choice for a beginner. Avoid compression and "sparse" allocations and unless you are really good with dedicated storage, you probably want to stay with file-based virtual HDDs.

QCOW2 has some interesting features when performance doesn't matter and when you want compressed partitions.  I've never used it longer than a day, so perhaps it has changed.  If I were an VCP provider and trying to upsell VMs, I might use QCOW2 for very small VMs as a way to encourage upgrades to larger RAM and more V-HDD offerings ... for more money.  Just sayin'.

With a Linux file system, you can use normal system tools to migrate between the different V-HDD systems easily. Just mount both using a liveCD and have at it with 'dd' or rsync or tar or .... any of the 50 other tools that handing ownership, permissions, soft/hard links and other special files correctly.  Do not just copy the files over (this is for lurkers who may not know better).

I stopped using KVM directly with 10.04 and started using **virt-manager** as a front end.  Highly recommended for anyone with fewer than 50 VMs to handle or fewer than 20 physical hosts. It is almost too easy to manage an entire KVM infrastructure with it after setting up ssh-keys between all the systems for your userid.

---

### Post by 1clue on 2013-06-20
Thanks for the response, will try it ASAP.

*Note:  This post was longer, then I realized that most of it has nothing at all to do with the subject.  I'm trimming it down.*

This effort is being undertaken for three reasons:  First, to learn it.  Second, to find out if it's a viable option for a not-yet-assembled server for my company.  Third, because my Mac is getting a bit long of tooth and the tools I use are more power hungry than they were when I got it.  I'm not afraid of making a mistake if I can learn something from it.

Storage:  I'm making Linux guests as volumes on LVM2 so far, and I really like it.  My goal is to have all the guests on resizable LVs.  I have fair but not "professional IT shop" ability with RAID and LVM2.

If I can migrate the Windows machines to LVM volumes then I would like to do so.  Not sure about resizing a Windows partition on the fly, but maybe from a booted iso image?

I'm not a beginner for virtualization, but I'm a beginner for KVM and for converting from one engine to another.

Mostly the Linux images are simple enough I might just reinstall instead of convert, except one.  The Microsoft licenses will be a move, not a copy.

Now on to the conversion:

If I understand what you're saying, it means I need a reliable backup before I begin, and then have a functional-but-soon-to-be-trashed second.  If I understand correctly, I open the VM, shut it down (not suspended) in Parallels, remove the non-common hardware, and then convert what's left?  Then re-add hardware once it's in KVM?

virt-manager:  It's one of the bigger reasons I went with this.  I'm also trying to install a virtualization server for my company, with yet another set of VMs.  I'll be doing that part (installing for the compan remotely, i'm about 1400 miles from the site.  They're planning on the free VMware hypervisor, which I've played with a little bit.  It's a PITA.  I'd like to make an argument to install KVM on that box, and virt-manager will be a very large part of that argument.  Anyway that's all later, and assuming I get this project working.

Thanks.

---

### Post by 1clue on 2013-06-20
**A note about Microsoft, non-free software and virtualization:**

Anyone reading this, be sure you know what your license terms are.  In my case all the VMs are using either a test license or a development license.  That means either me or my company paid hundreds of dollars to be able to use a whole lot of software, with legal restrictions on how you can use it.  Some licenses are for a single piece of hardware, (OEM license) and can't be moved even if you put it on a VM, install Linux on the box and then put the VM back on the same box.  It won't run.  Other licenses are designed around virtualization, and they don't mind if you suddenly gain a couple cores or change CPU type.

I'm not advocating Microsoft.  I don't use it for anything but testing, and that's not optional for me.  What I'm advocating is that, whatever your software's license terms, you do your best to follow them.  That includes the Open Source stuff.

If you plan to put non-free software on a VM, then get a license that's friendly about it.  You can download the images for just about any Microsoft software directly from Microsoft. You can run it for a month no problem, and call them with your requirements and they will help you figure out the best license to use.  I've done so on several different occasions.  I strongly recommend downloading direct from Microsoft and then order the keys, you get a clean, unpolluted product that way.

Don't be afraid to call these guys.  If you call, they know you are trying to be legal.  They won't even blink about installing on a VM on Linux.  There are some licenses where you can reinstall the same image over and over, and sometimes they have one where you can have multiple instances of it.  Sometimes those licenses are not very expensive.  More importantly, some of those licenses aren't advertised anywhere, you have to ask for them.

On top of that, they don't actually sell the licenses there, you have to go to an authorized reseller to do it.  So they don't know what you wound up buying.

Frankly it doesn't matter how crazy you get with your request.  They may tell you there isn't one, but you won't know if you don't ask.  I don't know if there's a license where you can pass the image around within a company, but it wouldn't surprise me.

For example, if you're testing software you can get a technet subscription, which basically means you can install one of just about anything Microsoft has -- operating systems, server software, whatever.  They have several different levels for how much software you need.  You can only use it for testing in that case.  I don't remember what the original price cost, but the annual renewal is $250.  That's incredibly cheap compared to buying all that, and if you're just testing software you can't beat it.  

Personally speaking, since I only use this stuff for testing, every time I've called Microsoft for license advice, I've come out of it surprised that it was that cheap.

---

### Post by CharlesA on 2013-06-21
That's a Technet subscription isn't it? I remember looking into it before, but I couldn't really get past the huge price initially.

I am currently running a retail version of win7 on my vm server and haven't bothered with getting more copies of Windows even though I have looked into it in the past.

---

### Post by 1clue on 2013-06-21
Yes, a TechNet subscription is what I'm using for testing.  I have one VM which was under an older MSDN developer license, which is more expensive but more liberal in terms of what you can do with it.

Frankly if you're using fewer than maybe 4 Microsoft VMs then technet might not be worth it for you.  The only thing is, if you continuously move the VM from one host to another, or if you reinstall the same image over and over and use that same license key, then you'll want something special.  The license I'm using, I can't use the images for anything except testing.  No personal use, no business use or production data.  Which is perfect for me, I Really Don't Like these things, I just have to make sure my stuff works from those clients.

There's another advantage:  If you're a software developer and you have the MSDN license, then Microsoft is a lot more lenient in the license terms.  That's no secret, the guys from this Microsoft help number told me on more than one occasion.

Yes the initial price was up there.  At the time all I needed was a Win7 Pro image, and that was a lot less money for an unencumbered license I could use for any purpose.  But looking ahead, if you see a few more on the horizon it's worth it.  I remember thinking, if I download and install a bunch of images right now and then let it expire, then wait 3 years or so, and then buy again on year 4 it might be cheaper still.  But 4 years is a long time with respect to software, and maintaining the subscription means whatever you don't have, you can probably just download it and install it and you don't have to worry.

Seriously, I hadn't intended this thread to be a go-get-your-microsoft-license thread.  I just put this here because I'm moving Microsoft licenses and there's a lot of FUD around about Microsoft licenses, and on Linux forums there's a lot of FUD about commercial software in general.  A lot of guys I've talked to over the years think there's something shady or even illegal about putting a Microsoft VM onto a Linux VM, or about moving the image once it's there.

I think that the OEM license idea is a big part of that.  It's not even stock Windows anymore, and it's designed for a specific piece of hardware.  It's been buttered up so much you can't see the bread, and chances are it's already got some sort of malware on it.  And then for some of the bargain basement stuff it turns out that the copy of Windows is illegal sometimes, which is tragic.

Microsoft knows how people use computers.  They know about Virtualization and they know about Linux.  They would rather you use Microsoft's virtualization, but they know it's not going to happen in every case.  Probably by now every medium or large business in the world uses VMs for something, and once people choose a virtualization engine they're probably not going to change very easily.  But when it comes down to brass tacks, they're going to get their license fee because that's what makes them go.  You're using Windows, which means you buy their product.

They also know that people want clean installation images, and they let you download them without fuss.  Frankly anymore I don't know that I would ever buy a Microsoft product from a brick and mortar place, it's faster to download one and then you have a month to get the license key in.  And you know it's CLEAN.

That said, they also know how consumers use computers.  They buy a laptop or desktop, then they use it until it doesn't work anymore and they buy another one and sell the old one at a garage sale.  So I think some of the common licenses and "home edition" stuff is pretty restrictive.

---

### Post by CharlesA on 2013-06-21
Yeah, MS seems to be pretty good with their licenses for products that they support. I had to migrate a bunch of Win2K3 machines to a new VM host and they all ended up becoming locked because MS didn't support 2K3 via MSDN (anymore) which is what my work has for testing. Getting stuck at the "you need a new product key, but we don't support this product anymore, so you SOL" pretty much blew.

What a waste of time and energy - especially since those VMs were migrated from an EXSi server to VirtualBox (why?!?!) and then to Hyper-V.

*facepalm*

---

### Post by TheFu on 2013-06-21
I like to spread the anti-MS FUD myself.  Trying to even the playing field just a little since Linux doesn't ahve a $500M advertising budget to get their message out.

I love that I only have to manage 3 licenses inside the company Everything else is BSD, Apache, GPL, or LGPL licensed. No keys to lose for those. No worries if I've installed an image somewhere I shouldn't.  No concerns over migrating a VM between physical systems that might break a sub-sub paragraph of a "accept or don't use" license agreement displayed during installation.

My company has a technet subscription for our single MS software developer.

I have a retail Win7 Ultimate license (from from MS for attending a Win7 Launch day event. It runs inside a KVM VM and records TV shows for me. That's it. Playback of those shows is on XBMC after I remove any DRM crap that WTV files may or may not contain.

My laptop has a Win7 Home license - tied to that specific laptop. Can't be moved.  My real desktop runs on a remote system under KVM "in a private cloud" somewhere.  I use NX remote desktop to access it. The remote VM runs FreeNX - 2-3x more efficient than RDP or VNC, IME.  Spice is interesting and I've gotten it working for a remote desktop on the same LAN. I'm unsure about the security, so using NX when I'm remote is it.  I've used NX from around the world to remote back to my desktop. Clearly, audio and video doesn't work well, but normal "office productivity apps" work just like being local.

Seems we've left the KVM migration question. Did you need anymore help with that?

---

### Post by 1clue on 2013-06-21
> **CharlesA said:**
> ... Getting stuck at the "you need a new product key, but we don't support this product anymore, so you SOL" pretty much blew.

What a waste of time and energy - especially since those VMs were migrated from an EXSi server to VirtualBox (why?!?!) and then to Hyper-V.
*facepalm*

Ya, from my perspective that's a good time to look hard at some other software.  If you need actual support, there are a lot of distros out there that offer a contract for that sort of thing.

> **TheFu said:**
> I like to spread the anti-MS FUD myself.  Trying to even the playing field just a little since Linux doesn't ahve a $500M advertising budget to get their message out.


Frankly I think there's no need for anti-MS FUD.  People who are snooping around on various Linux forums are already unhappy probably, and there's plenty about the way M$ and other companies do business that can make Linux look good.

I think you tell the absolute truth about it, and people will naturally come this way.  As it is you have corporate types spreading FUD about FOSS, and you have RMS clones running around spewing the evils of all commercial software, and people think they have to choose all one or all the other.  That's just not true.  It's much more natural to dip a toe into the pool before diving in, and IMO the biggest strength of FOSS is that it works well with commercial software or to replace it entirely.

> 
I have a retail Win7 Ultimate license (from from MS for attending a Win7 Launch day event. It runs inside a KVM VM and records TV shows for me. That's it. Playback of those shows is on XBMC after I remove any DRM crap that WTV files may or may not contain.

Seems we've left the KVM migration question. Did you need anymore help with that?

I think if I personally were to buy a standard Windows license it would be in a VM, and then I would just move that around as necessary.

KVM:  I haven't had a chance to get back to it yet.  I'll ping here again when I get results.

---

### Post by CharlesA on 2013-06-21
> **1clue said:**
> Ya, from my perspective that's a good time to look hard at some other software.  If you need actual support, there are a lot of distros out there that offer a contract for that sort of thing.

Too bad most of the software the company I work for writes runs on Windows. They ended up moving to Server 2008 via MSDN.

> I think if I personally were to buy a standard Windows license it would be in a VM, and then I would just move that around as necessary.


Indeed.

---

### Post by 1clue on 2013-06-21
Yeah, my company most of the implementations are on Windows too.  No real reason for it, most of it runs on a Java virtual machine anyway.  About the only thing that makes a difference is the database middleware has to work with whatever database.

---

### Post by CharlesA on 2013-06-21
The DB servers they were using were MS SQL and Oracle, so no *nix alternatives there.

Oh well.

---

### Post by 1clue on 2013-06-21
Oracle installs on Linux.  It's definitely not free, but we have a couple customers who feel that Linux is up to the task to put their outrageously expensive, outrageously difficult to manage database on it.

MS SQL isn't available no, and it seems that wine/crossover don't have what it takes to make it go either.  But a SQL Server license is going to make the operating system license price the least of your worries.

I'm converting the image for my second try.  I really hope I didn't mess up my original.  did a directory copy to a backup location before, so I should be able to just copy it back and get a working machine.

---

### Post by TheFu on 2013-06-22
> **1clue said:**
> But a SQL Server license is going to make the operating system license price the least of your worries.
Don't forget all the required CALs. Wouldn't want the BSA audit discovering those. ;)

> **1clue said:**
> I'm converting the image for my second try.  I really hope I didn't mess up my original.  did a directory copy to a backup location before, so I should be able to just copy it back and get a working machine.

I don't know anything about parallels - can it export to any known VM virtual-disk formats used by other solutions?  I know virtualBox will convert between 4-5 different virtual-HDD layouts. I've used this myself.

While I'm here, I try to use these emulated hardware:
* SATA (intel driver)
* Intel PRO/1000 NIC (e1000 driver)
* Nominal VGA graphics / Cirrus card
* No sound
* No USB
* No serial/parallel ports
That should be enough to get a VM booted. Then from inside I can figure out the other devices.  Of course, if it is a Linux VM, I'll try to use virtio drivers for networking and HDD - much more efficient. Also, I won't emulate a graphics card - no need unless you are running a desktop hostOS and a desktop clientOS.  I rarely do that.  Heck, even my normal desktop VM runs on a pure server host - no video card installed.

---

### Post by 1clue on 2013-06-22
Import failed.

Don't see an export menu in Parallels.  I think commercial products tend to import things to their format rather than the other way around.

I know that for products that are contemporary to each other, Parallels is supposed to be able to open VMware, and VMware is supposed to be able to open Parallels.  A coworker had an older version of Parallels and tried to open a newer VMware image she downloaded and it just started converting automatically, but that failed.  I'm about ready to try that in reverse, maybe take a Parallels image and open it in VMware player or something.

---

### Post by CharlesA on 2013-06-22
I wonder if you could try cloning the VM and restoring it to the VHD in KVM. Dunno if that would work tho.

---

### Post by 1clue on 2013-06-22
The problem I'm getting in both cases is that the disk is not bootable.  I think maybe a bootable flag is turned off somehow?

In this case, I removed all removable hardware except the disk.  Nothing was left that was configurable in any way, and the disk was an IDE.  Absolutely no change on the results.

I don't see how the hardware for the VM means all that much.  The kvm-img command takes the raw disk file, not any of the other files that describe hardware.  Disks can contain drivers for hardware that doesn't exist on the system, so IMO when I convert it with kvm-img and open it with kvm, it should be able to install its own hardware, its own drivers and go.

For that matter, I can't explain how many times I've taken a working disk out of one linux box and dropped it into other PC hardware and had everything work fine.  I might have to add a network driver or something, and if it was X-capable I'd have to set up the card.

This is acting like the partition doesn't have the bootable flag set.

---

### Post by TheFu on 2013-06-23
A raw disk file actually can have many different headers, so perhaps Parallels is not creating the header in a way that KVM understands?  Can you mount the img file using a loop?

Have you considered using **vboxmanage** to transform the Parallels image into something KVM likes?  That is how I converted an ESXi install.

OTOH, I've always had troubles moving Windows installs around, it is just the Linux and BSD ones that moved easily.

---

### Post by 1clue on 2013-06-23
I've tried everything in the directory which contains the disk image.  kvm-img doesn't understand anything except the one file.  It converts that file nicely, but just can't boot from it.

I'm tempted to just install a new system and be done with it.  All the monkeying around, I could have paid for it by doing something else somebody pays me for.

---

### Post by CharlesA on 2013-06-23
I found some info on converting Parallels to VBox but it involved vmware converter... [http://www.ehow.com/how_5817287_convert-parallels-virtualbox.html](http://www.ehow.com/how_5817287_convert-parallels-virtualbox.html)

It looks like it converts the machine to a VMDK and then imports it into Vbox like that. I dunno why you'd want to do that though.

---

### Post by 1clue on 2013-06-23
There's one image that might be worth the effort.

Thanks.

---

