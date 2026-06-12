---
title: "Hyper-V Ubuntu Server 16.04 stopped working"
date: 2016-05-10
forum: Virtualisation
---

### Post by tkbpule1 on 2016-05-10
I am running Ubuntu Server through Hyper-V on my desktop Dell.  My hard drive is on a WD My Passport Ultra 2 TB external Hard drive.  I used the generation 2 configuration on Hyper-V.  I've had it working for about 2 months.  Sunday, my server was up and running fine.  Yesterday, I tried to turn it on and it connected, it says start was successful and that it is running but the screen is black.  I tried restarting my computer 5 times, but it didn't help.  So, I installed a new virtual machine, the same way, Hyper-V with the hard drive on my external hard drive.  It worked fine yesterday, but today the same thing is happening to this one.  Does anyone know what the problem is?  Could my external hard drive be the problem?  Thanks for you help.

I also have Ubuntu Desktop running through Hyper-v with the hard drive on my WD Passport, and it continues to work without any problems.

---

### Post by MAFoElffen on 2016-05-10
If, when you do a VM hard reset, if will flash the grub start menu. At that menu, press the <E> key > At the edit screen <Arrow Down> to the line that starts with "linux". > <Arrow Right> until you get to the end of the line >
Append the end of the line with
```

text --verbose debug drm.debug=0xe plymouth:debug

```
Recheck for any syntax errors in what you added. Then press <Cntrl><X> to boot.

That will boot server in a text mode verbose boot message mode. Post back with what you find or if even that changes nothing...

---

### Post by tkbpule1 on 2016-05-11
Hey, 

  I appreciate you responding.  Unfortunately, that didn't change anything. I've never seen the grub menu before, so I explored a little bit.  Should I try to start in recovery mode.

Thanks again.

---

### Post by MAFoElffen on 2016-05-12
Note, when you first start (cold boot from the VM Manager) Ubuntu as a virtual in a hypervisor (not just with Hyper-V), it will skip by too fast to display the grub menu. But if you restart the VM (Actions > Force Reset), it keeps that seesion Window ope while it reboots. Start hitting the left shift button and the brub menu should display. Once it displays, either hit and up or down arrow kep to get it to stay there, or select the <E> key.

You can't alternatively use the root prompt from the recovery menu, if you can't get to the grub menu.. right? So the pre-requisite to all those options, is to first be able to see the Grub Menu. That is the boot manager for you to be able to get to those  other options.

---

### Post by tkbpule1 on 2016-05-12
I think you misunderstood my reply..I did get into the grub menu and I added the code you suggested.  It did not help.  When I hit ctrl-x to reboot, the screen was black with no activity.  So, after trying your method, I went exploring the grub menu further. And I found that I could boot in recovery mode.  I didn't do that yet.  I was waiting for a response from you to make sure that was your next suggestion. 
Again, I appreciate your feedback.  Please continue to try to help
Thank you.

---

