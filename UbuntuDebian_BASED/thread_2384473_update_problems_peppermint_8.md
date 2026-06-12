---
title: "update problems: peppermint 8"
date: 2018-02-07
forum: Ubuntu/Debian BASED
---

### Post by holdfast on 2018-02-07
Hi Can someone help me. I'm using ubuntu 16.04.2 & having problems with updating. When I do so I get errors & with the following information:

```
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 568988 files and directories currently installed.)
Removing linux-image-extra-4.13.0-26-generic (4.13.0-26.29~16.04.2) ...
depmod: FATAL: could not load /boot/System.map-4.13.0-26-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-26-generic /boot/vmlinuz-4.13.0-26-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-26-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_gpF2VD/lib/modules/4.13.0-26-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_gpF2VD/lib/modules/4.13.0-26-generic/modules.builtin: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-26-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-26-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.13.0-26-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up initramfs-tools (0.122ubuntu8.10) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-4.4.0-103201712311231-generic (4.4.0-103201712311231.0+mediatree+hauppauge) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-103201712311231-generic
vmlinuz(/boot/vmlinuz-4.4.0-103201712311231-generic
) points to /boot/vmlinuz-4.4.0-103201712311231-generic
 (/boot/vmlinuz-4.4.0-103201712311231-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-103201712311231-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-103201712311231-generic /boot/vmlinuz-4.4.0-103201712311231-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-103201712311231-generic /boot/vmlinuz-4.4.0-103201712311231-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-103201712311231-generic /boot/vmlinuz-4.4.0-103201712311231-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-103201712311231-generic

gzip: stdout: No space left on device
cpio: write error: Broken pipe
find: ‘standard output’: Broken pipe
find: write error
E: mkinitramfs failure find 1 cpio 1 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-103201712311231-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-103201712311231-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-103201712311231-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-extra-4.4.0-103201712162024-generic (4.4.0-103201712162024.0+mediatree+hauppauge) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-103201712162024-generic /boot/vmlinuz-4.4.0-103201712162024-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-103201712162024-generic /boot/vmlinuz-4.4.0-103201712162024-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-103201712162024-generic /boot/vmlinuz-4.4.0-103201712162024-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-103201712162024-generic

gzip: stdout: No space left on device
cpio: write error: Broken pipe
find: ‘standard output’: Broken pipe
find: write error
E: mkinitramfs failure find 1 cpio 1 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-103201712162024-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-103201712162024-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-103201712311231-generic:
 linux-image-extra-4.4.0-103201712311231-generic depends on linux-image-4.4.0-103201712311231-generic; however:
  Package linux-image-4.4.0-103201712311231-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-103201712311231-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-mediatree:
 linux-image-mediatree depends on linux-image-4.4.0-103201712311231-generic; however:
  Package linux-image-4.4.0-103201712311231-generic is not configured yet.
 linux-image-mediatree depends on linux-image-extra-4.4.0-103201712311231-generic; however:
  Package linux-image-extra-4.4.0-103201712311231-generic is not configured yet.

dpkg: error processing package linux-image-mediatree (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu8.10) ...
update-initramfs: Generating /boot/initrd.img-4.10.0-42-generic

gzip: stdout: No space left on device
cpio: write error: Broken pipe
find: ‘standard output’: Broken pipe
find: write error
E: mkinitramfs failure find 1 cpio 1 gzip 1
update-initramfs: failed for /boot/initrd.img-4.10.0-42-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-4.4.0-103201712311231-generic
 linux-image-extra-4.4.0-103201712162024-generic
 linux-image-extra-4.4.0-103201712311231-generic
 linux-image-mediatree
 initramfs-tools
```

Can anyone help?

many thanks

Holdfast

---

### Post by #&amp;thj^% on 2018-02-07
Post any errors from this command:
```
sudo apt autoremove
```
Please use Code Tags for large txt...easier to read and keeps format. 
Found here: [https://ubuntuforums.org/showthread.php?t=2171721](https://ubuntuforums.org/showthread.php?t=2171721)
Thanks deadflowr; for the code tags.;)

---

### Post by wildmanne39 on 2018-02-07
*Thread moved to **New to Ubuntu, a more appropriate forum**.*

