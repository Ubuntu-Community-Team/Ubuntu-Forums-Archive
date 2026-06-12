---
title: "Virtual Box install"
date: 2014-06-24
forum: Virtualisation
---

### Post by kakashi_12 on 2014-06-24
Installed Kubuntu in a virtual box to try it out. It did not find the Network driver I guess. Or something's not set right. I can't find the "Hardware Driver" utility to have it search for the drivers. And I tried to install Guest Additionals, but that was no help.

---

### Post by SeijiSensei on 2014-06-24
The standard emulated network card is an Intel Gigabit adapter, which Linux supports out of the box.  

Are you using "NAT" mode or "Bridged?"

---

### Post by kakashi_12 on 2014-06-24
Neither. Host Only Adapter.

---

### Post by kakashi_12 on 2014-06-24
Switched to NAT. That worked! Thanks.

Although, I think I switched it cause it wasn't working in the other virtual machines. Let me check the others.

---

### Post by kakashi_12 on 2014-06-24
Ya, NAT does not work for Windows 7. Infact I can't find anything to work for that OS. It just won't find the driver. And the guest additions didn't do crap for it.

I know this isn't a windows forum, but i don't suppose you have an idea what to do for that?

---

### Post by SeijiSensei on 2014-06-25
Is this Win7 inside Ubuntu, or Win7 inside Windows? If the latter, you might need to enable [Internet Connection Sharing](http://windows.microsoft.com/en-us/windows/using-internet-connection-sharing#1TC=windows-7) to use NAT.

If you use a bridged connection, the VM will be treated like any other machine on the network.  It will receive an IP from your DHCP server and have the same relationship to the network that the host does.

---

### Post by kakashi_12 on 2014-06-25
Win7 inside Win7. Do I enable ICS inside the host or guest machine?
Sounds like the bridge would be easier.

---

### Post by kakashi_12 on 2014-06-25
Nope bridged did not work. It still can not find the driver for the NIC. I even installed the Guest Additions and it still can't find the driver. How will it find it if it can't connect to the internet? Sounds like a Virtual Box problem.

---

### Post by Bucky Ball on 2014-06-25
*Thread moved to **Virtualisation**.*

No, this is not a Windows forum. Please post a new thread regarding Windows issues in 'Other OS/Distro Support'. Better still, improve your chances by posting in a Win forum. Continuing down the Win support path will lead to this thread being moved there anyway as you are steering away from your original support request. Thanks.

---

### Post by at_first_light on 2014-07-18
It sounds like you are using custom network settings? The default network settings used by virtualbox should provide network access (internet) to all supported operating systems provided the virtual machine was created using the proper OS selection from the list; guest add-ons aren't required. In the case of Ubuntu 64bit and Windows 7 64bit the default settings are NAT with a Intel PRO/1000 MT Desktop adapter. 

Out of curiosity what tool did you use to determine that the virtual machine isn't getting network access? Are you running anything on the host operating system that might be blocking it (eg: a firewall setting).

---

### Post by TheFu on 2014-07-18
> **kakashi_12 said:**
> Win7 inside Win7. Do I enable ICS inside the host or guest machine?
Sounds like the bridge would be easier.

ICS is not needed.

In the future, it is best to clearly say what the hostOS is and which clientOS is being used. We can't read minds.

Inside the guestOS, only the virtual network card provided by Vbox is seen. The real hardware doesn't matter.  The Intel PRO/1000 is the default and fully supported by Windows-vista and later.  For any Linux, always choose the virtio device - for higher performance and lower overhead.  There is a virtio driver for Windows - get it from Redhat - but I haven't found the extra trouble to be worth the effort and the doesn't seem to be any performance increase. 

HostOnly networking limits the network to only that subnet INSIDE the virtual machine.  If you want VMs to talk externally, use either NAT or bridge networking. This is documented clearly in the vbox help files at some length.  I always use bridged networking.

---

