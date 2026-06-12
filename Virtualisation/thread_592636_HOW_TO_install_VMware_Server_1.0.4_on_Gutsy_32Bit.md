---
title: "HOW TO: install VMware Server 1.0.4 on Gutsy 32Bit"
date: 2007-10-26
forum: Virtualisation
---

### Post by AndyCat on 2007-10-26
Here is how I did it. I had a fresh install of Gutsy 32 bit.

1. Go to **[http://vmware.com/download/server/](http://vmware.com/download/server/)** and download the latest version (1.0.4)

2. Make sure you register so you can get the serial key at [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)

3. Make sure you install this:** sudo aptitude install build-essential linux-headers-'uname -r' xorg-dev xinetd**

4. Now you can extract the file you dowloaded to a new folder
use this:  **tar -zxvf VMware-server**

5. CD to the created folder and do this:** sudo ./vmware-install.pl**

6. Installation will start. Select the default options and in 5 minutes you will have your VMware Server Working

7. Hope this helps the desperate ones!!!!

---

### Post by MemoryDump on 2007-10-26
do you need a serial number to run this server?
 I tried installing VMware using another similiar HowTo I was following and at some point I was prompted for a serial number.

---

### Post by AndyCat on 2007-10-26
Hello  there MemoryDump. Yes you do need to get a serial to install VMware Server.
Just go to [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html) and register yourself and they will give you the serial key you need.

Let me know if you need help.... Ill be glad to help you!

---

### Post by FredB on 2007-10-26
What a pity there is no 64 bits version for Gutsy AMD64 :(

---

### Post by mayonaise15 on 2007-10-26
Worked perfectly.  Thanks AndyCat.

---

### Post by AndyCat on 2007-10-26
Im glad it helped you mayonaise15..... 
At the moment im trying to make VMWARE server to run on 64 bit systems... ill be posting if I can do it.....
:popcorn:

---

### Post by rhardie on 2007-10-31
I was successful up until step 4 (tar -zxvf VMware-server) where I received the response as follows:

rocky@rocky-desktop:~$ tar -zxvf VMware-server
tar: VMware-server: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

My download is on the desktop and I simply did cut and paste for the step 4

AMD 64, Ubuntu 7.10

Thanks in advance

---

### Post by MemoryDump on 2007-10-31
> **rhardie said:**
> I was successful up until step 4 (tar -zxvf VMware-server) where I received the response as follows:

rocky@rocky-desktop:~$ tar -zxvf VMware-server
tar: VMware-server: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

My download is on the desktop and I simply did cut and paste for the step 4

AMD 64, Ubuntu 7.10

Thanks in advance

after you type "tar -zxvf VMware-server" hit TAB. It should auto-complete the rest of the file name for you. It should match the file you downloaded.

---

### Post by davidshere on 2007-10-31
Uh... any idea how to install VMWare Player?

---

### Post by tact on 2007-10-31
vmware player is in the repositories.  use synaptic.

be warned tho...  vmware-server and vmware player do not play well together.  You have to remove one COMPLETELY before the other...  

and by COMPLETELY - I mean you dotn just do the uninstall process... you then need to go on a hunt and destroy mission to find and delete any and all directories, config files etc....

if not you will have grief.

If your system is a vmware "virgin"...  never had any flavour of vmware installed.  then no issue.

---

### Post by rhardie on 2007-11-02
MemoryDump:

I attempted your "tab" suggestion and received a "beep" sound.

---

### Post by FredB on 2007-11-02
What gives a ls in console ?

---

### Post by fabarf on 2007-11-03
Worked perfectly here, now i need more free space in my hd for making vms :) thx

---

### Post by depele on 2007-11-04
I get this error 
I am installing command-line

```
The path "/usr/src/linux/include" is a kernel header file directory, but it
does not contain the file "linux/version.h" as expected.  This can happen if
the kernel has never been built, or if you have invoked the "make mrproper"
command in your kernel directory.  In any case, you may want to rebuild your
kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

```

==> keeps asking the location of directory of c header files.

for your information: 
```
depele@server:/usr/src/linux/include$ ls
acpi          asm-frv      asm-m68knommu  asm-sh64     crypto    net
asm-alpha     asm-generic  asm-mips       asm-sparc    Kbuild    pcmcia
asm-arm       asm-h8300    asm-parisc     asm-sparc64  keys      rdma
asm-arm26     asm-i386     asm-powerpc    asm-um       linux     rxrpc
asm-avr32     asm-ia64     asm-ppc        asm-v850     math-emu  scsi
asm-blackfin  asm-m32r     asm-s390       asm-x86_64   media     sound
asm-cris      asm-m68k     asm-sh         asm-xtensa   mtd       video
```

I had some troubles compiling my kernel...

tried already to recompile but no succes.

---

### Post by AndyCat on 2007-11-06
ls stands for directory listing and u could use ls -al  as formatted listing with hidden files

---

