---
title: "'configuring' multiple VMs"
date: 2013-01-27
forum: Virtualisation
---

### Post by rex_dante on 2013-01-27
Hi all!
I'm posting this thread after hard hitting ma head for hours on configuring NETWORKING on my VM network (through NAT). Also, I wanna know that do I need a "workstation" version of VMware or VirtualBox to have ALL my guest OS systems in ma virtual machine which I'm hosting on Ubuntu 12.04, BOOT TOGETHER.

_I know that what I wrote above would get a bit choppy for you guys so let's get it straight-_

[B]1. Do I need a "workstation" version of VMware or VirtualBox or any other VM program you recommend, to have all my "guest" operating systems and they're-
[/B][I]* Windows XP SP2
* Windows 7 Professional
* Ubuntu
* Kubuntu, boot together and "I can switch to them ON FLY".
[/I]
**2. How to configure "networking" in all guest OS? Such that, each VM system should be able to PING each other and my HOST system too .i.e. Ubuntu 12.04 at which the VM is hosted.**

**3. Do the Open-Source version of VMware workstation would solve my problem? As I don't wanna buy it. I <3 open source and also a supporter of it.** :p

[U]My system specifications are-
[/U] *CPU:* **AMD FX-4100 Quad-Core Bulldozer 3.6 Ghz**
*GPU:* **ATI Radeon HD 4250 512 MB**
*MOBO:* **Gigabyte GA-880GM-D2H**
*RAM:* **4 GB DDR3 Kingston**
*HDD:* **1 TB Western Digit 7200 Rpm**

What say?

---

### Post by Cheesemill on 2013-01-27
Just use VirtualBox, it runs all of those guest OS's with no issues.

If you set them to bridged networking mode every OS can see every other OS as if they were individual machines on the same network.

How much RAM do you have? This is usually the limiting factor as to how many VM's you can run at the same time.

Also there is no such thing as a free open-source version of VMware Workstation, it is a commercial product that you have to pay for.

If you use VirtualBox it is best to use the version direct from Oracles repositories instead of the version that ships with Ubuntu as it is more up to date. This can be installed with the following commands...
```
echo "deb http://download.virtualbox.org/virtualbox/debian precise contrib" | sudo tee -a /etc/apt/sources.list
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-4.2
```

If you want support for USB then you need to install the extension pack as well, once you have VirtualBox installed just click on the link on [this]("https://www.virtualbox.org/wiki/Downloads") page and it will install itself into VirtualBox.

---

### Post by rex_dante on 2013-01-27
> **Cheesemill said:**
> Just use VirtualBox, it runs all of those guest OS's with no issues.

If you set them to bridged networking mode every OS can see every other OS as if they were individual machines on the same network.
I know all that thanks. But I wanna to know 'how can I do same with NAT?' As I want all guest systems to have a different IP range than that of my HOST OS one for a secret reason. ;)

> **Cheesemill said:**
> How much RAM do you have? This is usually the limiting factor as to how many VM's you can run at the same time.

I got 4 GB DDR3 1333 Mhz Kingston RAM. And that's enough I think. Also, I can remove one windows or linux OS from the network if I run out of resources.  :)

> **Cheesemill said:**
> Also there is no such thing as a free open-source version of VMware  Workstation, it is a commercial product that you have to pay for.
I'd like YOU to goto the link I've provided just below to make sure that it belongs to their Official website or not. ;) Check ;)
[https://my.vmware.com/web/vmware/details?downloadGroup=WKST-901-OSS&productId=293](https://my.vmware.com/web/vmware/details?downloadGroup=WKST-901-OSS&productId=293)

> **Cheesemill said:**
> 
If you use VirtualBox it is best to use the version direct from Oracles repositories instead of the version that ships with Ubuntu as it is more up to date. This can be installed with the following commands...
```
echo "deb http://download.virtualbox.org/virtualbox/debian precise contrib" | sudo tee -a /etc/apt/sources.list
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-4.2
```If you want support for USB then you need to install the extension pack as well, once you have VirtualBox installed just click on the link on this page and it will install itself into VirtualBox.
Thanks for all this, but I've installed it already and was testing on it (VirtualBox and also VMware too).


You didn't replied one thing that-
How do I can 'switch' to the different guest systems ON FLY (mean all guest systems are booted up and I can switch to anyone I want) ?
As I don't know how to do so. **Also, keep in mind that my HOST OS is Ubuntu and NOT windows.**

Thanks mate. :D

---

### Post by Cheesemill on 2013-01-27
> **rex_dante said:**
> I know all that thanks. But I wanna to know 'how can I do same with NAT?' As I want all guest systems to have a different IP range than that of my HOST OS one for a secret reason. ;)
If all of your VM's are set to use NAT it should just work. All of your VM's and the host OS get their own IP on the NAT subnet.

> I got 4 GB DDR3 1333 Mhz Kingston RAM. And that's enough I think. Also, I can remove one windows or linux OS from the network if I run out of resources.  :)
That's definitely *not* enough RAM to run all of those guest OS's simultaneously. I would be wanting to allocate 2GB of RAM to each machine plus whatever you need for the host OS. I wouldn't try running all of those VM's at the same time unless my host system had about 10GB, 8GB at an absolute minimum.

