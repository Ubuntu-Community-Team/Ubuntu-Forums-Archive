---
title: "100% CPU usage"
date: 2009-11-01
forum: Ubuntu Moblin Remix
---

### Post by phyzik on 2009-11-01
Hi everyone!

I have been keeping an eye on Moblin project for a long time so when I saw it built on top of Ubuntu, I had to try it out. So I downloaded the .iso file and made a USB Startup disk.

Unfortunately, that's when the problems started. I tried the Live session first inside Virtualbox and after that a real Live session.

Even though have a decent laptop, with 2GB of RAM and a Core 2 Duo 2.0 GHz processor, Live session was painfully slow, with processor usage always above 60%.
At first I thought it was because Moblin only supports netbooks, but isn't UMR essentially Karmic with a special interface?

So, any ideas on what the problem might be?

Also, I had no success finding a "shut down" button. Where is it? How do you turn off computer running Moblin?

---

### Post by Glucklich on 2009-11-02
The CPU problem is easy to solve. I gave this answer to someone else earlier and it seems to fixed their problem. Run:

> sudo dpkg-reconfigure -phigh xserver-xorg

Restart and should be fine.

And yes, it isn't optimized for netbooks yet. There were some bugs on the LPIA so they kept it i386 (as you can see on the download description). So, it's basically what you said... regular Ubuntu with a visual interface makeup.

Regarding your "log out button" problem... Did you made a clean install? I've only seen that problem when people updated their systems from 9.04 to 9.10.

Edit: Here's the thread I was talking about.

[http://ubuntuforums.org/showthread.php?t=1309738]("http://ubuntuforums.org/showthread.php?t=1309738")

---

### Post by phyzik on 2009-11-04
Thanks for the reply, but that doesn't really solve my problem.

The issue was during Live session (Ubuntu Moblin Remix wasn't installed on a hard drive, but booted from flash drive to RAM), so I don't see how I can reconfigure X.org since it's not installed at all, and you cannot edit files on installation media.

I mean, your suggestion might be helpful if I do install Moblin, but I wanted to be sure that it would work prior to installing it...

---

