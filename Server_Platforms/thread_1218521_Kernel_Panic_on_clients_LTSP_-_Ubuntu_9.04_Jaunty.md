---
title: "Kernel Panic on clients LTSP - Ubuntu 9.04 Jaunty"
date: 2009-07-20
forum: Server Platforms
---

### Post by Guevara76 on 2009-07-20
I have installed Ubuntu 9.04 and server kernel, update the chroot to the latest version of the kernel and boot the clients, get the message:  

> end_request: I/O error, dev nbd0, sector 188822 Kernel Panic - not syncing: 
attempted to kill init! 
Dumping ftrace buffer: 
 (ftrace buffer empty) 

More messages of errors: 

> killed process 377 (ipconfig) killed  
/init: .: line 1: can't open /tmp/net-eth0.conf 
out of memory: kill process 381 (init) score 18 or a child 
 killed process 381 (init) 

messages.log: [http://paste.ubuntu.com/222917/](http://paste.ubuntu.com/222917/)  
syslog.log: [http://paste.ubuntu.com/222920/](http://paste.ubuntu.com/222920/)  
dmesg: [http://paste.ubuntu.com/222921/](http://paste.ubuntu.com/222921/) 
 daemon.log [http://paste.ubuntu.com/222922/](http://paste.ubuntu.com/222922/)  
debug: [http://paste.ubuntu.com/222923/](http://paste.ubuntu.com/222923/) 
 udev: [http://paste.ubuntu.com/222926/](http://paste.ubuntu.com/222926/)      

I tried this:

appending the following in a new line at the end of /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default    

> IPAPPEND 3    

I have not had success.     Server is Ubuntu 9.04 Desktop with Kernel Server: 

  > $ uname -a
Linux servidor-desktop 2.6.28-13-server #45-Ubuntu SMP Tue Jun 30 20:51:10 UTC 2009 i686 GNU/Linux    


I stopped with 22 terminals because of this problem. 

Regards.

---

### Post by npnutn on 2009-07-20
Have you done ltsp-update-kernels and ltsp-update-image?

---

### Post by Guevara76 on 2009-07-20
Excuse the formatting of text, but could not fix.

Yes, i update sshkeys, kernel and image, but the bug persist. In Launchpad/LTSP said that the bug is the ubuntu and not LTSP project.

Recommended placing the module of the network card in initramfs / modules to start with the system, like this:

 

> 1.  Add the driver to:  /opt/ltsp/i386/etc/initramfs-tools/modules
 2. sudo chroot /opt/ltsp/i386
3. update-initramfs -c -k <kernel-version>
4. exit
5. sudo ltsp-update-kernels But is not the solution for the bug. 
Anyone know how to resolve this bug? ''/

---

### Post by Guevara76 on 2009-07-21
I try put the mudule on modules archive but not works! :(

---

### Post by Guevara76 on 2009-07-22
1. Add the driver to: /opt/ltsp/i386/etc/initramfs-tools/modules
2. sudo chroot /opt/ltsp/i386
3. update-initramfs -c -k <kernel-version>
4. exit
5. sudo ltsp-update-kernels

did not work.
I tried also using the desktop kernel and rebuild the image of the client does not work.
I put the module in the modules archive and the bug persists.
Appeared a message that udev was killed too.

Regards.

---

