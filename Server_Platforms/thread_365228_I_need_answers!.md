---
title: "I need answers!"
date: 2007-02-19
forum: Server Platforms
---

### Post by namelessone on 2007-02-19
I keep on posting questions about ltsp but I'm not getting answers... so... here's another question.

I chroot into /opt/ltsp/i386. Here I edited the sources.list file, but when I typed apt-get update, it can't connect to the server at server.ubuntu.com.

It says > Temporary failure resolving security.ubuntu.com

Can someone help? Please?

---

### Post by kidders on 2007-02-19
Hi there,

Could you describe how you did the chroot?

---

### Post by namelessone on 2007-02-19
I typed the following in the terminal: > sudo chroot /opt/ltsp/i386

---

### Post by kidders on 2007-02-19
Hi there,

This may seem like a strange thing to say, but I sincerely hope that makes it impossible for you to do almost everything with your box. After all, the point in a chroot-ed environment is to protect your system from interference/damage. For instance, /etc/resolv.conf will be inaccessible (which is the cause of your particular problem). Also, /dev, /proc & /sys will be unavailable, making it quite tricky for any application running from within the chroot jail to interface with your kernel & hardware.

I'm not familiar with LTSP really, but I do know that you'll tend to have to do quite a bit of work to create a fully functional chroot-ed Linux environment, since they're generally designed to *not* to be fully functional.

My first suggestion would be to check the chroot jail's /etc/resolv.conf to make sure it's sensible ... but once that's out of the way, you might run into further problems.

Is that any help?

---

### Post by namelessone on 2007-02-20
I think I understand. It sounds like it's gonna be more work than it's worth. I'm just gonna log in with a thin client and use apt-get from there. I think that should work.

---

### Post by kidders on 2007-02-20
Yep. I suppose if I were more familiar with LTSP, I might be able to offer you some alternatives to doing so ... but that sounds perfectly fine.

If, at some point, you wanted to try the chroot again, here is a rough impression of the kind of thing you'd have to do. (Whether it's more or less work than this kinda depends on what you intend to do in the chroot jail, when you get into it.)

[LIST=1]
[*]Copy /etc/resolv.conf into the jail.
[*]Copy /etc/nsswitch.conf in as well, if you're doing fancy things with authentication.
[*]Rebind /dev to /path/to/jail/dev.
[*]Mount procfs & sysfs filesystems into the jail.
[*]Do the chroot.
[*]Update your working environment (this is often critical) with something like "source /etc/profile"
[/LIST]

If you stumble across an LTSP howto at some stage that looks like it's asking you to do something along these lines, you'll probably have more success modifying/upgrading its environment centrally.

I hope that helps.

---

