---
title: "Once stable server now hangs several times a day - need help"
date: 2015-06-10
forum: Server Platforms
---

### Post by Seawhy on 2015-06-10
We have a production Ubunu Server that hosts our company's website and email, and we're running 12.04 LTS. The server is fully patched, as far as 12.04 goes. This once rock-solid server that only ever needed a reboot when we applied a new kernel every few months is now hanging multiple times a day, and it's driving us crazy. We've spent hours troubleshooting this and we're stuck. We need help and advice from the experts here. 

The server is in a co-location facility about an hour drive from our offices. Physically, the server has 24 GB of RAM, Xeon CPUs, redundant power supplies, and has an Intel RS2BL080 (LSI Megaraid) card with 8 WD SATA drives running RAID 6.

Some of the hard disks in our array have been running for the 5 years since this server was first deployed, and a few were starting to develop errors. We've replaced a few of them--one at a time obviously--and the array is currently "optimal" with no media errors showing on any of the drives.

Thinking we must have some problems on our filesystem, we've forced filesystem checks and rebooted the system. Unfortunately, the results of the fsck don't seem to get logged anywhere--why is that??? In any case, the check doesn't seem to help.

A couple of days ago we had a tech go to the data centre and boot the rescue kernel option from grub and run a filesystem check on all filesystems from the menu. That didn't help (the server hung a few hours later), so we had him go back and boot from Ubuntu Desktop 12 disc and go through the process of activating the lvgroup and then running an "e2fsck -yf" which ran through, apparently fixed some errors and then finished. Server still hangs frequently.

If we do a dry run read-only fsck on our filesystem while it's running, with "fsck -nf " then the system shows a number of errors that for some reason weren't fixed during the offline checks.

We've asked the data centre staff to take a picture of the screen after a hang, and the server says "kernel panic" on the monitor. With that in mind, we set the system to automatically reboot if the kernel panics.

Still, sometimes the server just hangs. I happened to be ssh'd into it recently when it hung, and the file system had been remounted as read only.

We're tired because we get middle of the night alerts, and are at a loss as to what to do next. Help!

UPDATE: 20150612 - Well, we made it through the night. No hangs. Nothing unusual in /var/log/kern.log. I think the newer kernel driver combined with the old raid controller firmware was a huge part of the problem, if not the entire problem. Upgrading the firmware was difficult because we had to do it from a bootable usb drive and the updater program wouldn't run, crashing with an 'out of memory error' which is a problem with using FreeDos apparently; had to find a bootable XP disk image and configure the config.sys which I used to be great at, but that was 1999. Finally, upgrading the firmware had to go up incrementally--we couldn't go from 12.07 to 12.14 in one jump, it actually took four. As I write this, uptime is over 15 hours which is great because we were hanging about every 3 to 5 hours. We're optimistic. Thanks to everyone for your help.

UPDATE: 20150613 - Uptime is becoming a more familiar thing again. As I sit here with my first cup of coffee of the day, uptime is now 1 day 15:30 hours. Considering that earlier this week we weren't seeing 5 hours, I am cautiously optimistic that this issue has been resolved. Time will tell, of course. And lesson learned, raid controller firmware updates will become a part of our regular checklist, at least quarterly.

---

### Post by cariboo on 2015-06-10
Have you tried running with a previous kernel, if that works, you may want to file a bug against the current kernel.

---

### Post by Seawhy on 2015-06-10
Since we've updated everything, would we have any incompatibilities with software that's looking for the current kernel?

I've never tried installing a previous kernel and am not even sure of the procedure to do that. Is there a link somewhere that would give step-by-step?

---

### Post by ajgreeny on 2015-06-10
Let's see how many and which kernels you have on the server before we suggest something.

Show us the output of ```
ls /boot | grep vmlinuz 
```which will list them; all of these will be available from the grub menu so you can boot to old kernels without difficult if the latest gives problems and you will not have to install an older kernel to do so, they will be there, waiting for you.

