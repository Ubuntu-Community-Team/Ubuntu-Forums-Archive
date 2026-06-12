---
title: "Upgrading 9.10 Server to 10.04 Server via SSH... possible?"
date: 2010-06-16
forum: Server Platforms
---

### Post by JPorter on 2010-06-16
I have several remotely hosted boxes (running 9.10 Server 64-bit) that I'd like to upgrade at some point to Lucid Server, preferably using [FONT="Courier New"]do-release-upgrade[/FONT].  

Is this possible currently via SSH, without lockout or breakage?

Theoretically, I can have the datacenter staff do the upgrade for me, but I'd prefer to do it myself if it's possible to do so.

Sorry if this question has been posted before, I searched but didn't see it addressed directly.

Thanks!

---

### Post by cybernet on 2010-07-12
i have an upgrade in progress over ssh
i let you know of something showup

---

### Post by mysteron on 2010-07-16
I've done this many times. For me there have been no trouble with doing a dist-upgrade through SSH.

Remember though, as with any major system maintenace, do a backup of the system's important data and configs first :)


/mysteron

---

### Post by YesWeCan on 2010-07-16
Just a kind warning. Be careful if you are running RAID. I had a RAID1 set up on 9.04 server 64bit, remotely accessed by SSH. The upgrade to 10.04 went ok until reboot. The reboot hung because one of the RAID disks could no longer be mounted. Of course, I didn't know this and I had to wait for a remote person to check out where my server had gone. I had to disable automatic mounting of RAID for it to reboot on its own. Subsequently, I modified the RAID config and now it reboots ok.

---

### Post by arrrghhh on 2010-07-16
I always upgrade via SSH, but it is on a local network... so if something does blow up, I do have physical access to the box.

There is a potential for damage from various fronts, but there's nothing outright that would keep you from doing it.  RAID is one consideration as YesWeCan pointed out, another is GRUB.  I've had issues with GRUB before that have caused the box to not boot after an upgrade, and I had to select the kernel it was using manually to get it to work correctly.

---

### Post by imbjr on 2010-07-16
> **JPorter said:**
> I have several remotely hosted boxes (running 9.10 Server 64-bit) that I'd like to upgrade at some point to Lucid Server, preferably using [FONT="Courier New"]do-release-upgrade[/FONT].  

Is this possible currently via SSH, without lockout or breakage?

Theoretically, I can have the datacenter staff do the upgrade for me, but I'd prefer to do it myself if it's possible to do so.

Sorry if this question has been posted before, I searched but didn't see it addressed directly.

Thanks!

I did this on my home LAN not too long ago with no problems. You just have to make sure you've backed up appropriately and pay close attention to any prompts that might appear.

---

