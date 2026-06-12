---
title: "VMWare 8 on Ubuntu 11.10: &quot; Unable to build kernel module &quot;-ERROR"
date: 2012-04-07
forum: Virtualisation
---

### Post by mixim on 2012-04-07
Hello guys,

Downloaded the latest VMWare workstation from their homepage, executed and installed it.

On first run it asked me for installing the gnu c compiler, which i did.

When i try to run vmware again, i met this error, and although i found other issues related to this, none of the solutions seemed to be for ubuntu 11.10 with kernel 3.0.0-17.

I am running an Ubuntu Minimal + LXDE setup, so I am missing several of packages that are standard in regular 11.10 install. Might this affect it?

Attached a screenshot, also the log output:

```
2012-04-08T00:29:19.603+01:00| vthread-3| I120: Log for VMware Workstation pid=4923 version=8.0.2 build=build-591240 option=Release
2012-04-08T00:29:19.603+01:00| vthread-3| I120: The process is 64-bit.
2012-04-08T00:29:19.603+01:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2012-04-08T00:29:19.603+01:00| vthread-3| I120: Host is Linux 3.0.0-17-generic Ubuntu 11.10
2012-04-08T00:29:19.603+01:00| vthread-3| I120: Msg_Reset:
2012-04-08T00:29:19.603+01:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2012-04-08T00:29:19.603+01:00| vthread-3| I120: ----------------------------------------
2012-04-08T00:29:19.603+01:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2012-04-08T00:29:19.603+01:00| vthread-3| I120: Msg_Reset:
2012-04-08T00:29:19.603+01:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2012-04-08T00:29:19.603+01:00| vthread-3| I120: ----------------------------------------
2012-04-08T00:29:19.603+01:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2012-04-08T00:29:19.603+01:00| vthread-3| I120: Msg_Reset:
2012-04-08T00:29:19.603+01:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2012-04-08T00:29:19.603+01:00| vthread-3| I120: ----------------------------------------
2012-04-08T00:29:19.603+01:00| vthread-3| I120: PREF Failed to load user preferences.
2012-04-08T00:29:19.603+01:00| vthread-3| W110: Logging to /tmp/vmware-root/modconfig-4923.log
2012-04-08T00:29:19.665+01:00| vthread-3| I120: modconf query interface initialized
2012-04-08T00:29:19.666+01:00| vthread-3| I120: modconf library initialized
2012-04-08T00:29:19.681+01:00| vthread-3| I120: Your GCC version: 4.6
2012-04-08T00:29:19.682+01:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.0.0-17-generic
2012-04-08T00:29:19.682+01:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-04-08T00:29:19.682+01:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-04-08T00:29:19.683+01:00| vthread-3| I120: Validating path /lib/modules/3.0.0-17-generic/build/include for kernel release 3.0.0-17-generic
2012-04-08T00:29:19.684+01:00| vthread-3| I120: Your GCC version: 4.6
2012-04-08T00:29:19.688+01:00| vthread-3| I120: Your GCC version: 4.6
2012-04-08T00:29:19.694+01:00| vthread-3| I120: Header path /lib/modules/3.0.0-17-generic/build/include for kernel release 3.0.0-17-generic is valid.
2012-04-08T00:29:19.694+01:00| vthread-3| I120: Validating path /lib/modules/3.0.0-17-generic/build/include for kernel release 3.0.0-17-generic
2012-04-08T00:29:19.695+01:00| vthread-3| I120: Your GCC version: 4.6
2012-04-08T00:29:19.700+01:00| vthread-3| I120: Your GCC version: 4.6
2012-04-08T00:29:19.706+01:00| vthread-3| I120: Header path /lib/modules/3.0.0-17-generic/build/include for kernel release 3.0.0-17-generic is valid.
2012-04-08T00:29:19.716+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.718+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.719+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.720+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.721+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.730+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.732+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.733+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.734+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.735+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.736+01:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.0.0-17-generic
2012-04-08T00:29:19.736+01:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-04-08T00:29:19.736+01:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-04-08T00:29:19.737+01:00| vthread-3| I120: Validating path /lib/modules/3.0.0-17-generic/build/include for kernel release 3.0.0-17-generic
2012-04-08T00:29:19.738+01:00| vthread-3| I120: Your GCC version: 4.6
2012-04-08T00:29:19.742+01:00| vthread-3| I120: Your GCC version: 4.6
2012-04-08T00:29:19.748+01:00| vthread-3| I120: Header path /lib/modules/3.0.0-17-generic/build/include for kernel release 3.0.0-17-generic is valid.
2012-04-08T00:29:19.758+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.759+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.761+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.762+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.763+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.764+01:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.0.0-17-generic
2012-04-08T00:29:19.764+01:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-04-08T00:29:19.764+01:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-04-08T00:29:19.764+01:00| vthread-3| I120: Validating path /lib/modules/3.0.0-17-generic/build/include for kernel release 3.0.0-17-generic
2012-04-08T00:29:19.765+01:00| vthread-3| I120: Your GCC version: 4.6
2012-04-08T00:29:19.770+01:00| vthread-3| I120: Your GCC version: 4.6
2012-04-08T00:29:19.777+01:00| vthread-3| I120: Header path /lib/modules/3.0.0-17-generic/build/include for kernel release 3.0.0-17-generic is valid.
2012-04-08T00:29:19.794+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.795+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.796+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.797+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.799+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.953+01:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.0.0-17-generic.
2012-04-08T00:29:19.953+01:00| vthread-3| I120: Can't get required utilities make, tar, echo, grep, rmmod, insmod
2012-04-08T00:29:19.953+01:00| vthread-3| W110: Could not prepare build system.

```