---

### Post by Impavidus on 2018-02-08
Also post output of this one:```
dpkg -l | grep linux-
```That tells us which kernel (meta-)packages you've currently installed or partially installed.

It seems you've got a full /boot partition and some dirt from a failed attempt to clean up.

---

### Post by holdfast on 2018-02-08
Hi 1fallen, Thanks for getting back to me. I'm a novice when it comes to forums & particularly this ubuntu forum. So I'm not sure what you mean when you say "[COLOR=#000000]Please use Code Tags for large txt...easier to read and keeps format. "[/color] I've checked the link you added but am still unsure what you mean? Any help would be appreciated.

I have used the terminal command you suggested & got a long print out with the following error:

```
Errors were encountered while processing:
 linux-image-extra-4.13.0-26-generic
 linux-image-extra-4.10.0-37-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Is that helpful.

Take care  Holdfast

Hi Impavidus

Thanks for your reply. Here is the printout I get when I use the above command:
```

dpkg -l | grep linux-
ii  ladspa-sdk                                      1.13-2                                                      amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                      4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                  1.157.14                                                    all          Firmware for Linux kernel drivers
ii  linux-firmware-hauppauge                        0.1.0+xenial                                                all          Si2168-B40 firmware, needed on Hauppauge DVB-T2/C/T tuners in Europe, Australia and New Zealand.
ii  linux-headers-4.10.0-40                         4.10.0-40.44~16.04.1                                        all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-40-generic                 4.10.0-40.44~16.04.1                                        amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.10.0-42                         4.10.0-42.46~16.04.1                                        all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-42-generic                 4.10.0-42.46~16.04.1                                        amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-26                         4.13.0-26.29~16.04.2                                        all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-26-generic                 4.13.0-26.29~16.04.2                                        amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-103201712162024             4.4.0-103201712162024.0+mediatree+hauppauge                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-103201712162024-generic     4.4.0-103201712162024.0+mediatree+hauppauge                 amd64        Linux kernel headers with slipstreamed mediatree drivers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-103201712311231             4.4.0-103201712311231.0+mediatree+hauppauge                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-103201712311231-generic     4.4.0-103201712311231.0+mediatree+hauppauge                 amd64        Linux kernel headers with slipstreamed mediatree drivers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-16.04                 4.13.0.26.46                                                amd64        Generic Linux kernel headers
ii  linux-headers-mediatree                         0.16.9+xenial                                               all          Header files related to linux-image-mediatree
rc  linux-image-4.10.0-37-generic                   4.10.0-37.41~16.04.1                                        amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.10.0-38-generic                   4.10.0-38.42~16.04.1                                        amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-40-generic                   4.10.0-40.44~16.04.1                                        amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-42-generic                   4.10.0-42.46~16.04.1                                        amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-103201712131415-generic       4.4.0-103201712131415.0+mediatree+hauppauge                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-103201712162024-generic       4.4.0-103201712162024.0+mediatree+hauppauge                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-103201712311231-generic       4.4.0-103201712311231.0+mediatree+hauppauge                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-92201708161632-generic        4.4.0-92201708161632.0+mediatree+hauppauge                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-53-generic                    4.8.0-53.56~16.04.1                                         amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rH  linux-image-extra-4.10.0-37-generic             4.10.0-37.41~16.04.1                                        amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-38-generic             4.10.0-38.42~16.04.1                                        amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-40-generic             4.10.0-40.44~16.04.1                                        amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-42-generic             4.10.0-42.46~16.04.1                                        amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rH  linux-image-extra-4.13.0-26-generic             4.13.0-26.29~16.04.2                                        amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-103201712131415-generic 4.4.0-103201712131415.0+mediatree+hauppauge                 amd64        Linux kernel extra modules with slipstreamed mediatree drivers for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-103201712162024-generic 4.4.0-103201712162024.0+mediatree+hauppauge                 amd64        Linux kernel extra modules with slipstreamed mediatree drivers for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-103201712311231-generic 4.4.0-103201712311231.0+mediatree+hauppauge                 amd64        Linux kernel extra modules with slipstreamed mediatree drivers for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-92201708161632-generic  4.4.0-92201708161632.0+mediatree+hauppauge                  amd64        Linux kernel extra modules with slipstreamed mediatree drivers for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-53-generic              4.8.0-53.56~16.04.1                                         amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-mediatree                           0.16.9+xenial                                               all          linux-image packages wih integrated LinuxTV.org mediatree drivers
ii  linux-libc-dev:amd64                            4.4.0-109.132                                               amd64        Linux Kernel Headers for development
ii  linux-sound-base                                1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
```

Hope that is helpful. Take care Holdfast

Thanks Wildmanne39, wasn't sure where to put it. Take care Holdfast

---

### Post by #&amp;thj^% on 2018-02-08
> **holdfast said:**
> Hi 1fallen, Thanks for getting back to me. I'm a novice when it comes to forums & particularly this ubuntu forum. So I'm not sure what you mean when you say "[COLOR=#000000]Please use Code Tags for large txt...easier to read and keeps format. " I've checked the link you added but am still unsure what you mean? Any help would be appreciated.

I have used the terminal command you suggested & got a long print out with the following error:

[/COLOR]Errors were encountered while processing:
 linux-image-extra-4.13.0-26-generic
 linux-image-extra-4.10.0-37-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is that helpful.

Take care  Holdfast
No worries, just part of the learning curve. :D
Yes that is helpful.

Impavidus also has some useful code to run so we don't run amuck with removing important packages.
So if you would be as kind to also show us the return of:
```
dpkg -l | grep linux-
```
EDIT: Just seen you post that back now!
Yuck that's quite a mess we have here, need some time to plan a solution for you.

---

### Post by #&amp;thj^% on 2018-02-08
All right then lets have a look at what kernel your using currently with:
```
uname -r
```
Paste that back here so we don't uninstall it.
We are getting close here, barring anything else from cropping up. :)

---

### Post by holdfast on 2018-02-09
hi 1fallen,

Here is the out put from the above command:

4.10.0-42-generic

take care

hold fast

---

### Post by #&amp;thj^% on 2018-02-09
Greetings holdfast:)
All of the kernels showing this at "rc" the begining
Meaning:```