---

### Post by Seawhy on 2015-06-10
We're now running 3.2.0-83, so hopefully this helps. Thanks for the suggestion.

---

### Post by Seawhy on 2015-06-10
ls /boot | grep vmlinuz

vmlinuz-3.2.0-77-generic
vmlinuz-3.2.0-79-generic
vmlinuz-3.2.0-80-generic
vmlinuz-3.2.0-83-generic
vmlinuz-3.2.0-84-generic

---

### Post by Seawhy on 2015-06-10
> **ajgreeny said:**
> ...all of these will be available from the grub menu so you can boot to old kernels without difficult if the latest gives problems and you will not have to install an older kernel to do so, they will be there, waiting for you.

Since physical access is often very tricky for us, is there a way of telling grub to boot a previous kernel remotely?

---

### Post by cariboo on 2015-06-10
I had a look at [this]("http://statusq.org/archives/2012/10/24/4584/") page, it tells you how to boot from a previous kerenel. I haven't tried it, but from what I see it should work.

---

### Post by Seawhy on 2015-06-11
Server has gone down twice since my last post. So, neither kernel "80" nor "85" made any difference.

Last night, however, I was logged in to the server via putty and was tailing /var/log/kern.log and I think I have some further hints as to what's going on. I've pasted what I believe to be the relevant portion of the capture to [http://pastebin.com/xtB8vpkU](http://pastebin.com/xtB8vpkU)

Here's my theory as to what might be happening. Please tell me if I'm on the right track or maybe completely off-base. I think the more recent kernels perhaps include newer versions of the kernel drivers for our Intel RS2BL080 controller (pastebin controller info: [http://pastebin.com/YhrnZUvb](http://pastebin.com/YhrnZUvb)), but we're still using old (ancient?) firmware on our controller. My guess is that maybe there's some sort of mismatch going on which is causing us grief. My hope is that updating the firmware will be the solution to our grief. What do you think?

Questions:
1. Can we update the controller firmware live? Or do we need to boot from a cd? We have backups, but obviously don't want to have to use them.
2. Are controller firmware updates safe to do?

---

### Post by Seawhy on 2015-06-11
Just an update to anyone following this.

Today we updated the raid controller firmware and we are now completely current with that. Time will tell whether the server becomes more stable after this.

So far /var/log/kern.log doesn't indicate any significant errors from what I can see.

Fingers crossed. Let's hope I get a full night's sleep, I really need it.

---

### Post by tgalati4 on 2015-06-11
It's possible that your motherboard has developed a problem.  Have you cleaned and inspected the server?  Any bulging capacitors?  It's also possible that you have a bad RAM chip.  Try reseating RAM and moving them around in their slots.  Run *memtest* (which can really only be done locally) and let it run for several hours--30 complete passes.  If it locks up, then you definitely have a hardware problem.  If you have RAM errors they will be obvious.  If you have a power supply problem--try removing RAM (say use 8 GB) and possibly declock the server in BIOS.  If it runs well at the slower speed then that may be your solution until you get it replaced.

What is the manufacturer of the server?

---

### Post by Seawhy on 2015-06-12
Right. Good points all around.

The server is in a co-location facility. Mostly dust-free, temperature controlled. Next scheduled maintenance, we'll take the system out and check all of the cables, visually inspect the motherboard, etc.

It's not a brand-name server, but a custom built one. 

This server's eventual replacement will be a quality brand name.

---

### Post by tgalati4 on 2015-06-13
Xeon's tend to run hot and if the motherboard is not well-made, then they can fail after a few years due to delamination and heat-stroke under the chip.

---

### Post by Seawhy on 2015-06-13
Good point. This one is running an ASUS server motherboard. Given that the firmware updates to the raid controller seem to have resolved the problem, at least as far as we can tell, I think the motherboard is probably okay.

---

