---
title: "Xen, HVM, and ZFS: A bad combo?"
date: 2013-06-17
forum: Virtualisation
---

### Post by mukiex on 2013-06-17
I'm hoping this is a known issue, or at least that someone here might have some experience with it.
To the very least, I'd love to know which logs to check.

Currently installed software:
Ubuntu 12.04
Xen 4.1 4.1.2-2ubuntu2 (earlier version. A bug was back-ported in recently. Google: 22 invalid argument)
ZFS via ppa:zfs-native/stable (zfsonlinux.org kernel module, stable version)
Windows 7 DomU (HVM, PCI Passthrough for video card and USB card)

Herein lies the problem:

Originally I thought the ZFS module was still "unstable". It wouldn't finish a scrub (At around the 2.5tb mark on a 17tb pool) and would become unresponsive after heavy I/O operations. A cursory check of the logs found odd errors for the mvsas module.

Initially I thought that maybe I was burning through RAM by not limiting ARC on ZFS, and /proc/meminfo confirmed that suspciousion by showing me ~200 megs free (out of 24 gigs). So I capped the ARC at 4 gigs. My windows VM uses 11, I've got 24 on the host hardware, so I figured I was fine. And to an extent I was: MemFree stayed healthy. But ZFS, or at least the hardware underneath, was still experiencing issues, and I would occassionally get an unresonsive pool or VERY slow transfers (~1mbyte/sec, vs the ~250 it normally gets).

Then one day I rebooted it and forgot to start my Windows HVM guest up. Scrub completed without a single issue. System never once got slow, or unresponsive. Performance is great.

So the question is, wherein lies the cause here? Are there any known issues with PCI passthrough in earlier versions of Xen? The problem I listed above (22 invalid argument) has only **very** recently been diagnosed and fixed in Xen development (within the last three weeks). Could moving to a Dom0 mean I should recompile some modules with different options to better integrate with Xen? Is there any program that will issue a cursory sweep of installed modules and recompile for those circumstances?

I will gladly upload any logs, lspci info, whatever might help.

Any information would be greatly appreciated. I'd hate to have to wait 'til 14.04 (as I'm not sure that issue above is getting fixed in the current repo).

Edit Note: Possibly unrelated (but who knows): The Windows machine itself is stable for the most part, but there is one major flaw: After a while, HDMI audio through the video card being passed through fails dramatically. Sound starts to warble and slow down, and any app playing sound (xmbc, vlc, etc.) becomes very unresponsive and slow.

---

### Post by heiko_s on 2013-06-17
See if the advice in red near the beginning of [HOW-TO make dual-boot obsolete using XEN VGA passthrough]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013") helps with regard to the 22: invalid argument.

I haven't tried ZFS so any advice of mine would be guesswork.

In general, make sure you leave enough CPU resources to dom0. You can pin CPU cores/threads to dom0, or give dom0 higher priority. IIRC pinning is the preferred option. Can you post your /etc/xen/domU.cfg (win7.cfg) file?

---

### Post by mukiex on 2013-06-20
Possible solution for Google-ers:

1. Nothing really on the ZFS front. I'll update this post in a few months when I update to Xen 4.2 or 4.3. On the plus side, it's been running for over a day without issue. I guess I'll have to shut down the VM and reboot every time I need to run a scrub. (with 3 parity drives, this won't be often)

2. Windows HDMI audio errors or dropping out or warping or repeating: Try substantially increasing your shadow memory. I bumped up mine to a gig because RAM is cheap. I lowered the Windows VP to 10 gigs, so I saved 1 gig in the end. System has run beautifully since.

---

### Post by heiko_s on 2013-06-20
Wow, never thought the shadow memory could make such a difference. I'm curious to see your Windows config file - would you be able to post it?

---

### Post by mukiex on 2013-06-23
> **heiko_s said:**
> Wow, never thought the shadow memory could make such a difference. I'm curious to see your Windows config file - would you be able to post it?

Keep in mind it's hella ghetto, but:

```

name = "livingroom"
builder='hvm'
vcpus = 2
memory = 10240

kernel = "/usr/lib/xen-4.1/boot/hvmloader"

# Should be at least 2KB per MB of domain memory, plus a few MB per vcpu.
shadow_memory = 1024
disk = [
        #Installation Setup
        'phy:/dev/disk/by-id/scsi-SATA_WDC_WD400BD-75J_WD-WMAMA2290578,hda,w'
        ]
vif = [ 'type=ioemu, bridge=xenbr0' ]

# boot on floppy (a), hard disk (c) or CD-ROM (d)
boot="c"

# Radeon 6570 'n USB port
pci=[
        '01:00.0','01:00.1'
        ,
        '05:00.0','05:00.1','05:00.2','05:00.3'
        ]
# Prevent time inconsistencies
localtime=1

```

I could probably get away with far lower shadow memory, like 512 or even 128, but RAM is cheap, and not having my audio drop out after X minutes or hours randomly is worth the gig.

---

### Post by heiko_s on 2013-06-25
Your config file looks nice and short - thanks for posting! For a Windows guest I would add the MAC address option in the vif = ... line - this way Windows will always see the same MAC address when booting. Just a thought. I'll need to read up on shadow_memory - never gave it a thought.

---