r: the package was marked for removal
c: the configuration files are currently present in the system
```
1st rule of thumb, Keep the Boot directory clean and tidy with:
```
sudo apt-get autoremove
```
Great way to prevent what you now have on your hands.

In the first two columns of your dpkg -l generated list of kernels you will find information on the package as follows:

    Column (desired action):
```
    u = Unknown
    i = Install
    h = Hold
    r = Remove
    p = Purge

```
    Column (package status):

   ```
 n = Not-installed
    c = Config-files
    H = Half-installed
    U = Unpacked
    F = Half-configured
    W = Triggers-awaiting
    t = Triggers-pending
    i = Installed
```

For your first example

```
rc  linux-image-4.4.0-103201712131415-generic       4.4.0-103201712131415.0+mediatree+hauppauge
```

Hope this is not too much information at once but maybe keep it your back-pocket for later.

Now try this if you would:
```
sudo dpkg --purge linux-headers-4.4.0-103201712162024 linux-headers-4.4.0-103201712162024-generic linux-headers-4.4.0-103201712311231 linux-headers-4.4.0-103201712311231-generic linux-image-4.4.0-103201712131415-generic linux-image-4.4.0-103201712162024-generic linux-image-4.4.0-103201712311231-generic
```
Now if you see anything not listed from code above listed in the terminal for removal paste that back here to see, before accepting the change in the terminal.
Just a heads-up i will be in and out all day today.(Busy Busy)

---

### Post by Impavidus on 2018-02-10
First of all, let's purge some packages marked rc:```
sudo dpkg --purge linux-image-4.8.0-53-generic linux-image-extra-4.8.0-53-generic
sudo dpkg --purge linux-image-4.10.0-38-generic linux-image-extra-4.10.0-38-generic
sudo dpkg --purge linux-image-4.4.0-92201708161632-generic linux-image-extra-4.4.0-92201708161632-generic
sudo dpkg --purge linux-image-4.4.0-103201712131415-generic linux-image-extra-4.4.0-103201712131415-generic
```
Those packages don't take up any space on your hard drive. Purging them only removes some clutter from dpkg's output.

Next try and remove another old kernel:```
sudo dpkg --purge linux-headers-4.10.0-40 linux-headers-4.10.0-40-generic linux-image-4.10.0-40-generic linux-image-extra-4.10.0-40-generic
```
That should free up some space.

There are also two partially installed old kernels. Try and remove those:```
sudo dpkg --purge linux-image-4.10.0-37-generic linux-image-extra-4.10.0-37-generic
sudo dpkg --purge linux-image-4.4.0-103201712162024-generic linux-image-extra-4.4.0-103201712162024-generic
```
That should free up some more space.

Now try and make the package manager happy:```
sudo apt install -f
```
Hopefully, that will install and configure linux-image-4.4.0-103201712311231-generic, linux-image-extra-4.4.0-103201712311231-generic and linux-image-mediatree. It may also install linux-image-4.13.0-26-generic or remove linux-image-extra-4.13.0-26-generic. It doesn't really matter, as we can fix that later.

Now it appears you have both the normal 16.04 HWE kernel (linux-image(-extra)-4.10.0-42-generic, to be upgraded to 4.13.0-26, but the upgrade to 4.13.0-32 is available already) and the linux-image-mediatree kernel. I assume that's for some special hardware. You're currently running the normal kernel. You probably want both, if only to have a fallback in case one of them doesn't work. But to get automatic upgrades to the normal kernel, you have to install one extra package.

If you reboot, make sure to boot kernel 4.10.0-42. That's the one you use now and the one not affected by those commands, making it the only kernel guaranteed to work until this is all fixed.

Show us the effect of above commands:```
dpkg --list | grep linux-
```

---

### Post by holdfast on 2018-02-10
Hi 1fallen, for all your time & efforts. It's taking me a while to take in & understand this information. I have pasted the instructions you gave into my terminal & the following came back:

```
sudo dpkg --purge linux-headers-4.4.0-103201712162024 linux-headers-4.4.0-103201712162024-generic linux-headers-4.4.0-103201712311231 linux-headers-4.4.0-103201712311231-generic linux-image-4.4.0-103201712131415-generic linux-image-4.4.0-103201712162024-generic linux-image-4.4.0-103201712311231-generic
[sudo] password for monica: 
(Reading database ... 402189 files and directories currently installed.)
Removing linux-headers-4.4.0-103201712162024-generic (4.4.0-103201712162024.0+mediatree+hauppauge) ...
dpkg: dependency problems prevent removal of linux-headers-4.4.0-103201712311231-generic:
 linux-headers-mediatree depends on linux-headers-4.4.0-103201712311231-generic.


