---
title: "How to remove gpraphics stack"
date: 2016-10-01
forum: Server Platforms
---

### Post by NotQuiteSU on 2016-10-01
Everytime I log in, I get a message:
> There is a graphics stack installed on this system. An upgrade to a
configuration supported for the full lifetime of the LTS will become
available on 2016-07-21 and can be installed by running 'update-manager'
in the Dash

I must have installed something when putzing around with Myth or another GUI dependent tool. How can I find/remove this graphics stack?

---

### Post by ajgreeny on 2016-10-01
What version of Ubuntu are you running and if it is 14.04 can you remember if it was one of the point releases, eg 14.04.3 or 14.04.4 there will be necessary upgrades to the hardware enablement stack very soon, if not already.

What is the output of ```
lsb_release -dc && echo "Desktop:	$DESKTOP_SESSION" && uname -mrn
```which will tell us a lot about your software and versions.

See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) which may explain in more detail.

---

### Post by NotQuiteSU on 2016-10-05
Sorry, waited a while to reply. Th efull mesage is:

> 
New release '16.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


WARNING: Security updates for your current Hardware Enablement Stack
ended on 2016-08-04:
 * [http://wiki.ubuntu.com/1404_HWE_EOL](http://wiki.ubuntu.com/1404_HWE_EOL)



> 
$ lsb_release -dc && echo "Desktop:$DESKTOP_SESSION" && uname -mrn
Description:    Ubuntu 14.04.5 LTS
Codename:       trusty
Desktop:
<hostname> 3.19.0-69-generic x86_64



---

### Post by Bashing-om on 2016-10-05
NotQuiteSU; Hello ;

As to:
> 
WARNING: Security updates for your current Hardware Enablement Stack
ended on 2016-08-04:

when you read the link you find what (H)ard(W)are (E)nablement - stack is .
In your case you have the vivid stack installed ( 3.19.0-69-generic x86_64 ) that is End_of_Life.
In the normal course of updates you should have been offered to upgrade to the current  HWE stack ( xenial) .

Let's see what the results are when you try and fully update the system:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade
df -h
df -i
dpkg -l | grep linux

```
maybe we have work to do to get the new stack to install. The df and dpkg commands will show us if we have to, then we have to.

[INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by NotQuiteSU on 2016-10-06
Can I just remove it? I though server didn't have a graphics stack? And if I do those commands, won't I be upgrading to 16?

---

### Post by Bashing-om on 2016-10-06
NotQuiteSU; Welp;

no.
> 
And if I do those commands, won't I be upgrading to 16?

these commands update the installed packages, and will not release-upgrade to 16.04 .

Hummm ..
> 
Can I just remove it? 

do not think so, got to have some graphical components to have any kind of display .

Now what is an option if you want out of the HWE cycle is to re-install the trusty packages and remove the vivd packages . Will requite a bit of attention to detail is all .

Now depends on what you want to do .
[INDENT][INDENT][INDENT]we do it your way
[/INDENT][/INDENT][/INDENT]

---

### Post by NotQuiteSU on 2016-10-08
updated, but the graphics wasnt

```
$ dpkg -l | grep linux
ii  libselinux1:amd64                                           2.2.2-1ubuntu0.1                     amd64        SELinux runtime shared libraries
ii  libv4l-0:amd64                                              1.0.1-1                              amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                        1.0.1-1                              amd64        Video4linux frame format conversion library
ii  linux-firmware                                              1.127.22                             all          Firmware for Linux kernel drivers
ii  linux-generic-lts-vivid                                     3.19.0.69.51                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-68                                     3.19.0-68.76~14.04.1                 all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-68-generic                             3.19.0-68.76~14.04.1                 amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-69                                     3.19.0-69.77~14.04.1                 all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-69-generic                             3.19.0-69.77~14.04.1                 amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-vivid                             3.19.0.69.51                         amd64        Generic Linux kernel headers
rc  linux-image-3.19.0-25-generic                               3.19.0-25.26~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-43-generic                               3.19.0-43.49~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-47-generic                               3.19.0-47.53~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-49-generic                               3.19.0-49.55~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-51-generic                               3.19.0-51.58~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-56-generic                               3.19.0-56.62~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-58-generic                               3.19.0-58.64~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-59-generic                               3.19.0-59.66~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-61-generic                               3.19.0-61.69~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-64-generic                               3.19.0-64.72~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-65-generic                               3.19.0-65.73~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-66-generic                               3.19.0-66.74~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-68-generic                               3.19.0-68.76~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-69-generic                               3.19.0-69.77~14.04.1                 amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                         3.19.0-25.26~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-43-generic                         3.19.0-43.49~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-47-generic                         3.19.0-47.53~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-49-generic                         3.19.0-49.55~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-51-generic                         3.19.0-51.58~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-56-generic                         3.19.0-56.62~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-58-generic                         3.19.0-58.64~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-59-generic                         3.19.0-59.66~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-61-generic                         3.19.0-61.69~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-64-generic                         3.19.0-64.72~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-65-generic                         3.19.0-65.73~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-66-generic                         3.19.0-66.74~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-68-generic                         3.19.0-68.76~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-69-generic                         3.19.0-69.77~14.04.1                 amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                               3.19.0.69.51                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-96.143                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                 all          base package for ALSA and OSS sound systems
ii  util-linux                                                  2.20.1-5.1ubuntu20.7                 amd64        Miscellaneous system utilities
```

---

### Post by Bashing-om on 2016-10-08
NotQuiteSU; Hummm ...

I had expected the package manager to install the xenial X stack, As it did not, we can direct the system to do so .. OR if ya rather - revert the system to the trusty (14.04) HWE .
My preference is to remain  on the trusty stack as I have no need of supporting any new hardware. On older hardware there is nothing to gain from enabling HWE, and can be trying to keep up with HWE - as you have found out.

It is your call as to what you want to do . Forward to xenial stack ; 
back to the trusty stack.
We can not stay here, as vivid (3.19.0-XXXX) is End_Of_Life and has no support .

[INDENT][INDENT]decisions decisions decisions
[/INDENT][/INDENT]

---

