---
title: "virtualisation for testing pupose"
date: 2010-01-11
forum: Virtualisation
---

### Post by sanderd17 on 2010-01-11
Hi, lately I've been trying out some other linux distros but I don't want to burn a cd every time I test a distro. And if I test a distro, I would like it to behave like it behaves when it's installed. 

Do you think virtualisation would be easy to use for this purpose? e.g. install distros without using a cd and remove them again.

If virtualisation will help me, where can I find a good howto? 
And as last question: is there a chance I will screw up my system when installing a virtualisation server/client?

I want to use virtualisation for helping people with installation problems to. So I can try to install an application without messing with my own system.

Any advise is welcome.

---

### Post by fouadatmeh on 2010-01-11
Hello,
Virtualization IS the answer for you since it will do exactly what you are asking for..
Starting with virtualization is very easy, it is almost intuitive (the main idea is that you run a software inside your pc "host" and it will create a "virtual" pc inside it "guest".. this application will take the resources to run the guest (ram, hdd space, CPU)  from the host, so make sure your pc is powerful enough to run two os's at the same time (specially RAM)... also the hdd drive for the guest will look as a single large file on the host)
try this ebook: "http://www.sun.com/systems/solutions/virtualizationfordummies/virtualization-for-dummies.pdf"

usually you will not screw up your system as a virtual machine is just like any other application you install on your pc..

The two main virtualization softwares are VirtualBox and VMWare.. both of them are great and they offer free software for you to use (VirtualBox and VMWare Player are free for personal use... I don't know about corporate usage!)
personally I am using virtualbox and it is working great for me :)

---

### Post by pricetech on 2010-01-11
I installed VirtualBox OSE from the repos and it was a piece of cake to set up.  I'm only using it for testing apps under XP, but it has worked in that capacity just fine.

---

### Post by sanderd17 on 2010-01-12
I tried out Virtualbox, the download was quite large (34Mb) but now I'm loving it. The setup was really easy. I now have puppy linux installed with a virtual hard drive of 200MB (not big but enough for puppy). 
And windoze vista is also installed. I thought 100x the size of puppy (=20GB) would be enough but since windoze is so stupid to divide the virtual hdd in 2 equal pieces I don't have any space left on my 10GB virtual C drive. Maybe I'll try again with a bigger amount of space or maybe I'll delete windoze. I don't need that anyway, it was just a little test to see the speed of a virtualised OS.
What I do love about installing windoze this way instead of dual booting is that I can now mount an iso file as is would be a cd in windoze. 

Thanks for the advise.

---

