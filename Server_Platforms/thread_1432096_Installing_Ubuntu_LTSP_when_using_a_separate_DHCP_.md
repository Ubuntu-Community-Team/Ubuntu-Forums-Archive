---
title: "Installing Ubuntu LTSP when using a separate DHCP and TFTP server"
date: 2010-03-17
forum: Server Platforms
---

### Post by hrickards on 2010-03-17
Hi,

I want to install Ubuntu LTSP on top of an already existing system. However, I want to use a different DHCP and TFTP server. Do I simply just install &#8216;ltsp-server-standalone&#8217; with apt and run &#8216;sudo ltsp-build-client&#8217;, stop the DHCP and TFTP server and stop them from starting automatically? Would I then just copy over the pxelinux.cfg/default file from /var/lib/tftpboot along with the initrd.img and vmlinuz images to the TFTP server?

Thanks

Edit: Do I need to actually copy the whole /var/lib/tftpboot/ltsp directory over to the TFTP server?

---

### Post by hrickards on 2010-04-03
I've set this up as I described in my original post, and AFAICT it seems to work. I just copied over the contents  of the /var/lib/tftpboot/ltsp directory to the TFTP server.

---

