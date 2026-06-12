---
title: "Virtualbox - kernel driver no installed"
date: 2014-12-10
forum: Virtualisation
---

### Post by ktz84 on 2014-12-10
I have the latest version of virtualbox installed from the virtualbox ppa which is version: 4.3.20 however everytime I restart a virtual machine I get a message to say:

```
Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]


as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

I try to install virtualbox-dkms as suggested and I get the following message: 

```
The following packages have unmet dependencies. virtualbox-dkms : Depends: virtualbox (>= 4.3.18-dfsg-1)
E: Unable to correct problems, you have held broken packages.

```

Last time I checked 20 was higher than 18 so what gives?

If I run the vboxdrv setup then it will run however next time restart I have to do that whole process again.

Here's the output:

```
Stopping VirtualBox kernel modules ...done.Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...done.

```

That seems to suggest not only that DKMS is installed but it managed to configure it as there is done beside it so a little confused as to why it's moaning everytime I restart.

---

### Post by slickymaster on 2014-12-11
Can you please try this:```
sudo apt-get install linux-headers-generic build-essential dkms
sudo apt-get remove --purge virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

---

### Post by ktz84 on 2014-12-11
Thanks slickymaster I've tried the above and the interesting point is that when I try to purge virtualbox-dkms it says it's not installed:

```
Package 'virtualbox-dkms' is not installed, so not removed
```

and then when I try to install I get the following familiar message:

```
sudo apt-get install virtualbox-dkmsReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 virtualbox-dkms : Depends: virtualbox (>= 4.3.18-dfsg-1)
E: Unable to correct problems, you have held broken packages.
```

Any ideas how to get beyond that?

Thanks

---

### Post by slickymaster on 2014-12-12
Can you please post back the output you get from```
apt-cache policy virtualbox
```

---

### Post by ktz84 on 2014-12-12
Thanks again slickymaster. Doing that showed me the problem. I hadn't installed it through apt instead I'd forgotten I'd installed from the deb file on virtualbox site. The ppa seems to lag the latest version as when installed via ppa I'm on 4.3.18 and virtualbox-dkms was installed automatically as part of that. I've restarted and no moaning from virtualbox when I try to start my vms.

---

### Post by slickymaster on 2014-12-15
You're welcome, I'm glad you got it working. Happy *buntuing.

---

### Post by pete37 on 2015-03-02
I have the identical problem as you, but I don't understand your fix; can you explain it in laymans terms please.

---

### Post by pete37 on 2015-03-02
am getting an error code (1)

---

### Post by jdeca57 on 2015-03-02
Did you use the software from Oracle or the version of Ubuntu? And what version of Virtualbox are you using because at this point it's already 4.3.22. Did you have that problem with 4.3.18/20? By the way, is your OS version 14.10?

---

### Post by pete37 on 2015-03-02
Ubuntu is 14.10 and the VB we installed  is 4.3.24 but somehow it is now 4.3.18.  My friend installed it and I believe he got it from Oracle

---

### Post by ktz84 on 2015-03-02
The problem with installing directly the .deb from Oracle is that when there is a kernel change virtualbox then stops working.

What worked for me was to remove the .deb installation of virtualbox.

sudo apt-get remove virtualbox

I then went to Oracle's website and followed the instructions for Debian based linux distros.

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Even though I'm on 14.10 only up to 14.04 (Trusty) is listed for ppas so I just went with that as it is the latest and I've had no issues.

Hope that help resolve your issues.

---

### Post by jdeca57 on 2015-03-03
> **pete37 said:**
> Ubuntu is 14.10 and the VB we installed  is 4.3.24 but somehow it is now 4.3.18.  My friend installed it and I believe he got it from Oracle

Sorry, I only got the update to 4.3.24 this morning. I'm using Ubuntu 14.04 and added the line with trusty (as in the Virtualbox website) to the /etc/apt/sources.list and since then I always run the latest Virtualbox. (well, one day late) But to be honest, the changes between subversions as in [https://www.virtualbox.org/wiki/Changelog](https://www.virtualbox.org/wiki/Changelog) are hardly noticeable and for non-LTS I'd stick with the version of Ubuntu. Unless you have a concrete issue, of course.

---

