---
title: "KernelCheck HYDRA Beta (1.1.0 Beta) Testers Needed!"
date: 2007-10-24
forum: The Cafe
---

### Post by master_kernel on 2007-10-24
_First, straight from the website..._
KernelCheck HYDRA is the beta codename for its successor, KernelCheck 1.1.0. This release will be a MAJOR release, and is currently scheduled to be released by the end of the first week of November 2007. The beta version of 1.1.0 is available from the pool repository. This version will include many speed updates and automatic compilation of popular proprietary video drivers. nVidia users are needed to test this feature. Any feedback with the beta testing is appreciated.

Any beta testers are appreciated!

When giving feedback, please include the architecture (32bit or 64bit) of your system, the error(s), and any other related information.

[COLOR="Red"]
Note: Do not use the Check for Updates button as this will downgrade KernelCheck to the last stable release.[/COLOR]

---

### Post by master_kernel on 2007-10-24
Note: The proprietary driver options do not work because of a change in the 2.6.23 kernel. I will try to fix this ASAP. Until I do, it is advised that you don't try to compile these drivers into the kernel.

---

### Post by John.Michael.Kane on 2007-10-24
> **master_kernel said:**
> Note: The proprietary driver options do not work because of a change in the 2.6.23 kernel. I will try to fix this ASAP. Until I do, it is advised that you don't try to compile these drivers into the kernel.

So how are nVidia users suppose to give feedback? being their driver is proprietary.

---

### Post by master_kernel on 2007-10-24
nVidia users can give feedback by telling if their drivers compiled correctly with the kernel or not. In other words, if you reboot, are your nVidia drivers working?

---

### Post by master_kernel on 2007-10-29
ATi fglrx driver testing needed... currently functions correctly on my computer but other input is needed.

---

### Post by kevdog on 2007-10-29
Where can I test this?  I was expecting a svn release however when I went to the website I was greeted with a bunch of different folders.  Im kind of confused

---

### Post by master_kernel on 2007-10-30
Sorry, I should have been more clear. You can go to the download page and click on the testing link and download the tar.gz file. Just extract that and install as usual.

---

### Post by master_kernel on 2007-11-01
nVidia driver installation should work now, but I need feedback from nVidia users.

---

### Post by plun on 2007-11-01
> **master_kernel said:**
> nVidia driver installation should work now, but I need feedback from nVidia users.

I tested it with Debian Sid and the 2.6.23-1 kernel without trouble.

I cannot see any meaning with the Xorg reconfigure :confused: 

Today I tested with Hardy Heron and the prepatch to 2.6.24 but it 
doesn't compile.... are log files stored anywhere ?

a noapic make error as I remembers it.

Kernelcheck must be more robust to handle errors,  with errors
an endless loop occurs...you cannot just close the terminal window.
Also to remove src files....

EDIT

> arch/x86/kernel/built-in.o: In function `smp_send_nmi_allbutself':
/usr/src/linux/arch/x86/kernel/crash.c:85: undefined reference to `genapic'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.23'
make: *** [debian/stamp-build-kernel] Error 2


Crashfix   [http://lkml.org/lkml/2007/10/24/128](http://lkml.org/lkml/2007/10/24/128)

---

### Post by master_kernel on 2007-11-06
I probably should add log files. Any suggestions on how to do this?

---

### Post by plun on 2007-11-10
> **master_kernel said:**
> I probably should add log files. Any suggestions on how to do this?

Just installed greenhydra-RC2.....   :)

nVidia build fails, I am using the "old fashioned way".

sudo sh NVIDIA-Linux-x86-100.14.23-pkg1.run -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-2.6.23

A proposal.... is it maybe possible to create a 3rd party project
for kernelcheck  ?

[http://ubuntuforums.org/forumdisplay.php?f=46](http://ubuntuforums.org/forumdisplay.php?f=46)

A lot of users/"bravehearts" are interested in kernels and it must be better to have all threads in one place.

The best place for logfiles must be /var/logs but maybe its a good idea to make a choice for a user if she/he wants to save a logfile.

Thanks  :)

---

### Post by master_kernel on 2007-11-10
> **plun said:**
> Just installed greenhydra-RC2.....   :)

nVidia build fails, I am using the "old fashioned way".

sudo sh NVIDIA-Linux-x86-100.14.23-pkg1.run -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-2.6.23

A proposal.... is it maybe possible to create a 3rd party project
for kernelcheck  ?

[http://ubuntuforums.org/forumdisplay.php?f=46](http://ubuntuforums.org/forumdisplay.php?f=46)

A lot of users/"bravehearts" are interested in kernels and it must be better to have all threads in one place.

The best place for logfiles must be /var/logs but maybe its a good idea to make a choice for a user if she/he wants to save a logfile.

Thanks  :)
I wish they would add a 3rd party sub-forum, but I guess I'd have to contact a moderator to have them do that.

Do you run the code you mentioned above before the kernel is compiled or after? I'm trying to get it to install on the system and also install the kernel source.

EDIT: would this code work **before** the kernel is compiled?
sudo sh NVIDIA-Linux-x86_64*.run --kernel-name=2.6.23.1-hydra -a

---

### Post by master_kernel on 2007-11-18
**ANNOUNCEMENT:** KernelCheck will include support for integrating the Kamikaze and mm- patchsets.

---

### Post by master_kernel on 2007-11-19
**ANNOUNCEMENT:** Vote for the KernelCheck logo here: [http://ubuntuforums.org/showthread.php?t=617680](http://ubuntuforums.org/showthread.php?t=617680)

---

