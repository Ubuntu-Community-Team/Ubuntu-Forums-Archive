---
title: "Ubuntu Server 22.04 LTS + SSD + dm-crypt = instability / disk corruption?"
date: 2022-04-30
forum: Server Platforms
---

### Post by anezmorv on 2022-04-30
**[SIZE=4]Click this link to go to the "solution": [/SIZE]**[https://ubuntuforums.org/showthread.php?t=2474486&p=14095592#post14095592](https://ubuntuforums.org/showthread.php?t=2474486&p=14095592#post14095592)[B][SIZE=4]

TL,DR:
[/SIZE][/B][SIZE=2]The goal: build an encrypted file server + VM host.[/SIZE]

[LIST]
[*]Purchased all new hardware
[*]Installed Ubuntu Server 22.04 LTS without FDE
[*]Setup VirtualBox + Windows 10 guest VM
[*]Everything worked as expected
[*]Wiped system
[*]Reinstalled Ubuntu Server 22.04 LTS with FDE through dm-crypt/LUKS
[*]System stability went straight to hell
[*]Spent several days googling / tweaking settings
[*]Gave up, reinstalled Ubuntu without FDE
[*]Everything works as expected (except lack of encryption)
[*]Abandoned project
[/LIST]

[B][SIZE=4]Update
[/SIZE][/B]

[LIST]
[*]The same problem happens with Ubuntu 20: FDE w/ dm-crypt, transfer a large file, kcryptd workers hit 99% IO load, transfer dies / OS locks up
[*]This is not a virtualbox problem, the Ubuntu 20 system did not have virtualbox installed
[*]Swapping the SSD for an known-working and reliable spinning hard disk had no effect, problem persists
[/LIST]

**[SIZE=4]Intro[/SIZE]**

Yes, I am aware that this is a massive wall of text. If this was a single easy problem then I would've found my answer on google or stack overflow and been on my way. Complex, fiddly issues tend to not be associated with quick and easy diagnosis.

Somehow I traced all of my problems back to the LUKS / dm-crypt FDE option that I enabled during setup. I wrote out this brain dump in case someone wants to see a full description of exactly what happened.

Also, if you found this thread on the 8th page of Google results at 3AM on a Monday, staring into the mute remains for some key, some solution to your plight, you should know right now that I have no solution for you. I ultimately gave up. Fighting these problems took too much time and I had to abandon the project. I couldn't build the system I wanted to build with full-disk encryption on Ubuntu Server 22.04.

I'm posting this thread for two reasons:
[LIST=1]
[*]A sign post / hint guide for the next poor user who suddenly finds themselves dealing with some of the same problems
[*]Maybe someone else in the forum can offer some insight for a real solution.
[/LIST]

**Hardware:**
[LIST]
[*]AMD Ryzen 5 5600
[*]ASRock B550 Steel Legend
[*]NEMEX 32GB DDR4-3200 PC4-25600 ECC unbuffered DIMM
[*]Corsair 850W PSU
[*]Kingston 120GB A400 SATA SSD
[*]Ubuntu Server 22.04 LTS with full-disk encryption (enabled during installation)
[/LIST]

**My laundry list of issues:**
[LIST]
[*]My Windows guest running under VirtualBox 6.1 won't stay up for more than a few seconds before crashing / BSODing / rebooting.
[*]The Ubuntu host hangs while shutting down for reboot. the chassis reset button has no effect in this state.
[*]Incoming SSH file transfers will move ~5GB and then just stop dead at 0 bytes/second.
[*]I had one kernel panic.
[/LIST]

[SIZE=4]**Hardware Testing / Temporary System Setup**[/SIZE]

This is what I did after receiving all of the new hardware.

First, SSD testing. I attached the new Kingston SSD to another PC and ran a destructive badblocks test. badblocks reported no errors. smartctl also reported no errors.

Second, RAM testing. I assembled the system described above, including the Kingston SSD. I then ran MemTest86+ from a boot disk for about 2 days and saw no issues there either.

Third, CPU/RAM/OS combo testing. I installed Ubuntu Server 22.04 without FDE enabled just so I could test the hardware. I ran Prime95 for a week and saw no errors. edac-util reported no ECC errors either.

I installed VirtualBox 6.1 straight from the default Ubuntu package repo (I did not download the .deb from Oracle). I moved a ~30GB Windows VM over SSH file transfer to the new box and booted it as a headless VM. I was able to connect to the Windows guest VM over Remote Desktop without issue. The VM ran Prime95 overnight without any issues.

At this point everything seemed perfect. I was ready to tear the system down and build it up for "production".

[SIZE=4]**The Troubles Begin - Setup**[/SIZE]

I booted from a GParted boot disk and deleted all partitions from the SSD. I ran dd to zero out the first ~10GB of the disk to ensure that all remnants of the test OS were completely gone. Then I booted from the same Ubuntu 22.04 LTS DVD that I had used to install the system the first time.

During installation, on the "Guided storage configuration" page, I chose:
[LIST]
[*]Use an entire disk
[*]Set up this disk as an LVM group
[*]Encrypt the LVM group with LUKS
[/LIST]

Then I set the password. On the next screen I had to adjust the encrypted OS partition size to *actually* use the entire disk (it only wanted to use 58G out of the available ~107GB), and then I let the installer fly.

I wasn't worried about the incorrect partition size since I'd seen that before when doing LUKS on Ubuntu 20. Kinda annoying it's still an issue with the latest installer, though.

[SIZE=4]**The Troubles Begin - Broken SSH Transfers**[/SIZE]

On next boot I entered my LUKS password and the OS started as expected. I got my SSH key setup again, and then started moving the ~30GB Windows VM over to the freshly installed system.

WinSCP moved about 5GB and stopped. Then it froze. Then it dropped the connection. Hmm, weird. Maybe it's an issue with my main Windows desktop. I rebooted it and tried again. Same problem. I rebooted my network switch. Same problem. Tried different ports on the switch for both the Linux and Windows desktop. Same problem.

WTF. SSH transfers were working flawlessly 20 minutes ago on the non-FDE Ubuntu installation on exactly the same hardware.

Running iotop I saw that at the beginning of the SSH transfer the disk was writing at ~110MB/sec, which meant the gigabit connection was maxed out. Then disk throughput would drop to zero but a bunch of the kcryptd workers would be slamming the disk at 99% IO load. This went on long enough to stall and eventually kill the SSH file transfer.

Also, while these kcryptd workers were busy going nuts on the disk, terminal echo still worked but nothing else did. ls -la froze, htop froze, screen froze. Basically anything that touched the disk just stopped dead until the kcryptd workers got out of the way.

I found these two Stack Exchange threads:

[https://serverfault.com/questions/1012566/luks-high-transfer-rates-followed-by-high-io-wait](https://serverfault.com/questions/1012566/luks-high-transfer-rates-followed-by-high-io-wait)
[https://askubuntu.com/questions/918580/how-do-i-troubleshoot-a-disk-io-performance-issue-possibly-related-to-dm-crypt-l](https://askubuntu.com/questions/918580/how-do-i-troubleshoot-a-disk-io-performance-issue-possibly-related-to-dm-crypt-l)

Specifically this thread, which provided what I thought was a solution:

[https://askubuntu.com/questions/918580/how-do-i-troubleshoot-a-disk-io-performance-issue-possibly-related-to-dm-crypt-l/1363929#1363929](https://askubuntu.com/questions/918580/how-do-i-troubleshoot-a-disk-io-performance-issue-possibly-related-to-dm-crypt-l/1363929#1363929)

And so I ran this command:

```
cryptsetup --allow-discards --perf-no_read_workqueue --perf-no_write_workqueue --persistent refresh <name of my disk>
```

Then rebooted. SSH transfers suddenly started working again.

**[SIZE=4]The Troubles Continue - Broken VirtualBox Guests[/SIZE]**

I got the Windows guest VM moved over and installed VirtualBox 6.1. I opened up the GUI through Xserver forwarding over SSH and registered the VM. Then I told it to start, but accidentally clicked "Start" instead of "Start Headless".

The VM booted up, showed the Windows logo, got to the login screen, and then flashed blue and restarted. Okay fine, maybe the VM didn't like running with Xserver over SSH. Understandable. I killed the VM and restarted headless. This time I made it to the desktop through Remote Desktop but after about 10 seconds the connection dropped.

The VirtualBox log said the VM had a "critical error" and automatically restarted it. I reconnected to the VM display and caught a BSOD in the middle of a dump. "SYSTEM THREAD EXCEPTION NOT HANDLED" in ntfs.sys. Okay... something is really wrong here.

The VM never booted again after that. The Windows logo would come up for just a second and then the VM would reboot itself.

I nuked the VM and transferred it over again. Then I ran b3sum on the VM files to confirm that they had transferred correctly from the source. The hashes matched, so no corruption there. I re-registered the VM and tried again. Same problem, boots and runs for few seconds, crashes hard and eventually destroys itself after a few boot loops.

Well. That's discouraging.

Fine, whatever. Maybe it's just Windows being Windows. I decided to rebuild the Windows VM directly on the Ubuntu server. I copied the ISO over, setup a blank VM, started it up, got into the Windows installer, setup partitions, files were copying... bam, another error. "Windows cannot install required files." I checked the ISO hash with b3sum, so the installation media was good. A fresh VM failing during Windows installation? This had to be a problem with the host.

I dug all over the VirtualBox forums and ticket lists looking for anything to go on. A lot of users have had issues mixing up paravirtualization acceleration between hyper-V and KVM and then trashing their VMs. But that didn't fit here - the same Windows VM had been working just fine on the non-FDE Ubuntu 22 system I was running barely an hour before. And how could VirtualBox basic default settings be wrong on a new VM?

Bad RAM? I ran memtest86+ again overnight. No errors reported.

**[SIZE=4]The Troubles Continue - Reboot... doesn't[/SIZE]**

Over the course of dealing with the broken VMs I rebooted the system several times. I did the same way I've done it for years:

```
sudo reboot
```

SSH would drop and the monitor would flash a bunch of scrolling text and then turn off. All of this is expected. Except, the PC itself would not reboot. Lights will stay on, fans will stay on, but the UEFI splash screen would never come up.

In a bizarre turn of events, even pushing the chassis reset button had no effect. I had to hold the power button down to forcefully turn the system off. (And yes, the reset button is wired correctly, I tested that.)

I didn't spend any time digging into this problem, so I have no clues to offer.

[SIZE=4]**Final Troubles - kernel panic**[/SIZE]

During one of my reboot / forced power off / boot cycles, shortly after unlocking the disk for boot, the system halted with kernel panic before it hit the login prompt. At this point I was so frustrated that I just yelled "Of course! Why not kernel panic? Might as well just catch fire too!" and immediately hit the power switch. I should have taken a moment to record exactly what caused the kernel panic, but didn't.

**[SIZE=4]Giving Up[/SIZE]**

I had spent about a week chasing clues and vestiges of solutions on google, reading 8+ year old forum threads, translating trouble tickets written in Russian / Japanese / whatever, but there was no golden solution that pointed to a root cause for my VM crash issue. And the system itself seemed to be getting less stable with every boot. The reboot hang was seldom at first, but was now happening on every reboot, apt started complaining about broken packages, eventually the network connection stopped coming up on boot. Every bit of it smelled like a bad CPU, bad RAM, a bad disk, or all of the above.

The original test system worked PERFECTLY. Absolutely no problems at all. The "production" system had only one thing different... it used full disk encryption through dm-crypt / LUKS, as offered by the Ubuntu Server 22.04 LTS installer.

But there was no way it could be dm-crypt. I'd been using it for years on older Ubuntu installations. The last mutterings of dm-crypt data corruption bugs happened in 2006. Freaking Amazon uses it for their cloud infrastructure. It could not. Possibly. Be. dm-crypt.

Or could it?

Having nothing to lose at that point, I wiped the SSD and loaded up the Ubuntu installer again, this time reinstalling the entire system without FDE. VirtualBox installed, Windows VM copied over, let's go.

...and it worked perfectly fine. In fact I've been running Prime95 in the Windows VM since getting everything reinstalled again (about 4 hours now) and it hasn't had any hiccups. Compare that to the FDE installation where things were going wrong within a minute of logging in for the first time.

That was all the evidence I needed to point my finger at dm-crypt, or the integration thereof in Ubuntu 22.


**[SIZE=4]Conclusions[/SIZE]**

I, uh. Er. I guess dm-crypt is broken? Somehow? Maybe? Something to do with trim settings that cause the SSD to blow up sectors that are actually in use?

I don't know what else to say about this. I'm not a kernel developer. I'm not even really a tech person. I just use Linux where I feel like it's the right tool for the job. In this case I was trying to build an encrypted file server - something I have done several times before on Ubuntu 18 and 20 - and dm-crypt on Ubuntu 22 was absolutely not having it.

Installing Ubuntu 20 or older isn't an option since the older kernels don't know how to read from my ECC controller, apparently.

Anyway if you read this far, thanks. This was a chore to type out and probably even worse to read.

To those looking for a solution to the same problem - good luck. May you succeed where I failed.

To those who wish to offer advice or help - I'll check the thread regularly for a few days to answer any questions.

---

### Post by TheFu on 2022-05-01
WWWW TL; DR.

22.04 is very new.  All third party software for it will be beta quality at best.  Wait until the .1 release in August if you can't use 20.04.x now. I have 1 22.04 server system running in a VM today. I probably won't use the release for production for a year as my 3rd party software catches up. For a play desktop system, I might jump on in mid-June.  I wait to avoid issues.

Using very new hardware is always a risk in Linux. It takes time to get support.
BTW, the HWE kernel for 20.04 is 5.4.x, so the ECC controller may not be an issue.

I've only been using LUKS about 7 yrs and only on laptops or portable storage devices. I've been afraid to use it on any server, since I sometimes need to reboot the servers when I'm on the other side of the planet and don't have remote BRS access to the systems. I have been tempted to encrypt everything, just to make HDD warranty returns less of a concern. But I haven't had any warranty returns in a few years, so that worry hasn't popped up like a perfectly cooked catfish. ;)

---

### Post by TheFu on 2022-05-01
I realize I'm not actually very helpful. Sorry. To me, new is the enemy of stable and stability is 1000x more important than 'new'.

BTW, the release notes for 22.04 say a new version of ssh is included and that something changed related to RSA-based keys. I moved to ed25519 keys everywhere a few years ago, so I didn't read that too closely.

I haven't used virtualbox in a very long time.  Began switching from Xen to KVM around 2010. That took a few years, as physical servers had to be updated.  Virtualbox was always unstable for me on a Linux host, so it was used on Windows for a few more years, until KVM graphics performance became awesome around 2016.  In 22.04, the virtio GPU drivers should make it even more awesome.

BTW, I have a Ryzen 5600G running non-ECC RAM at 3200 Mhz with a few KVM VMs. It is very stable. On an older Ryzen 2600, I had to reduce the RAM speed to 2666 Mhz after adding a 2nd bank of unmatched, but exactly the same brand and model, RAM.  Both systems have the same Asus B450 motherboard. I specifically avoided the B550 because the onboard NICs were all 2.5Gbps and poorly supported. Hardware that is too new is often bad for Linux.  Both the ryzen systems are running the exact same BIOS version.  The 5600G needs a newer kernel (v5.10+) to better support the iGPU.  The older 2600 is running v5.4.x.  But neither have encrypted storage connected.

As for LVM, I've taken to setting up the LVs sized the way I like, though I don't know how to accomplish that using encryption. The installer really has a terrible UI for dealing with LUKS, LVM, and sizing.  I think the last time I did an install, it still forced msdos/mbr partition tables. Yuck.

---

### Post by anezmorv on 2022-05-01
> **TheFu said:**
> WWWW TL; DR.

Ha yeah, I don't think I've written that much text on the internet in a long time. The post started out as a rant but I realized that wouldn't be productive so I rewrote it to include as much detail as possible.


> **TheFu said:**
> 22.04 is very new.  All third party software for it will be beta quality at best.  Wait until the .1 release in August if you can't use 20.04.x now. I have 1 22.04 server system running in a VM today. I probably won't use the release for production for a year as my 3rd party software catches up. For a play desktop system, I might jump on in mid-June.  I wait to avoid issues.

Besides Virtualbox, I'm not using any 3rd party software. Vbox was just an innocent bystander. I just used the FDE option through the Ubuntu installer, and if that counts as 3rd party software then &#129335;

> **TheFu said:**
> Using very new hardware is always a risk in Linux. It takes time to get support.
BTW, the HWE kernel for 20.04 is 5.4.x, so the ECC controller may not be an issue.

I started off with Ubuntu 20 but it couldn't find my ECC controller, so I reluctantly tried Ubuntu 22... and then [I]disaster struck

[/I]

> **TheFu said:**
> I've only been using LUKS about 7 yrs and only on laptops or portable storage devices. I've been afraid to use it on any server, since I sometimes need to reboot the servers when I'm on the other side of the planet and don't have remote BRS access to the systems. I have been tempted to encrypt everything, just to make HDD warranty returns less of a concern. But I haven't had any warranty returns in a few years, so that worry hasn't popped up like a perfectly cooked catfish. ;)

I have another system running Ubuntu 20 with dm-crypt/LUKS. It just runs networking monitoring scripts and not much else. Very lightly loaded. Last night I tried transferring a giant file over to it and the exact same problem happened: kcrypt workers hit I/O load of 99%, the system froze up, SSH transfer died. I had to hard power-off the box after 90+ days of uptime. Damn it! 

So apparently this isn't just limited to Ubuntu 22. There's something going on with dm-crypt.

> **TheFu said:**
> [COLOR=#000000]I realize I'm not actually very helpful. Sorry. To me, new is the enemy of stable and stability is 1000x more important than 'new'.[/COLOR]

In this case, any attention is better than no attention at all :)

I had some struggles with setting up RSA keys on Ubuntu 22, but that was quickly resolved after a google search. Regenerate new keys with ED25519, install them, done. It just works.

VirtualBox has been stable as a rock for me, hence my reluctance to tear up my entire infrastructure and rebuild on something like Proxmox or ESXi. Maybe at some point in the future. But for now it doesn't seem like Vbox is at fault here. It just happened to be the thing I was working on when the system started showing problems.

Believe me, the first thing I thought about was VirtualBox failing. But after playing around with my Ubuntu 20 LUKS system night, which doesn't even have virtualbox installed, it seems like this is truly the fault of dm-crypt, or how it's implemented under Ubuntu.

---

### Post by TheFu on 2022-05-01
Ubuntu 20 is ambiguous.  Is that 20.04 TLS or 20.10 (which is not supported).  

Some ideas ... the HWE for 20.04 runs 5.11+ kernels. You could put in a single stick of non-ECC RAM and see if that works with 20.04, upgrade to the latest available kernel, then swap that ECC RAM in.

---

### Post by anezmorv on 2022-05-01
> **TheFu said:**
> Ubuntu 20 is ambiguous.  Is that 20.04 TLS or 20.10 (which is not supported).

It's Ubuntu 20.04.3 LTS running 5.4.0-100-generic kernel on an Intel i5-3570. Non-ECC. Same problems, dm-crypt freezes the whole system under high I/O load.

> **TheFu said:**
> Some ideas ... the HWE for 20.04 runs 5.11+ kernels. You could put in a single stick of non-ECC RAM and see if that works with 20.04, upgrade to the latest available kernel, then swap that ECC RAM in.

I might pull the system back out of the closet in a few weeks and make another attempt, but for now I'm pretty over it. I tried, I failed, that's it.

Also since the my Ubuntu 20.04 LTS box has exactly the same problems I don't think using an older version of the OS will solve my issues.

Here's another data point. A few days ago I installed Ubuntu 22.04 LTS on an old HP N40L microserver. 4x1.5TB in ZFS RAIDZ2. OS installed on a 5400RPM laptop drive. No encryption anywhere. Despite its age, the system works without issue. Gigabit is maxed out while writing to the ZFS array. No lag at all.

I installed virtualbox on the N40L just now to see how it did. There were no problems moving the Win10 VM over. It runs perfectly stable too, although a bit slow.

Which means out of these two systems:
* An ancient HP N40L I salvaged from an e-waste bin, running on spinning rust
* A sparkling new Ryzen 5, running on SSD

The N40L with no encryption is vastly more performant (and stable!) than the Ryzen running with encryption. That's insane.

---

### Post by anezmorv on 2022-05-14
I hate to leave a question unanswered so I recently dove back into this problem.

Turns out, both Ubuntu and VirtualBox are to blame for this mess.

**[SIZE=4]Blaming Ubuntu (or maybe just Linux in general)[/SIZE]**

First, Ubuntu ships with dm-crypt configured to use read and write worker queues. Turns out these worker queues aren't as efficient as they should be. dm-crypt (or whatever is managing all this useless queue garbage, remember I'm not a kernel developer) waits for the queues to fill up with a bunch of crap, and then absolutely slams the disk hard trying to dump multiple queues at once. Naturally the disk dies under the load and the entire system locks up, completely negating any benefit to using a queue. I suspect only users running NVMe drives wouldn't notice this. Cheap SATA SSD? Yes. Old spinning hard drive? Absolutely.

In other words, I can install Ubuntu with LUKS just by following the installer, and be left with a system that is unusable for all but the simplest tasks.

I confirmed Fedora has the same issue, so it's not just unique to Ubuntu. I'm shocked no one has looked into fixing this.

Anyway, I "fixed" it by running:
```
cryptsetup --allow-discards --perf-no_read_workqueue --perf-no_write_workqueue --persistent refresh <name of my disk>
```

This disables the queues and passes data directly through to the disk. I think. Maybe. I'm not a kernel developer. I know it solved my SSH transfer and system lock-up issues though.

**[SIZE=4]Blaming VirtualBox[/SIZE]**

Secondly, on the VirtualBox side, I found this ticket: [https://www.virtualbox.org/ticket/10031?cversion=0&cnum_hist=14](https://www.virtualbox.org/ticket/10031?cversion=0&cnum_hist=14)

My interpretation is VBox has its own timeouts for its internal I/O emulation whatever thing, which gives up on trying to use the host disk if it takes too long. This failure is then passed along to the VM guest in a non-graceful manner, where the guest VM is left holding the bag thinking that its own disk has failed. And what exactly is a VM to do, if it can't read or write data from its own disk? Well, it cakes its pants and dies horribly, as I discovered when running both Windows and Linux guests.

That's just a guess though.

I "fixed" this problem by converting my VMs over to KVM and using virt-manager to replace the VirtualBox UI. Fortunately it's easy to convert the VDI files to QCOW2 and then load them up.

KVM is much more stable running on a system with LUKS. Dunno why. I'm not a kernel developer.

Switching virtualization software definitely wasn't an ideal solution, but that VBox ticket is over 10 years old now, so it's probably never gonna get fixed.

So there you have it. What a complete disaster.

Microsoft's goofy data collection and auto-reboot shenanigans aside, I've been running encrypted Windows file servers since 2011 without any issues that come close to what I had to deal with here. Apparently Linux still has a long way to go to catch up to same level of usability.

C'est la vie.


**[SIZE=4]Making the jump to KVM[/SIZE]**

Here's some info for anyone else who wants to make the jump from VirtualBox to KVM + virt-manager.

If you're using an SSH client that supports X-forwarding, just running virt-manager and do whatever you need to do with the UI.

I confirmed that USB passthrough to a Windows virtual machine works. External hard disks can pass data back and forth, no issue. You may have to edit your udev rules to allow access to the USB device though.

The biggest issue I had was setting up a bridged network interface. With VBox using a bridged network adapter is very simple. Just assign the VM's adapter to the physical adapter and the VM is presented to the network as though it's a real machine. It has its own MAC, pulls an IP from DHCP, done.

KVM doesn't work like that. It requires a bridge adapter that already exists and is assigned its own subnet.

If you want KVM to act like VirtualBox does with bridged adapters connected directly to the physical network, then you'll have to do some netplan hackery. Use my netplan file as an example:

[B]Original settings

[/B]```

network:
  ethernets:
    eno1:
      dhcp4: true
  version: 2

```


[B]Modified settings (for KVM bridged VMs)

[/B]```

network:
    version: 2
    renderer: networkd
    ethernets:
        eno1:
            match:
                name: eno1
            dhcp4: no
            optional: yes
    bridges:
        br0:
            macaddress: 74:46:a0:b4:39:b9
            dhcp4: yes
            interfaces:
                - eno1

```

This will force the bridge to pull an IP over DHCP. Otherwise you'd have to go down the routing table rabbit hole and that's just pain on top of pain.

If you don't want to mess up your static DHCP mappings then set the bridge to the MAC of your physical NIC. In my case this was eno1.

---

### Post by TheFu on 2022-05-14
I don't use DHCP on my systems, except for laptops and devices that don't have a way to enter a static IP.  I've been burned by DHCP servers having problems and systems being unable to get on the LAN due to that.

KVM doesn't know anything about networking. It just uses the what is provided by the OS.

Network setups aren't part of KVM-qemu.  Once that is understood, then we come at the problem from a different angle.  Setup the bridge using whatever the server networking config tool is and use static IPs on the hypervisor host.  This bridge doesn't need to be on a different subnet from the normal LAN, but it can be, if you like.  I think libvirt does setup a NAT-LAN for guest VMs. I only use those for toy VMs that will live for less than a week, if that long.

You've lost me on the routing table comment. I see that more with VPNs and can't ever recall having any issue with bridges.

I played with USB passthru 1-2 yrs ago. It isn't part of my workflow for VMs. When I did, all the Linux VMs, "just worked" and Windows needed me to exclude the device from the host, so it (Windows) could grab it for exclusive use.  Since I don't allow mounts of storage devices through udev, I didn't need to do much, but a normal desktop user would likely have a fight.  For USB storage devices I use all the time, I use autofs which will mount them automatically when requested and umount them when there aren't any open files.  It is very convenient once setup, plus autofs supports all the mount options that the mount command and file system support, so we aren't stuck with terrible performance that non-Linux file systems get by default.

---

### Post by RedScourge on 2022-09-15
So now that it has been a while, did you ever figure out which is actually to blame? Was the common factor Virtualbox or Ubuntu? Did KVM actually solve it?

I may have just stumbled into this exact same mess, as I recently upgraded and now I'm getting crashing servers.

Also FYI, the above cryptsetup command does not likely persist across reboots, however you can add those options in /etc/crypttab with something like this, though with your own device names, UUIDs, etc:

```
dm_crypt-1 UUID=5aec3088-9e3f-48d1-89c4-d461d05a0af3 none luks,noauto # HDD, performance options disabled
dm_crypt-3 UUID=85670040-289d-4f87-ba9f-ec320c599fd8 none luks,discard,no-read-workqueue,no-write-workqueue,noauto #SSD, performance options enabled

```

FYI "noauto" makes them not be unlocked on boot, you would NOT want this for a whole-drive encryption setup, this is just for where you have drives that you unlock later after boot

---

### Post by RedScourge on 2022-09-17
UPDATE: While my setup and symptoms appeared identical, I no longer think this is my issue; I have two servers, an old one, and a new one, and the old one is not experiencing this sort of corruption, and I have now gone back and confirmed that my corruption issue on the new server only started when I inserted an old Radeon HD 5500 or so GPU for the VGA port since although the machine has a 5600G with its own iGPU, my KVM switch is VGA only. I shut down the machine, installed the card, and ever since then, the new machine's VMs started getting routine general protection faults, service segfaults/restarts, and data corruption, seemingly randomly and proportional to use. memtester has failed to reveal any problems, so I think I just have to take that video card out and get an active HDMI adapter and use the built-in graphics and I will probably be fine. 

I think the cryptsetup and kernel updates they've released in the intervening time have probably solved the issue highlighted by this thread; but the other possibility is that the original poster was also using an old Radeon HD like I was when the issue appeared and maybe that was the true cause of the issues.

---

