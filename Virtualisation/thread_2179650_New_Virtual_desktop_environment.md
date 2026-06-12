---
title: "New Virtual desktop environment"
date: 2013-10-09
forum: Virtualisation
---

### Post by cjmitton on 2013-10-09
I'm looking to set up a 'test' environment for a couple of my users to try out running Ubuntu desktop to replace our old windows PC's.  I've had a little play with Ubuntu and like the interface and looking at the main website thought it might be worth trying a virtual desktop environment for them.

I'm new to this area of computing, having used MS Hyperv for some servers but nothing more.

I'm open to looking at new horizons so thought it would be good to post a question to get me on a good starting point, rather than stumbling along.  I need to know what my base server to have the desktop running on to start with, then any installation tips for the desktop vm's and finally what to use on the PC's to open / run the vm's.

---

### Post by grahammechanical on 2013-10-09
There is a section on this forum called Virtualisation where these kinds of questions are dealt with. I have only a little experience of running a VM and that was on Ubuntu and not on Windows. How old are these old Windows PCs? I gave up running a VM because my machine did not have the power to make it a useful choice. I found that 1GB of RAM was insufficient. You run the risk of giving a bad impression of the new OS of your choice to your users.

Do you have a machine that is not being used and is close to being obsolete? Why not install Ubuntu on it and use it as training machine? Why not dual boot with Ubuntu on one of the other machines and use the machine as either a work machine or a training machine depending the OS chosen at the boot menu?

Are there any Windows programs that cannot be substituted by Linux programs? 

Regards.

P.S. It comes into my mind that you may be thinking of using Ubuntu as a Thin Client. I have no knowledge of that area at all. But I did find this

[https://help.ubuntu.com/community/ThinClients](https://help.ubuntu.com/community/ThinClients)

---

### Post by 1clue on 2013-10-09
Hi,

You intend to install Ubuntu on virtual machines in order to see if it's an adequate replacement, is that correct?

Important question: Do you intend to upgrade hardware?

If you have machines that are slow and old running Windows, then running Windows plus a VM with a windowing *buntu on it probably won't work very well for you.

If you have a newer 64-bit multi-core processor and at least 4g RAM then you might be able to do something.

If you intend to replace Windows with *buntu on the same (old) hardware then I would advise you consider Xubuntu or Lubuntu, as they are designed to be less resource-hungry.  It's the same software repository, just different software choices.

Anyway, depending on your answer to that question we can continue with a best approach.

---

### Post by howefield on 2013-10-09
Thread moved to the "*Virtualisation*" forum.

---

### Post by RichardET on 2013-10-10
I have used VMware on 64 bit Ubuntu to run Windows Vista/7 as a guest, and also use of VMware on Windows 7/8 64 bit machines, running Unbuntu as the guest.  While this machine running Ubuntu has only 4 GB of RAM, my Windows machine has 24 GB, so I can run multiple VM's;  I would definitely suggest having a test host with at least 8 GB of RAM, and an extra 100 GB of disk space.
The beauty of using a VM is that a 200 GB virtual machine usually only uses about 50 GB of real space, but could over time fill up as you add more software/data to it.  Honestly, VMware with core i5/i7 processors is so good now, I am having trouble answering the question which OS is truly better?  With a VM, its all good.

---

### Post by TheFu on 2013-10-13
Depending on your hardware, you'll have many choices.  Specific needs will lead to specific solutions, but in general ...

* use virtualbox. 
* avoid Unity or any "cheesy" GUI that demands 2/3-D GPU acceleration
* Pre-allocate the entire virtual-HDD unless you use SSDs. This is the most important choice during setup. Almost everything else can be changed later.
* Avoid non-LTS releases of Ubuntu. Stability is NOT a primary goal for these. Newer is NOT always better.
For more details - I give talks on optimizing VirtualBox machines - [check out this article.]("http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox")  Fo non-GPU intensive tasks, getting 90% of native performance is pretty easy these days with a single VM.

---

