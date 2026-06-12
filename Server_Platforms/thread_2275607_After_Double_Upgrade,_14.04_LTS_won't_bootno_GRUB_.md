---
title: "After Double Upgrade, 14.04 LTS won't boot/no GRUB - on ESXi 5.0"
date: 2015-04-27
forum: Server Platforms
---

### Post by 3rods on 2015-04-27
---------------- Background

I've started testing the upgrade path from 10 LTS to 14 LTS with my servers. All of my servers are ubuntu and sit on top of ESXi 5.0. 

The first server I chose to upgrade is a simple DNS server, no other services are running other than SSH. After the first **do-release-upgrade** the server was updated to 12 LTS and was working fine. DNS request where working, it could access the internet, and SSH was working. 
----------------
---------------- The Issue

After that I issued another **do-release-upgrade** to bring the server up to 14 LTS. Everything seemed to look OK, but when I rebooted the server all I get is a black screen with an underscore cursor that doesn't blink. 

---------------- 

Since this server is on ESXi, I took a snapshot right after the completion of the second upgrade, but before the reboot. I'm not really sure what to troubleshoot. I tried removing grub-pc and adding it back just to allow it to update everything. But after I rebooted, it still hung at that screen. 

I've tried holding shift (both left and right...) and repeatedly tapping shift (both) a few times, but the grub menu won't load. I suspect that it's not installed correctly. Do I need Grub EFI? 

**What should I look at to repair this non-booting issue? **

----------------

---

### Post by 3rods on 2015-05-28
Boot to the CD and repair the grub loader. This will allow you to boot in to a working system. One of the updates must bork the boot loader.

---

