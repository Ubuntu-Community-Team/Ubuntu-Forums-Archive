---
title: "Wily Desktop, How do I set to work on Desktop Version Only?"
date: 2015-05-16
forum: Ubuntu Development Version
---

### Post by sam-c on 2015-05-16
Wily Desktop, How do I set to work on Desktop Version Only?
I downloaded Wily desktop.
Installed it on one of my partitions.
It Runs like it is in a Phone??
Thanks
Uncle Sam

---

### Post by PaulW2U on 2015-05-16
Where did you download the image from?

Here - [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/) ?

Or here - [http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/) ?

The first link is to the normal desktop, Unity 7. The second link is for the next generation of the desktop, Unity 8 which will look somewhat like an Ubuntu phone at present. I think you'll probably need to re-download and re-install using the first link.

---

### Post by grahammechanical on 2015-05-16
The Ubuntu Desktop Next ISO image is one of 3 ways in which we can experience Unity 8 on a desktop machine. The Ubuntu phone runs on Mir and uses Unity 8 so when we install Unity 8 on a desktop machine what we get is the phone OS. 

Ubuntu Desktop Next was meant to be a place where experiments with convergence were to happen. But we recently heard that things are going to be done differently. Ubuntu will be developed in 2 parallel branches (to put it simply). One branch will be the usual Ubuntu that is updated by apt-get with deb packages. The other branch will be built on Ubuntu Snappy Core with snap packages and transactional updates. 

We expect to see ISO images of Ubuntu snappy personal (or whatever name sticks to it - maybe Ubuntu Next) some time in the next six months. Who knows when! Meanwhile, to run Ubuntu Wily Werewolf we install the usual desktop ISO images and not desktop-next images.

Regards.

---

### Post by Elfy on 2015-05-21
> **Cavsfan said:**
> Is there something that is telling the system that I'm using a phone instead of a PC? Because every install since Trusty wants to keep only one kernel:
Unless I edit the **/etc/apt/apt.conf.d/01autoremove-kernels** file after deleting the 3rd oldest kernel I would end up with only one kernel.

[http://ubuntuforums.org/showthread.php?t=2251168](http://ubuntuforums.org/showthread.php?t=2251168)

Here is the bug I filed and it only has 3 people on it, which I do not understand.

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1440608](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1440608)

Can we please not have every thread in here end up being about your kernels. Thanks.

---

### Post by VMC on 2015-05-21
> **Elfy said:**
> Can we please not have every thread in here end up being about your kernels. Thanks.

Thank you. I'm wondering if Sam got lost in all this rhetoric. He hasn't been back since.

---

### Post by bapoumba on 2015-05-21
Off topic posts moved to their own thread.

---

### Post by sam-c on 2015-05-25
ye its sam and what I dread most Partition Managing My whole Disk went again....
Uncle Sam:mad:

---

