---
title: "PXE TFTP Boot"
date: 2010-02-05
forum: Server Platforms
---

### Post by mnbbrown on 2010-02-05
I have just install tftpd-hpa on our server. I am using it to remote install Windows XP and to have access to BartPE. It works but after it recieves it IP address it just pauses at a prompt that says 'boot:'  for 30 seconds before beginning to download the BartPE image.

I am using pxelinux.0 from the syslinux dist as the boot file which invokes startrom.0 as the kernel. 

Any idea what the problem could be??????:D:D:D

---

### Post by koenn on 2010-02-06
maybe you have a 30 sec. timeout configured in the pxe conf ?

---

### Post by Stuart42 on 2010-03-01
I know this isn't directly related,  but for net installs of Windows XP, I've been using Ultimate Deployment Appliance for vmware-server. It uses the ris-linux package.

---

