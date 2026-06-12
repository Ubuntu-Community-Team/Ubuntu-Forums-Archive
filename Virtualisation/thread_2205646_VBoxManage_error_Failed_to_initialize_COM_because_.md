---
title: "VBoxManage error: Failed to initialize COM because the global settings directory"
date: 2014-02-15
forum: Virtualisation
---

### Post by fatih3 on 2014-02-15
Hi,

I am running VirtualBox on my Ubuntu Server with phpVirtualBox until today without any Problem. I set up Windows XP and 10GB VHD size is too low.

So I try to modify the size of the HDD with the command line

```
VBoxManage modifyhd Windows XP.vdh –-resize 30000
```

The result is any Error which I can not solve
```
VBoxManage: error: Failed to initialize COM because the global settings directory '/home/fatih/.config/VirtualBox' is not accessible!
```

The Folder "fatih" does not have a file or folder called .config even not Virtualbox

Any idea what am I doing wrong? 

Regards

---

### Post by ian-weisser on 2014-02-15
Does phpVirtualBox run as another user? Run the VBoxManage command as that user.

---

### Post by fatih3 on 2014-02-15
Thanks.. Did it as root and it worked but resizing VHD damaged the File :(

---

