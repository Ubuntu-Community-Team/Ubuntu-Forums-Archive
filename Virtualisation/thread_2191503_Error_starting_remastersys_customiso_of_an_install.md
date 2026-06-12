---
title: "Error starting remastersys customiso of an install"
date: 2013-12-03
forum: Virtualisation
---

### Post by Bucky Ball on 2013-12-03
Hi all,

Firstly, I created my first virtual machine using Virtualbox yesterday. It took a bit of nutting out but now everything is running great and I have about five of them! Loving it. But couple of questions.

I created an ISO of my minimal install as a backup using remastersys with:

```
sudo remastersys dist
```

That all worked fine and the customiso.iso file is there. I assign that to a virtual machine, choose 'Try LiveCD', all goes well until it gets to this error message and hangs:

```
Stopping Mount network filesystems [ok]
```

I've been doing a bit of thinking and wonder if anyone can let me know if I'm on the right track. 

The fstab of the install I created the ISO from has entries to mount local partitions on my hard drive. Now, as I haven't got to how to share drives with VB yet, I'm thinking the customiso vm is trying to mount these from the fstab, but of course can't: it's a virtual machine and can't see the outside world without some persuasion. 

Any ideas?

There is a LOT I don't know about vms for the moment, but I'll keep digging and asking questions. ;)

---

### Post by QIII on 2013-12-03
Before remastering, you probably would have done better to sanitize fstab.  Not sure exactly how best to do that, since I've never created a VM that way.

Also, did you remove any proprietary hardware drivers?

---

### Post by Bucky Ball on 2013-12-03
Will look into sanitizing fstab. What I did was comment out the partitions in the fstab and create a new ISO, installed that in a VM and the error is the same (find attached). This is where it just hangs. 

Not using any proprietary drivers. Is a minimal install with not much else. Wait, think there is java and flashplayer in there. Would they do it? If so, kind of defeats the purpose of backing up the install to an ISO in case the install dies. :-k

---

### Post by QIII on 2013-12-03
Doubt Java and Flash have anything to do with it.  Your pared-down fstab probably still has UUIDs from the original install, which would be wrong for the VM.

---

### Post by Bucky Ball on 2013-12-03
> **QIII said:**
> Doubt Java and Flash have anything to do with it.  Your pared-down fstab probably still has UUIDs from the original install, which would be wrong for the VM.

I commented them out but don't think all perhaps. I'll having a check. Just learning the ropes. 

I take it I should comment out everything in fstab? Does sanitize create a blank or suitable fstab for the custom-iso.iso?

* Just checked and yes, the / partition is the only one not commented in that fstab. Probably trying to mount that? Should I comment out and then REMEMBER to remove the hash BEFORE I reboot the machine (or fstab won't mount anything on that install next boot!). I can always access that fstab from another install, though, so no biggie. ;)

* Just researching sanitizing the fstab but not finding much at the moment.

---

### Post by QIII on 2013-12-03
I just looked at one of my VMs, and installed from normal install media it has UUIDs from the virtual disk.

Can you get to the GRUB menu, mount the device r/w, check your UUIDs and then manually add them to your fstab with vi?

Edit:  Blind leading the blind here...  I've never used remastersys, so I don't know what the heck it does when you install like you have.

---

### Post by Bucky Ball on 2013-12-03
Well, 'remastersys dist' makes a live ISO of the install you are using. You can then burn it to a CD/DVD and you have a backup of your install (without your personal files in my case). To test the ISO you can make a CD and boot from that or mount the ISO in a VM, just like any other ISO. 

So the ISO it creates is like any other ISO of Ubuntu you'd download, except it has your customisations and tweaks, apps installed, etc. So nothing exotic, just an ISO so should mount as a VM like any other. I can't get into the fstab of the remastersys ISO of my install, because it is an ISO. ;)

Might burn a CD and see if that throws the same message ...

---

### Post by Bucky Ball on 2013-12-03
Just an update. Find screenshot attached.

I tried launching the ISO without 'quiet splash' and it ended with an extra line:
```

Stopping Mount network filesystems    [ok]
Stopping CPU interrupts balancing daemon    [ok]
```

---

### Post by Bucky Ball on 2013-12-04
Ideas anyone? Stumped myself. Seems to be only my custom ISO (and another distro from memory) that hang at that error. 

All other VMs are working pretty much fine, though. What fun! But seriously; I want to have a barebones ISO backup of my custom mini install. 

I had a two monitor setup using arandr in the minimal install I remastersys'd so thought that might be causing the problem. Unplugged the monitor and did another 'remastersys dist' but made no diff. Same error. :-k

---

### Post by JKyleOKC on 2013-12-04
If it's UUIDs that are causing the problem, have you tried rolling fstab back to the old sda/hda nomenclature for the drives? If the ISO lets you see the startup reports long enough to determine whether it's identifying drive as sdX or hdX, that may get you past the UUID problem -- but might well run into more down the road.

It's also possible to identify drives by their labels, and that might be as good as using UUIDs to make sure the same physical drive always gets the same mount point. However I've never tried this approach, just thought about it from time to time...

---

