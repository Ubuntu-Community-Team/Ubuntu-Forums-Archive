---
title: "VMWare Horizon on Raspberry Pi running Ubuntu 18.04"
date: 2020-05-12
forum: Virtualisation
---

### Post by piotrus22 on 2020-05-12
Hi everyone,

I hope you're all keeping well during these crazy times. I am a Linux noob but recently got a Pi again and started messing around. Once COVID hit I wanted to try to make a lightweight computer to log into my work virtual desktop with. I've had some experience with ubuntu years ago, but thus far have been unsuccessful in trying to get VMWare Horizon running on my Raspberry Pi 4 (4gb ram). I was able to INSTALL it successfully (per the screenshot below), but when I go to run vmware-viewer from the terminal, I get the message: /usr/bin/vmware-view: line 162: /usr/lib/vmware/view/bin/vmware-view: cannot execute binary file: Exec format error

I've spent hours searching, uninstalling, reinstalling, nuking entire ubuntu, crying about why it's not working, staying up to 5am determined to fix it and failed. So i turn to you - the unseen gods of the computing world. please help!!

I am running ubuntu 18.04 (per vmware docs it's the last supported version of horizon). I've tried both with Horizon Client 7 and currently trying with 5.4. No dice. thank you in advance!!

[ATTACH=CONFIG]285840[/ATTACH]

---

### Post by slickymaster on 2020-05-12
Thread moved to **Virtualisation** for a better fit

---

### Post by TheFu on 2020-05-13
rPi is ARM CPU.
It appears you've pulled the wrong program installer down based on the *Exec format error*
We cannot run a program compiled for a different CPU in the wrong CPU. The installed version of vmware-view seems to be compiled for the wrong CPU.

```
$ file  /usr/lib/vmware/view/bin/vmware-view
```
should return the type of CPU a program is compiled to run on.

---

### Post by piotrus22 on 2020-05-13
Thanks TheFu. Here's what's returned:

```
$ file /usr/lib/vmware/view/bin/vmware-view
/usr/lib/vmware/view/bin/vmware-view:  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically  linked, interpreter /lib64/l, for GNU/Linux 2.6.4, stripped
```

so this confirms rpi4 cannot run it right? as x86 is AMD and rPi is ARM?

---

### Post by TheFu on 2020-05-13
> **piotrus22 said:**
> Thanks TheFu. Here's what's returned:

```
$ file /usr/lib/vmware/view/bin/vmware-view
/usr/lib/vmware/view/bin/vmware-view:  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically  linked, interpreter /lib64/l, for GNU/Linux 2.6.4, stripped
```

so this confirms rpi4 cannot run it right? as x86 is AMD and rPi is ARM?

That is correct.  There might be a package with the correctly compiled-for-ARM available.  IDK. We dumped all VMware stuff in 2011.

---

