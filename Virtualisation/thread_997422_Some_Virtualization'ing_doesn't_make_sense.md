---
title: "Some Virtualization'ing doesn't make sense"
date: 2008-11-29
forum: Virtualisation
---

### Post by Arukas on 2008-11-29
I've done a lot more reading about virtualization and some things don't make any sense.  I tried to install openVZ.  When I booted into the openVZ-kernal nothing worked so I just installed it.  

Next I tried KVM 
[PHP]https://help.ubuntu.com/community/KVM[/PHP] 

It says type this command to see if your processor support virtualization.
[PHP]egrep '(vmx|svm)' --color=always /proc/cpuinfo[/PHP]

And my processor apparently don't.

What is the deal?  This seems to be a vague thing. Is this a different type of virtualization.  I'm looking to have hypervisors. (multiple OSes at once)  KVM seems to have this requirement but not openVZ.

I'm looking into VMware Workstation, because it was the program in the demo I saw.  But I read the documents, and it says nothing about having a a processor that supports virtualization.

Can anyone shed any light on this?

---

### Post by bodhi.zazen on 2008-11-29
KVM is hardware based.

See if these links help :

[http://aplawrence.com/Linux/kvm_virtualization.html](http://aplawrence.com/Linux/kvm_virtualization.html)

[http://www.phoronix.com/scan.php?page=article&item=623&num=1](http://www.phoronix.com/scan.php?page=article&item=623&num=1)

As far as what to use for virtualization, what are you wanting exactly ?

---

### Post by damis648 on 2008-11-29
EDIT: Nvm thats not what you want.

---

### Post by Arukas on 2008-11-29
I want to run Windows XP in Ubuntu.  There's just to many programs that I need that insist you on using XP and updating it too.  Plus I've seen setup where you can tranfer files and stuff between Host and Guest.  

Plus, I'd like to have a friendly way to back up my XP files when I need to reinstall the VM (not a question of "IF xp crashes, but when"

So is hardware Virtualization something I do not need?  I know hypervisor (mult OS sound like what I am looking for)


Plus I'm thinking of going to Ubuntu64 so I can have more RAM for the VM, but at this point, I don't know if that makes a difference.

---

### Post by bodhi.zazen on 2008-11-29
With those criteria I suggest you look at VirutalBox or VMWare.

There are how to's on the forums and google.

---

### Post by damis648 on 2008-11-30
> **Arukas said:**
> I want to run Windows XP in Ubuntu.  There's just to many programs that I need that insist you on using XP and updating it too.  Plus I've seen setup where you can tranfer files and stuff between Host and Guest.  

Plus, I'd like to have a friendly way to back up my XP files when I need to reinstall the VM (not a question of "IF xp crashes, but when"

So is hardware Virtualization something I do not need?  I know hypervisor (mult OS sound like what I am looking for)


Plus I'm thinking of going to Ubuntu64 so I can have more RAM for the VM, but at this point, I don't know if that makes a difference.


Then you will want virtualbox.
Do in terminal to install:
```
sudo apt-get install virtualbox-ose
```
and then reboot. You will find it in Applications>System Tools

---

### Post by Arukas on 2008-11-30
Thanks for the help.  I want to point out, the guides and howtos weren't very helpful to me.  I did learn a new word "Hypervisor" and a military officer came up with the pronunciation of JeOS.

However, I'm taking VirtualBox just gets the job done, and VMware is better and not free.  Still how does openVZ factor in.  

Also, since XP will still connect to the internet, do I still need to install my antivirus and firewall?  

I do have XP already running in VMware, however, I notice XP must get virtualize alot because it seemed prepared for the VM environment, plus it seems to run better.  Go figure.

---

### Post by bodhi.zazen on 2008-11-30
> **Arukas said:**
> Thanks for the help.  I want to point out, the guides and howtos weren't very helpful to me.  I did learn a new word "Hypervisor" and a military officer came up with the pronunciation of JeOS.

However, I'm taking VirtualBox just gets the job done, and VMware is better and not free.  Still how does openVZ factor in.  

Also, since XP will still connect to the internet, do I still need to install my antivirus and firewall?  

I do have XP already running in VMware, however, I notice XP must get virtualize alot because it seemed prepared for the VM environment, plus it seems to run better.  Go figure.

1. VMWare Server is free

2. VirtualBox PUEL (downloaded from the web site) may be easier to user then the OSE from the repos.

3. OpenVZ will NOT run windows.

4. Yes, the rabbit hole is deep. Keep at it, start simple. Read either the VMWare or VirtualBox documentation. They will seem technical, but they are great starting places.

[http://download.virtualbox.org/virtualbox/2.0.6/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.0.6/UserManual.pdf)

---

### Post by Arukas on 2008-11-30
Wow so VMWare server is free.  That's good.  So what's the difference between the server and workstation?  It seems all the same.  Although, from what I've read workstation is capable of doing 3d graphics and that is still discourage.

---

### Post by fishtoprecords on 2008-12-01
> **Arukas said:**
>   So what's the difference between the server and workstation?  It seems all the same.

I agree, I'd love to understand the differences and suggest that the answer goes in the big sticky megathread.

A related question:

Does the VM server that hosts the other OS run under the hosting OS? or does it run above it as some sort of super OS, and you then run Ubuntu, Debian, OS-X or Windows under it? or something like that which I don't grok.

Thanks

---

### Post by bodhi.zazen on 2008-12-01
> **fishtoprecords said:**
> I agree, I'd love to understand the differences and suggest that the answer goes in the big sticky megathread.

The differences keep changing ;) Check the VMWare site for additional information.

---

### Post by Arukas on 2008-12-01
I don't find that site very user friendly.  I was looking for the system requirments ,when I thought virtualization need to be supported by your cput,and never found them.  I had to look else where.

However, From what I've read elsewhere though, workstation > server, because it has a few extra features.  For people, who run ubuntu as host, server is probably better, because most those extra features in workstation or only avabilbe in the windows version.  (from my expiereince)  Plus when you factor in the cost vs. benefits.

---

### Post by fishtoprecords on 2008-12-01
> **bodhi.zazen said:**
> The differences keep changing ;) Check the VMWare site for additional information.

I find the VMware site to be opaque. Whatever difference are completely lost on me.

Please, pick any version and explain what the heck they are talking about.
What do I need to run a VM with Winders under my nice Ubuntu 8.10 system?

---

### Post by bodhi.zazen on 2008-12-01
VMWare is a for profit company, they want to sell you a product.

As is common with many such companies, they give you a taste of the goods for free.

Over time, the product, in this case virtualization, has become more powerful. There is also competition, including KVM, VirtualBox, OpenVZ, Xen, and Windows Virtualization (whatever that is called) just to name a few.

Because of this competition, the quality of the free offerings have greatly improved ...

VMWare even offers ESXi for free ... :lolflag:

I only have so much time, and I am *trying* to maintain at least some basic information on KVM, VirtualBox, and VMWare, both 32 and 64 bit, and both guest and host, on these forums. Lord knows I am NOT an expert on these subjects, I am just a user like you.

If I wrote something on the Versions of VMWare it would be outdated in short order. I personally am unwilling to purchase all the various virtualization software, VMWare or otherwise, for this purpose (how many products does VMWare offer ? Now add in parallels, Xen, and well, you get the idea).

This information is maintained by others on the web and frankly is a goggle search away.

[http://en.wikipedia.org/wiki/List_of_VMware_software](http://en.wikipedia.org/wiki/List_of_VMware_software)

[http://en.wikipedia.org/wiki/VMware](http://en.wikipedia.org/wiki/VMware)

If you do not understand the VMWare Web page, contact them directly.

Now if you, or anyone else is willing to maintain this information, let me know and I can add a link into the Mega-thread.

---

### Post by fishtoprecords on 2008-12-02
> **bodhi.zazen said:**
> VMWare is a for profit company, they want to sell you a product.

This information is maintained by others on the web and frankly is a goggle search away.

I'm all for paying for products that are clearly superior to free ones. But VMware seems to be far more interested in getting me to give them money than to explain what is needed for any specific needs.

I've googled, read the mega-thread. Followed threads. I've written operating systems. That you, @bodhi.zazen, don't feel like answering simple questions is fine, but enough with the attitude. I was not asking for an indepth discussion of each product and each version, I asked what parts are needed to run Windows under Ubuntu as a replacement for Wine.

It looks like VMware's server is needed, but I can't tell what else.

Perhaps there is someone else here with better attitude and some information.

---

### Post by bodhi.zazen on 2008-12-02
Windows will run in any VMWare product, Server is probably the best option unless there is some feature you *need* that is not available in Server.

Alternates to VMWare include KVM/QEMU and VirtualBox.

What is it that makes you think you need something ? What is it that VMWare Server will not do for you that you are looking to add ?

---

