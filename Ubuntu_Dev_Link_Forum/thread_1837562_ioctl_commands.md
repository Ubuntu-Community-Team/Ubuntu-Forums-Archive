---
title: "ioctl commands"
date: 2011-09-02
forum: Ubuntu Dev Link Forum
---

### Post by grj017 on 2011-09-02
Hi,

Generally we use any one of the follwing macros to define any ioctl command. 
_IO(): For a command that has no arguement 
_IOR(): For copying data to user space
_IOW(): For copying data from user space 
_IORW(): For copying data from user to kernel and kernel to user
But in my driver, I have used _IO() macro to define all my ioctl commands and I have used an arguemnet and I do copy arguement data from user to kernel and kernel to user. My driver is working fine. I want to know, what is fundamental difference among all above macros?

Thanks and best regards,
Ganga

---

### Post by Iowan on 2011-09-02
Closed - duplicate:
[http://ubuntuforums.org/showthread.php?t=1837564]("http://ubuntuforums.org/showthread.php?t=1837564")

From the Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.

---

