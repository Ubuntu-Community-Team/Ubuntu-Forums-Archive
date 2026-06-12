---
title: "[SOLVED] Heavy Loads in Virtualization!  Need Some Tips"
date: 2008-08-29
forum: Virtualisation
---

### Post by Sugi on 2008-08-29
After a year of using VirtualBox, I am a little disappointed.  I had a lot of issues with VirtualBox.  One issue is memory leak after closing down VirtualBox.  I would have to restart Ubuntu to get everything back.  Also VirtualBox lagged with heavy-loads.  It was almost unbearable.

So, people of ubuntu.  I need some tips.  I need a light weight virtual software for my Ubuntu installation that is able to handle heavy loads.  I will be installing Windows with adobe software (Yes, I know PS CS2 works within Wine, but I need CS3 and updates. And I need Adobe software other than just Photoshop).

I have read a lot about VMware VS VirtualBox VS Qemu.  It seems like Qemu with kqemu out preforms the others. VirtualBox is for simple use and VMware (free version) does not hold its own like the other virtual software.

Please, let's not turn this into which Virtual Software is better.  I need to know which virtual software can handle heavy-loads. There is a difference. 

Specs:
Ubuntu Hardy Heron
Laptop
Intel Duo 2.0 GHz
2 gigs DDR2

Thanks,
Sugi


**Update:**
My CPU is not supported by KVM.  So I decided to go back to VirtualBox.  But I got to learn a lot about KVM.  So, it wasn't a lost.

If anyone is interested in KVM.  GO for it.  It's a great little program.

How are some useful links to get you started:

Ubuntu's KVM Wiki:
[https://help.ubuntu.com/community/KVM]("https://help.ubuntu.com/community/KVM")
Virtual Machine Manager:
[http://virt-manager.et.redhat.com/]("http://virt-manager.et.redhat.com/")
HOWTO KVM Guest Linux
[http://www.greenhughes.com/content/virtualisation-with-kvm-and-virtmanager-kubuntu-804]("http://www.greenhughes.com/content/virtualisation-with-kvm-and-virtmanager-kubuntu-804")
Another HOWTO KVM Guest Linux
[http://www.phoronix.com/scan.php?page=article&item=983&num=1](http://www.phoronix.com/scan.php?page=article&item=983&num=1)
HOWTO KVM Guest Windows XP
[http://www.cmready.com/polyoperable/?p=13](http://www.cmready.com/polyoperable/?p=13)

Enjoy,
Sugi

---

### Post by ansicplusplus on 2008-08-30
Hy Sugi,
with kvm you can assign more than one cpu to the vm. I have a vm with 3 cpus running on a quadcore and the vm uses all of them for a multithreaded decoding app.
I am not sure whether the heavy load you mention is on the host or inside the vm. Inside the vm adding some cpus could work for you.
Yours, ansicplusplus

---

### Post by Sugi on 2008-08-30
Sorry, the heavy load is in the VM.  If I asign two cpu to it, won't i need one for ubuntu though.  I only have two cpus.

Sugi

---

### Post by Sugi on 2008-09-01
Bump

---

### Post by ansicplusplus on 2008-09-01
> **Sugi said:**
> Sorry, the heavy load is in the VM.  If I asign two cpu to it, won't i need one for ubuntu though.  I only have two cpus.

Sugi
Hy Sugi,
if you assign 2 cpus (kvm -smp 2) the vm guest will see 2 cpus. It doesn't mean the host can't use them any more. They simply share the 2 cpus as they would share 1 cpu on a single core. In my opinion you should try kvm for your purpose.
Yours, ansicplusplus

---

### Post by Sugi on 2008-09-01
Well, I installed KVM and here's my report.

I put about a good 8 hours in research on KVM and finally installed it, but I was a little scared because of this statement.

> egrep '(vmx|svm)' /proc/cpuinfo

I check that command in my terminal and nothing came up.  That means, my laptop can not handle hardware acceleration, but I decided to go with the installation anyways.

Well, it was too slow because of lack of hardware.  I knew this going into it though, but maybe some day I will try out KVM with the right hardware.  I do like the fact it's based off of Qemu.  

If anyone is thinking about installing or testing out KVM.  I think you should.  It looks amazing and can be really powerful for a light weight application.  I will edit my main thread and update it with information and links.

My final results are I went back to VirtualBox, because it works on my computer. I am a little disappointed but that's oh kay.  I learned a lot KVM.  So, it wasn't a lost.

Sugi

---

