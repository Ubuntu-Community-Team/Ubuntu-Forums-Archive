---
title: "DropBear-SSH/BusyBox LUKS unlock broken after Ubuntu upgrade"
date: 2018-10-02
forum: Server Platforms
---

### Post by arwdcs on 2018-10-02
I remotely unlock my Ubuntu 16.04 server after a reboot using a DropBear SSH connection and then I run a script that starts the process of unlocking the LUKS encrypted drives and booting up my server.  It's all worked flawlessly for several months (i.e. since initial setup).

Today, after a routine sudo apt-upgrade OS that required a reboot upon completion, I got my usual shell after reboot, but typing the usual unlock command fails with an error:

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.


#unlock
kill: you need to specify whom to kill
Connection to (web-url.com) closed.


I had to bring a backup server online for now as I don't get back to the office and thus have physical access to the server for over a week, but does anyone have any ideas what might be broken - and how to fix it (remotely or locally)?

Google has been of no use to me on this so far.  Any help appreciated.

---

### Post by slickymaster on 2018-10-02
Thread moved to **Server Platforms** for a better fit

---

### Post by TheFu on 2018-10-02
I would guess, and it is only a guess, that the initrd update failed.  If you boot into the last working kernel, life could be good. Maybe.

This is one of those times when having a RIBLO/IPMI to have console access at boot would really help.  If/when you set that up, lock down the access a few different ways. There are a bunch of security issues with all those remote consoles to the point that they need to be on separate physical networks with network access locked hard to 1-2 specific, trusted, systems.

---

### Post by arwdcs on 2018-10-02
Thank you very much for replying.  I learned something new at least today from your post ([COLOR=#000000]RIBLO/IPMI[/COLOR]) which I will definitely research.  ALSO, I managed to get someone to take a screen shot of the monitor.  It's a little worse than I thought as I had previously ASSUMED that although SSH login was broken, the local terminal would be OK.  It's not the case, but I can at least google some more on the issue.  I attach a screen shot in the hope someone recognises what might be broken.  Hopefully I don't face a total rebuild, but I have not lost data and what doesn't kill me might actually make me stronger eventually! LOL

THANK YOU again for your reply, TheFu

---

### Post by TheFu on 2018-10-02
That screenshot is what I expected.  Just choose an older kernel at boot next time.
BTW, normally adding IPMI or RIBLO isn't possible after the hardware is shipped. Really low-end servers don't often support it, but any "real server" should.  These cards let you have someone put in boot media and walk away.  You can install an OS onto empty hardware.  OTOH, if someone connects to this remote device, they totally own the box. There have been a few highly, highly, embarrassing security failures and I expect there are 100+ more for these devices.

---

### Post by arwdcs on 2018-10-02
I may ultimately have to re-install the whole friggin system, as I did an 'apt auto remove'with my last update which probably zaps the old kernel.  It might be beyond me to install an older Kernel, but I will research it before I get access to the equipment next week.  I will update this thread once I have a conclusion in the feint hope others can learn.  But lord, how are we able to anticipate such a failure?  I performed the same update on an adjacent server and rebooted it as insurance, and it worked fine (but this device didn't). Not sure how we are supposed to protect against that.  Makes me think rebooting after an update that requests a a restart is something I should just not do remotely.

Thanks so much for your replies.  Very much appreciated!

---

### Post by TheFu on 2018-10-02
Installing an older kernel isn't likely to fix the issue.  You'll need to get the initrd corrected and you might as well do that on the current kernel.  Things usually get updated fine. Perhaps once every other year, or if you do a release migration, things seem to get screwed due to encryption.

I keep 3 kernels around just for this reason.

If you use encryption, you must have 100%-know-you-can-restore backups.  No questions. No issues at restore time.  If you don't have that, don't touch encryption.

Whenever I'm going to travel, I don't patch that week or while gone.  Learned that in 2008 the hard way. 

I was overseas for 2-3 weeks (travelled a bunch that year) and had some issue take down an important server.  Back then I took a Nokia N800, not a laptop.  I hadn't moved to 99% virtualization for services back then, so there wasn't anything that I could do. The service was down for a week.  

Ever since then I don't patch when I'm going to be out of town and I don't patch remotely unless I'll be back before the next morning.  As it is, I only patch during pre-approved maintenance periods, early weekend mornings. Only hardware failures seem to cause issues these days that a reboot brings to light.  With almost everything running inside virtual machines, I can rebuild a service from recent backups usually within 30-45 min, if necessary, from anywhere in the world.  The different VM host machines don't need to be rebooted very often, but they run 16.04 or 14.04 still. 

We don't have any 18.04 deployed anywhere and don't have plans for it this year.  Stability is more important than "new" for us.

---

### Post by arwdcs on 2018-10-02
Thanks TheFu.  Thankfully, some of what you say I already do.  My servers were down for about an hour, half of that was me trying to recover them (and failed), but in 30 minutes I brought a backup online and had everything recovered: two web sites, a cloud server and a document server.  Aprt from an hour downtime, no-one would know.  All I lost was some scripting I did this AM which I had not backed up.  Not too bad.

I probably can't defer updating an OS that long as I now have to spend a lot of time overseas (I have been in UK from April to September), but servers have to remain in US for legal reasons.  But at least the back-up plan worked flawlessly.  I have TWO backup servers.  Right now, that seems light! LOL.

I get back to the US next week by rare coincidence, so I can fix this (if I have to do a full re-install),so not so bad.  I agree it was probably my hardware that's at issue.  I may have to buy a better setup for my primary server.

I also don't even look at 18.04 for the same reasons you intimated: I want STABLE more than anything.  Maybe I would even look at debian, which is "allegedly" even more stable but very similar to ubuntu (so I don't have to learn another distro).  At age 58, this **** gets old faster than a good bottle of wine.

So privileged to have had a dialog with you TheFu.  Thanks so much!

---

### Post by arwdcs on 2018-10-13
Well I want to close this thread out.  After I got physical access to the server, I still couldn't fix it.  No console access, no anything.  So I did a re-install of the OS.  I was able to update my bios but I have no idea if it will prevent this from happening again.  I was hoping to fix this and post instructions, but it's not to be this time.  Thanks to those who contributed, and my apologies to anyone else trying to fix a similar problem.  GOOD LUCK!

---

