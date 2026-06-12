---
title: "Kernel 2.6.15 + new udev"
date: 2006-01-14
forum: Requests
---

### Post by rohandhruva on 2006-01-14
Hi,

Kernel 2.6.15 and the new udev obsoletes hotplug, so that our system boot ups will be much much faster. Please see if it is possible, but i hope its not too "intrusive" by your standards. :( It will be a real help, on my piii 550mhz :)

Thanks,
Rohan.

---

### Post by hav0x on 2006-01-14
Please read [The Backports Team Policy]("http://ubuntubackports.org/wiki/index.php/Requesting_A_Backport") BEFORE filing requests!

---

### Post by ashrack on 2006-01-14
[QUOTE=rohandhruva]Hi,

Kernel 2.6.15 and the new udev obsoletes hotplug, so that our system boot ups will be much much faster. Please see if it is possible, but i hope its not too "intrusive" by your standards. :( It will be a real help, on my piii 550mhz :)

Thanks,
Rohan.[/QUOTE]
What is this 'udev obsoletes hotplug'?

---

### Post by mr_pouit on 2006-01-14
[QUOTE=ashrack]What is this 'udev obsoletes hotplug'?[/QUOTE]
from the udev package in dapper :
> Package: udev
Version: 079-0ubuntu3
Section: admin
Priority: important
Architecture: i386
Depends: libc6 (>= 2.3.4-1), libselinux1 (>= 1.28), libsepol1 (>= 1.10), module-init-tools (>= 3.2.1-0ubuntu3), initramfs-tools (>= 0.040ubuntu1), grepmap (>= 1.1.0-1)
[b]Conflicts: hotplug
Replaces: hotplug[/b], initramfs-tools (<< 0.040ubuntu1)
Installed-Size: 732
Maintainer: Scott James Remnant <scott@ubuntu.com>
Description: rule-based device node and kernel event manager
 udev is a collection of tools and a daemon to manage events received from
 the kernel and deal with them in user-space.  Primarily this involves
 creating and removing device nodes in /dev when hardware is discovered or
 removed from the system.
 .
 Events are received via kernel netlink messaged and processed according to
 rules in /etc/udev/rules.d, altering the name of the device node, creating
 additional symlinks or calling other tools and programs including those to
 load kernel modules and initialise the device.

---

### Post by rohandhruva on 2006-01-15
Hello,

Hav0x :
1) The 2.6.15 kernel is in ubuntu dapper.
2) It builds cleanly, of course.
3) Kernel wont introduce any new libraries, so thats not a problem.
4) Same goes for perl/python/gcc.
5) Kernel 2.6.15 is surely meaningful -- because it indirectly helps in faster bootups.

Now, where is the problem ? Even for warty, kernels with the new grepmap were provided, though the backports were not "official" back then. 

ashrack:
Kernel 2.6.15 depends on the new version of udev, which does the all the work that was earlier managed by hotplug, thus removing the need of hotplug, which used to delay boot ups.

Regards, 
Rohan.

---

### Post by hav0x on 2006-01-15
[-X
They wont backport kernels, is all i'm saying ...

---

### Post by macleod199 on 2006-01-15
[QUOTE=rohandhruva]
3) Kernel wont introduce any new libraries, so thats not a problem.
[/QUOTE]

You have this backwards. It's all the other system packages that rely on specific API/ABI/functionality of the .12 release that would need to be updated ot the new interfaces. Sadly the 'stable' 2.6 kernel release series has devolved into a constantly shifting target.

---

### Post by globe_trotter on 2006-01-17
And what about udev?
I'm on breezy ppc, on 2.6.15 + udev 0.060 i lost some nodes (/dev/input/event* for example, needed by pbbuttonsd).. So, what about backporting at least udev? What's the matter with it?

Thanks globe.



EDIT: Tried dpkg -i --simulate with dapperdeb, and it conflicted with hotplug (it will not be more needed, but it is a dep for other packages (kernel,hal) and so it wouldn't just be simple upgrade..

---

### Post by rohandhruva on 2006-01-17
Well.. sad... The dapper livecd i tried booted up really faster than breezy. But yes, i do get your point, havox, macloed, and globe_trotter. :(

Rohan.

---

### Post by brainkilla on 2006-01-17
Well, perhaps you could try Dapper Flight 3, as some of my friends told me F2 was pretty usable...

---

