---
title: "Qemu/kvm Ubuntu 12.04 guest dies randomly"
date: 2012-07-06
forum: Server Platforms
---

### Post by toshko3 on 2012-07-06
Hi,
I have Ubuntu server 12.04 64bit as host and Ubuntu server 12.04 64bit as guest.
The thing is that the guest randomly dies and it is soooo frustrating. There is PDC on the guest and people cannot work. It happens almost every day.
There are no logs in the syslogs of host and guest in the time of crash.
The only mentioning of the dying is in this log /var/log/libvirt/qemu/ubuntu-pdc.log:

2012-07-05 14:38:30.798+0000: shutting down

When I manually shut down the guest at least there is a line before the "shutting down" like this:

qemu: terminating on signal 15 from pid 1160
2012-07-05 14:39:01.150+0000: shutting down


I saw that there are also these errors in /var/log/libvirt/libvirtd.log:

1160: error : qemuMonitorIO:603 : internal error End of file from monitor

but they are appearing when I shutdown the guest manually, too.

Please, guide me how could I diagnose this case! :confused:

---

### Post by toshko3 on 2012-07-09
Anyone knows how could I diagnose this?

---

### Post by toshko3 on 2012-07-10
OK, now with the latest dying, I had leaved a console in the guest turned on with htop. So, when the machine died, there was a message - "Power button pressed.", which leads me to acpid. There was no power button pressed and no script is turning the machine off. No crons either. :confused:
Anybody knows of a bug in acpid or any configurations?

---

### Post by toshko3 on 2012-07-10
Well, now it did it again, with acpid stopped. It just didn't print the message. It just dies...
Please, help!!!

---

### Post by galets on 2012-09-04
I'm seeing same issue on win2008 guest

---

### Post by toshko3 on 2012-09-14
I hope that can be helpful - the problem was because there was no space left for one of the images I used for that VM. It was qcow2 image and was not preallocated, so it increased rapidly. I had calculated the space I will need and provided it, but with the addition of internal snapshots of the image it became more than expected.

[https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/1022901](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/1022901)

---

