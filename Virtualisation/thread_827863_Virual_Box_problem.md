---
title: "Virual Box problem"
date: 2008-06-13
forum: Virtualisation
---

### Post by ^^viktor^^ on 2008-06-13
I`ve just installed  Virtual Box and when I run it, it gives me this:
> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

What is the problem. I`m completely new to this stuff so any help would be appreciated.

---

### Post by techstop on 2008-06-13
This thread tells you all about installing VirtualBox;

[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

In particular, you need to add the user you are running VirtualBox as to the vboxusers group by running the following in the console;

```
sudo usermod -G vboxusers -a username
```

...where username is your username obviously. 

That thread will also tell you how to enable USB in the proprietary version of VirtualBox.

---

