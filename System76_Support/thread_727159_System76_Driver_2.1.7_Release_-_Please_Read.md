---
title: "System76 Driver 2.1.7 Release - Please Read"
date: 2008-03-17
forum: System76 Support
---

### Post by crichell on 2008-03-17
Hey Everyone - System76 Driver 2.1.7 has just been sent to the repos and includes some bug fixes and support for new System76 machines that have been released.  All daru2 customers will want to install the driver update.

System > Administration > System76 Driver.  Click the Install Tab > Click Install.

Check below for other fixes that may apply to your system.

Also import our public GPG key so apt won't complain about un-authenticated packages.

Run:

```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get upgrade
```

And the changelog....

Version 2.1.7

1.) Add kernel line parameter ec_intr=0 to menu.lst on daru2 under
Ubuntu 7.10.  Fixes acpi battery indication.
2.) Update acpi-support on Ubuntu 7.10 for models daru1, daru2,
gazp1, gazp2, gazp3, gazp5, gazv2, gazv3, gazv4.
3.) Fix usplash bug after restoring a nVidia based system with Ubuntu
7.10 64 bit from standard Ubuntu disk.  This fix was built into 
manufacturing images but not applied when customer restored from disk.

--------------------------------------

Version 2.1.6

1.) Add new system76 serval model serp4

--------------------------------------

Version 2.1.5

1.) Add new system76 model ratv5

--------------------------------------

Version 2.1.4

1.) Add new system76 models wilp5, sabv3, ratv4


Cheers,

Carl

---

### Post by gaussian on 2008-03-17
> **crichell said:**
> 
1.) Add kernel line parameter ec_intr=0 to menu.lst on daru2 under
Ubuntu 7.10.  Fixes acpi battery indication.


This did not work for me, in my DARU2 it removed the manually added parameter ec_intr=0 from the menu.lst.

```

me@ubuntu:~$ dpkg-query -W system76-driver
system76-driver 2.1.7

me@ubuntu:~$ ls /boot/grub/menu*
/boot/grub/menu.lst   /boot/grub/menu.lst_sys76backup_20080317_h19m39s54
/boot/grub/menu.lst~
me@ubuntu:~$ diff /boot/grub/menu.lst /boot/grub/menu.lst_sys76backup_20080317_h19m39s54 
67c67
< # kopt_2_6=root=/dev/mapper/ubuntu-root64 ro
---
> # kopt_2_6=root=/dev/mapper/ubuntu-root64 ro ec_intr=0
133c133
< kernel                /vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root64 ro 
---
> kernel                /vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root64 ro ec_intr=0 
139c139
< kernel                /vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root64 ro single
---
> kernel                /vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root64 ro ec_intr=0 single



```

---

### Post by gamx on 2008-03-18
I am afraid that the kernel fix is not working in my daru2 either. The battery reading still goes crazy every now and then and the display brightness changes, exactly in the same way as before.

---

### Post by gaussian on 2008-03-18
> **gamx said:**
> I am afraid that the kernel fix is not working in my daru2 either. The battery reading still goes crazy every now and then and the display brightness changes, exactly in the same way as before.

Here the fix is working perfectly, my post was only about the functioning of System 76 Driver. What it did here was to remove the fix :(

---

### Post by thomasaaron on 2008-03-18
gamx, please post the output of...
cat /boot/grub/menu.lst
... so that I can see exactly how the file looks.

Also, did you reboot your computer after running the driver?

---

### Post by gamx on 2008-03-18
here it is...

Thanks.

---

### Post by thomasaaron on 2008-03-18
Gamx,

This section...

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root ro quiet splash
initrd		/initrd.img-2.6.22-14-generic


...shows that ec_intr=0 has not been added as a kernel option. That's why your power manager is still flakey.

Did you run your the 2.1.7 driver or just install it?

Go to: System76 > Admin > System76 driver and click the About button. It should say that you are using 2.1.7. Then click the "Install" tab and the "Install" button. After you have done this, look at the file and see if ec_intr=0 has been added as a kernel option.  

It should look like this:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root ro quiet splash ec_intr=o
initrd		/initrd.img-2.6.22-14-generic

If it has been added, reboot your computer and you should be all set.
If it has not been added, you can enter it manually, save it, and reboot. Let me know. If it is not adding it, it might be a bug in the driver.

---

### Post by gamx on 2008-03-18
Version 2.1.7 appeared as an automatic update this morning. After installing it and rebooting I checked that it was installed by running dpkg-query -W system76-driver. Would it change anything if I had done that through System>Administration>System76 Driver ?

I will add the information manually and reboot.

---

### Post by imhavoc on 2008-03-18
Yay! My battery monitor (on Daru2) is finally behaving itself. Very nice.

Is there a fix for resuming from suspend on the Daru2 for 32-bit kernels? I haven't bitten the bullet and updated to 64-bit, yet. I may have time to do that in the next couple of weeks, though. I can suspend and resume one time, then the resume goes nuts the second time I suspend.

(I have a coworker with an Apple iBook. I have to admit to a little jealousy that she never reboots her stupid Mac.)

---

### Post by thomasaaron on 2008-03-18
No, as far as I know, S1 suspend can't be done on 32-bit.

---

### Post by gamx on 2008-03-18
With the manual fix in menu.lst everything seems to work fine so far...

---

### Post by gaussian on 2008-03-18
I took a look at the source code for the driver and found the explanation why in my case it removed the existing ec_intr=0. Here is the code (from acpi.py):

```

grub_menu = fileinput.input('/boot/grub/menu.lst', inplace=1)
    for line in grub_menu:
        print line.replace(' ec_intr=0',''),
    grub_menu = fileinput.input('/boot/grub/menu.lst',inplace=1)
    for line in grub_menu:
        print line.replace('splash','splash ec_intr=0'),

```

I actually don't know python, but I think this means that it first removes any existing " ec_intr=0" instances and then adds a new one after any instances of "splash" in menu.lst. The problem with this is that if you have removed the splash option all the code will do is to remove "ec_intr=0". Not a biggie for me, I can always manually adjust (I will not add the "splash" back).

---

### Post by greg_g on 2008-03-18
Just FYI to everyone, "installing the driver" doesn't actually change anything on your system.  To have any of the changes you must the RUN the driver by going to System -> Administration -> System76 Driver and click on the Install button.

Yes, the word "install" is being overloaded with meanings here, which is unfortunate.

---

### Post by jarsin on 2008-03-18
Edit: disregard, the lock up problem seems to have gone away for the time being after a couple reboots...  Will post again if it comes back up.

---

### Post by blackhole54 on 2008-03-22
> **crichell said:**
> Also import our public GPG key so apt won't complain about un-authenticated packages.l

Thanks for taking care of that.

Just out of curiosity, was the graphical updater not complaining about the lack of a signature?  And if not, isn't that a security bug?

---

### Post by ewg on 2008-03-23
System 76 sable
ubuntu 7.10


All I get after install driver is 2.1.1

I ran the code Carl supplied at the front of this thread and did intall but still have 2.1.1

Thanks,

---

### Post by thomasaaron on 2008-03-24
Try this:

Make sure you're connected to the Internet.

From a command line, enter:
sudo wget [http://planet76.com/repositories/system76-driver-2.1.7.deb](http://planet76.com/repositories/system76-driver-2.1.7.deb)
sudo dpkg -i system76-driver-2.1.7.deb

Then go to System > Administration > System 76 Driver
Click the restore tab and restore button.

Reboot your computer.

---

