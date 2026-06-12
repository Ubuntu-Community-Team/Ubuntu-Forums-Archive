---
title: "LTSP kiosk and normal ldm"
date: 2009-09-07
forum: Server Platforms
---

### Post by pgemme on 2009-09-07
I am trying to figure out if I can use the ltsp kiosk mode and the regular build on the same server.  I have run:
 ```
ltsp-build-client --kiosk --base /opt/ltspkiosk
```Then in my /etc/ltsp/dhcp.conf file I assign different root-paths to different machines

 ```
option root-path "/opt/ltspkiosk/i386"
host test-dell
 {
         hardware ethernet <mac-address>;
         fixed-address 192.168.1.99;
         option root-path "/opt/ltsp/i386";
 }
```But I get **tftp: client does not accept options**. Then the assigned file becomes /opt/ltspkiosk/images/i386.img

In lts.conf I tried changing my screen_07 to be rdesktop, which works, but the kiosk image still loads and change the screen.

Can I run ltsp built as kiosk and normal and have different clients boot off of different ones?

---

### Post by pgemme on 2009-09-07
I already figured it out.  Sometimes you just need to give up and post, haha.

I can add a file named after the mac address to the /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/ folder.
```
DEFAULT vmlinuz ro initrd=initrd.img nbdport=2001
```[B]change to:
[/B]```
DEFAULT vmlinuz ro initrd=initrd.img nbdport=2000
```Once I have it listen to the other port - it will boot the correct image.

---