> I'd like YOU to goto the link I've provided just below to make sure that it belongs to their Official website or not. ;) Check ;)
[https://my.vmware.com/web/vmware/details?downloadGroup=WKST-901-OSS&productId=293](https://my.vmware.com/web/vmware/details?downloadGroup=WKST-901-OSS&productId=293)
That page just proves what I was saying, VMware Workstation is a closed source application that you have to pay for. That page has a link for the 30-day free trial of VMware Workstation or you can download the open-source VMware Player (which isn't the same as VMWare workstation).

> You didn't replied one thing that-
How do I can 'switch' to the different guest systems ON FLY (mean all guest systems are booted up and I can switch to anyone I want) ?
As I don't know how to do so. **Also, keep in mind that my HOST OS is Ubuntu and NOT windows.**
This is related to the DE you are running rather than the virtualization solution you are using. At the end of the day a VM is the same as any other application that runs in a windows, you use the same method that you would do for switching between any other applications, for example ALT+TAB.

---

### Post by rex_dante on 2013-01-27
I WANT TO MAKE A "PRIVATE" VIRTUAL NETWORK LAB for  TESTING. That's why I've posted the thread. I got to something that I've to use "VMware Server" to accomplish my goal.

Just asking, SO USING "VMWARE SERVER", I MIGHT BE ABLE TO DO WHAT I WANNA DO. Am I right?

---

### Post by Cheesemill on 2013-01-27
VMware Server no longer exists as a product.

The last version was discontinued in 2010 and reached end-of life in June 2011.

Your options for running VM's under a host OS are either VMware Workstation, VirtualBox, KVM or Xen.
Of these I would recomend either VMWare Workstation or VirtualBox as they are by far the easiest to configure.

> I WANT TO MAKE A "PRIVATE" VIRTUAL NETWORK LAB for  TESTING.
There is another networking setup you can use in VirtualBox called a host-only network.
This is a private network that is only available from your VM's and the host OS.

---

### Post by rex_dante on 2013-01-27
> **Cheesemill said:**
> VMware Server no longer exists as a product.

The last version was discontinued in 2010 and reached end-of life in June 2011.

Your options for running VM's under a host OS are either VMware Workstation, VirtualBox, KVM or Xen.

What do you mean by "end of the life" ?
You mean I won't be able to setup a network testing lab environment with VMware server?
And I can do the same with VirtualBox and other the two you suggested?

I'm really confused and pissed off at the moment please respond. :(

---

### Post by Cheesemill on 2013-01-27
> **rex_dante said:**
> What do you mean by "end of the life" ?

It means that VMware Server is no longer supported, it wont run on a Ubuntu 12.04 machine.

There is a networking setup you can use in VirtualBox called a host-only network.
This is a private network that is only available from your VM's and the host OS.

---

### Post by haqking on 2013-01-27
> **rex_dante said:**
> What do you mean by "end of the life" ?
You mean I won't be able to setup a network testing lab environment with VMware server?
And I can do the same with VirtualBox and other the two you suggested?

I'm really confused and pissed off at the moment please respond. :(

virtualbox is free and opensource and will do everything you want.

For networking, use NAT if you want the VM's to have Internet access, bridged if you want them on the same segment as your host using DHCP or static for your LAN or host only or internal if you want a private network between only the VM's and/or host.

see the manual for more information [http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

---

### Post by rex_dante on 2013-01-27
> **Cheesemill said:**
> It means that VMware Server is no longer supported, it wont run on a Ubuntu 12.04 machine.
Okay. I got it. Kindly reply to my LAST question in my previous post sir. (sorry for being impolite, this thing is testing my nerves from 2 days and also got some graphical issues too) :((

---

### Post by haqking on 2013-01-27
> **rex_dante said:**
> Okay. I got it. So just reply to my LAST question asked above. :(

You might want to be more polite, we are all volunteers and the support is free and not a right ;-)

---

### Post by rex_dante on 2013-01-27
> **haqking said:**
> You might want to be more polite, we are all volunteers and the support is free and not a right ;-)
Edited my previous post sir. I feel really bad to behave like that. I didn't meant to do that. I'm sorry. :((

---

### Post by haqking on 2013-01-27
> **rex_dante said:**
> Edited my previous post sir. I feel really bad to behave like that. I didn't meant to do that. I'm sorry. :((

You can use Vmware server but it is not longer supported so not full featured or updated and I dont think will work in 12.04.

Virtualbox however will do everythying you need as outlined above.

Peace

---

### Post by rex_dante on 2013-01-27
> **haqking said:**
> You can use Vmware server but it is not longer supported so not full featured or updated and I dont think will work in 12.04.

Virtualbox however will do everythying you need as outlined above.

Peace
I think that too NOW. As I watched a video tutorial on it on YT. A guy was installing BT and XP together and both OS had their separate window. :3
Thanks for the support. :)

---

### Post by haqking on 2013-01-27
> **rex_dante said:**
> I think that too NOW. As I watched a video tutorial on it on YT. A guy was installing BT and XP together and both OS had their separate window. :3
Thanks for the support. :)

I have over 30 different virtual machines. some only talk to each other, some talk to the host, some have Internet access etc etc.

Virtualbox will do everything you want.

Peace

---

### Post by rex_dante on 2013-01-27
> **Cheesemill said:**
> It means that VMware Server is no longer supported, it wont run on a Ubuntu 12.04 machine.

There is a networking setup you can use in VirtualBox called a host-only network.
This is a private network that is only available from your VM's and the host OS.
Got it completely now. :3

Thank you very much man for your constant support. And please don't mind my kiddish behaviour. I was getting so pissed off on this thing pretty badly. I'm sorry. :((

---

