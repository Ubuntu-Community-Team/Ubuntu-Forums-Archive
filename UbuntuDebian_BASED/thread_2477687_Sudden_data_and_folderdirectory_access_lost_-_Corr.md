---
title: "Sudden data and folder/directory access lost - Corrupt package?"
date: 2022-08-03
forum: Ubuntu/Debian BASED
---

### Post by girtza on 2022-08-03
Hello there,  I am new to both Ubuntu and Pop! OS, as well as these  message boards.  Hopefully I am posting my question in the correct  place.  If not, please let me know and I'll be glad to move it to the  correct place.    

Information: 

Current package release:  5.17.15-76051715-generic 
System:  IBM Lenovo X200 Tablet/laptop 
Drive:   256 Gig SSD 
OS:  POP! OS  

Issue: 

   I've been using Pop OS for over a  year with no issues, however just recently I noticed issues during an  update with my Pop install.  I was receiving errors (See below) during  both boot up and the Terminal update process (Instead of Pop Shop)  and  shortly thereafter, I have lost complete access to any folder (Pictures,   Documents, Music, Videos, Downloads, etc.)  and am worried I have lost  all data in the process.  Connecting the drive to another computer  won't work, as it only displays a 512 MB (Out of 256 Gig) partition with  no access to a user home folder or data.    

Errors:  

+ When accessing  ANY folder or directory: (For this example, I'll use the downloads  folder)  

"Oops! Something went wrong. Unable to find "home//downloads.  Please check the spelling and try again."   


+ When attempting to force  an update using the "sudo apt-get install -f" command:  

```
Reading package  lists... Done 
Building dependency tree... Done 
Reading state  information... Done The following packages were automatically installed  and are no longer required:   linux-headers-5.17.5-76051705  linux-headers-5.17.5-76051705-generic  linux-image-5.17.5-76051705-generic    linux-modules-5.17.5-76051705-generic Use 'sudo apt autoremove' to  remove them. 
0 upgraded, 0 newly installed, 0 to remove and 3 not  upgraded. 1 not fully installed or removed. 
After this operation, 0 B of  additional disk space will be used. 
Setting up  linux-image-5.18.10-76051810-generic  (5.18.10-76051810.202207071639~1659108431~22.04~c9172fb) ... Processing  triggers for linux-image-5.18.10-76051810-generic  (5.18.10-76051810.202207071639~1659108431~22.04~c9172fb) ...  /etc/kernel/postinst.d/dkms:  * dkms: running auto installation service  for kernel 5.18.10-76051810-generic    ...done.  
/etc/kernel/postinst.d/initramfs-tools: update-initramfs: 
Generating  /boot/initrd.img-5.18.10-76051810-generic zstd: error 25 : Write error :  No space left on device (cannot write compressed block)  
E: mkinitramfs  failure zstd -q -1 -T0 25 update-initramfs: failed for  /boot/initrd.img-5.18.10-76051810-generic with 1. run-parts:  /etc/kernel/postinst.d/initramfs-tools exited with return code 1 dpkg:  error processing package linux-image-5.18.10-76051810-generic  (--configure):  installed linux-image-5.18.10-76051810-generic package  post-installation script subprocess returned error exit status 1 
Errors  were encountered while processing:  linux-image-5.18.10-76051810-generic  E: Sub-process /usr/bin/dpkg returned an error code (1) 

```

+ When  attempting to boot the laptop:

```
Cryptsetup: Waiting for encrypted source  device UUID=9dc96fe9-599e-4f38-991a-550bf430ab4e...   

[      6.232545] BPF:  
[      6.232545] BPF: [121967] FUNC 
[       6.232545] BPF:  type_id=8151 
[ 6.232545] BPF:
[      6.232545] BPF: [      6.232545] BPF:   Invalid name 
[ 6.232545] BPF:
[      6.232545] BPF:   [      6.232545] BPF:  [121967]  FUNC 
[      6.232545] BPF:  type_id=8151 
[      6.232545] BPF: 
[       6.232545] BPF:  Invalid name 
[      6.232545] BPF: 
[      6.232545] BPF:   type_id=486 bits_offset=576 
[      6.232545] BPF: 
[      6.232545]  BPF: 0_ONLINE type_id=122146 bits_offset=640 
[      6.232545] BPF: 
[       6.232545] BPF:  Invalid name 
[      6.232545] BPF:  
Busybox v1.30.1  (Ubuntu 1:1.30.1-7ubuntu3) built-in shell (ash) Enter 'help' for a list  of built-in commands.  
(initramfs) _   

```


I can boot into the laptop if I  go into the Bios and switch SATA mode:   "Compatibility"  to "AHCI"  At  which point the blue Ubuntu screen comes up and lets me boot to a  previous package release either normally or in recovery mode.  I still,  however, cannot access any data once I sign back in.    

I'm ok with  reloading this laptop drive, but I really need my data off before I do  that.  I'm hopeful it is recoverable.    I have tried many methods  mentioned in forums to address the issue (Such as Sudo commands to  remove, update, repair, etc.)  As well as commands to repair or rebuild  the initramfs, But nothing is working and I'm not sure where else to go  or what else to do.    


Any help or assistance would be very much  appreciated!   

Regards, 
-Adam

---

### Post by howefield on 2022-08-03
Thread moved to the "*Ubuntu/Debian BASED*" forum.

You might want to format your paragraph if you really want someone to read it.

---

### Post by girtza on 2022-08-03
Yikes!  
When I wrote it out, it was organized and everything.  The formatting must have been removed when I posted it.  I'll go edit it now.

Thank you!

*EDIT*  

It's working now.  I had to use the Advanced option in order to maintain formatting.  It should look correct now.

---

### Post by ajgreeny on 2022-08-03
I've no idea why but the settings you have chosen for the text entry box can sometimes cause this wall of text  problem if you chose the ***Enhanced Interface - Full WYSIWYG Editor***.

Go to Settings top right of each forum page -> My Account -General Settings and scroll right down to Miscellaneous Options.
Change the Message Editor Interface to the ***Standard Editor - Extra formatting controls*** and the problem may disappear.

---

### Post by girtza on 2022-08-03
Thanks for this tip, Aj! 

Looks like I need to make a few more posts (10) before I can access the Misc. options section.  I'll be sure to return and do so when able.  

Much appreciated!

---

