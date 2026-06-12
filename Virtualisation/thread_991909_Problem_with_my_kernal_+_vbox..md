---
title: "Problem with my kernal + vbox."
date: 2008-11-24
forum: Virtualisation
---

### Post by waxyfresh on 2008-11-24
i get a error when booting about my kenral not supporteing virtual box,and the photos show he erors i get when i try to run vbox,runningthe command they give me dose not work.

---

### Post by waxyfresh on 2008-11-24
Anyone?

---

### Post by Simian Man on 2008-11-24
I believe this can happen after kernel updates.  Try this:
- Update your system (I see that orange update notifier :))
- Reboot
- run 'sudo /etc/init.d/vboxdrv setup'

Then see if that fixes your problem.

---

### Post by waxyfresh on 2008-11-24
david@IceWeasel:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for david: 
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
david@IceWeasel:~$ 



No change.

---

### Post by waxyfresh on 2008-11-24
david@IceWeasel:~$ virtualbox 
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-source package and the appropriate
         headers, most likely  linux-headers-generic.

	 You will not be able to start VMs until this problem is fixed.



How do i figure out what to install?

---

### Post by silverglade00 on 2008-11-24
Open Synaptic and install all of the virtualbox-ose-* packages. Also, install linux-headers-generic like it says.

---

