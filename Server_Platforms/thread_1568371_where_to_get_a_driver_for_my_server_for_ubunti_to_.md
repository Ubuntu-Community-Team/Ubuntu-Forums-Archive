---
title: "where to get a driver for my server for ubunti to see my hard drive."
date: 2010-09-05
forum: Server Platforms
---

### Post by hockey97 on 2010-09-05
Hi, I just used the alien tool for ubuntu. I downloaded a redhat .rpm file this file is a driver for an sas controller on the server board. I currently can't get a sas hard drive to work. I want to use ubuntu on my server but there isn't a device driver for it. No driver in .deb. So I used alien to convert a .rpm to a .deb. I am lost right now on how to install this. My bios sees the hard drive but when I try to install the OS it would say no hard drive found please select a hard drive controller driver. In the list I couldn't find the one that works on mine. So I hit the button that said to load one from a disk. So It started to look for a flppy disk. Yet I have no floppy drive just a dvd-rom drive.

any ideas?

---

### Post by scorp123 on 2010-09-05
Are you using Ubuntu Server? I have lots of SAS stuff in my servers but never needed to download external drivers.

Which leads us to the next topic: In Linux drivers highly depend on the Linux kernel. So even if I told you how to install the converted package it would probably not work as Ubuntu most likely is at a different kernel version than the Red Hat distro that *.rpm package was created for.

Can you please provide the following output:
```
sudo lspci
```

And then this one:
```
sudo lsdev
```

It could be that these tools are not installed yet on your system. If that is the case the command line will complain and tell you which packages you need to install to get those programs. Please install them if they are missing (the command line will tell you the name of the packages).

---

