---
title: "Booting Ubuntu LTSP via external TFTP server"
date: 2012-07-02
forum: Server Platforms
---

### Post by Karl1982 on 2012-07-02
I'm working on an issue with Ubuntu 12.04 LTSP.  I want to boot it from an external TFTP server.  I've copied the LTSP folder to another TFTP server, but it doesn't boot properly (just a blinking cursor).  It boots fine if I use the TFTP server running on the LTSP server

What has to be modified in order for TFTP and LTSP to reside on separate servers?

I'm also having an unrelated LTSP boot issue on another forum... if anyone has any input on that, it would be greatly appreciated.  [http://reboot.pro/17146/](http://reboot.pro/17146/)

---

### Post by Cheesemill on 2012-07-03
Have you changed the settings in your DHCP server to point the clients to the new TFTP location?

---

### Post by Karl1982 on 2012-07-03
[FONT=Lucida Console]Yes, the DHCP options are correct.

Sorry, I seem to have gotten my symptoms mixed up with another issue I'm working on.  Let me take a step back.  I have a working LTSP server with its own automatically-installed TFTP server.  When I boot a client to it, everything works as intended. [/FONT][FONT=Lucida Console]

When I take the contents of /var/lib/tftpboot and transfer it from the testing Precise LTSP server to a production Lucid server,  it fails to boot correctly.  It drops me at (initramfs).  I'm thinking maybe a kernel argument needs to be changed for this to work because it seems to assume on some level that the TFTP server is also hosting LTSP.

The reason for this is we already have a working PXE boot environment that hosts other things such as diagnostics and PEs, so I want the production server currently hosting the PXE TFTP service to keep it, but this server provides other services as well and wouldn't be appropriate for hosting LTSP.

Here's what it says: [/FONT][FONT=Lucida Console]

[/FONT]  ```
ip: RTNETLINK answers: File exists
Error: Socket failed: Connection refused
Exiting.
mount: mounting /dev/nbd0 on /root failed: Input/output error
/scripts/init-bottom/ltsp: line 27: panic: not found
chroot: can't execute '/usr/bin/test': No such file or directory
mount: mounting /root on /rofs failed: Invalid argument
mount: mounting /rofs on /root/rofs failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init-ltsp.
No init found. Try passing init= bootarg.
```

---

### Post by Karl1982 on 2012-07-03
Problem solved!  I was right, by default it makes the assumption that the TFTP server is also the LTSP server.

Here are the default boot arguments for LTSP stored in /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default:

```
default ltsp


label ltsp
kernel vmlinuz
append ro initrd=initrd.img root=/dev/nbd0 init=/sbin/init-ltsp quiet splash plymouth:force-splash vt.handoff=7 nbdroot=:ltsp_i386 

```If you look at the nbdroot argument, the space between the = and : is suspiciously blank.  I took a shot in the dark and threw the actual IP address of the LTSP server in there, and it booted right up.  I guess it assumes the TFTP server's IP if not specified, which was no longer correct once the TFTP boot files were relocated.

---

