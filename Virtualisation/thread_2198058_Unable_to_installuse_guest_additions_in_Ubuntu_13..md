---
title: "Unable to install/use guest additions in Ubuntu 13.10!"
date: 2014-01-06
forum: Virtualisation
---

### Post by 6tr6tr on 2014-01-06
I'm running Ubuntu 13.10 in VirtualBox and I'm trying to install guest additions but it never works. I'm unable to resize the window or copy-paste with the host OS. I tried installing two different ways:

1. Via the VirtualBox "install guest additions" which gives me a CD to run

2. sudo apt-get install virtualbox-guest-additions-iso


The "sudo apt-get" appeared to run perfectly but after restarting, I'm still unable to resize the window. What do I need to do?

---

### Post by QIII on 2014-01-06
Hello!

Pardon the obvious question, but you are attempting to install the guest additions in the guest OS, correct?

---

### Post by 6tr6tr on 2014-01-06
> **QIII said:**
> Hello!

Pardon the obvious question, but you are attempting to install the guest additions in the guest OS, correct?

Correct. The guest OS is Ubuntu 13.10, the host is opensuse (which doesn't have apt-get).

On Ubuntu, it now says that guest additions is installed if I try to install it, but none of the features are working! Can't copy-paste or resize.

---

### Post by 6tr6tr on 2014-01-06
If I try to install from the "CD" instead of from repositories, I get:

> Verifying archive integrity... All good.
Uncompressing VirtualBox 4.1.12 Guest Additions for Linux.........
VirtualBox Guest Additions installer
Removing installed version 4.1.12 of VirtualBox Guest Additions...
Removing existing VirtualBox DKMS kernel modules ...done.
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules
The headers for the current running kernel were not found. If the following
module compilation fails then this could be the reason.

Building the main Guest Additions module ...fail!
(Look at /var/log/vboxadd-install.log to find out what went wrong)
Doing non-kernel setup of the Guest Additions ...done.
Installing the Window System drivers
Warning: unknown version of the X Window System installed.  Not installing
X Window System drivers.
Installing modules ...done.
Installing graphics libraries and desktop services components ...done.



---

### Post by QIII on 2014-01-06
I would first try to install the missing headers and then reinstall the guest additions.

```
sudo apt-get install linux-headers-generic
```

You may also need to install build-essential and dkms

```
sudo apt-get install build-essentiall dkms
```

If you end up needing to specifiy the kernel version (linux-headers-someversion), you can find our your kernel version using 

```
uname -r
```

---

### Post by 6tr6tr on 2014-01-07
> **QIII said:**
> I would first try to install the missing headers and then reinstall the guest additions.

```
sudo apt-get install linux-headers-generic
```

You may also need to install build-essential and dkms

```
sudo apt-get install build-essentiall dkms
```

If you end up needing to specifiy the kernel version (linux-headers-someversion), you can find our your kernel version using 

```
uname -r
```

Thank you, but I just ran those installs (they went successfully) AND I installed the headers with the uname -r and I still get the same error! "The headers for the current running kernel were not found."

But the headers ARE installed!

> dpkg --get-selections | grep linux-headers
linux-headers-3.11.0-12                install
linux-headers-3.11.0-12-generic            install
linux-headers-3.11.0-15                install
linux-headers-3.11.0-15-generic            install
linux-headers-generic                install


Why can't it find the headers?

---

### Post by QIII on 2014-01-07
OK.  Navigate to the VBOXADDITIONS "CD".  Do you see a file VBoxLinuxAdditions.run?  Is that the file you are using to install the guest additions?

---

### Post by 6tr6tr on 2014-01-07
> **QIII said:**
> OK.  Navigate to the VBOXADDITIONS "CD".  Do you see a file VBoxLinuxAdditions.run?  Is that the file you are using to install the guest additions?

I finally solved it! I saw another post on the web where someone had a similar problem. The virtualbox-additions package and CD are apparently missing some pieces, so this solves it:

```
sudo apt-get install virtualbox-guest-dkms


```

After I ran that and restarted, I am now able to do copy-paste and the resolution is higher!

---

### Post by QIII on 2014-01-07
Excellent!  I'd never have guessed.

Please mark this thread solved so others can find it.

Have fun with it now!

---

