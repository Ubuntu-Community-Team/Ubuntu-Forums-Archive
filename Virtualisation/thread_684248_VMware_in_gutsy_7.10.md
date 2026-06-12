---
title: "VMware in gutsy 7.10"
date: 2008-01-31
forum: Virtualisation
---

### Post by evolving_monkey on 2008-01-31
I am trying to install vmware in Ubuntu Gutsy 7.10 and not getting anywhere, I have tried the tar.gz files but that hasn't worked either. I am still learning so it may be user error.  I want to start using Ubuntu at work to lower some costs and this would really help. I have also tried from Add/Remove and that doesn't work either. Does anyone have any suggestions or a good tutorial?


Thanks for you time.

---

### Post by jleaker01z on 2008-01-31
> **evolving_monkey said:**
> I am trying to install vmware in Ubuntu Gutsy 7.10 and not getting anywhere, I have tried the tar.gz files but that hasn't worked either. I am still learning so it may be user error.  I want to start using Ubuntu at work to lower some costs and this would really help. I have also tried from Add/Remove and that doesn't work either. Does anyone have any suggestions or a good tutorial?


Thanks for you time.

I never did get VMWare working myself.  VirtualBox on the other hand, installed and worked like it should right off the bat.

---

### Post by p_quarles on 2008-01-31
Moved to Virtualization forum.

---

### Post by evolving_monkey on 2008-01-31
I have tried VirtualBox but it doesn't seem as stable as virtual machine. VirtualBox crashed on me where as virtual machine didn't in 7.04.

---

### Post by Parvo on 2008-02-01
You have to enable 3rd party partner software options. system>admin>software sources. then search for VMware server in Synaptic Package Manager. It should pop right up. Worked for me, hope this helps

---

### Post by darkkith on 2008-02-01
I've installed via the tar.gz from vmware's website (vmware-server) without problem.  I guess sometimes you need a vmware-any-any patch, but how far do you get with the ./vmware-install.pl ?  any specific errors, etc...

---

### Post by evolving_monkey on 2008-02-03
Thanks Parvo, that worked. It installed and worked without a problem. I'll build a few this week and see how it goes.  

I think I'll play with a few of the other options. I didn't realize there were  that many virtualization options out there now.

---

### Post by Niej on 2008-02-03
Hi, I wondering if anybody knows how to read and use the usb ports form within a windows xp virtual machine on Ubuntu 7,10 using the vmware server.
The poor xp doens't see the pendrives upon connection.
thanks in advance

---

### Post by evolving_monkey on 2008-02-03
I know it worked for me in Feisty but I haven't had a chance to try it in Gutsy yet. When I was looking for an answer to this question I remember reading a few things about USB. Some of it suggested that a few of the virtualization options have trouble with USB. If I find anything that looks like an answer I'll post back.

---

### Post by darkkith on 2008-02-04
You have to first add the USB controller in the VM -> Settings dialogue

You can now plug in your pendrive and Ubuntu will initially mount it.  You *may* need to umount it i am not sure, however you should now be able to see it in vmware, but likely have to connect to it in the VM -> Removable Devices -> USB Devices menu .. 

once you connect it, it should be available.

i think you can automate this as well by telling ubuntu (somehow) to ignore this deviceID, and then telling vmware (presumably in the vmx) make this deviceid available

---

