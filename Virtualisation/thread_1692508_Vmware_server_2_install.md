---
title: "Vmware server 2 install"
date: 2011-02-21
forum: Virtualisation
---

### Post by nabberuk on 2011-02-21
Hey,

This is really annoying me now and i don't know if it's something simple i'm overlooking!!

I have a clean install of Ubuntu server 10.10 (64 bit), I've downloaded the latest version of vmware server 2 (.gz version). The first part of the install went fine, but i'm not running into issues with vmware-config.pl.

The error i'm getting is;

```
The directory of kernel headers (@@VMWARE@@ UTS_RELEASE) does not match your running kernel (version 2.6.35-25-server). Even if the module were to compile successfully, it would not load into the running kernel.
```

No when i type uname -r i get;

```
2.6.35-25-server
```

In my /usr/src/ folder i have;

```
linux-headers-2.6.35-25-server
```

I supply the following answer to vmware-config.pl;

```
/usr/src/linux-headers-2.6.35-25-server/include
```

but still get this stupid message!!!

Has anyone any idea's?

Thanks,
Nathan

---

### Post by nabberuk on 2011-02-21
UPDATE:

I've added the following line to /usr/src/linux-headers-2.6.35-25-server/include/linux/version.h.

```
#define UTS_RELEASE &#8220;2.6.35-25-server&#8243;
```

The new error message is...;

```
The path "/usr/src/linux-headers-2.6.35-25-25-server/include" is a kernel header file directory, but it does not contain the file "linux/autoconf.h" as expected. This can happen if the kernel has never been built, or if you have invoked the "make mrproper" command in your kernel directory. In any case, you may want to rebuild your kernel.
```

I've checked in the folder and sure enough there is no autoconf.h. any ideas?

thanks,
Nathan

---

### Post by nabberuk on 2011-02-21
Well, it looks like the install from vmware is broken for newer kernels. Thanks for putting this in a easy place to find vmware!!

If anyone needs to install it, theres a nice guide here using a 3rd party installer.

[http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-10.10-kernel-2.6.35](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-10.10-kernel-2.6.35)

Nathan

---

### Post by HermanAB on 2011-02-22
Howdy,

VMware Server 2 is a total POS and it is now abandonware.

Rather use Vmware Player or Virtualbox.

---

### Post by Ondalf on 2011-02-26
I'm running that Server 2 in Ubuntu 10.10 but encountered massive loads with IO because of bugging kernel feature so I recommend to upgrade into daily current mainline kernel. 2.6.35-2.6.37 suffers from this bug. I'm running 2.6.38-999 (built 02/24/2011) and that doesn't fail with io that much anymore. More about this problematic way in [VMware communities]("http://communities.vmware.com/thread/304233?tstart=0").

---

