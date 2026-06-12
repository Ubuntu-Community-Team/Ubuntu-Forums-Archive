---
title: "LTSP Remotely (Ubuntu 9.10)"
date: 2010-01-03
forum: Server Platforms
---

### Post by gliverman on 2010-01-03
I understand that LTSP in Ubuntu 9.10 connects via SSH so I want to make a CD that can be used off site to connect to my internal LTSP server.  Internally, I connect to the LTSP server via PXE. The public facing firewall forwards SSH to this server already.  What I am hoping is that I can build a CD for students and staff to use from home that will connect them to the LTSP server.  Anyone got any ideas how to do this?

---

### Post by Lars Noodén on 2010-01-03
You won't get a fast response with a remote connection, so keep that in mind.  But it does sound like a very interesting test.   

There will also be some security considerations, many of the protocols have weak or non-existent encryption.  So you might want to tunnel as much as possible over SSH.  

You'll want to first set up a remote hard drive so that it will boot locally then connect to LTSP.  That is for practice:
[https://blueprints.launchpad.net/ltsp/+spec/ltsp-client-install](https://blueprints.launchpad.net/ltsp/+spec/ltsp-client-install)

Once that is the way you like it, use that as the basis for a live CD.  
Use CD-RWs or Flash devices [like USB sticks](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar) for that.  
That will allow you to correct your practice runs.  Once the disks are in the hands of the students there will be a *very* high attrition rate for the disks.  I never got better than 6 uses out of any of them due accidental and intentional abuse or loss.

Consider using [BusyBox](http://www.busybox.net/) to build the boot image.  If you need ssh in busybox, then consider using the [dropbear](http://matt.ucc.asn.au/dropbear/dropbear.html) version based on openssh for client or server.  

If you need to pretend that the remote box is on the same LAN as the Terminal Server, then SSH can be used as a VPN with modifications to the routing table.  See the manual page for that -- if it's needed.  OpenVPN is another option, but procrastinate either solution as long as you can.

---

### Post by gliverman on 2010-01-04
Thank you for the info.  I have put some files on an external web server and am able to boot (sorta) with gPXE.  I get my PXE boot menu from pxelinux.0 and the info in pxelinux.cfg/default and can boot the kernel and initramfs from the web.  During the initramfs part though it fails at looking for the NBD server (my guess is it is looking for the local IP address that would normally exist if I was inside the remote network).The error is shown below:

[IMG]http://www.westga.edu/~gliverma/images/gPXE_error01.png[/IMG]

How can I change where it is looking for the NBD server and such or should I try and open a tunnel prior to all of this?



Thanks for the help!

---

### Post by Lars Noodén on 2010-01-05
That's the right idea, but it needs to go without pxe boot.  
pxe boot grabs the first server on the local network that happens to answer.  Some will find themselves outside your LAN and without a pxe server.  Others will find themselves outside your LAN but with a pxe server that does something other than point to your terminal server.  So the USB stick or whatever, has to have the kernel and everything else it needs to connect to the external IP address of your terminal server.

Can you make your own busybox with a ssh client?  That will be the foundation for booting.  

[http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Introducing-initramfs-a-new-model-for-initial-RAM-disks/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Introducing-initramfs-a-new-model-for-initial-RAM-disks/)

Parallel to that, boot from a local device.  I looked at a lot of links for detailed or uptodate information, but the documentation for LTSP seems to be a little sparse (many circular links) so it might be necessary to check the LTSP lists:

[http://lists.sourceforge.net/lists/listinfo/ltsp-discuss](http://lists.sourceforge.net/lists/listinfo/ltsp-discuss)
[http://marc.theaimsgroup.com/?l=ltsp-discuss&r=1&w=2](http://marc.theaimsgroup.com/?l=ltsp-discuss&r=1&w=2)

The good news is that sparse documentation means that you can probably do a conference or workshop circuit or set up consulting for a few months.

---

### Post by jeight on 2010-08-17
Maybe I don't understand completely what is going on here, but wouldn't it be easier to make a live cd with something like Arch linux? Just install the X window manager and install the files needed to run x2go (alternative to freenx) [www.x2go.org](www.x2go.org) and then have it run at startup. Then when you boot from cd, x2go will pop up immediately, and the students can use that to securely log in using RSA authentication through ssh.

---

