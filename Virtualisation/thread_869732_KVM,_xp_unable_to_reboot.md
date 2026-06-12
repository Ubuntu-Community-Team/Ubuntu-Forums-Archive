---
title: "KVM, xp unable to reboot"
date: 2008-07-25
forum: Virtualisation
---

### Post by hinn on 2008-07-25
Hi
Started to use KVM for my virtualization needs, which happens to be a few Xp machines doing some automated tasks.

I'm running KVM both on Ubuntu server and Ubuntu desktop (both hardy, 8.04).

One problem I have is that the Xp machines running on the desktop can't reboot (they tries, but the domain/machine is shutoff without ever starting up again), while the machines on the server can't do it.

All machines are clones and don't really differ in their settings, and they are also started the same on the server and desktop (follow the same instructions when installing kvm).

So.. I have looked around as far as my, rather poor, linux knowledge allow me, and no searches has yet been successful.

So, anyone have had the same problem, or know where I could look into it further? Tried to find some settings somewhere which would differ but havn't find anything 

Thanks in advance

---

### Post by igwk on 2008-07-26
I have the same problem and I've never been able to figure it out.  It might have something to do with running WinXP with the -noacpi option, but I haven't tried it without that option.

I should also mention that I'm running kvm-71 that I've compiled from source code rather than installing the ubuntu packaged version.  I wasn't able to get restarting to work with the older versions either.

---

