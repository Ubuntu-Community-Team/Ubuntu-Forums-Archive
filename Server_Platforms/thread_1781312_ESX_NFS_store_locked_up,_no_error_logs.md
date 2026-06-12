---
title: "ESX NFS store locked up, no error logs"
date: 2011-06-13
forum: Server Platforms
---

### Post by VMOS on 2011-06-13
Good morning, bit of a shot in the dark here. We've got two identical dall r710s, both running identical installs of ubuntu 10.04.
They've both been running continuously for almost a year and both of them have locked up, become completely unresponsive and required a hard reboot.
After reboot, everything was fine.
In both cases, the screen was blank with no errors and all the logs on the server stop dead at the point of failure with no errors.
We've tentatively ruled out hardware faults as the drac is monitoring that independantly of the OS and didn't show anything.

Not a lot to go on, but that's what I've got. Has anyone experienced or heard of anything similar?

Pretty much the only thing on the server is NFS, so that's what I'm concentrating on at the moment, here's the versions.

nfs-kernel-server Version: 1:1.2.0-4ubuntu4

linux-headers-server Version: 2.6.32.21.22

---

### Post by rubylaser on 2011-06-14
Do you have automatic security updates turned on?  Any recent updates, etc? If so, did you try to boot an older kernel?  I seriously doubt NFS is causing this lockup.  To test, you could boot from the LiveCD, and remove your NFS shares from /etc/exports, or even go as far as removing nfs-kernel-server from the upstart scripts.  That would rule out NFS as a potential culprit.

---

### Post by VMOS on 2011-06-15
no there's no automatic updates. The reason I'm blaming NFS is because that's pretty much all there is on this server, no apache, mysql, ftp, mail, it's just a big fat store.

I don't think I'll be able to reproduce this issue in a hurry as it's only happened once in nearly a year of operation. If these servers weren't so critical, I'd be tempted to dismiss it.

I'm thinking something has been counting up for a year and it's reached some critical number, causing an overflow and making it fall over. That might explain why it happened on two servers almost at the same time.
Does that even sound plausible?

---

