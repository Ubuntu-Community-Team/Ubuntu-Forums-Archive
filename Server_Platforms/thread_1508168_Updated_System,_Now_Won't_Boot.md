---
title: "Updated System, Now Won't Boot"
date: 2010-06-12
forum: Server Platforms
---

### Post by fogNL on 2010-06-12
When Ubuntu 10.04 came out, I installed my server.  It has been running good up until I ran updates today, one of which was a kernel update.  So, I shut down stuff I had run on it, and rebooted the server with 'shutdown -r now'.  It's a headless server, so i waited for a bit and then tried to ssh over, and it wouldn't connect.  I plugged a keyboard/monitor into it, and I see this:

[IMG]http://img689.imageshack.us/img689/5476/img0007hs.jpg[/IMG]

Now, I'm running a software raid 1 with two disks.  I have a 40GB drive and a 120GB drive.  The 120 has been partitioned with 40GB (for the Raid), 2GB for swap and the rest for a storage partition that is currently not in use (empty, just consists of Lost+Found).

Thinking that maybe it was just running fsck in the background or something, I let it go for about a half hour.  When I came back, nothing had happened, so I did a Ctrl+Alt+Delete and rebooted.  This time, I brought up the grub kernel selection.  It only consisted of the one kernel entry, the 1 kernel entry with rescue mode, and 2 memtest entries.  

This is the entry for the main kernel line:

[IMG]http://img693.imageshack.us/img693/9981/img0009bk.jpg[/IMG]

So, I popped in my USB stick with 10.04 install on it and tried to run fsck manually, but being raid partitions, I can't fsck them.  I am new with software RAID setups, and have no idea where to go to from here.  I was searching around online and came across a bunch of info, but I was half afraid of wiping out my data or something.

What can I do from here?

---

### Post by fogNL on 2010-06-12
Ok, so, i'm after trying everything I can think of, so, next question..

Is there some way I can mount my raid drives from a live cd/usb and copy my data off?  I try to mount, but it doesn't recognize the 'raid' filesystem

---

### Post by fogNL on 2010-06-12
Finally figured out how to mount my drive from a live system, and I went in to check out the logs.  I was seeing this during my reboots:

> Jun 12 18:50:25 terra kernel: [    6.010803] vga16fb: mapped to 0xc00a0000
Jun 12 18:50:25 terra kernel: [    6.010808] vga16fb: not registering due to another framebuffer present
Jun 12 18:50:25 terra kernel: [    6.128193] Console: switching to colour frame buffer device 210x65
Jun 12 18:50:25 terra init: smbd main process (609) terminated with status 1
Jun 12 18:50:25 terra init: smbd main process ended, respawning
Jun 12 18:50:26 terra init: smbd main process (649) terminated with status 1
Jun 12 18:50:26 terra init: smbd main process ended, respawning
Jun 12 18:50:26 terra init: smbd main process (654) terminated with status 1
Jun 12 18:50:26 terra init: smbd main process ended, respawning
Jun 12 18:50:26 terra init: smbd main process (659) terminated with status 1
Jun 12 18:50:26 terra init: smbd main process ended, respawning
Jun 12 18:50:26 terra init: smbd main process (664) terminated with status 1
Jun 12 18:50:26 terra init: smbd main process ended, respawning
Jun 12 18:50:26 terra init: smbd main process (669) terminated with status 1
Jun 12 18:50:26 terra init: smbd main process ended, respawning
Jun 12 18:50:26 terra init: smbd main process (674) terminated with status 1
Jun 12 18:50:26 terra init: smbd main process ended, respawning
Jun 12 18:50:26 terra init: smbd main process (679) terminated with status 1
Jun 12 18:50:26 terra init: smbd main process ended, respawning
Jun 12 18:50:26 terra init: smbd main process (684) terminated with status 1
Jun 12 18:50:26 terra init: smbd main process ended, respawning
Jun 12 18:50:26 terra init: smbd main process (689) terminated with status 1
Jun 12 18:50:26 terra init: smbd main process ended, respawning
Jun 12 18:50:26 terra init: smbd main process (694) terminated with status 1
Jun 12 18:50:26 terra init: smbd respawning too fast, stopped
Jun 12 18:50:28 terra init: avahi-daemon main process (639) terminated with status 255
Jun 12 18:50:28 terra init: Disconnected from system bus
Jun 12 18:50:28 terra kernel: Kernel logging (proc) stopped.


So, I started thinking that maybe samba was trying to re-establish a share that was no longer existing.  I checked my fstab, nothing in there.  I don't really need samba at the moment, so i just chroot'd into the file system and un-installed it.

Now, on reboot, i get pretty much the same thing except the last line is:

"init: Failed to spawn smbd main process: unable to execute: No such file or directory"

So, it seems that something else is trying to start samba now.  How can I find out what?  Or just bypass this some how??

---

### Post by bashologist on 2010-06-12
I'm not sure exactly what your problem is but I have a guess. If your startup just stops try pressing the "s" key.

---

### Post by fogNL on 2010-06-12
> **bashologist said:**
> I'm not sure exactly what your problem is but I have a guess. If your startup just stops try pressing the "s" key.

Yeah, the startup just stops there.  Nothing else happens unless i either press Ctrl+Alt+Delete (which reboots the system gracefully), or I can press PgUp/PgDown which toggles between console and the ubuntu splash screen.  No other keys do anything.  I am unable to ping the system from the network.  I've left the system for up to an hour, and no response.  Its not like its locked up, more like its hung waiting for something.

I don't know what's going on.

---

### Post by bashologist on 2010-06-12
So you're saying no other keys work meaning the "s" key doesn't fix the problem. For me my boot stopped and when I press "s" it skips mounting of a drive.

---

### Post by fogNL on 2010-06-12
> **bashologist said:**
> So you're saying no other keys work meaning the "s" key doesn't fix the problem. For me my boot stopped and when I press "s" it skips mounting of a drive.

Nope, the 's' didn't do anything, just hung there.

I'm wondering how i can figure out what is trying to start smbd.  I have a feeling once I track that down, I may find my problem.

---

### Post by fogNL on 2010-06-12
Ok, fixed the problem

Last month I configured my computer with an ipv6 tunnel, and added some static IP's to my /etc/network/interfaces .  For some reason, it wasn't right, and that was causing my boot to freeze.  Removed those static entries from a live cd, and everything works now.

So, it had nothing to do with my upgrade, it was just the first time i rebooted since i added those static entries.

Thanks for the help

---

