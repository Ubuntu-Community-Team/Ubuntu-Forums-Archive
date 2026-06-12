---
title: "For those who are down on using the terminal..."
date: 2007-05-23
forum: Testimonials &amp; Experiences
---

### Post by rillip on 2007-05-23
I just had an unusual experience involving the terminal that I thought I would share, as it goes contrary to what most people say about it.

Ubuntu, overall, does a pretty good job of eliminating the terminal from your every day life, unless you want to use it. There are gui interfaces for almost everything, and they work really well, most of the time.   The main reasons for this are a) it's usually easier to point, click, choose rather than research the command, look up the manual, find the options you want, etc. Unless you're very familiar with the command, a GUI provides easier access.

Many people who give detracting stories about Linux in general cite frustrating sessions fumbling around in the terminal trying to add a repoistory or modify some configuration file, etc.

Here's my story:

I decided since I wasn't using my Windows partitions very much to resize and give myself some more room in Linux. Long story short, after some trials with unlocking varios partitions, having to delete, recreate, etc. I got it partitioned the way I wanted.  When I booted back up, I had no problems, but I couldn't access my other partitions, just the one root is installed on.  I went to the GUI for disk control in Kubuntu.  In the partitioning the device numbers (i,e, /dev/sda1, /dev/sda2) had switched around and my mountss were pointing to the wrong things.  I was able to fix all but the largest one, the one I had nearly doubled.

For some reason, every time I tried to mount, it just would not do it.  It'd give me errors about /mnt/storage is already in use or could not find the specified file system on /dev/sda2, but I had unmounted it and was no longer trying to use sda2 at all.  In fact, sda2 was mounted without issue and usable!

I fought with the stupid thing for over half an hour before I just gave up and decided to try it manually.  I was able to mount the drive in ten seconds from the terminal, no problem.  I went back to the GUI, saw it was still showing the wrong info.  I saw /etc/fstab mentioned in one of the error messages I got.

So, I did this from the terminal:

sudo nano /etc/fstab

It shows me a line for /mnt/storage pointing to sda2 right above the working mount for sda2.  I delete that line, and then in less than twenty keystrokes (ctrl+k ,ctrl+u, change "shared" to "storage" and 2 to 1, then ctrl+o, enter, ctrl+x) had it fixed.

I never looked up the manual, I never had to google, I just spent two minutes and edited my /etc/fstab, and it worked. Two minutes manual vs 45+ with GUI, assuming I ever got it working.

This is just something to consider the next time you hear someone complain about confusing commands, the difficulty of the terminal, etc.  Sometimes, it's really easier!  It's just different.

---

### Post by freebeer on 2007-05-23
Yup.  Good example!

I still don't understand people's fear or consternation of the command line.  One of the things I hated about migrating to the Windows world (from DOS) was the lack of control.  Some things were just better and faster in the command line.  Subsequent versions of Windows kept pushing the user away from the control a command line gave him/her.

When I decided to try Linux one of the strong motivating factors was that I'd now have a powerful command line interface that gave me back control of my machine.  It's so much more empowering! :D

---

