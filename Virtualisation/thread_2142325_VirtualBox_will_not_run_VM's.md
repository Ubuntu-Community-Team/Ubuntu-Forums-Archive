---
title: "VirtualBox will not run VM's"
date: 2013-05-05
forum: Virtualisation
---

### Post by sccjono on 2013-05-05
Hello all, I'm still new to Linux in general so please excuse my ignorance. I have taken the plunge and installed 12.04 LTS 64bit on my laptop and for the most part I am more than happy.

However I am struggling to get VirtualBox working. If I launch it from a terminal get...
```
jono@hppavg6:~$ virtualboxWARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-dkms package and the appropriate
	 headers, most likely linux-headers-generic.


	 You will not be able to start VMs until this problem is fixed.
Error opening file for reading: Permission denied

```

If I launch it from Gnome I get the following when I try to start a VM

Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing
'/etc/init.d/vboxdrv setup' as root.

I have found several other threads on this but most are resolved by either installing the headers for my kernal. (Already installed). Excecuting the above command (not found on my system). Or to remove and re-install virtualbox-dkms. The latter reports...

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  virtualbox-dkms virtualbox-ose-dkms
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 4,019 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 218498 files and directories currently installed.)
Removing virtualbox-ose-dkms ...
Removing virtualbox-dkms ...


------------------------------
Deleting module version: 4.1.12
completely from the DKMS tree.
------------------------------
Done.

jono@hppavg6:~$ sudo apt-get install virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  virtualbox-dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/675 kB of archives.
After this operation, 3,898 kB of additional disk space will be used.
Selecting previously unselected package virtualbox-dkms.
(Reading database ... 218236 files and directories currently installed.)
Unpacking virtualbox-dkms (from .../virtualbox-dkms_4.1.12-dfsg-2ubuntu0.2_all.deb) ...
Setting up virtualbox-dkms (4.1.12-dfsg-2ubuntu0.2) ...
Loading new virtualbox-4.1.12 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-28-generic
Building initial module for 3.5.0-28-generic
Error! Bad return status for module build on kernel: 3.5.0-28-generic (x86_64)
Consult /var/lib/dkms/virtualbox/4.1.12/build/make.log for more information.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.



```




Does anyone have any ideas?

Jon

---

### Post by ibjsb4 on 2013-05-05
Sounds like you did the install from the software center.  I find the the site install is a bit more trouble free.  So I would suggest just starting over again.  In terminal enter:

```
sudo apt-get remove --purge virtualbox
```

Then

```
sudo apt-get install dkms build-essential
```

Then go to the site

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

And don't forget the [B]Extension Pack

[/B][https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Then reboot and see what ya got

---

### Post by sccjono on 2013-05-06
Thank you so much, that worked perfectly.

Jon

---

### Post by ibjsb4 on 2013-05-06
And welcome to the forums :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

