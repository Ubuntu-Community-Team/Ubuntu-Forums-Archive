---
title: "PXE Boot and 4GL.."
date: 2008-09-03
forum: Server Platforms
---

### Post by colskinet on 2008-09-03
Hi all

I am trying to setup a Ubuntu (Hardy) PC to act as a "server" so that new PC's we have delivered can boot from PXE, connect to the Ubuntu server and then use G4L to download a image file and be setup on our domain.

Would the following tutorial work ok for this :

[http://www.howtoforge.com/ubuntu_pxe_install_server](http://www.howtoforge.com/ubuntu_pxe_install_server)

If anyone has any other ideas/thoughts on how to automate this system please do let me know!

Kind regards
Colin

---

### Post by windependence on 2008-09-04
Are you planning to pixieboot Windows machines off this box? I'm not sure how that would work but I think it's possible.

-Tim

---

### Post by colskinet on 2008-09-04
Hi Tim

Our plan of attack is this:

Setup Ubuntu as an FTP Server to store "images" of new build PC's

Use a USB stick or CD to boot new machines that we want to restore the images too, after being imaged they will then be put onto our domain and have software installed via Group Policy.

Rather than use the CD/USB stick we would like to just boot straight from the network into the PXE server..

Hope that is a bit clearer for you

Regards
Colin

---

### Post by windependence on 2008-09-04
I don't see why that wouldn't work. Sounds like a good idea.

-Tim

---

### Post by promodus on 2008-09-04
G4U uses dd afaik. Which is a block-level disk/partition imaging tool. 
Ghost, as the G in G4U coincidentally, is a file-level disk/partition imaging tool. This would not include empty space.
What would I use? And save yourself a lot of time...
Use PING
Partimage Is Not Ghost.
Don't we love these recursive Open Source acronyms?
(You can always roll your own imaging software via an NFS boot Ubuntu, btw)

To install PING:
```
apt-get install dhcp3-server tftpd-hpa syslinux
```

[COLOR="Navy"]Configure dhcpd appropriately, add ```
filename "pxelinux.0";
``` to your subnet scope.[/COLOR]

from there
```
cd /var/lib/tftpboot && 
mkdir /var/lib/tftpboot/pxelinux.cfg && 
ln -s /usr/lib/syslinux/pxelinux.0 /var/lib/tftpboot/pxelinux.0 &&
wget http://ping.windowsdream.com/dl/PING_2.01/kernel &&
wget http://ping.windowsdream.com/dl/PING_2.01/initrd.gz &&
mv /var/lib/tftpboot/kernel /var/lib/tftpboot/pingkernel
mv /var/lib/tftpboot/initrd.gz /var/lib/tftpboot/pinginitrd.gz
cat > /var/lib/tftpboot/pxelinux.cfg/default << "EOF"
      DEFAULT rescue
      PROMPT 0
      LABEL rescue
      KERNEL pingkernel
      **APPEND vga=normal devfs=nomount pxe ramdisk_size=33000 load_ramdisk=1 init=/linuxrc prompt_ramdisk=0 initrd=pinginitrd.gz root=/dev/ram0 rw noacpi noapm pci=noacpi lba acpi=off apm=off**
"EOF"

```

(What's Bold is one line. this may wrap on copy & paste)

[http://ping.windowsdream.com/ping.html](http://ping.windowsdream.com/ping.html)

---

### Post by _Petya_ on 2008-11-18
You also have to add the line

```
next-server 1.2.3.4;
```

to your subnet scope, where 1.2.3.4 is the IP of the TFTP server. You even have to include this, if the TFTP server is running on the same machine as the DHCP.

Petya

---

