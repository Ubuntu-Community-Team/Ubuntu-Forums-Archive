---
title: "Kprobe installation on Ubuntu"
date: 2009-02-12
forum: Ubuntu Dev Link Forum
---

### Post by mamehmood on 2009-02-12
Hi every One, 

I need to install Kprobes. I have Ubuntu 8 installed on my system and i have kprobes-2.6.9-final.tar.gz. Can any body explain me how to isntall Kprobe? On IBM web site ([http://www.ibm.com/developerworks/library/l-kprobes.html](http://www.ibm.com/developerworks/library/l-kprobes.html)) follwoing commands are given 

$tar -xvzf kprobes-2.6.8-rc1.tar.gz
$cd /usr/src/linux-2.6.8-rc1
$patch -p1 < ../kprobes-2.6.8-rc1-base.patch 

but there is no such folder like linux-2.6.8-rc1 instead i have 
linux-headers-2.6.24-19          linux-headers-2.6.24-22-generic
linux-headers-2.6.24-19-generic  linux-headers-2.6.24-23
linux-headers-2.6.24-22          linux-headers-2.6.24-23-generic
 can any body tell me how to install Kprobe ? I shall be very thankful

Regards

---

### Post by bhundven on 2009-04-15
If your kernel is >= 2.6.9, then kprobes should already be apart of the kernel. No patch needed!

You should just need to rebuild your kernel with the following options enabled:
```

CONFIG_KPROBES=y
CONFIG_RELAY=y
CONFIG_DEBUG_INFO=y

```

I recommend following the guide:
[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

---

