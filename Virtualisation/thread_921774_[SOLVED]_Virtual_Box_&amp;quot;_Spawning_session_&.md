---
title: "[SOLVED] Virtual Box &amp;quot; Spawning session &amp;quot;"
date: 2008-09-16
forum: Virtualisation
---

### Post by Dyffo on 2008-09-16
I have just installed  the latest V Box 2.02, this installation seems to have gone O.K. My problem is I am trying to install XP on to VB. I have done all the preliminary settings, but when I try to go from Powered Off and start to perform the install I get the message " Spawning session" and the programme locks up - any ideas.My previous version of V.B. worked O.K !!!

---

### Post by jlintz on 2008-09-17
I seem to be experiencing the same problem, I was using 2.02 fine and just rebooted and when I came back up , virtualbox wont spawn a virtual

---

### Post by Dyffo on 2008-09-17
I solved the problem by deinstalling VB in Synaptic, then reinstalled version 2.02 for 
Gutsy instead of Hardy Heron, which is on my system. This reinstall was from the V.B website. All works fine now.

---

### Post by Nano on 2008-09-18
If you run virtualbox from a terminal you will see this message:
```

WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.

```

I bet that was the problem you were experiencing :)

---

### Post by Dyffo on 2008-09-18
Run the command "sudo /etc/init.d/vboxdrv setup" and see if that helps.This worked for me !!!!

---

### Post by ramomamo on 2008-09-18
Yes, the problem is that the module vboxdrv is not loaded at boot time.

```
sudo modprobe vboxdrv
```

or edit /etc/modules and add it there so it loads automatically next boot.

---

### Post by be4truth on 2008-10-02
> **Dyffo said:**
> Run the command "sudo /etc/init.d/vboxdrv setup" and see if that helps.This worked for me !!!!

Worked for me too.

---

### Post by stroyer on 2008-10-08
Works great now! Thanks

---

### Post by run1206 on 2008-10-08
> **Nano said:**
> If you run virtualbox from a terminal you will see this message:
```

WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.

```

I bet that was the problem you were experiencing :)

Yes, i experienced that problem too.  Then i ran..
```
sudo apt-get install linux-headers-generic
``` 
and it recognized the vboxdrv module!!! Running Virtualbox on Intrepid now! Thanks to you and ramomamo! :D

---

### Post by Kokesh on 2008-10-08
What helped to me (after upgrading to Intrepid beta (done 2008-09-07):
```
sudo /etc/init.d/vboxdrv setup
```

(should be done after any kernel upgrade, VBox usually informs about that when you update kernel)

---

### Post by run1206 on 2008-10-08
> **Kokesh said:**
> What helped to me (after upgrading to Intrepid beta (done 2008-09-07):
```
sudo /etc/init.d/vboxdrv setup
```

(should be done after any kernel upgrade, VBox usually informs about that when you update kernel)

true, i wasn't sure if Intrepid would recognize the module and scripts the same way that Hardy did :( ; hopefully future kernel updates would be able to automate that process.

---

### Post by Mouth on 2008-10-13
Perfect! Exactly my problems, and the correction worked of course.
It's a shame that VirtualBox doesn't present that error/issue when run in GUI mode.

---

### Post by zeddock on 2008-10-15
> **Mouth said:**
> Perfect! Exactly my problems, and the correction worked of course.
It's a shame that VirtualBox doesn't present that error/issue when run in GUI mode.

Thankyou Thankyou Thankyou!

Worked for me too, and I second the disbelief that vbox does not present that in GUI.

zeddock

---

### Post by GetVerticalPV on 2008-10-15
Beautiful - this fixed my issue too...

---

### Post by JunySan on 2008-10-16
Thanks!!! :)

---

### Post by Todaro on 2008-10-16
> **Dyffo said:**
> Run the command "sudo /etc/init.d/vboxdrv setup" and see if that helps.This worked for me !!!!

For me too. Thanks! :popcorn:

---

### Post by myspacejmagenst on 2008-10-16
I used the command "sudo /etc/init.d/vboxdrv setup" and it worked like a charm! I'm on 8.04 Hardy Heron. This was what > ~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.


---

### Post by alejaaandro on 2008-10-19
> **Dyffo said:**
> Run the command "sudo /etc/init.d/vboxdrv setup" and see if that helps.This worked for me !!!!

thnx... worked for me too..

---

### Post by phentex on 2008-10-25
now what is the point of intrepid having dkms...

---

### Post by jol-blazey on 2008-12-01
```
sudo /etc/init.d/vboxdrv setup
```
Just running this fixed the Spawning Session problem for me immediately (on hardy)

---

