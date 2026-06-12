---
title: "LTSP: boot server != ltsp server, how?"
date: 2009-01-28
forum: Server Platforms
---

### Post by golubovsky on 2009-01-28
Hi,

How would I configure/build LTSP client if the boot server is not the same as LTSP server?

Given a 64-bit computer (host) which runs several 32-bit VMs (with kvmadm); Ubuntu (8.04 fresh internet install with mini.iso) ltsp server is on one of these VMs. The host computer provides bridging, so all VMs are on the same subnet. The host computer also runs TFTP and DHCP. Diskless client is of course a separate PC ;)

I copied ltsp client's Linux kernel and initrd from Ubuntu VM (/opt/ltsp/i386/boot, vmlinuz-2.6.24-16-generic and initrd.img-2.6.24-16-generic)to the tftpboot directory of the host computer as vmlinuz-ltsp and initrd-ltsp resp. I added these lines to the host computer's pxelinux.cfg/default (similarly to those in the ltsp's pxelinux.cfg/default):

label Ubuntu LTSP
kernel vmlinuz-ltsp
append initrd=initrd-ltsp ro quiet splash

If I select this item in the client's PXE boot menu, the image starts booting, I see Ubuntu splash screen, but it cannot mount root because it tries to do that with the boot server (connection refused, as the host does not provide anything for this). I tried to append the "ip" parameter with IP if the Ubuntu VM as the second field: no effect.

ifconfig shows correct IP address on client's eth0.

Any suggestions?

Thanks.

---

### Post by jimv on 2009-02-04
Never done this, and I'm not entirely sure I understand the situation, but I'll give it a shot anyway.

Would it be possible for you to share the directory that contains the needed files from the boot server and mount it in the appropriate location on the LTSP server?

Also, I was messing with setting up PXE boot for my machines at home last night, and I notice this parameter for the DHCP server:

"net-server [server ip]"

Which apparently tells the clients which server has the boot files on it.  I didn't try it, because my DHCP server happened to also be the PXE server.

Here's the article I was looking at:  [http://www.linuxdevices.com/files/misc/pxe_boot_stb-howto.html](http://www.linuxdevices.com/files/misc/pxe_boot_stb-howto.html)

Hope this helps!

---

### Post by haddog on 2009-02-15
You finda solution? I am curious how to do this also. I have a standard setup also where the dhcp server and LTSP server are the same box.

---

