---
title: "Updated Xen distro... now VPS wont boot"
date: 2010-08-29
forum: Virtualisation
---

### Post by l0xin on 2010-08-29
I was running Ubuntu 9.04 on my Xen VPS and did a "do-release-upgrade" to upgrade to 10.04. Everything seemed to go ok until it was time to reboot. After rebooting, my VPS now doesn't boot properly.

Logging into the Xen console gives me

> 
init: ureadahead main process (542) terminated with status 5
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (543) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue): 
Entering the VPS root password logs me into it, but with the file-system as read only (the first line of dmesg is "Bootdata ok (command line is  root=/dev/sda1 ro)")

Am I stuffed, and going to have to send an e-mail off to technical support, or is there anything I can do to sort it myself?

---

### Post by l0xin on 2010-08-29
Turns out the problem is that Xen guests use the kernel of the host, which in my case is 2.6.18, and 9.10+ requires kernel 2.6.31 or later.

---

### Post by TheFu on 2010-08-30
Xen dom0 kernel support was dropped from Ubuntu. You'll need to migrate to a different hypervisor like KVM, virtualbox, ESX/ESXi, etc.... If you used paravirtual guests - and it sounds like you do - then you may want to convert them to HVM boot too.

Or you could search for how to built a Xen kernel yourself and install that as Dom0. You'll need to take over all kernel updates yourself.  I believe that I read some people were using the Xen kernel from Debian releases successfully. I do not know if that is true.

I understand that DonU Xen machines are supported by KVM (at least on 10.04 KVM), but don't have any experience with them. I need to research that myself.

I elected to stay on 8.04 LTS running Xen until I had tested a good migration to some other VM technology. That release will be supported for a while longer, so I'm hopeful that KVM will mature a little more.

---