### Post by Bucky Ball on 2013-12-04
Same machine, same UUIDs. ;)

The minimal install is on another partition of the same machine. Remastersys a dist of that and create and ISO, boot to another 12.04 on the same machine, launch the ISO in a VM, get the error. Burn a DVD and boot from that; get the same error. I have actually tried doing a burn with all entries in fstab hashed out so the UUIDs wouldn't be a problem but made no difference. :-k

---

### Post by JKyleOKC on 2013-12-05
> **Bucky Ball said:**
> Same machine, same UUIDs. ;)

The minimal install is on another partition of the same machine.And all of this is on the **host machine**, right? Because each VM is logically a completely different machine. Thus the quoted statements are meaningful only if everything involved, **including** the test installation, is on either the host, or a single VM. However your original description of the problem seems to indicate that the ISO was created on the host, and then tested on a VM -- and if that's the case, then the UUIDs would **NOT** be the same because the virtual disk in the VM is **NOT** the physical disk of the host.

Sorry if this sounds like I'm talking down to you; however many if not most newcomers to virtualization and vbox in particularly don't seem to have a really clear picture of just how much smoke and mirrors come into play here. It works so very well that it's easy to forget that everything is really just an illusion! You may want to investigate the VBoxManage program's "showvminfo" capability; it will give you lots more than you want to know about such things as the UUIDs of a VM's virtual disks...

---

### Post by Bucky Ball on 2013-12-05
[QUOTE=JKyleOKC]... the UUIDs would NOT be the same because the virtual disk in the VM is NOT the physical disk of the host.[/QUOTE]

All I needed to know. 

[QUOTE=JKyleOKC]Sorry if this sounds like I'm talking down to you ...[/quote]

Me too. Well aware its on a virtual disk - there's a lot I don't know about VMs but that I know - but hadn't thought it would change the UUIDs.

Can you now explain, in that case, what the problem is and where do I look to start fixing it? Thanks for any help.

---

### Post by Bucky Ball on 2013-12-05
Just noticed something that may or may not be of interest. At the end of creating a LiveCD of my minimal install, remastersys told me 'Hybrid ISO - Not all BIOS can boot' just before it finished creating the ISO.

Now, when I launch that ISO in a VM I get a message saying 'might not run on this BIOS', or something like it, just before the other two errors,but it doesn't hold things up. The next two errors I've reported are where it hangs. 

The  'might not run on this BIOS' error also appears when one of the other VMs is booting, but things are fine and just carries on to the desktop. That's why I thought it was inconsequential here, but maybe not.

---

### Post by JKyleOKC on 2013-12-05
> **Bucky Ball said:**
> Just noticed something that may or may not be of interest. At the end of creating a LiveCD of my minimal install, remastersys told me 'Hybrid ISO - Not all BIOS can boot' just before it finished creating the ISO.That could well be the trigger for the problem, but since I've never used remastersys at all I'm as much in the dark about fixing it as you are, unfortunately.

What I **can** help you with is getting a possibly clearer picture of what's going on behind the "virtual" curtain. I've had to do some deep digging into parts of vbox, as a consequence of having had the virtual disk that housed my e-mail files crash a few years ago. Those files formed a critical part of my data recovery business so I wanted to recover as much of them as possible.

What I found out was that a virtual disk, in VDI format at least, is almost identical to a disk image created by such Windows programs as Acronis True Image. There's a large header area, used by vbox for housekeeping chores, followed by the disk image itself. While I no longer remember all the details, it's possible to get access to that image and actually mount it as if it were a separate physical disk. That's what I had to do, to recover the most essential correspondence and customer data.

Vbox creates its own UUIDs for most everything; the "showvminfo" command I mentioned previously will show you these, and you can use them where needed in place of VM names or labels. The VM also includes its own BIOS, which is totally separate from the host system's BIOS. And since many different host system BIOS versions exist, the virtual BIOS inside of vbox has to be a generic one-size-fits-all affair -- consequently it's unable to deal with features that may be unique to the specific physical BIOS of a host system. However remastersys might be using some such feature.

The term "hybrid BIOS" in the error message suggests to me that you might be seeing a situation where some workaround for incompatibilities between EFI and MBR booting is in play. That's the only implication I can draw from "hybrid" but I have no idea exactly what could be going on.

This means, I suspect, that remastersys may not be a usable tool for your purpose, but it might instead simply indicate that you need to change some of the configuration of your test VM. It seems obvious to me that some of the choices available in the VM settings change parts of the virtual BIOS; for instance, there's a checkbox to choose EFI booting, with MBR booting implied if this isn't checked. The hypervisor enabling/disabling boxes also must modify BIOS settings. Perhaps tweaking these settings might get you past the problem, or at least far enough past it to complete booting so you could check the *dmesg* and *syslog* files to see what's happening.

For myself, I solve the original problem of preserving a pristine (virtual) system for future use by simply copying its VDI file (mine are usually only 10 GB) to a different partition or drive, and then using the VBoxManage cloning capability to create a new copy for use when needed. The cloning process automagically changes the UUIDs. I could do the same for the VM file itself, but I simply create a new VM (with identical attributes except for the disks) via vbox, and assign the cloned VDI to it as its drive. Since that VDI already includes its operating system, it works right off the bat. This may not be a solution for you, and definitely leaves the immediate problem unsolved, though...