dpkg: error processing package linux-headers-4.4.0-103201712311231-generic (--purge):
 dependency problems - not removing
Removing linux-image-4.4.0-103201712131415-generic (4.4.0-103201712131415.0+mediatree+hauppauge) ...
Purging configuration files for linux-image-4.4.0-103201712131415-generic (4.4.0-103201712131415.0+mediatree+hauppauge) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-103201712131415-generic /boot/vmlinuz-4.4.0-103201712131415-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-103201712131415-generic /boot/vmlinuz-4.4.0-103201712131415-generic
dpkg: dependency problems prevent removal of linux-image-4.4.0-103201712162024-generic:
 linux-image-extra-4.4.0-103201712162024-generic depends on linux-image-4.4.0-103201712162024-generic.


dpkg: error processing package linux-image-4.4.0-103201712162024-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-4.4.0-103201712311231-generic:
 linux-image-mediatree depends on linux-image-4.4.0-103201712311231-generic.
 linux-image-extra-4.4.0-103201712311231-generic depends on linux-image-4.4.0-103201712311231-generic.


dpkg: error processing package linux-image-4.4.0-103201712311231-generic (--purge):
 dependency problems - not removing
Removing linux-headers-4.4.0-103201712162024 (4.4.0-103201712162024.0+mediatree+hauppauge) ...
dpkg: dependency problems prevent removal of linux-headers-4.4.0-103201712311231:
 linux-headers-4.4.0-103201712311231-generic depends on linux-headers-4.4.0-103201712311231.


