---
title: "PXEBoot / Want reboot not busybox"
date: 2011-10-21
forum: Server Platforms
---

### Post by Jonathan L on 2011-10-21
Hi All

Any kind soul know the solution to a booting problem?

I have a number of PXE-booted clients.  Everything works perfectly: DHCP, TFTP, NFS.  But what I want is that if there's a failure in the booting, we don't end up in busybox, we retry the boot.  This means that if the NFS server is down, just at the second a client reboots, we get stuck in the busybox as there's no reoot file system to boot from.

The error message on the client is
```
...
[   1.836829] hub 2-1:1.0: 6 ports detected

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Done.
Unable to find a live file system on the network
```My PXE config contains:
```
DEFAULT vesamenu.c32
MENU TITLE Network boot
menu tabmsg Select system and press ENTER
timeout 100
LABEL ubuntu-10.04.3-desktop-i386
  MENU LABEL ubuntu-10.04.3-desktop-i386
  KERNEL ubuntu-10.04.3-desktop-i386/vmlinuz
  APPEND initrd=ubuntu-10.04.3-desktop-i386/initrd.gz root=/dev/nfs boot=casper netboot=nfs nfsroot=boss:/exports/ubuntu-10.04.3-desktop-i386 splash --
```I'm sure there's a magic word on the APPEND line that needs adding, but haven't found it yet.

Many thanks in advance.

Jonathan.

---

### Post by Jonathan L on 2011-10-24
Basically solved.

Appears to be quite generic: can add panic=5 (or whatever time you like) to stop going into busybox shell.  This is the working fragment of pxelinux.cfg/default:
```
LABEL ubuntu-10.04.3-desktop-i386
  MENU LABEL ubuntu-10.04.3-desktop-i386
  KERNEL ubuntu-10.04.3-desktop-i386/vmlinuz
  APPEND initrd=ubuntu-10.04.3-desktop-i386/initrd.gz root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.1.32:/exports/ubuntu-10.04.3-desktop-i386  [COLOR=Red]panic=5[/COLOR] --
```Results for for PXE booting with casper:

[LIST]
[*] If server system is up (ie, pingable) but NFS software doesn't deliver these files or NFS server process isn't running, works perfectly: get timeout in approx 20s and then reboot
[*] If server spec is unparsable (ie nfsroot=hostname:/blah) works perfectly
[*] If server is not reachable (ie, off and unpingable, or wrong IP address) then works correctly but the timeout of the nfsmount is extremely long (6m30s * 60 ie 6 hours) ... looking into a way to make this quicker (appears to be a mod to /scripts/casper) but appears that it would work fine if the NFS server came up.  Given that most of the time the PXE server is also the NFS server, this is a minor concern.  (If the PXE server is down, the PXE bios will retry, or not, per BIOS config.)
[/LIST]
  
Notes for any further work:

Details per ubuntu-10.04.2-desktop-i386 Live CD, which uses casper.

The initrd.lz of the LiveCD () contains the boot script /init, which sets panic= and then sources
```
/conf/initramfs.conf
/conf/conf.d/*
/scripts/functions

Line 619 of /scripts/casper is the message we see.

```The panic() function defined there checks $panic and either reboots or calls sh.
```
if [ -n "${panic}" ]; then
        sleep ${panic}
        reboot
fi
...
/bin/sh ...
```Appears we can stick "panic=5" in any conf file, or panic=5 on command line (init line 157). (casper triggered by boot=casper, init line 145, 229)

Can't see how to set NFSOPTS or set proto=udp anywhere.  /scripts/nfs has a different mechanism.

---

