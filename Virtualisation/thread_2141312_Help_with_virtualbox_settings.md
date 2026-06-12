---
title: "Help with virtualbox settings"
date: 2013-05-02
forum: Virtualisation
---

### Post by harrysolomon on 2013-05-02
I'm a complete Linux newbie and I've got a couple of questions about properly configuring Ubuntu 13.04 to run on my computer using Virtualbox.

1)  How much Base Memory should I allocate to this virtual machine?  The default amount assigned in Virtualbox is 512MB and I've tried to run Ubuntu using this setting and it's clearly not enough as the system runs really slow.   I've then increased the number up to 1024MB and it seems to be running better.   Can anybody recommend anything else?
The host computer I'm running this all on is an HP EliteBook 8460P laptop with 4GB of installed Physical Memory and and 4GB of Available Virtual Memory..

2)  What is the ideal size of the hard drive?   Again, the recommended size in Virtualbox for the *.vdi file is 8GB.  I've tried this setting but it seems to be too small.  By the time I've finished installing the OS and applying all the required software updates, the *.vdi file is already up to 7.7GB.  
I also tried creating a hard drive of 10GB but I'm wondering if I just should go even larger than that.   The host computer I'm running this on currently has 215GB of free hard drive space.
Also, I'm thinking it might just be better to configure this hard drive as Dynamically Allocated instead of Fixed?  
Any advice would be greatly appreciated.   

Any other suggestions as to how I can properly configure all of this would be welcomed.

Thanks.

---

### Post by CharlesA on 2013-05-03
It would help you know what OS the host machine is running. I've run Ubuntu with 1GB of RAM before and it has run fine.

Have you enabled hardware virtualization in the BIOS? According to the [specs of the processor]("http://ark.intel.com/products/52229/"), it supports hardware virtualization but HP might have locked it out.

As far as hard drive size, it depends on what you are going to be using the VM for. I usually setting for 15 to 20GB, though.

---

### Post by SeijiSensei on 2013-05-03
I'm with Charles.  On a 4 GB Windows host, I'd allocate 1 GB to the Ubuntu guest.  (For Windows guests on Linux hosts, I give Windows 1.5-2.0 GB.)  The disk size depends on the size of the files you intend to store on Linux.  If you save most everything to the Windows side using "Shared Folders" or onto a mounted network share, then the Linux partition need not be that big.  However since you have 215 GB of free storage, I'd probably allocate 20-25 GB of that to the virtual machine.

---

### Post by cortman on 2013-05-03
1 GB will be barely enough for vanilla Ubuntu; if you're simply interested in trying Linux and are not insistent upon Ubuntu itself, you may want to try a slightly lighter variety. I wrote a fairly detailed how-to on installing Lubuntu 12.10 in a VM with all of VirtualBox's bells and whistles, available [here]("http://cortman.wordpress.com/2013/03/14/lubuntu-12-10-virtual-box-setup/").
I'm surprised that Ubuntu is using 7.7 GB- I run a Lubuntu VM with only 4 GB and I have a number of packages installed.
I've always used Fixed size drives myself (they are supposedly a bit faster) but I see no problem with using Dynamic.

---

### Post by harrysolomon on 2013-05-04
Thanks for your response.

The host machine is running Windows 7 and yes I have enabled virtualization in the BIOS, as it _was_ disabled by default.   My reason for running Ubuntu is just so I can learn to use it.   The reason I'm running it in Virtualbox is that the laptop in question is a work-issued machine and they were not keen on my repartitioning the hard drive so I could install Ubuntu on it's own partition.  

My goal is to get Ubuntu running and to be able to install additional packages as needed.  The one thing I definitely want to get running is Wine as my company uses a number of web-based applications designed for IE and I want to see if I can work with them in Ubuntu.

---

### Post by harrysolomon on 2013-05-04
Thanks.   I will be saving everything on the Windows side directly on the laptop and not on network drives/shares, so I'll definitely go with the larger file size.

---

### Post by harrysolomon on 2013-05-04
Thanks for the suggestion, I'll definitely take a look at your Lubuntu 12.10 guide.  I don't specifically have to learn Ubuntu, I just chose it after doing some reading about it.  As I'm a complete Linux newbie I'm definitely interested in knowing about other possible alternatives that might work for me as well.

---

