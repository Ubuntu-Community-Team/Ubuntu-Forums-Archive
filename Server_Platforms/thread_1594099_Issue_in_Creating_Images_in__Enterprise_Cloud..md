---
title: "Issue in Creating Images in  Enterprise Cloud."
date: 2010-10-12
forum: Server Platforms
---

### Post by naangilsunder on 2010-10-12
Hi All,
  We have Downloaded and installed  Ubuntu 10.10 Server Edition for Enabling Private cloud environment The installation went  successfully on  2 servers (1 –Front,2-Node).
  Trying to build windows images as per below document .
  [http://cssoss.wordpress.com/2010/05/10/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-edition-chapter-4-%E2%80%93-image%C2%A0management/](http://cssoss.wordpress.com/2010/05/10/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-edition-chapter-4-%E2%80%93-image%C2%A0management/)
  Initially I got the warning message  for KVM-pxe, I downloaded and installed [http://packages.ubuntu.com/maverick/kvm-pxe](http://packages.ubuntu.com/maverick/kvm-pxe)
  And now the message not gets appear. Now my problem is when I execute the command,
  **sudo kvm -m 1024 -cdrom  ISOs/Win2003Disk1.iso -drive file=win-2k3.img,if=scsi,boot=on -nographic -vnc :0**
  Installation process gets started but once the files get copied and boot back the screen is blank and nothing gets displayed.


Previously we where using 10.04 we followed the same procedure and was working fine.


  Pls help.

---

