---
title: "An Idea to have the advantage of ZFS in Ubuntu."
date: 2008-09-05
forum: Virtualisation
---

### Post by eldaria on 2008-09-05
Hi everyone.
I'm reinstalling my server, this time I want to try out some virtualization.

One of the things I also would like to add is ZFS.
So my first thought was to use OpenSolaris as host, and then run various Servers in Virtualization.
But when I ran the compatibility check to see if it would work on my Hardware it came up with so many missing drivers I had to throw that idea out, I mean no drivers for 3 of my 4 Harddrive controlers, and no driver for network card. 
Ok so I had kind of given up the idea of having ZFS.

So I went ahead and installed VMware server, and had installed 1 Ubuntu server, when I thought.
What if I Install OpenSolaris as a virtual server, and attached the drives directly instead of disk images, that would give Opensolaris access to the drives to run ZFS on them, and then I could share the files system over nfs, giving the other virtual servers access to the advantage of zfs, while running linux.
And since they would all run on the same server, the nfs would be blazing fast not having to go over the actual network.

ok so this might be far out, but do you guys think it could work? or would there be so much overhead that zfs-fuse would be a better option?

Right now my config looks like this.
3 GHz Pentium D 930 with 4GB RAM
1 ATA 160GB drive used for Boot and Swap, and rest is LVM Group noMirror
2 ATA 250GB drives configured with Software Raid 1, and LVM on top in group Mirror.
1 SATA 250GB drive with LVM in group noMirror

In this Ubuntu server 6.06 and everythig is running as services, LAMP + Mail + nfs/samba + some other.


My Original plan was this:
OpenSolaris Host with ZFS handling all harddrives + nfs and Samba.
On top of this xen virtualization or Virtualbox, running individual servers:
Ubuntu Apache
Ubuntu SQL
Ubuntu Mail
Trixbox Telephony
Windows XP for Playstation and XBox media server

How I figured it could look instead.
on the 160GB, I install a minimal partition for Ubuntu Hardy server, like 2-4GB, 512MB Swap, 4GB for Hosting guest image for Solaris. The rest i set up as a raw partition.
Also the 3 250GB drives are set up as raw drives.
Now in this config I install VMWare server, and install OpenSolaris Guest OS.
In OpenSolaris i now add the 3 Raw drives and 1 raw Partition and set up as a ZFS pool.
I share this as NFS and Samba depending on what is needed.
I mount the NFS share on Host, and use this for the rest of the guests.

Odd setup, but could it work?
What do you guys say?

Regards,
Brian.

---

### Post by tofagerl on 2008-09-05
I did this exact thing last night, but I had a CPU load of 8-9 when writing files to a raid-z, and when I tried to read files from the raid, I got under 300kbit/sec.

Obviously, this is a YMMV kind of thing, but it scared the willies out of me, so I deleted the OpenSolaris vm and installed ZFS-Fuse, which picked up the zfs pools with a simple zpool import.
I still get a load of over 1 when writing to the raid-z, but never over 2. 

This is with an old Athlon 64 X2 2GHz, 2gb ram and 4 500gb disks. 

In other words: Very happy with zfs-fuse, though it has only been a day.

---

### Post by eldaria on 2008-09-05
Cool, someone tested this wacky idea. :-).
I guess I will drop that idea.

So how is your actual performance on ZFS-fuse, compared to ext3?

I read around that it is almost 30% slower, but I could only find tests that were old, no recent tests.

---

### Post by tschaboo on 2009-08-30
> **tofagerl said:**
> I did this exact thing last night, but I had a CPU load of 8-9 when writing files to a raid-z, and when I tried to read files from the raid, I got under 300kbit/sec.

[...] 

This is with an old Athlon 64 X2 2GHz, 2gb ram and 4 500gb disks. 


I did basically the same thing today but using VirtualBox 3.0.4 instead of VMWare Server and i get much better performance!

I have the same processor, 3GiB RAM and 3 disks (2x250GiB, 1x120GiB). The smallest disk holds Ubuntu 9.04 64bit and a logical volume used as Solaris Root (osol 2009.06). The other two disks are managed by LVM as well and again I'm giving VirtualBox the logical volumes directly instead of going with an image file.

Running ZFS (on the other 2 disks) in the virtual machine on Solaris i get the following benchmarks, all done with dd to 10GiB-files and all numbers in MiB/s:

```

                write        read
single disk     53,5         63,1
mirror          51,3         93,0

```

In this case the throughput of the virtual harddisks seems to be the limiting factor. I did the same benchmark again, using LUKS on ubuntu to encrypt the volumes and get the following numbers:

