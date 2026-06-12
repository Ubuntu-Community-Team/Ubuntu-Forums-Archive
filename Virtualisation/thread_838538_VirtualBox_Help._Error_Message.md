---
title: "VirtualBox Help. Error Message"
date: 2008-06-23
forum: Virtualisation
---

### Post by Landscapeman on 2008-06-23
I have been trying to use VirtualBox OSE with Ubuntu 8.04. I keep getting this error message:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I have downloaded the module for my kernel and the generic module also but yet to have any luck. Any ideas that would help me? Thank You.

---

### Post by forestpixie on 2008-06-23
Add yourself to the vbox usergroup - this is as good as any although there is a cli way but I can never remeber it

[http://ubuntuforums.org/showpost.php?p=4415865&postcount=10](http://ubuntuforums.org/showpost.php?p=4415865&postcount=10)

---

### Post by Landscapeman on 2008-06-23
I have done this but it did the same thing. I have reinstalled VirtualBox from the site. Any Ideas?

---

### Post by forestpixie on 2008-06-23
If you do this in a terminal, what is the return

```
grep vbox /etc/group
```

If it shows that you are in the user group try restarting the vbox 

```
sudo /etc/init.d/vboxdrv restart
```

---

### Post by Landscapeman on 2008-06-23
vboxusers:x:124:landscapeman,root

---

### Post by Landscapeman on 2008-06-23
vboxusers_:x:_124:landscapeman,root

---

### Post by forestpixie on 2008-06-23
and after a restart?

---

### Post by Landscapeman on 2008-06-23
It now boots but the give me:
No bootable medium found! System Halted.

---

### Post by Landscapeman on 2008-06-23
Along with this message:

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x00004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {f95c0793-7737-49a1-85d9-6da81097173b}

---

### Post by forestpixie on 2008-06-23
If it has started and you've not installed anything yet then

> No bootable medium found! System Halted.

would be what I expected to see

You need to set the vm to boot from cd first in it's settings - they are all pretty self explanatory - and put a cd in the drive so that it can install from it

The second error relates to it not having access to USB yet - there is a thread somewhere which goes through that - search for it in the virtualisation forum, it is there - that's where I found it.

---

### Post by Landscapeman on 2008-06-23
Thanks for the Help.

---

### Post by forestpixie on 2008-06-23
You're welcome - hope all goes ok, can you mark thread solved if it is please :)

---

### Post by Landscapeman on 2008-06-23
I still cant figure out how to install windows. I still keep getting the error message. I made sure that it boots from the cd yet the nothing.

---

### Post by Raptor354 on 2008-07-15
Just a thought.  Are you running 64-bit Ubuntu?

Raptor354

---