---

### Post by Bucky Ball on 2013-12-07
I made some progress or just progressed to another problem. First I opened /etc/init/failsafe.conf and changed all the 'sleep' lines to '1' so it would skip straight to the problem. Remastersys and VM and get to an error:  'Booting system without full network configuration' 

After doing some research, I opened /etc/network/interfaces and hashed out all lines but the lo ones:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto wlan0
# iface eth0 inet dhcp
```

Did a remastersys, tried it in a virtual machine and same hang. 'Booting system without full network configuration' . I will be more specific about that error when I'm in that install in awhile.

Maybe I need to do a combination of hashing out all network interfaces and all fstab lines and unplugging everything from the computer. Incidentally, the above remastersys was done with just the laptop; no second monitor or even USB devices plugged in (like wireless keyboard/mouse).

I will continue to stumble forth ... :-k

PS: Find attached screenshot of the error I'm now hanging at. This message was coming after that:  'Booting system without full network configuration'. For some reason that's now gone. I just ran again and hanging before any network message this time. Go figure.

Incidentally, after much research it appears:

Stopping Mount network filesystems
Stoppying cpu interrupts balancing daemon

... are nothing to worry about and should be ignored as not relevant here. All other pages recommend, though, editing the /etc/init/failsafe.conf file and reduce all the sleep times and everything will be dandy and it will go to normal boot. Not for me.

PPS: My only other idea is ... apparently there is a /skel file for remastersys where you can exclude files and folders. I might look into that and get the remaster to miss anything that might in the least bit smell suspicious. Any thoughts? I will research it ...

---

### Post by JKyleOKC on 2013-12-07
You're way past me now. Might be worth while to browse through the vbox source code, but I'm certain it will be clogged with so much detail that any clues will be difficult to identify...

---

### Post by Bucky Ball on 2013-12-08
Ok, a new line of thought. The install I am remastering has nothing in the /home directory but symlinks to directories on a storage drive. Theoretically, it should be pretty much empty, bar my settings. 

I'm wondering ... is remastersys somehow dragging in the data from the symlinks? That's why my image is too large? It appears that ISO9660 maximum file size is 2Gb. My / directory appears to be 118Gb when I look at it's properties! 

It shows as just over 11Gb in Gparted which is why I'm wondering if there is something odd going on with the symlinks. Thoughts?

I think I've got the /etc/skel worked out, but wouldn't know what to put in there and can't figure that for now. What I really want is to find ways of taking things out and finding out what's being included exactly ...

* Scratch the above idea. Just did a remaster and the final ISO image is 1.03Gb. Under 2Gb. Still getting the message. Don't think I should be worrying about the 'hybrid iso' message either. These two lines from near the end of the remastersys log:

Creating Mini.iso in /home/remastersys/remastersys
Making Mini.iso a hybrid iso

But after doing some research I figure just about every other ISO I've tried probably is a hybrid, too, so somehow doubt that's the problem. 

Is there a log that tells me what happens when the ISO crashes when installing as a VM? There's nothing I understand in the virtual box log, but there is an error at the bottom which I'll hunt down later:

```
00:04:12.225 ********************* End of statistics **********************
00:04:12.228 NAT: zone(nm:mbuf, used:1)
00:04:12.228 NAT: zone(nm:mbuf_cluster, used:0)
00:04:12.228 NAT: zone(nm:mbuf_packet, used:0)
00:04:12.228 NAT: zone(nm:mbuf_jumbo_pagesize, used:0)
00:04:12.228 NAT: zone(nm:mbuf_jumbo_9k, used:0)
00:04:12.228 NAT: zone(nm:mbuf_jumbo_16k, used:0)
00:04:12.234 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
00:04:12.341 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={1968b7d3-e3bf-4ceb-99e0-cb7c913317bb} aComponent={Console} aText={The virtual machine is being powered down}, preserve=false
```

The long number in the error doesn't match any of my UUIDs and I'm wondering if it should. Which brings us back to the theory, JKyleOKC, that it is getting the UUIDs wrong. So, if I put /etc/fstab in the exclude list in remastersys and see what happens ...

What looks like it might be a UUID comes after this, though:

```
00:04:12.234 Changing the VM state from 'DESTROYING' to 'TERMINATED'.

```

---

### Post by Bucky Ball on 2013-12-08
Excluding /etc/fstab got me back to the 'Waiting for network configuration ...' error again. See attached.

Perhaps if I now exclude /etc/network ...

* Update: Tried excluding /etc/fstab and /etc/network. Made no diff. Just don't get the 'Waiting for network config' messages now. Messages in the attachment identical apart from the blue network message ...

---

### Post by JKyleOKC on 2013-12-08
You're **way** beyond me now! Might be worthwhile starting a thread at [http://forums.virtualbox.org/](http://forums.virtualbox.org/) to get attention from the actual vbox developers. That's where I found the details about the VDI format that let me try recovering data from a busted virtual drive (that had been truncated and lost some of its critical information).

---

