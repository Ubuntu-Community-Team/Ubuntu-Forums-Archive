---
title: "VMware workstation questions"
date: 2014-04-12
forum: Virtualisation
---

### Post by nomenkultur on 2014-04-12
I have never used VM's or virtualization since I prefer bare metal installs, due to hardware compability issues I have no choice but to use VMware workstation to run ubuntu but being new I have a couple of quick questions:

 - I wish to completely isolate windows8 from the internet, I want to have only a network connection in my virtual machine running ubuntu... I wasn't able to do this: If I disconnect my wifi in windows my virtual machine has no internet access. My question:  In order to have internet in my ubuntu virtual machine do I have to have my wi fi connection up in windows8??

 - Vmware workstation emulates the ethernet port but it has no option to emulate the wi fi card... is it because the drivers are not compatible with ubuntu?

 - am I wasting my time with vmware workstation since what I set out to do, isolate windows from the internet, is completely impossible if I want to have a network connection in my VM?

 thanks for bearing with me

---

### Post by ajgreeny on 2014-04-12
Yes, don't waste time trying to do that as it is totally impossible as far as I'm aware with the virtualisation applications available at present, eg VMware or VirtualBox.

Who knows what might happen in the future, but I wouldn't hold my breath waiting.

---

### Post by Antony_Nikrooz on 2014-04-17
Some thoughts: Use a USB wifi adapter (that has linux drivers) and use a USB passthrough in vbox. Or use bridged networking (wifi may fail here, you'll probably need wired), then set the IP config in windows to something that doesn't work, but give your linux machine a sensible IP address / route

---

### Post by RichardET on 2014-04-19
> **nomenkultur said:**
> I have never used VM's or virtualization since I prefer bare metal installs, due to hardware compability issues I have no choice but to use VMware workstation to run ubuntu but being new I have a couple of quick questions:

 - I wish to completely isolate windows8 from the internet, I want to have only a network connection in my virtual machine running ubuntu... I wasn't able to do this: If I disconnect my wifi in windows my virtual machine has no internet access. My question:  In order to have internet in my ubuntu virtual machine do I have to have my wi fi connection up in windows8??

 - Vmware workstation emulates the ethernet port but it has no option to emulate the wi fi card... is it because the drivers are not compatible with ubuntu?

 - am I wasting my time with vmware workstation since what I set out to do, isolate windows from the internet, is completely impossible if I want to have a network connection in my VM?  I am just curious - why all the trouble?  why not run the network through Win. 8?

 thanks for bearing with me

If you select bridged instead of NAT, and assign the VM to its own networking card, it should work as you want.  Have you looked on the VMware support site?

---

### Post by wrchis on 2014-04-20
Setting your Windows firewall to only allow VMWare (or however your firewall sees the virtual machine) traffic to pass it might work too if you only have one network card. You might have to use a third party firewall to do that though, I am not sure how fine grained the control is on the built-in Windows one.

---

### Post by dcstar on 2014-04-23
You have things the wrong way around. VM's use the **host** resources, if you want to "isolate" Windows 8 from the Internet put it in a VM without a network connection.

You can use Ubuntu as a host platform, convert your existing Windows 8 with the free VMware tool to a VM and run it inside Ubuntu.

---

### Post by yallaen on 2015-04-05
This is probably late to the party; I run Kali Linux in a VM all the time and it's isolated from the network. I have it set to HOST ONLY, and it remains isolated within the VM lan. VMWare will assign it a different IP address via DHCP internally. It's not allowed to go outside of the host. I've tested several times, and it does not tranverse the host's NIC card. I have several VMs set up in host mode; I use it for my virtual network to practice pentesting on. That way, I'm safe from accidently launching an attack OUTSIDE into the real world, which would be BAD.

I hope that helps anyone that has similar questions!

---

