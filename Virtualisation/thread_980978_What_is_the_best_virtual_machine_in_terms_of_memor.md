---
title: "What is the best virtual machine in terms of memory footprint?"
date: 2008-11-13
forum: Virtualisation
---

### Post by coolnfunky_raj on 2008-11-13
Hi all

I am running Ubuntu 8.04 on Dell 1501. I have 1GB memory, AMD 64 processor and about 4GB disk space left. I want to run Photoshop CS3 and Illustrator. I know there are open source alternatives, but I have to learn to use  Adobe products for my work. I thought I can run these on Wine, but unfortunately I found that wine doesnt support these very well.

I am thinking of using a virtual machine and run XP on it to get photoshop and illustrator. I am looking for a virtual machine that supports AMD 64 and has relatively small footprint so that it can run (somewhat) smoothly with my 1GB memory. 

Can anyone recommend me one?

Thanks
Raj

---

### Post by tjwoosta on 2008-11-13
i have a laptop that is running ubuntu 64bit with only 1 GB ram


i use virtualbox-ose from the repositories (synaptic package manager)


when you are setting up a new virtual machine it will ask you how much memory and disk space you want to use

i set mine to use 256MB ram and 10GB disk space for the virtual machine and it runs windows xp perfectly

---

### Post by handydan918 on 2008-11-13
+1 on vbox OSE.
Using it here on a 64bit, 1GB machine, no sweat. Near native speeds.

---

### Post by jimmy the saint on 2008-11-13
I would recommend getting VBox from their site, or by adding their repos to you list.  By doing so, you can set up a shared folder, which makes it much easier to work with photos that you already have on your system.  I would be a little concerned with having such a small ammout of disk space left though.  Adobe products require a LOT of memory and disk space, neither of which you seem to have much of.  Keep in mind that you are going to need enough RAM to run your OS, VBox, Windows, and the adobe products.  

Good Luck.

Edit: clarification
Windows XP is easy to run on a modest machine.  Adobe products are what are going to pose the issues.

---

### Post by binbash on 2008-11-13
I tried vmware workstation and virtualbox (Not OSE) both are really good, i dont see any problems at all but i prefer vmware

The ONLY recomendation i can give you : 

USe VLITE or NLITE to make xp or vista smallest!At the moment my vista using around 55mb ram,so you can give 150 200 mb memory to virtual machine.

---

### Post by gaspard.leon on 2008-11-13
go virtual box, and buy yourself another stick of ram, it's cheap and it helps alot!

I usually go with later versions of software, but the one from the repos might be alright...

I have heard a lot about VMWare, but I have not used it.
Also, VirtualBox is FOSS if you get the OSE...

---

### Post by bodhi.zazen on 2008-11-13
If you have the hardware, IMO KVM has the smallest memory requirements.

---

### Post by crawdaddyangry on 2008-11-13
Hi

I agree VirtualBox will work fine for those applications I have had no serious issues. XP Pro CS3 and Dreamweaver do well on my 8.04 AMD machine I do think that RAM and HD may be a concern for you however. You might consider a RAM upgrade the 1501 can support 2G.

---

### Post by coolnfunky_raj on 2008-11-14
Thank you all for your replies. I already dual boot win xp and Ubuntu. I dont remember booting into win xp in recent history though. But, I would still like to have the dual boot because I sometimes mess up my Ubuntu and I want an alternate operating system to boot into to recover my files. But, I dont want to reboot everytime I want to use photoshop or illustrator. 

I already have about three NTFS partitions in win xp with about 10GB disk space left there. Can I use this space in NTFS partition for my virtual machine in Ubuntu without messing up the NTFS partition or should this disk space be in the reiserfs partition? 

If I cannot use NTFS, can I safely reallocate NTFS partitions and make the existing reiserfs bigger?

---

### Post by bodhi.zazen on 2008-11-14
> **coolnfunky_raj said:**
> Thank you all for your replies. I already dual boot win xp and Ubuntu. ... <clip ... > But, I dont want to reboot everytime I want to use photoshop or illustrator.[/code]

In theory you could boot your windows XP partition with VMWare, VBox, or KVM. See the sticky in there forums for links on how to do this.

> I already have about three NTFS partitions in win xp with about 10GB disk space left there. Can I use this space in NTFS partition for my virtual machine in Ubuntu without messing up the NTFS partition or should this disk space be in the reiserfs partition?

In theory yes, store the virtual machine there. In practive 10 gb is a small space for a virtual XP machine. 

[quote]If I cannot use NTFS, can I safely reallocate NTFS partitions and make the existing reiserfs bigger?

Yes, you can resize your partitions. Boot a live CD and use gparted.

Once you have made a decision on what you are wanting to do exactly, let us know if you need help.

---

