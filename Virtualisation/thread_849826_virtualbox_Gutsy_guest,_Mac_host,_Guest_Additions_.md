---
title: "virtualbox Gutsy guest, Mac host, Guest Additions don't work"
date: 2008-07-04
forum: Virtualisation
---

### Post by Goliath! on 2008-07-04
I have VirtualBox 1.6 installed on Mac 10.4.  I created an Ubuntu Gutsy guest.  I installed the VirtualBox Guest Additions.  Everything seemed to go fine - no errors, no warnings.  The VM runs fine.

BUT the guest additions don't work.  No mouse integration and shared folders don't work, no seamless mode.

When I try to mount a shared folder I get:

/sbin/mount.vboxsf: mounting failed with the error: No such device

When the VM is running, the options for Seamless Mode and Disable Mouse Integration are disabled.

My xorg.conf (in Gutsy guest) says it's using the vboxmouse driver.


I have Googled, searched this forum, and posted on VirtualBox forum.

Any ideas/help/comments/clues/questions/insults?  Please?

---

### Post by Goliath! on 2008-07-04
Just to be specific, it's VirtualBox 1.6.2.

I'm using Gutsy because I tried Hardy and it was a mess.  Mouse was funny, couldn't get Guest Additions to install, and it just kept freezing on me.

Also tried Parallels and Fusion with Hardy and got stopped because they don't officially support their guest additions on Hardy yet.

---

### Post by Goliath! on 2008-07-05
I'm marking this as resolved, although I don't know exactly what changed to make things work.

Given that Gutsy wasn't working much better than Hardy, I started over from scratch.

I created a new VM using 8.04 and installed the Guest Additions.  And everything worked fine.

No explanation.  It didn't work before, it works now.  Whatever.

All I can say is that if you have a similar problem, just keep working at it.  You'll get it eventually.  It really does work!  Try a re-install.  Linux is a finicky beast; speak softly and nicely to it, and keep trying, and you'll get it.

---

