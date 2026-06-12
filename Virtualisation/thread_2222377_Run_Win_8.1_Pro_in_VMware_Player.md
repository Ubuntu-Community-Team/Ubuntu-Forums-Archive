---
title: "Run Win 8.1 Pro in VMware Player?"
date: 2014-05-06
forum: Virtualisation
---

### Post by Bhakti108 on 2014-05-06
After many years on Ubuntu I moved away a couple of months ago due the necessity of having to work in Premier Pro. However I cannot stand Windows, even with its improvements, so after a great deal of thought I have decided to come back and to try running WIN 8.1 pro and Adobe premier pro on the VM ware virtual machine. Has anyone got any experience of how well this might work? and is there anything I should really consider before going ahead. 
Second question - can Linux do something like windows storage spaces _ I did like the ease of setting up mirrored software drives rather than a hardware RAID set up. I have a 120gb SSD for system and 2 x 3TB HDD but still like the software solution. Can LVM manage the same sort of thing? 

Thanks

---

### Post by lukeiamyourfather on 2014-05-06
Premiere Pro is one of those applications you'd probably want to dual boot for, but it will technically work in a virtual machine. There's ZFS on Linux which has many of the same features and largely inspired Microsoft ReFS and Storage Spaces.

[http://zfsonlinux.org/](http://zfsonlinux.org/)

---

### Post by anaconda on 2014-05-06
I am running windows 8.1 pro (64bit) in virtualbox, and it seems to be working quite well even though I only have 4GB of RAM on my machine.
I enabled 3d and 2d acceleration and 2 processors in it from the virtualbox settings (before doing that it WAS slow)

But I dont think I will ever use it for anything else than learning how to use it...

PS. installation was a real pain in the a**... It went well enough untill I started updating it. Installing the updates took about 8 HOURS and I have a fast internet connection. Its totally nuts. who has enough time to do that?

---

### Post by Bhakti108 on 2014-05-12
Thanks both for the information. 
I decided to try the VMware route, but like anaconda after waiting like two hours for the first lot of updates, I canned it. Then started a crazy two days cos I thought well I might as well dual boot. When win 8 started updating to 8.1 it crashed and re crashed and sdtalled and crashed again, took down my internet dongle, did all sorts of crazy stuff, until finally the blue screen of complete death "WHEA UNCORRECTABLE ERROR" -- I figure someone upstairs is telling me something, so Win 8 goes out the window. I am thinking of hackintosh my second drive and dual booting with mac, cos Premier pro runs on mac. So I will do all my daily stuff in Linux which I love and switch for my editing stuff to hackmac!

I will know in a few days if it will work. waiting for the install disk to arrive. 

Thanks once again.

---

