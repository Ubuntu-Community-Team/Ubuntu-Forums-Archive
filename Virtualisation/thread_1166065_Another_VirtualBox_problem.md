---
title: "Another VirtualBox problem"
date: 2009-05-21
forum: Virtualisation
---

### Post by iAndrew on 2009-05-21
Yes, I've done research on this. I still have a different error, and so far none of my searches have gave me any help.

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

Is the error.

My kernel is : 2.6.24-24-generic

I can start the /etc/init.d/vboxdrv without any problems, and yes I have restarted my computer.

Running the open source edition off the repositories.

/edit

I browsed through this forum found a guide:
[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

It's for 8.04 users who want to install it and have trouble.

I have no idea why it isn't stickied, it's definitely useful.

---

### Post by jkarcz on 2009-05-22
Does the user attempting to start vbox or vboxdrv have admin rights?  ie. the first user account setup when installing Vbox?

---