dpkg: error processing package linux-headers-4.4.0-103201712311231 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-4.4.0-103201712311231-generic
 linux-image-4.4.0-103201712162024-generic
 linux-image-4.4.0-103201712311231-generic
 linux-headers-4.4.0-103201712311231
```

Hope that is helpful.

Take care

Holdfast

Hi Impavidus

Thanks for your help. I used the commands you gave and those from 1fallen.

Here's a copy of the terminal output you asked for:

```
dpkg --list | grep linux-
ii  ladspa-sdk                                      1.13-2                                                      amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                      4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                  1.157.14                                                    all          Firmware for Linux kernel drivers
ii  linux-firmware-hauppauge                        0.1.0+xenial                                                all          Si2168-B40 firmware, needed on Hauppauge DVB-T2/C/T tuners in Europe, Australia and New Zealand.
ii  linux-headers-4.10.0-42                         4.10.0-42.46~16.04.1                                        all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-42-generic                 4.10.0-42.46~16.04.1                                        amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-26                         4.13.0-26.29~16.04.2                                        all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-26-generic                 4.13.0-26.29~16.04.2                                        amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
pi  linux-headers-4.4.0-103201712311231             4.4.0-103201712311231.0+mediatree+hauppauge                 all          Header files related to Linux kernel version 4.4.0
pi  linux-headers-4.4.0-103201712311231-generic     4.4.0-103201712311231.0+mediatree+hauppauge                 amd64        Linux kernel headers with slipstreamed mediatree drivers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-16.04                 4.13.0.26.46                                                amd64        Generic Linux kernel headers
ii  linux-headers-mediatree                         0.16.9+xenial                                               all          Header files related to linux-image-mediatree
ii  linux-image-4.10.0-42-generic                   4.10.0-42.46~16.04.1                                        amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
pi  linux-image-4.4.0-103201712311231-generic       4.4.0-103201712311231.0+mediatree+hauppauge                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-42-generic             4.10.0-42.46~16.04.1                                        amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-26-generic             4.13.0-26.29~16.04.2                                        amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-103201712311231-generic 4.4.0-103201712311231.0+mediatree+hauppauge                 amd64        Linux kernel extra modules with slipstreamed mediatree drivers for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-mediatree                           0.16.9+xenial                                               all          linux-image packages wih integrated LinuxTV.org mediatree drivers
ii  linux-libc-dev:amd64                            4.4.0-109.132                                               amd64        Linux Kernel Headers for development
ii  linux-sound-base                                1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
```

Hope that is helpful. Not sure whether I should be using both the commands from yourself and 1fallen? Don't want to mess my system up. Have you any advice? take care Holdfast

---

### Post by deadflowr on 2018-02-10
Please use code tags when posting terminal output:
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by #&amp;thj^% on 2018-02-10
> **holdfast said:**
> Hi 1fallen, for all your time & efforts. It's taking me a while to take in & understand this information. I have pasted the instructions you gave into my terminal & the following came back:

```
sudo dpkg --purge linux-headers-4.4.0-103201712162024 linux-headers-4.4.0-103201712162024-generic linux-headers-4.4.0-103201712311231 linux-headers-4.4.0-103201712311231-generic linux-image-4.4.0-103201712131415-generic linux-image-4.4.0-103201712162024-generic linux-image-4.4.0-103201712311231-generic
[sudo] password for monica: 
(Reading database ... 402189 files and directories currently installed.)
Removing linux-headers-4.4.0-103201712162024-generic (4.4.0-103201712162024.0+mediatree+hauppauge) ...
dpkg: dependency problems prevent removal of linux-headers-4.4.0-103201712311231-generic:
 linux-headers-mediatree depends on linux-headers-4.4.0-103201712311231-generic.


dpkg: error processing package linux-headers-4.4.0-103201712311231-generic (--purge):
 dependency problems - not removing
