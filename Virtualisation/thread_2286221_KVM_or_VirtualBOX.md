---
title: "KVM or VirtualBOX"
date: 2015-07-10
forum: Virtualisation
---

### Post by luis67 on 2015-07-10
Hey everyone 
I'm planning to virtualize 6 Windows VM with ubuntu server as host but I'm not sure what environment choose if KVM or VirtualBOx
I have read about KVM it's fluent and don't use too much resources I'm not worried about to use the terminal or learn about it ,secondly, I have been using virtual box since ever but only to run windows as a test environment and I need to choose a reliable, well documented and scalable environment 


any advice?

---

### Post by Kai_Pirttimki on 2015-07-15
I have been using KVM in production servers since 2009 and I absolutely love it. It is stable as rock and really simple to use once you get to know it. There are nowadays many GUIs for KVM and libvirtd if you feel that you  want one... Haven't really had time or need to test those myself yet so I  cannot really make any recommendations. KVM is quite scalable too, you can use it on a single computer or in larger virtualization farms. NFS and iSCSI are your friends there...

Virtualbox is ok too. I use it daily also but IMHO it should be used only in desktop environments and maybe only for testing purposes. But that is only my opinion.

Basically it boils down to what you are planning to do with your six virtual machines...

---

### Post by jason_gibson2 on 2015-07-15
I go by the simple rule of KVM for virtualizing servers, Virtualbox for virtualizing anything with a Gui / point & click. I wouldn't use it any other way on my laptop. I use KVM exclusively on my htpc / ubuntu server.

---

### Post by CharlesA on 2015-07-15
I use KVM for anything I can connect remotely to, but I have those hosted on my home server. If I use VirtualBox, it is likely because it is running on my desktop and I have to have access to the GUI to do anything with it.

I've run into less issues with KVM than VirtualBox, though. The "kernel modules not loaded" error comes to mind.

---

### Post by luis67 on 2015-07-15
Thank You! KVM chose because it is very easy to use, plus I can import my other OS from physical Pc's

I let you some links that I used to convert my VM and configure KVM



[Configure KVM]("http://www.dedoimedo.com/computers/kvm-intro.html")

[Convert VM to KVM Images]("http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/")

---

### Post by ben152 on 2015-07-16
I'm "new" to Ubuntu so I'm probably not the best source but none the less, I have had good luck using Virtual Box. I wasn't even aware of KVM, guess I'll have to  go and experiment now... ;)

---

