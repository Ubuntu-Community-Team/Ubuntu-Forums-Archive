---
title: "LTSP i386 Client Error: exported device is too big for me"
date: 2014-04-23
forum: Server Platforms
---

### Post by charlieott on 2014-04-23
Running 12.04.4 LTSP Server.  Installed with the alternatives CD with F4 Modes "LTSP Server".

Initially an amd64 client was created and this works fine.

However, we have i686 Diskless workstations that we would like to use.  So I did this:

$ ltsp-build-client --arch i386

This finished successfully, so I added a host to the dhcpd.conf by MAC address, and specified that the image should be the i386 squashfs, rather than the original amd64.

When the client boots, the image is found and the pxelinux boot begins.

The error is:

"[COLOR=#555555][FONT=monospace]Negotiation: ..size= 54214229768MBError: Exported device is too big for
[/FONT][/COLOR][COLOR=#555555][FONT=monospace]me. Get 64-bit machine :-([/FONT][/COLOR][COLOR=#000000][FONT=Verdana]"

I assume this line in the i386 image's /boot/pxelinux.cfg/default is causing the error:
append ro initrd=initrd.img root=/dev/nbd0 init=/sbin/init-ltsp quiet splash plymouth:force-splash vt.handoff=7 nbdroot=:ltsp_i386

Not only is the size reported completely wrong, but the other issue is that the 'size' integer is a lot different every time I reboot the thin client.

This thread indicates there could be an issue with the nbd-client command: [http://sourceforge.net/p/nbd/mailman/nbd-general/thread/20120320085827.GW753@grep.be/](http://sourceforge.net/p/nbd/mailman/nbd-general/thread/20120320085827.GW753@grep.be/)[/FONT][/COLOR]

[[COLOR=#555555][FONT=monospace]the problem was fixed. After all it was a problem in Dracut with the[/FONT][/COLOR]nbd-client command which resulted in this error.
The line used was: nbd-client 192.168.0.1 '-N ltsp' /dev/nbd0 [COLOR=#555555][FONT=monospace]and removing the quotes fixed it.[/FONT][/COLOR]]

I'm really stuck on this one and have about 50 of these i386 thin clients to setup.   Any help would be greatly appreciated.

---

### Post by charlieott on 2014-04-24
I noticed that 14.04 uses package nbd-client 3.7, while 12.04 uses 2.9

Perhaps I need to start over and use 14.04... Of course, that could introduce different issues.

---

### Post by charlieott on 2014-04-24
Well, after digging deep.  It looks like I am running "long-outdated conditional code"

[https://github.com/yoe/nbd/commit/7719899c8ebd66ffa1864bb39152f5c919cca28c#diff-4d6a9b7f07e586a3384d41d35b330689](https://github.com/yoe/nbd/commit/7719899c8ebd66ffa1864bb39152f5c919cca28c#diff-4d6a9b7f07e586a3384d41d35b330689)

The conditions have been removed as of nbd-3.3  and the newer conditions look a bit different.  Guess I'll try the newest distro.

---

### Post by charlieott on 2014-04-24
SOLVED!!!

So I updated the nbd-server package to 3.7-1, then using chroot, updated the nbd-client package to 3.7-1.  Then rebuild the image (ltsp-update-image).

Rebooted the i386 Thin client... and BAM! worked like a charm.

Just have to remember to go ahead and update the nbd client inside the amd64 image too.

---

