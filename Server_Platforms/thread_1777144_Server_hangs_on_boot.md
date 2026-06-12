---
title: "Server hangs on boot"
date: 2011-06-07
forum: Server Platforms
---

### Post by janipewter on 2011-06-07
Hi all, my trusty Ubuntu server is giving me some problems...

After a powercut in the middle of the night (UPS battery also ran out before power came back) my server is now hanging on boot.

This is where it gets, and it just hangs indefinitely:

[[IMG]http://i.imgur.com/sP7ic.jpg[/IMG]](http://imgur.com/sP7ic)

---

### Post by linkageless on 2011-06-07
I've not thoroughly examined your screenshot, but I would be booting with a live cd if I had one to hand. Alternatively boot into single user by adding at the end of the kernel options in grub. In fact, by default you should have a 'rescue mode' (or similar) entry in your grub menu.

You might then try checking (fsck -f) each filesystem and take a look at any system logs you can get your hands on to work out how far it's getting.

edit: having taken another look, it seems that nothing is getting properly mounted here. If you still have an older kernel there try that, otherwise a livecd would be useful here. Might there have been an upgrade pending? Looks a little like this situation: [https://answers.launchpad.net/ubuntu/+source/util-linux/+question/131600](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/131600)

Obviously for safety, to get it back to the grub menu reboot it with ctrl-alt-del if you can, rather than killing the power.

---

### Post by janipewter on 2011-06-07
There was an upgrade pending (every time I logged in it said a restart is required).

I'll try booting it with an older kernel later, thanks.

---

