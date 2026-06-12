---
title: "Vbox liveCD boot failed"
date: 2012-04-27
forum: Virtualisation
---

### Post by mastablasta on 2012-04-27
I can not boot into live CD.

It gives me this strange message:
[http://ubuntuone.com/45l7rFZIwrFuJi4gKbKgZ0](http://ubuntuone.com/45l7rFZIwrFuJi4gKbKgZ0)

Why would it need pae kernel? system has 512MB allocated and the iso is i386 (so 32bit). iso was downloaded via torrent.

---

### Post by penn07 on 2012-04-27
> **mastablasta said:**
> I can not boot into live CD.

It gives me this strange message:
[http://ubuntuone.com/45l7rFZIwrFuJi4gKbKgZ0](http://ubuntuone.com/45l7rFZIwrFuJi4gKbKgZ0)

Why would it need pae kernel? system has 512MB allocated and the iso is i386 (so 32bit). iso was downloaded via torrent.

I got the same problem with  Pentium M t42 thinkpad.  could not install from CD but  upgraded from 11.10 with no problems ?

---

### Post by mastablasta on 2012-04-27
well i have Xubuntu in vbox, but just wanted to give Ubuntu a spin to see what they did with unity.

---

### Post by Cheesemill on 2012-04-28
The i386 kernel has PAE enabled by default nowadays.

If you want a non-PAE kernel then you can use the appropriate Mini CD to install with.
[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/mini.iso](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/mini.iso)

---

### Post by mastablasta on 2012-04-28
so why would that matter if i have PAE enabled or not? it is not supported by vbox?

I just downloaded 64bit version will try with that one to see what happens. Unfortunatelly i am notsure if i can try it out today...

---

### Post by Cheesemill on 2012-04-28
To run the PAE kernel your CPU has to support it and it needs enabling in your VM settings.

---

### Post by mastablasta on 2012-04-28
i just found it and wanted to post here the "solution". Because i tried 64bit and it rejected it (maybe the virtual cpu is 32bit?!).

---

### Post by CharlesA on 2012-04-29
Was the VM set for "Ubuntu" or "Ubuntu (64-bit)"?

---

