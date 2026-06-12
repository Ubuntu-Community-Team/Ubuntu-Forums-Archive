---
title: "Want to Virtualize, where to start"
date: 2007-11-29
forum: Virtualisation
---

### Post by TorchlightJay on 2007-11-29
Okay, so I want to make a virtual system but not sure where to start.


To give you a little idea of where I am and what I want to do, I currently have a 120 GB hard drive and it's partitioned 4 way. I have a 2 gig swap file, two 22 gig Linux partitions, and the rest (like 70-something) is a partition i use to store files. I mount it as a Storage folder and share my files between the two Linux partitions (I use Ubuntu and openSUSE). I would like to use other distros and just test them out or integrate them into my research and daily use. I figured VIrtualization would be a good route to take. 

Now this is what I want. I want to expand that storage to about 85 or so ( I may split it into two logical partitions and have one for personal stuff and one for work)  and have my swap file (may expand it if necessary) and then have the rest be a partition and use it for virtualization. Now my question is, how do I do this. Like do I need to install UBuntu or whatever Linux distro and then from there install vmware or xen or whatever and then create virtual machines? That way I first boot into Ubuntu then I boot into my other virtual distros? Is there another way where I install like a virtuallayer or something and then create my virtual machines or do I have to install and OS first? I hope I make sense, thank you all.

---

### Post by 11hjpphty76lkjj on 2007-11-29
I'm not exactly clear, but what I did is create 2 partitions, one for my ubutnu system, and one for my virtual images, install ubuntu, install virtualbox ([http://www.virtualbox.org/](http://www.virtualbox.org/)) setup the images to use the other partition for the virtual drive space. and install away.

A

---

### Post by TorchlightJay on 2007-11-29
> **kalosaurusrex said:**
> I'm not exactly clear, but what I did is create 2 partitions, one for my ubutnu system, and one for my virtual images, install ubuntu, install virtualbox ([http://www.virtualbox.org/](http://www.virtualbox.org/)) setup the images to use the other partition for the virtual drive space. and install away.

A

So what would you recommend my size be for the ubuntu install partition and what size for the other virtual space partition? Also what about swap space?

---

### Post by 11hjpphty76lkjj on 2007-11-29
Depends on how much space you have, how much you want to install, and how many virtual systems you honestly plan on using, and what you plan on installing on each one.  So say if you plan on using ubuntu to only run a virtual windows system but want to use windows 90% of the time, you'd want to make a smaller ubuntu partition and give more space to your virtual windows system. but if you wanted to use ubuntu 90% of the time you'd do the reverse.  depends all on your needs.

swap is usually 1.5-2x the amount of your ram.  I usually do a gig or so by default.  of course there are lots of different thoughts on this sort of thing. so someone else i'm sure has a differing view.

---

### Post by bodhi.zazen on 2007-11-29
Generally what I do is :

I give root partitions 10 Gb (for you that would be Ubuntu or OpenSUSE). You could go lower if you like.

Use a shared swap.

For "testing", run a live CD as an iso in qemu/VMWare server/VirtualBox

If you want to install, I use 8 Gb virtual hard drives for virtual machine (this is split between swap and root).

Use a large shared Data partition to share virtual machines and data between OpenSUSE and Ubuntu.

You can go smaller on your root partitions if you like, but those sized give you some breathing room.

You might also want to look at LVM which allows you to change the size of your partitions dynamically.

To get started , there is a sticky on the top of this forum :)

---

### Post by jba6511 on 2007-11-29
i run virtualbox from my ubuntu install and when virtualbox asks where I would like to store the virtual image, I just select my partition that has a folder I call virtual images and store it there. The program is installed in ubuntu but the image for the virtual machine is held on another partition.

---

