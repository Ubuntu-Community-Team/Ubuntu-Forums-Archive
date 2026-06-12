---
title: "server 12.04 LTS apt-get issue"
date: 2013-01-23
forum: Server Platforms
---

### Post by tymewyse on 2013-01-23
I have a server running 12.04 LTS Server running and have now run into an issue with it. I went to do an update and it keeps coming up with the error:

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-36-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

I tried using the -f apt-get -f install but keep getting this error:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-polkit-1.0 libutouch-grail1 libxml-namespacesupport-perl
  libxml-parser-perl libutouch-evemu1 libutouch-frame1 libutouch-geis1
  libxml-sax-base-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.2.0-36-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-36-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
2 not fully installed or removed.
Need to get 0 B/38.2 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 192147 files and directories currently installed.)
Unpacking linux-image-3.2.0-36-generic-pae (from .../linux-image-3.2.0-36-generic-pae_3.2.0-36.57_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-36-generic-pae_3.2.0-36.57_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-36-generic-pae': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-36-generic-pae_3.2.0-36.57_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

So, the question is how do add the missing kernel so it can be updated and fixed. 

Jeff

---

### Post by steeldriver on 2013-01-23
looks like you need to free ups some disk space

> **tymewyse said:**
> 
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-36-generic-pae_3.2.0-36.57_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-36-generic-pae': [COLOR=Red]No space left on device[/COLOR]
No apport report written because the error message indicates a [COLOR=Red]disk full[/COLOR] error
                                                                              

---

### Post by tymewyse on 2013-01-23
> **steeldriver said:**
> looks like you need to free ups some disk space

I have plenty of space available and even when I do an apt-get autoremove this:  

sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-36-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

 I run apt-get -f install to fix and get: 

sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-polkit-1.0 libutouch-grail1 libxml-namespacesupport-perl
  libxml-parser-perl libutouch-evemu1 libutouch-frame1 libutouch-geis1
  libxml-sax-base-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.2.0-36-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-36-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
2 not fully installed or removed.
Need to get 0 B/38.2 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 192147 files and directories currently installed.)
Unpacking linux-image-3.2.0-36-generic-pae (from .../linux-image-3.2.0-36-generic-pae_3.2.0-36.57_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-36-generic-pae_3.2.0-36.57_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-36-generic-pae': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-36-generic-pae_3.2.0-36.57_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


then I do and upgrade and get:

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-36-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

 It seems like everything is because of "linux-image-3.2.0-36-generic-pae but it is not installed". I have been reading all kinds of threads where others are having this issue also. Just trying to figure out how to correct it.

Jeff

---

### Post by ibjsb4 on 2013-01-23
You need to remove some old kernels.

[http://ubuntuforums.org/showthread.php?t=1927867](http://ubuntuforums.org/showthread.php?t=1927867)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+server+kernels&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+server+kernels&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by tymewyse on 2013-01-24
> **ibjsb4 said:**
> You need to remove some old kernels.

[http://ubuntuforums.org/showthread.php?t=1927867](http://ubuntuforums.org/showthread.php?t=1927867)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+server+kernels&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+server+kernels&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

Thanks for the info. When I try to purge the image with apt I get the same error. I do have Webmin running. Can I just delete the some of the old images from the file manager? 

 Sorry but this is the first time I have had to do this.

Jeff

---

### Post by steeldriver on 2013-01-24
I have manually removed (rm) initrd.img-3.x.x.x- image files before - I suggest running apt-get purge on the corresponding linux-image-3.x.x.x- package as soon as you have headroom to do so though to keep the package management system happy

See [http://ubuntuforums.org/showthread.php?t=2098490](http://ubuntuforums.org/showthread.php?t=2098490) for a similar situation

---

### Post by tymewyse on 2013-01-25
Thanks to everyone for the help. I got everything working. I manually removed a couple of the kernels and did a grub update and everything worked. It was frustrating because anything I did came with the same error.

Jeff

PS sorry I didn't mark it "SOLVED" correctly. It is now

---

### Post by tgalati4 on 2013-01-25
Bad things happen when you run out of either RAM, swap, or hard disk space.

---

### Post by ibjsb4 on 2013-01-25
Glad you got it sorted out.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