Grateful for any unput, thanks!

**EDIT: SOLVED BY DEDOIMEDO, thank you!**

---

### Post by Dedoimedo on 2012-04-08
What you want to do is install:

```
sudo apt-get build-essential
```

And then try again.

Cheers,
Dedoimedo

---

### Post by mixim on 2012-04-08
> **Dedoimedo said:**
> What you want to do is install:

```
sudo apt-get build-essential
```

And then try again.

Cheers,
Dedoimedo

That didn't work at first, but then i saw that i think you missed install:

```
sudo apt-get install build-essential
```

And that worked like a charm next time i fired up VMWare. Btw, how did you know this package was missing?

After start i faced another issue regarding the registration process, but that will be placed [here in another thread]("http://ubuntuforums.org/showthread.php?p=11828373#post11828373").

**ANYWAYS, THANK YOU DEDOIMEDO!**

---

### Post by Dedoimedo on 2012-04-08
Yup I missed install ... :) but I'm glad you figured it out.
Actually the missing stuff is written in your error log.

Moreover, once you do this a couple a thousand times for various software, kernel modules, kernel, and whatnot, it becomes kind of trivial.

Cheers,
Dedoimedo

---

### Post by dcstar on 2012-04-09
> **mixim said:**
> That didn't work at first, but then i saw that i think you missed install:

```
sudo apt-get install build-essential
```
.........

Which is people should just be told to use the GUI tools to install packages, instead of the command line which has these problems.

---

### Post by mixim on 2012-04-09
> **dcstar said:**
> Which is people should just be told to use the GUI tools to install packages, instead of the command line which has these problems.

Well, i both agree and disagree with you. For complete novices and switchers this could be true.

However in my case for example, i do not even have e GUI-tool installed since im using a clean LXDE install on minimal ubuntu (No Synaptic etc, mentioned before). For not novices it will be more smooth to give the command as it can actually lessen confusion due to misinterpretations or differences due to unsimilar distributions.

---

### Post by hecoo on 2012-10-28
anybody can help ? please , i google a few days and nothing ,if you need some more informatio i'm here everyday i will give it i need to configure this *** soon as posibly ..

---

