---
title: "VMWare Shared Folder not working"
date: 2014-02-06
forum: Virtualisation
---

### Post by tobey2 on 2014-02-06
Hi there,

I'm running ubuntu 13.10 VMWare Workstation 10 on my Win 8.1 host.
Now I'd like to share some files to ubuntu - so I read up on sharing folders.
Problem is: the folder cannot be mounted, nor is it found in ubuntu.
I did mostly all things I found on the internet considering this problem, but it doesn't help me.

```
sudo mount -t vmhgfs .host:/ /mnt/hgfs
```
will give me:
 ```
Error: cannot mount filesystem: No such device
```

I reinstalled vmwaretools about 5 times and even installed the openvmware tools.
As I am pretty new to linux, I cannot find the mistake.
However I guess it has something to do with vmware tools, because my VM looks like this when I do not enter fullscreen (see attached image).
Any help is greatly appreciated.

---

### Post by brokenhachi on 2014-02-08
how did you install the vmware tools? did you install all of the modules? ```
lsmod | grep -i vm
```

---

