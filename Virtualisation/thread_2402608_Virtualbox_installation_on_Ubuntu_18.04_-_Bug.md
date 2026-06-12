---
title: "Virtualbox installation on Ubuntu 18.04 - Bug"
date: 2018-10-02
forum: Virtualisation
---

### Post by straho on 2018-10-02
Hi!

After installing Virtualbox, in version 5.2.10-dfsg-6ubuntu18.04.1, and trying to start Windows 10 I get the error:

```
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/sbin/vboxconfig'

as root.
```


I've tried different things. This too:

```
sudo apt-get update
sudo apt-get install build-essential gcc make perl
```


Unfortunately, nothing helped. :/
I underline that I have Ubuntu version 18.04


I will be grateful for your help in this topic.

Thx

---

### Post by slickymaster on 2018-10-02
Thread moved to **Virtualisation** for a better fit

---

### Post by TheFu on 2018-10-02
Not to ask a stupid question, but did you run?  
```
sudo /sbin/vboxconfig
```
What was the result?

---

### Post by straho on 2018-10-03
I did it a few times. Each time the result is:

```
root@maciek-XPS-13-9360:/home/maciek# /sbin/vboxconfig
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Starting VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.


```

I'll just add that I did it with the command "sudo" and in root mode.

---

### Post by TheFu on 2018-10-03
And ... what does **dmesg** show that is relevant?

---

### Post by straho on 2018-10-05
Post to close.


Secure boot blocked virtalbox access to resources.

---

### Post by TheFu on 2018-10-05
If you want to close this, please use the "thread tools" button at the top and mark it as "SOLVED"
That helps the community, but posted the solution like you did is always VERY helpful too.

---