```

               write         read
single disk     53,5         62,1
mirror          38,6         64,0

```

In the mirrored configuration the CPU was the limit. Of course raidz instead of mirroring will slow down the already CPU-limited case even more and going through the network (I couldn't test that, because I don't have a gigabit-switch yet) might also have an impact, but I don't expect to reach numbers as horrible as yours are.

In case somebody is interested I could go into more detail on how I set up this stuff.

---

### Post by joel_ezekiel on 2009-08-31
I have some good news for you.

I am currently running Jaunty on my server and using it as a desktop. I have installed the 2.6.26-2 AMD64 Xen Debian kernel, just make sure you get the one with the fix for a bug which would cause it to freeze... something to do with the way the kernel/cpu/hypervisor handle something.

On this "server" thats actually my desktop i am running XP in a HVM for encoding things to DVD with ConvertX2DVD and running other silly .NET apps, and a paravirtualized OpenSolaris with 8 1TB drives passed through and a ZFS raidz2 shared with CIFS that i can copy off at about 70-80mb/sec over gigabit. Can copy to/from the same raid at about 200-300mb/sec, an impressive read/write considering it was copying to itself.

8Gb ram, q6600, ep45-ud3p board with a shitty little $20 VIA sata controller for an extra 2 ports. (I had a few problems with the jmicron and this sata controller would of never worked if i just used Solaris).

This imo is the cheapest way to have a fileserver as you can use ZFS and pretty much any old hardware as Linux now days supports most everything.