Removing linux-image-4.4.0-103201712131415-generic (4.4.0-103201712131415.0+mediatree+hauppauge) ...
Purging configuration files for linux-image-4.4.0-103201712131415-generic (4.4.0-103201712131415.0+mediatree+hauppauge) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-103201712131415-generic /boot/vmlinuz-4.4.0-103201712131415-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-103201712131415-generic /boot/vmlinuz-4.4.0-103201712131415-generic
dpkg: dependency problems prevent removal of linux-image-4.4.0-103201712162024-generic:
 linux-image-extra-4.4.0-103201712162024-generic depends on linux-image-4.4.0-103201712162024-generic.


dpkg: error processing package linux-image-4.4.0-103201712162024-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-4.4.0-103201712311231-generic:
 linux-image-mediatree depends on linux-image-4.4.0-103201712311231-generic.
 linux-image-extra-4.4.0-103201712311231-generic depends on linux-image-4.4.0-103201712311231-generic.


dpkg: error processing package linux-image-4.4.0-103201712311231-generic (--purge):
 dependency problems - not removing
Removing linux-headers-4.4.0-103201712162024 (4.4.0-103201712162024.0+mediatree+hauppauge) ...
dpkg: dependency problems prevent removal of linux-headers-4.4.0-103201712311231:
 linux-headers-4.4.0-103201712311231-generic depends on linux-headers-4.4.0-103201712311231.


dpkg: error processing package linux-headers-4.4.0-103201712311231 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-4.4.0-103201712311231-generic
 linux-image-4.4.0-103201712162024-generic
 linux-image-4.4.0-103201712311231-generic
 linux-headers-4.4.0-103201712311231
