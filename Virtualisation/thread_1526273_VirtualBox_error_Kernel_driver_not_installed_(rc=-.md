---
title: "VirtualBox error: Kernel driver not installed (rc=-1908) + Release Cand. kernel"
date: 2010-07-07
forum: Virtualisation
---

### Post by deckoff on 2010-07-07
Hello,
I try to install VirtualBox with a rel candidate kernel. I have to use it, because Ubuntu crashes with older, when playing video. So, I get this nasty error message from the title. Tried all tricks from here [http://ubuntuforums.org/showthread.php?t=1163811](http://ubuntuforums.org/showthread.php?t=1163811),but nothing helped. 
Can s/o help. Probably I would have to install the sources manually, but just dont now how to do it...

I manually installed the .deb header file,coping it to appropriate places

after running  [FONT=AR PL UMing TW, serif]sudo /etc/init.d/vboxdrv setup I get the following error message 

Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.2.6

------------------------------
Deleting module version: 3.2.6
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.2.6/source ->
                 /usr/src/vboxdrv-3.2.6

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=2.6.35-020635rc1-generic -C /lib/modules/2.6.35-020635rc1-generic/build M=/var/lib/dkms/vboxdrv/3.2.6/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.35-020635rc1-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/3.2.6/build/ for more information.
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.35-020635rc1-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'. Stop.
make: *** [vboxdrv] Error 2
[/FONT]

---

### Post by varunmagical on 2010-07-08
I am also facing this problem .. I have to reinstall virtualbox 3.2 package every time I boot my comp to use virtualbox :(

---

### Post by varunmagical on 2010-07-08
This is the kernel driver initialization problem .. maybe a bug in virtualbox or DKMS

[SIZE="6"]Here is the workaround:[/SIZE]
[SIZE="4"]Type following in your terminal every time you boot your computer:
[FONT="Arial Black"]> sudo /etc/init.d/vboxdrv setup[/FONT]

Wait for a minute for it to finish & you are good to go.
[/SIZE]

---

### Post by deckoff on 2010-07-08
THE solution FROM THE OTHER THREAD WORKED FORME

The problem here was my Linux knowledge, I hadnt installed new kernel proplerly - justed installed - header, source file and kernel, ALL 3 FILES: (linux-headers-2.6.33-02063305_2.6.33-02063305_all.deb
linux-image-2.6.33-02063305-generic_2.6.33-02063305_i386.deb
linux-source-2.6.33_2.6.33-02063305_all.deb)
PUT IN THE SAME FOLDER. 
RESTART
```


[FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


```
Now everything is ok with me

---

### Post by sh1ny on 2010-07-08
Use this for newer kernels :

[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

---