For installing Xen on Jaunty to use it as a Dom0
[http://www.infohit.net/blog/post/running-xen-on-ubuntu-intrepid-and-jaunty.html](http://www.infohit.net/blog/post/running-xen-on-ubuntu-intrepid-and-jaunty.html)

For OpenSolaris DomU
[http://taiter.com/blog/2009/02/opensolaris-200811-paravirtual.html](http://taiter.com/blog/2009/02/opensolaris-200811-paravirtual.html)
(This isnt exactly what i used to get my osol up and running but this is what i found with google and should get you started)

Edit: I am actually planning to turn this into a headless server after i get the parts to create my hackintosh for my desktop, anyone have any suggestions on which OS to use that supports Xen out of the box. I think the main options are CentOS or OpenSUSE. Otherwise i was contemplating compiling a pvops kernel and xen 3.4 but im not sure if i can be bothered.

---

### Post by tschaboo on 2009-09-03
Thanks for sharing your experience.

I did some more benchmarks with my VirtualBox-setup and it got slowed down more than expected when going through the virtual NIC. In the hope for more performance I tried Xen as well, but it's pretty tricky. I tried first with the link you provided for 9.04, then with 8.04 and now I'm running Debian Lenny since I prefer an OS which supports Xen out of the box. Performance is around 45% higher than with VirtualBox, so I'd like to keep Xen. But I'm having issues...

My virtual machine only comes up about 50% of the tries and it seems totally random. Sometimes it works, sometimes it stops here:

```
Using config file "/etc/xen/vm/osol0906/osol0906-3.cfg".
Started domain osol0906
                       v3.2-1 chgset 'unavailable'
SunOS Release 5.11 Version snv_111b 64-bit
Copyright 1983-2009 Sun Microsystems, Inc.  All rights reserved.
Use is subject to license terms.
Hostname: osol0906
Reading ZFS config: done.
Mounting ZFS filesystems: (6/6)

```

And I have no clue, what the problem is :(

Any ideas?

---

### Post by joel_ezekiel on 2009-09-06
No idea what your problem is there however since i moved to using the server in headless mode i have tried, Citrix XenServer, but it had no support for adding raw disk drives to a DomU that i could find, if anyone knows how this can be done please let me know as XenServer worked great.

I have also tried a number of different OS/Xen combination's from Fedora rawhide with latest xen/kernel/libvirt to CentOS. I've decided to stick with CentOS as its a clone of RedHat which officially supports Xen and should be the most stable. Debian froze on me, same freezes i had using there 2.6.26-1 Xen kernel on Ubuntu, the annoying thing is using the gitco repository for CentOS which has rpm's for Xen 3.3 and 3.4 with accompanying software, was very easy to set up and get pygrub to bood domu kernels on a zfs volume. But it also froze in the same way. So I'm a bit confused as to whats going on there.

Either way if you want stability and dead simple to get going although a little more tricky to get some distros working (I tried debootstrapping Ubuntu jaunty which crashed on me when at the starting kernel logger line). CentOS is the way to go, its been dead stable using only the RH/CentOS repo's. Then you can play with newer software that tends to break in DomU's or as i plan to do play with getting a stable newer Xen up and running on my new computer which is replacing my server as the desktop. (One disk with "hackintosh" the other for trying new Xen stuff), maybe one day the linux guys will stop fighting against Xen with KVM and work towards making Xen work well with newer software, the last properly supported kernel was 2.6.18, i don't understand why they would want to get rid of paravirtualization. I havent seen anything else that can provide the kind of speeds im getting from my network/drives on common hardware not supported well in Solaris.... oh well.

Anyway I had a similar problem to you accept my solaris domu just hung after the hostname line, i rebooted and it worked.... so i dunno.

But now I've managed to get CentOS dom0, OpenSolaris 121snv domu, XP hvm domu, F11 domu (it had python 2.6 so i changed it to CentOS) for sabnzbd usenet downloader. All working pretty well on cheap hardware and 4gb or memory. :D

edit: my boot config for osol anyway, figured i would show you for comparrison.
```
name = "fileserver"
vcpus = 1
memory = "2048"
kernel = "/etc/xen/kernels/unix"
ramdisk = "/etc/xen/kernels/boot_archive"
extra = "/platform/i86xpv/kernel/amd64/unix -B zfs-bootfs=rpool/52,bootpath=/xpvd/xdf@0:a"
disk = ['phy:/dev/VolGroup00/solaris,0,w','phy:/dev/sda,1,w','phy:/dev/sdb,2,w','phy:/dev/sdc,3,w','phy:/dev/sdd,4,w','phy:/dev/sde,5,w','phy:/dev/sdf,6,w','phy:/dev/sdg,7,w','phy:/dev/sdh,8,w']
vif = ['bridge=xenbr0,mac=00:16:3E:32:F3:1E']
on_shutdown = 'destroy'
on_crash = 'destroy'
on_reboot = 'destroy'
```

---

### Post by tschaboo on 2009-09-07
> **joel_ezekiel said:**
> CentOS is the way to go, its been dead stable using only the RH/CentOS repo's.
I tried the newest CentOS and also had those hangs.

> **joel_ezekiel said:**
>  i don't understand why they would want to get rid of paravirtualization. Neither do I. Especially when there are so many processors without virtualization-support out there that are fast enough to do virtualization with Xen.

> **joel_ezekiel said:**
> 
Anyway I had a similar problem to you accept my solaris domu just hung after the hostname line, i rebooted and it worked.... so i dunno.

Well, how often did you reboot? Just once and now it's running since then? Or do you reboot often and it just never happened again? I did about 20 test-boots and it hung 11 times like that.

> **joel_ezekiel said:**
> ```

ramdisk = "/etc/xen/kernels/boot_archive"

```
That's the only real difference to mine that I see. What's boot_archive? I have x86.microroot there. Did you just rename it, or is it a different archive?

---

### Post by joel_ezekiel on 2009-09-07
[quote=tschaboo]
Well, how often did you reboot? Just once and now it's running since then? Or do you reboot often and it just never happened again? I did about 20 test-boots and it hung 11 times like that.[/quote]
I think it started next go, ive set the server up to be able to be shutdown/booted now without needing to touch a thing and all the domU's boot and mount the fileservers share, im pretty excited about it running so well.. aswell as a vncsession starting for dom0, however after i managed to boot osol this is where boot_archive comes from.


[quote=tschaboo]That's the only real difference to mine that I see. What's boot_archive? I have x86.microroot there. Did you just rename it, or is it a different archive?[/quote]
First thing i do when installing solaris is install SUNWsmbs and SUNWsmbskr for CIFS, however this installs a kernel module i believe and to be honest im not that knowledgable about these things, but it also updates boot_archive after shutdown (after installing CIFS). So i copy boot_archive over to the dom0 and load that for the ramdisk instead of the one off the install disk. If i did not take this step I noted that this  causes smbsvr drive to not load at boot and every restart i was doing a rem_drv/add_drv and svcadm restart smb/server to get CIFS to work.

So that might help you with that issue anyway.
But as i said, everything on my end is great now, i couldn't of asked for a better setup, even my wife would be able to switch the server on after a power outage and access the fileserver and have usenet downloads continue automatically. Of course this is until i either break it from boredom/fiddling or when CentOS 5.4 comes out which should be in a week or two. :guitar:

edit: also make sure you grab the unix/boot_archive both from the dom0 after installing and make sure if your running 64bit to grab the ones inside the amd64 folder. hope this helps you

---

