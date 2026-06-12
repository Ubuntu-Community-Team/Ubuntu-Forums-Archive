---
title: "iscsi diskless server install - any luck anyone"
date: 2011-08-30
forum: Server Platforms
---

### Post by gurpal2000 on 2011-08-30
Hi

[SIZE=1]I followed example at [http://etherboot.org/wiki/sanboot/ubuntu_iscsi](http://etherboot.org/wiki/sanboot/ubuntu_iscsi) ("[/SIZE][SIZE=1]Installing ubuntu directly onto the iSCSI SAN followed" by "[/SIZE]Preparing the initrd"[SIZE=1]) and i get a freeze when rebooting via gpxe "Booting from BIOS drive 0x80".

There is so much doco on how to do this but none of it seems to work for me. I have a FIT-PC2 and a synology running dnsmaq which seems to serve all the files need via dnsmasq's builtin tftp server.

I heard there was some issues with open-iscsi version in the latest. Also what im finding is that during a server install the "login into iscsi" doesn't work. The installer seems to kill the network connection by the time you get to detecting drives so it can't detect any iscsi targets. Also it seems only the LIVE desktop CD seems to be able to activate iscsi when you install it manually as per the first wiki link above.

So - has anyone got NATTY server working. Both an install AND boot via ISCSI ? If so do i need to try harder ;-)

thanks,
[/SIZE]

---

### Post by gurpal2000 on 2011-08-30
seems booting oneric server alpha 3 (via usb) i can install to iscsi. I think the above bug is fixed :-)

still get a problem after booting though. halts on "booting from bios drive 0x80"

---

