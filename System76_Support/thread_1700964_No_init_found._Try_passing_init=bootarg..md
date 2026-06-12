---
title: "No init found. Try passing init=bootarg."
date: 2011-03-05
forum: System76 Support
---

### Post by jr223 on 2011-03-05
Please assist!

My System76 Ratel will no longer boot into ubuntu.
I think this was do to an update that was run yesterday?
Anyway on to the problem.

When I boot up my Ratel, it now takes a lot longer to see the ubuntu boot logo with the dots.
After a rather long time it goes into the Busy Box command line with the following message.

"No initfound. Try passing init=bootarg.
Busy Box v1.15.3 (ubuntu 1.1.15.3-1ubuntu5) builinsehll"
There was no problem until around yesterday I think when there was a big update through ubuntu.
Please help to fix.

Thanks
Jeff

---

### Post by isantop on 2011-03-07
I think you sent an email in too. We can continue either there or here, whichever you'd like.

---

### Post by jr223 on 2011-03-08
Yes thanks I did :)

I just wanted to say that your response to my issue was extremly fast and very satisfying.

Thanks
Jeff

---

### Post by ein.selbst on 2011-04-07
Hi,

would you be so kind and let others, like me, with the same problem, know something about the magic you had done to solve that problem?

After updating 64bit natty, my Lenovo U160 always boots until BusyBox came up with the following:

```
usb 2-1.5: new high speed USB device using ehci-hcd and address 3
No init found. Try passing init= bootarg.

BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```In case it makes a difference: I am using a SSD and btrfs. When I try to "exit" the busybox, I always get a Kernelpanic.

Any help is appreciated.
Thanks,
Sly

---

### Post by isantop on 2011-04-07
I'm not entirely sure for your system, since it's a Lenovo, and there may be another issue. It sounds like a botched install to me, so you might try reinstalling. Make sure you use a different CD than you used the first time.

---

### Post by ein.selbst on 2011-04-07
Yes, a reinstall would be the last option available. I would use the latest daily build. Because I haven't had internet for some time I had a +400MB update on the system before the problem occured.

However, I would have liked to know, how you solved the problem on the 76 machine.

Anyway, thank you for your quick answer.

Sly

---

### Post by isantop on 2011-04-07
We tried to reinstall it, but he had a bad hard disk.

---

### Post by aasami on 2011-04-10
This might be due to installing Natty on btrfs filesystem.
I have the same problem.
I installed Natty on btrfs without major problems and used it for more than a week.
Yesterday I have installed updates (as everyday) and on reboot, I was dropped into busybox. It was about 200MB updates with a new kernel update. I haven't found a solution (nor workaroud) for this issue yet.
Althought found this bug logged at launchpad.
Have a look and mark your self affected if applicable.
[https://bugs.launchpad.net/ubuntu/+bug/749448](https://bugs.launchpad.net/ubuntu/+bug/749448)

---

### Post by jr223 on 2011-04-27
> **ein.selbst said:**
> Hi,

would you be so kind and let others, like me, with the same problem, know something about the magic you had done to solve that problem?

After updating 64bit natty, my Lenovo U160 always boots until BusyBox came up with the following:

```
usb 2-1.5: new high speed USB device using ehci-hcd and address 3
No init found. Try passing init= bootarg.

BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```In case it makes a difference: I am using a SSD and btrfs. When I try to "exit" the busybox, I always get a Kernelpanic.

Any help is appreciated.
Thanks,
Sly

Hi 
In my case, the reason for the failed init was a bad and dying hard drive.
The best advice I can give is make sure to have the correct version of Ubuntu64 bit vrs. 32 on DVD.
Boot with this.
Please note I'm doing the below from memory so it is as close to what I can remeber as possible as I'm not infront of my Ratel.
When booting select -> boot from DVD
Once booted you should be able to select from -> Admin -> Tools ->Disk Tool -> Select -> Disk properties.
This will show the health of the disk.
In my case it was failing hence the init errors.

---

