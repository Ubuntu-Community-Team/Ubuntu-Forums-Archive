---
title: "Sun Virtualbox problem"
date: 2008-07-08
forum: Virtualisation
---

### Post by anigodin on 2008-07-08
Hello people,

A few weeks ago, after I upgraded to Hardy, I also upgraded the virtualbox to the new SUN version no. 1.6.0
I had a windows XP machine configured there and it worked once or twice after the upgrade (but not without driving me nuts..). 

A couple of days ago I tried to start the machine but every time I try I get this messege:


[B]VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

 [/B]

When I click ok, the machine close dowm. I tried to re-setup the kernel moudule as advised in the messege but nothing chages. all I get in the terminal is this:

[B] * Stopping VirtualBox kernel module                                           
 *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong[/B]


And of course I still cant start the machine.

Please help.. :-)

---

### Post by philinux on 2008-07-08
Whats in here.

/var/log/vbox-install.log

---

### Post by Shazaam on 2008-07-08
Sounds like you did a kernel update. Have you installed the correct headers for it?
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by anigodin on 2008-07-08
This is what I read in the log:

/etc/init.d/vboxdrv: 311: /usr/lib/virtualbox/src/build_in_tmp: not found

---

### Post by philinux on 2008-07-08
[http://ubuntuforums.org/showthread.php?t=783520](http://ubuntuforums.org/showthread.php?t=783520)

Post 4 link.

---

### Post by anigodin on 2008-07-08
Shaazam:
I ran the code you gave me and i got this messege:

linux-headers-2.6.24-19-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libxalan110 libxerces27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

Should I uninstall the two packages?

---

### Post by ptn107 on 2008-07-08
You've had a kernel upgrade then.  After _every_ Ubuntu kernel update you have to update the 'virtualbox-ose-modules' package for virtualbox to run (it will not do that for you)*.

```
sudo apt-get install virtualbox-ose-modules-$(uname -r)
```

Log out and back in.  All should be well.

* NOTE: Sometimes the virtualbox-ose-modules package is not updated in the repositories for a day or two after the kernel update is released.  Be patient.

---

### Post by anigodin on 2008-07-08
ptn,

I did what you said. now I get this messege:


The VirtualBox support driver which is running is from a different version of VirtualBox. You can correct this by stopping all running instances of VirtualBox and reinstalling the software..
VBox status code: -1912 (VERR_VM_DRIVER_VERSION_MISMATCH).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

---

### Post by Shazaam on 2008-07-08
> **anigodin said:**
> Shaazam:
I ran the code you gave me and i got this messege:

linux-headers-2.6.24-19-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libxalan110 libxerces27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

Should I uninstall the two packages?

It's up to you if you want to uninstall them. They are not related to linux-headers AFAIK.
philinux has your answer in his post.

---

### Post by ptn107 on 2008-07-08
Yep I see.  Your running a different version.  The current version provided by Ubuntu is 1.5.6-dfsg-6ubuntu1 and your running 1.6.0.  I'm guessing that you compiled your version from source from their website??

My solution is only for the version provided by Ubuntu.  So go ahead and uninstall the virtualbox-ose-modules-$(uname -r) package you installed.  It won't help.

Assuming you've installed your version correctly**, I think all you have to do is load the modules at the terminal:
```
modprobe vboxdrv
```
Make sure you have read and write access to /dev/vboxdrv.
Then run virtualbox.

**[http://www.virtualbox.org/wiki/Linux%20build%20instructions](http://www.virtualbox.org/wiki/Linux%20build%20instructions)

---

### Post by anigodin on 2008-07-08
Well, problem solved.

I tried what ptn told me and it still didnt work but I followed what was written in the error message. so I downloaded the latest version (v. 1.6.2) from Sun website.
I uninstalled the older version (1.6.0) and now it works...

Thanks you all for the time and trouble!

---

