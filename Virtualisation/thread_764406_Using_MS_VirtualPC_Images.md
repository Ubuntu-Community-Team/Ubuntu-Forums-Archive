---
title: "Using MS VirtualPC Images?"
date: 2008-04-23
forum: Virtualisation
---

### Post by markwilliams on 2008-04-23
I decided today that I would duel boot Ubuntu and Vista.  Until now I have been using only Vista.  I had installed VirtualPC with XP as a guest OS for old software that didn't work with Vista.  

Ideally I would like to use this VM with both Ubuntu and Vista, but I can see a few problems.  
1)If VMware, VirtualBox, or other virtualization software does allow VirtualPC VMs to be used would the VMs need to be converted each time I changed OS?
2)Would the differences in hardware emulated mean that XP would need to be activated each time?

If it isn't easy to share a VirtualPC VM between Vista and Ubuntu I might just use other virtualization software and reinstall XP and its applications.  

What software is recommended?

---

### Post by SL666 on 2008-04-23
I'm also interested in this.. I'd like to run ubuntu and a virtual vista box.

---

### Post by homerhomer on 2008-04-24
I would recommend Virtualbox or Vmware. both are great products and both will be able to work with Windows and Linux.  

Personally I would try to go with Virtualbox because it is free and works pretty well. I can also see the need to go with VMWare because it's pretty much the industry standard and it has better support with large enterprise. 

so.. if it's just for you and try Virtualbox.  you can get Open Source version but I have personally had better experience with the non-Open source version from there website. 

as far as using those MS Virtual PC images i'm not sure - maybe you can make ghost image and then restore it to a different Virtual Machine.   ??

hope this helps

---

### Post by kaivalagi on 2008-04-24
Ubuntu are pushing kvm, it may be worth putting some effort into using this for virtualisation...I think it may perform better too and will have better support long term from the ubuntu camp.

Virt manager is the front end for it...

Just a thought

---

### Post by SL666 on 2008-04-24
I fired up an XP machine under Gutsy on a POS celeron box yesterday, using virtualbox, i was *REALLY* impressed by its performance..

Anyone know how the virt manager for KVM stacks up against the virtualbox one?

---

