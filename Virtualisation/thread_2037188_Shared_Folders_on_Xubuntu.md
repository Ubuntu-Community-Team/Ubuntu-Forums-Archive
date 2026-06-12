---
title: "Shared Folders on Xubuntu"
date: 2012-08-03
forum: Virtualisation
---

### Post by linuxyogi on 2012-08-03
I have installed Xubuntu as a guest in virtualbox under PCBSD.
I have installed Guest additions on Xubuntu, shared a folder from PCBSD.

My question is how should I access the shared folders from Xubuntu ?

---

### Post by Toz on 2012-08-03
Have a look at virtualbox instructions for sharing and connecting to shared folders at: [http://www.virtualbox.org/manual/ch04.html#sharedfolders]("http://www.virtualbox.org/manual/ch04.html#sharedfolders").

Manually via:
```
mount -t vboxsf [-o OPTIONS] sharename mountpoint
```

Although I have never tried personally, there is information there on how to mount it automatically as well.

---

### Post by linuxyogi on 2012-08-03
```
$ sudo mount -t vboxsf Documents /home/tux/Documents/
/sbin/mount.vboxsf: mounting failed with the error: No such device

```

---

### Post by Toz on 2012-08-03
It works here for me, but I'm not using PCBSD. Might be an issue with PCBSD?

Is the vboxsf module loaded in Xubuntu?
```
lsmod | grep vbox
```

---

### Post by linuxyogi on 2012-08-03
> **Toz said:**
> It works here for me, but I'm not using PCBSD. Might be an issue with PCBSD?

Is the vboxsf module loaded in Xubuntu?
```
lsmod | grep vbox
```

 No the module is not loaded. I installed guest additions.

---

### Post by Toz on 2012-08-03
Were there any errors when you installed them? (I believe there is a log file created at /var/log/vboxadd-install.log). 

Make sure you've install build-essential and the kernel headers before you start. From a command line:
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

---

### Post by linuxyogi on 2012-08-03
```
$ cat /var/log/vboxadd-install.log 
/tmp/vbox.0/Makefile.include.header:94: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Creating user for the Guest Additions.
Creating udev rule for the Guest Additions kernel module.

```

Installing......

---

### Post by linuxyogi on 2012-08-03
After installing  build-essential and the kernel headers installed vbox guest additions again & now it mounts.

Thanks.

---

