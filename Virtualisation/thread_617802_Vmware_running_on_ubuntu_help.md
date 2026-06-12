---
title: "Vmware running on ubuntu help"
date: 2007-11-19
forum: Virtualisation
---

### Post by Jay389 on 2007-11-19
I want to transfer a file i downloaded on ubuntu to my windows xp that i run on vmware

I have no clue how to do that

My OS is ubuntu 7.10, i am running vmware server on it to have Win XP on

The file is a trial of Photoshop that i want to use

---

### Post by rbmorse on 2007-11-19
Set up a shared folder in the VMware guest machine (see the VMware help) and then from the host machine copy the Photoshop install file to the shared folder.  Then, working from the guest, you can move the file to somewhere more conveinient. 

Once set up, the shared folder shows up in "network neighboorhood" on the guest. 

It depends upon which version of Photoshop you're evaluationg, but you're going to be disappointed to various degrees.  Photoshop is just too resource heavy. Have you looked at TheGIMP 2.4?

---

### Post by juan@forum on 2007-11-19
do you have networking between them?

---

### Post by bodhi.zazen on 2007-11-19
Transfer, by any means, the file to windows and run it the way you would normally.

---

### Post by Jay389 on 2007-11-20
> **rbmorse said:**
> Set up a shared folder in the VMware guest machine (see the VMware help) and then from the host machine copy the Photoshop install file to the shared folder.  Then, working from the guest, you can move the file to somewhere more conveinient. 

Once set up, the shared folder shows up in "network neighboorhood" on the guest. 

It depends upon which version of Photoshop you're evaluationg, but you're going to be disappointed to various degrees.  Photoshop is just too resource heavy. Have you looked at TheGIMP 2.4?

Yes I have been using gimp for awhile now, but I want to see if I like photoshop better or not.

---

### Post by ChardFi on 2007-11-20
If you have VMware tools installed on the client you can simply copy the files on the host and paste them in the client OS.

If you don't then just install VMware tools and see step one.

Easy.

---

