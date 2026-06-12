---
title: "mount: unknown filesystem type 'iso9660' on 9.10 JeOS"
date: 2009-11-04
forum: Server Platforms
---

### Post by AlexLewisLnk on 2009-11-04
I am unable to mount a CD after installing 9.10 Server JeOS. The error I get is 

mount: unknown filesystem type 'iso9660'

Installing the normal server works just fine. I have gone through the package list and installed any missing packages the seem to be related to iso9660 but no luck. It appears to be a kernel issue because when I install the linux-image-server kernel it works. Is there another way to make the CD drive accessible without installing the heavier kernel?

---

### Post by realflash on 2009-11-19
If you check the configuration of the kernel running in 9.10 JeOS, the relevant functionality has been configured to be a module:

```

# cat /boot/config-2.6.31-14-generic-pae | grep -i iso9660
CONFIG_ISO9660_FS=m

```

'n' would be "don't provide this functionality at all", 'y' would be "compile this functionality into the kernel", and 'm' is "compile this as a module to be loaded on demand". Since that is what was chosen we need to make that the relevant module is on the hard drive.

In this instance the iso9660 module is provided by the file */lib/modules/2.6.31-14-generic/kernel/fs/isofs/isofs.ko* (as determined by some googling). On my non-JeOS 9.10 machine I found out what package that file is in:

```

# dpkg -S /lib/modules/2.6.31-14-generic/kernel/fs/isofs/isofs.ko
linux-image-2.6.31-14-generic: /lib/modules/2.6.31-14-generic/kernel/fs/isofs/isofs.ko

```

So yes indeed, the required module is provided by linux-image-2.6.41-14-generic, and by -server according to your testing. What do we have on JeOS?

```

# dpkg -l | grep linux-image
ii   linux-image-2.6.31-14-virtual    2.6.31-14.48  <snip/>

```

Hmm. So we have a lightweight kernel that doesn't include some of the modules it seems, and I would say the cut has gone a bit too far. Question is, what needs to be copied over to make it work? I have tried copying over that file and running insmod on it, but that doesn't work:

```

# insmod ./isofs.ko
insmod: error inserting './isofs.ko': -1 Invalid module format

```

I don't really know enough about it to take it further. Your workaround of upgrading to a different kernel with the module seems to be the right thing to do right now. My free memory actually went up from 103 to 105Mb after switching kernels, so not sure how much heavier it is. This is how I switched kernels:

```

# apt-get install linux-image-server linux-image-generic-pae linux-image-2.6.31-14-generic-pae
# reboot

```

Although I have acutally ended up on the generic kernel rather than the server one, so I haven't done something right.

---

