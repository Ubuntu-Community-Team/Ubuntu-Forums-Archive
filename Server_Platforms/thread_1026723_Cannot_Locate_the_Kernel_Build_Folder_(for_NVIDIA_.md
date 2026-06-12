---
title: "Cannot Locate the Kernel Build Folder (for NVIDIA driver install)"
date: 2008-12-31
forum: Server Platforms
---

### Post by california-ken on 2008-12-31
I am a new Linux user and am setting up a home Ubuntu Server system for learning/training purposes.

I am having great difficulty installing a NVIDIA driver package with the server kernel.  My Ubuntu searching has uncovered numerous references to problems with installing a NVIDIA ¨run¨ package related to getting a precompiled kernel interface for the installation process.

Documentation for the NVIDIA package (NVIDIA-Linux-x86-177.82-pkg1.run"says it needs a ¨build¨ folder in /lib/modules/{kernel name}.  In my /lib/modules directory there is a 2.6.25-2.386 folder that contains only a ¨build¨ folder and a 2.6.27-7-server folder that contains no ¨build¨ folder.

Where can I find the 2.6.27-7-server build folder or is there a way to create one that will work with the NVIDIA driver ¨run¨ file?

Thanks, I really need some help with this one.

Ken

---

### Post by cdenley on 2008-12-31
Why are you trying to compile the driver yourself. Ubuntu has 4 different versions of nvidia's driver in the repos, and the open-source driver. Doesn't one of those work for you? If you install nvidia's driver from the repos, it won't work right unless you install the restricted modules which is a little tricky with the server kernel. If you want more help, provide more information such as the output of this command, whether you really need a server kernel with the nvidia driver.
```

uname -r

```

To install the 177 nvidia driver
```

sudo apt-get install nvidia-glx-177

```

To install the restricted modules for the server kernel you are currently running (if you are running a server kernel)
```

sudo apt-get install linux-restricted-modules-`uname -r`

```

---

