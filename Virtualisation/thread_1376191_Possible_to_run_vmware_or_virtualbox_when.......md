---
title: "Possible to run vmware or virtualbox when......"
date: 2010-01-08
forum: Virtualisation
---

### Post by phawnex on 2010-01-08
Hi again I just want to know if any one can explain to me how to do the following:

I have an iMac with mac osx dual booted (throughn partitions)with ubuntu 9.10. I am planning to download a virtualization machine (vmware or vmplayer) and run ubuntu on it while operating os x. I am curious as to know if anyone knows howto keep my CURRENT ubuntu install and have it run on the vm ware. (without having to reinstall ubuntu all over again) while still using os x.

Can anyone explain to me please how one goes about doing this?  Please and thanks for your time.

---

### Post by phawnex on 2010-01-09
No luck?

---

### Post by HighCommander540 on 2010-01-09
> **phawnex said:**
> No luck?

Just mount your other partition as your VMWare partition. It should work as long as you have the "use physical drive" selected. Instead of the default "use files for HDD".

---

### Post by fjgaude on 2010-01-09
While booted into your Ubuntu partition, download Player. Install. And with your VM that I assume you created with another VMware product placed in a folder, like your home folder. Open Player and point it to the VM.

---

### Post by phawnex on 2010-01-09
k thanks for the pointers, im going to try it out.

---

### Post by phawnex on 2010-01-09
ok WITHIN mac osx i tried virtualbox and had no success being able to access my ubuntu partition on my physical harddrive.  

i tried to find vmplayer for mac osx and did not encounter anything. they have fusion but i have no idea if that does the same thing. 

is there any possible way to access my CURRENT install (partitioned) of UBUNTU and have it running (through virtualization) while im logged in and operating MAC OS X. 

sorry for the caps, they are not being used out of anger, just for specifications to my issue. if there is no possible way then ill be okay with it, and continue rebooting if i want to use ubuntu (which is very often)

if there is anything i can do please let me know. i am sorry about posting the same thing twice, im just a noob trying to see if this works. it would make life much easier on me lol.

thanks for your time

---

### Post by fjgaude on 2010-01-09
Okay, if you get, i.e., buy a copy of Fusion, load it into OSX, you can then create a Ubuntu VM and have OSX as your host OS and Ubuntu as your guest.

I thought you were wishing to boot into Ubuntu and then run Player and load a VM you already have.

I don't know of a way to do what I think you wish. Maybe someone else does.

---

### Post by phawnex on 2010-01-09
yea thanks for the help i figure ill keep my ubuntu partition on it for now and virtualize another distro so i can learn more about linux in general in the virtual environment, and eventually delete the ubuntu partition when i feel comfortable and install another distro, or build up another computer with only Linux as the OS.

thanks bro

---