```

Hope that is helpful.

Take care

Holdfast

Hi Impavidus

Thanks for your help. I used the commands you gave and those from 1fallen.

Here's a copy of the terminal output you asked for:

```
dpkg --list | grep linux-
ii  ladspa-sdk                                      1.13-2                                                      amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                      4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                  1.157.14                                                    all          Firmware for Linux kernel drivers
ii  linux-firmware-hauppauge                        0.1.0+xenial                                                all          Si2168-B40 firmware, needed on Hauppauge DVB-T2/C/T tuners in Europe, Australia and New Zealand.
ii  linux-headers-4.10.0-42                         4.10.0-42.46~16.04.1                                        all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-42-generic                 4.10.0-42.46~16.04.1                                        amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-26                         4.13.0-26.29~16.04.2                                        all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-26-generic                 4.13.0-26.29~16.04.2                                        amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
pi  linux-headers-4.4.0-103201712311231             4.4.0-103201712311231.0+mediatree+hauppauge                 all          Header files related to Linux kernel version 4.4.0
pi  linux-headers-4.4.0-103201712311231-generic     4.4.0-103201712311231.0+mediatree+hauppauge                 amd64        Linux kernel headers with slipstreamed mediatree drivers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-16.04                 4.13.0.26.46                                                amd64        Generic Linux kernel headers
ii  linux-headers-mediatree                         0.16.9+xenial                                               all          Header files related to linux-image-mediatree
ii  linux-image-4.10.0-42-generic                   4.10.0-42.46~16.04.1                                        amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
pi  linux-image-4.4.0-103201712311231-generic       4.4.0-103201712311231.0+mediatree+hauppauge                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-42-generic             4.10.0-42.46~16.04.1                                        amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-26-generic             4.13.0-26.29~16.04.2                                        amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-103201712311231-generic 4.4.0-103201712311231.0+mediatree+hauppauge                 amd64        Linux kernel extra modules with slipstreamed mediatree drivers for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-mediatree                           0.16.9+xenial                                               all          linux-image packages wih integrated LinuxTV.org mediatree drivers
ii  linux-libc-dev:amd64                            4.4.0-109.132                                               amd64        Linux Kernel Headers for development
ii  linux-sound-base                                1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
```

Hope that is helpful. Not sure whether I should be using both the commands from yourself and 1fallen? Don't want to mess my system up. Have you any advice? take care Holdfast

Impavidus is a repected user here in UF, you will be able to follow what suggestions he has to offer with confdence.
Welp I was hoping the "4.4.0-103201712311231.0+mediatree+hauppauge" would come out ok but it's not going to coperate with us, so we go about this differently.


```
sudo apt --purge  linux-headers-4.13.0-26 linux-image-extra-4.13.0-26-generic 
```
Now try this, and report any errors back here to see.
```
sudo apt -f install 
```
And **[COLOR="#FF0000"]ONLY[/COLOR]** if there are no errors shown try to run:
```
sudo apt autoremove
```

---

### Post by Impavidus on 2018-02-11
1fallen is another well rspected user here and of course all of us occasionally miss something.

Things are looking better now. After running 1fallen's commands, could you run```
df -h
```That will tell us whether your /boot partition has been properly cleaned up.

I don't know about your linux-image-mediatree package. It's not in the official repositories. Did you get this computer preinstalled with Ubuntu or did you follow some instructions to install it? You may need it if you have some special hardware, or maybe you don't need it. But as long as you have both the 4.10 or 4.13 kernel and that 4.4.0-103201... kernel installed, grub will boot the 4.10 or 4.13 kernel by default as it's the highest number. Have you tested them both? Does everything work?

In any case, the 4.10 kernel and the 4.13.0-26 kernel are old. Unless you only want the 4.4.0 kernel, we have to get it upgraded to 4.13.0-32.

---

### Post by holdfast on 2018-02-11
Hi Impavidus, Thanks for your reply. Here is a copy of the terminal output you requested:

$ df -h
Filesystem                       Size  Used Avail Use% Mounted on
udev                             1.9G     0  1.9G   0% /dev
tmpfs                            379M  6.2M  373M   2% /run
/dev/mapper/peppermint--vg-root  290G   15G  261G   6% /
tmpfs                            1.9G  3.6M  1.9G   1% /dev/shm
tmpfs                            5.0M  4.0K  5.0M   1% /run/lock
tmpfs                            1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1                        472M  148M  300M  33% /boot
tmpfs                            379M   12K  379M   1% /run/user/1000

Perhaps I should have mentioned earlier. I'm using peppermint 8 operating system. This is based on ubuntu 14.04.5. The package you mention "[COLOR=#000000]linux-image-mediatree package". make I'm wondering if this was something I downloaded to try and make something else work? 

I'm wondering if I need to use something like bleachbit to clean up my system & prevent similar problems to the one's i've had at present. 

I've a number of updates waiting and wonder if I need to try & install these?

Once more thanks for your help.

Holdfast[/COLOR]

---

### Post by #&amp;thj^% on 2018-02-11
> **holdfast said:**
> Hi Impavidus, Thanks for your reply. Here is a copy of the terminal output you requested:

$ df -h
Filesystem                       Size  Used Avail Use% Mounted on
udev                             1.9G     0  1.9G   0% /dev
tmpfs                            379M  6.2M  373M   2% /run
/dev/mapper/peppermint--vg-root  290G   15G  261G   6% /
tmpfs                            1.9G  3.6M  1.9G   1% /dev/shm
tmpfs                            5.0M  4.0K  5.0M   1% /run/lock
tmpfs                            1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1                        472M  148M  300M  33% /boot
tmpfs                            379M   12K  379M   1% /run/user/1000

Perhaps I should have mentioned earlier. I'm using peppermint 8 operating system. This is based on ubuntu 14.04.5. The package you mention "[COLOR=#000000]linux-image-mediatree package". make I'm wondering if this was something I downloaded to try and make something else work? 

I'm wondering if I need to use something like bleachbit to clean up my system & prevent similar problems to the one's i've had at present. 

I've a number of updates waiting and wonder if I need to try & install these?

Once more thanks for your help.

Holdfast[/COLOR]

That Looks a lot better now! :)
Now run:
```
sudo apt -f install
```
If any errors paste them back here to see.

---

### Post by deadflowr on 2018-02-11
> Perhaps I should have mentioned earlier. I'm using peppermint 8 operating system.
Indeed
*Thread moved to **Ubuntu/Debian BASED***

Unless there is confusion going on, as you have posted it being either Ubuntu 16.04.2 or Peppermint 8.
?

Also, please read my post #12.

---

### Post by holdfast on 2018-02-11
Sorry Deadflowr, I've only just realised what you meant in #12 about code tags. I'll seek to use those in the future. Take care Holdfast

---

