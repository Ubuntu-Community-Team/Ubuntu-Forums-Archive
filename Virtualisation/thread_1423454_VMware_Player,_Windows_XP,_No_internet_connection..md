---
title: "VMware Player, Windows XP, No internet connection."
date: 2010-03-06
forum: Virtualisation
---

### Post by WutCake on 2010-03-06
Hello, i've just got Windows XP to work, but i cannot get the internet connection to work, why is this?

i'm using Ubuntu 9.04, Jaunty.
VMware Player 2.5

oh and, i tried VMware server 2 before but i couldnt get it to work because it didnt let me browse my computer files for ISO-file (LOL) and now it's not working either haha

[page that i used as guide to install from.]("https://help.ubuntu.com/community/VMware/Player")

---

### Post by fermulator on 2010-03-07
What type of network connection did you configure VMware to give your Guest WinXP OS?

[http://en.kioskea.net/faq/1166-vmware-the-different-modes-of-vmware-network](http://en.kioskea.net/faq/1166-vmware-the-different-modes-of-vmware-network)

[EDIT] - even better, see the mega thread on networking: [http://ubuntuforums.org/showpost.php?p=6122142&postcount=3](http://ubuntuforums.org/showpost.php?p=6122142&postcount=3)

---

### Post by WutCake on 2010-03-08
> **fermulator said:**
> What type of network connection did you configure VMware to give your Guest WinXP OS?

[http://en.kioskea.net/faq/1166-vmware-the-different-modes-of-vmware-network](http://en.kioskea.net/faq/1166-vmware-the-different-modes-of-vmware-network)


not sure, the default i guess?
i tried to use all modes between, didn't know you had to configure VMware to give you internet access :[

> **fermulator said:**
> 
[EDIT] - even better, see the mega thread on networking: [http://ubuntuforums.org/showpost.php?p=6122142&postcount=3](http://ubuntuforums.org/showpost.php?p=6122142&postcount=3)

okey, i'm confused, it says mostly stuffs about virtualBox in there.

---

### Post by WutCake on 2010-03-12
BuMp !

---

### Post by Exca on 2010-03-12
Can you show us the result of an **ifconfig** on your host and an **ipconfig /all** on your virtual XP ?
 
Can you try to **ping google.com** from both your Ubuntu host and virtual XP ?

---

### Post by WutCake on 2010-03-13
> **Exca said:**
> Can you show us the result of an **ifconfig** on your host and an **ipconfig /all** on your virtual XP ?
 
Can you try to **ping google.com** from both your Ubuntu host and virtual XP ?

ping'ing google works find on host,

however, it doesn't work at all on virtual.

Edit; way too big picture, see [link]("http://i39.tinypic.com/302vzg4.png") instead.
(the ifconfig was too big to screenshot, so i manged it into the pic)

---

### Post by Exca on 2010-03-14
For your virtual XP, type **ipconfig /all** (with a space between **ipconfig** and **/all** !) ;)
Can you also show us what the **route **command gives on your ubuntu host ?

Have you another virtual machine on this host ? (and can it access to the web ?)

---

### Post by WutCake on 2010-03-14
> **Exca said:**
> For your virtual XP, type **ipconfig /all** (with a space between **ipconfig** and **/all** !) ;)
with a space or no space doesn't make a difference.

> **Exca said:**
> 
Can you also show us what the **route **command gives on your ubuntu host ?
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.131.0    *               255.255.255.0   U     0      0        0 vmnet1
192.168.37.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```                   [SIZE=1](this is when VMware is turned off, dono if it make a difference.)[/SIZE]
> **Exca said:**
> 
Have you another virtual machine on this host ? (and can it access to the web ?)
 
yes, i'm also using VirtualBox, and that works just fine, but i wanted to see if VMware was better/faster.

---

### Post by Exca on 2010-03-14
> **WutCake said:**
> with a space or no space doesn't make a difference.

Ok, it seems that you do not have any network controller on this virtual machine. I use VMWare server 2, every time I create a new virtual machine, it automatically add a network controller and ask me which network I want this machine to connect to. (Bridged network, Natted network, or Host Only network).

> **WutCake said:**
> ```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.131.0    *               255.255.255.0   U     0      0        0 vmnet1
192.168.37.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```                   [SIZE=1](this is when VMware is turned off, dono if it make a difference.)[/SIZE]

According to this result, your 3 networks exist on this host. Can you check on your machine configuration if you don't forget to add a network controller ?

If you have one, go to your virtual XP, right click on computer (on the desktop) properties, and find your devices list (I don't know the exact name in English, I always use it in French ! ;)).

I think you should find here an unrecognised network adaptor (or an unknown device). If you're in this case, try to install the VMWare additional tools on this virtual machine, and reboot the virtual machine. I hope it will solve your problem !

---

### Post by dcstar on 2010-03-15
> **WutCake said:**
> 
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.131.0    *               255.255.255.0   U     0      0        0 vmnet1
192.168.37.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 **eth1**

```

And of course the VMware networking was specifically set up to use **eth1** instead of the default eth0, wasn't it?

---

### Post by WutCake on 2010-03-15
> **Exca said:**
> Ok, it seems that you do not have any network controller on this virtual machine. I use VMWare server 2, every time I create a new virtual machine, it automatically add a network controller and ask me which network I want this machine to connect to. (Bridged network, Natted network, or Host Only network).


I use VMware server 2, too, but i can't seems to add a isofile(or diskimg) so i got a diskimg from the website in the first post and VMware Player to install and run the GuestOS.


> 
According to this result, your 3 networks exist on this host. Can you check on your machine configuration if you don't forget to add a network controller 
machine configuration in GuestOS(winXP)?

> 
If you have one, go to your virtual XP, right click on computer (on the desktop) properties, and find your devices list (I don't know the exact name in English, I always use it in French ! ;)).My Computer -> Properties -> Hardware -> Device Manager, it says on the tab "other devices",  Ethernet Controller and Video Controller (VGA Compatible) with a yellow question mark on it as the icon.

> 
I think you should find here an unrecognised network adaptor (or an unknown device). If you're in this case, try to install the VMWare additional tools on this virtual machine, and reboot the virtual machine. I hope it will solve your problem !read above.
where is the "VMWare additional tools"(using VMwarePlayer!)? their website?


> **dcstar said:**
> And of course the VMware networking was specifically set up to use **eth1** instead of the default eth0, wasn't it?
probably, i don't know, as i said before, i wasn't too picky when installing the server.
but if that was the case, wouldn't bridged work anyway?

---

### Post by Exca on 2010-03-16
> **WutCake said:**
> I use VMware server 2, too, but i can't seems to add a isofile(or diskimg) so i got a diskimg from the website in the first post and VMware Player to install and run the GuestOS.

For VMWare Serve, you must have an ISO file in a DataStore on the Host Machine, but you can also use a device on your client machine, but it's another story ;)

> **WutCake said:**
> My Computer -> Properties -> Hardware -> Device Manager, it says on the tab "other devices",  Ethernet Controller and Video Controller (VGA Compatible) with a yellow question mark on it as the icon. (...)
Where is the "VMWare additional tools"(using VMwarePlayer!)? their website?

As long as Windows doesn't recognise the virtual network card, it won't access to internet, even for the bridget network.
To install VMWare Tools from VMWare Player, click on the "VM" Menu, and clic on "install VMWare Tools".

[IMG]http://sychlora.dvrdns.org/images/vmw_toolsinstall.png[/IMG]

Hope it helps!

---

### Post by WutCake on 2010-03-16
> **Exca said:**
> For VMWare Server, you must have an ISO file in a DataStore on the Host Machine, but you can also use a device on your client machine, but it's another story ;)

ok lol.


> 
As long as Windows doesn't recognise the virtual network card, it won't access to internet, even for the bridget network.
To install VMWare Tools from VMWare Player, click on the "VM" Menu, and clic on "install VMWare Tools".

[IMG]http://sychlora.dvrdns.org/images/vmw_toolsinstall.png[/IMG]

Hope it helps!
o_o
i feel so silly :( i didn't see the "install VMware Tolls"!

---

### Post by GrandVizier on 2010-03-19
I'm in a similar situation - I installed VMware Player on Ubuntu 9.10, installed XP on the VM and don't have access to the internet - as described previously, I looked and found that the Network Controller on XP wasn't registered - I installed the VM Tools, restarted and the Network Controller was ok, but the Ethernet Controller is still unrecognized 

when I run **ipconfig /all** on XP I get nothing 
here is **route** on my host:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
192.168.170.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.237.0   *               255.255.255.0   U     0      0        0 vmnet8
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

```
I'm going to try reinstalling the VM Tools (not expecting much from that) bt I can't figure out how I'm suppose to get the Ethernet drive for the VM recognized 
and not that I expect it matters at this point, but the host/client connection is NAT

oh, and i got my vmx from here:
[https://help.ubuntu.com/community/VMware/Player?action=AttachFile&do=view&target=WindowsXPVirtualMachine.zip](https://help.ubuntu.com/community/VMware/Player?action=AttachFile&do=view&target=WindowsXPVirtualMachine.zip)

---

### Post by GrandVizier on 2010-03-19
i don't know if this is the right solution, but its working now:
in the vmx file I changed
ethernet0.virtualDev = "e1000"
to
ethernet0.virtualDev = "vmxnet"

---

### Post by WutCake on 2010-03-20
> **GrandVizier said:**
> I'm in a similar situation - I installed VMware Player on Ubuntu 9.10, installed XP on the VM and don't have access to the internet - as described previously, I looked and found that the Network Controller on XP wasn't registered - I installed the VM Tools, restarted and the Network Controller was ok, but the Ethernet Controller is still unrecognized 

I'm going to try reinstalling the VM Tools (not expecting much from that) bt I can't figure out how I'm suppose to get the Ethernet drive for the VM recognized 
and not that I expect it matters at this point, but the host/client connection is NAT

could you give me the files that are needed from the windows CD? the windows isoCD i have, doesn't have those files, so i can't install VM Tools.

> **GrandVizier said:**
> i don't know if this is the right solution, but its working now:
in the vmx file I changed
ethernet0.virtualDev = "e1000"
to
ethernet0.virtualDev = "vmxnet"

i tried that, but no results (perhaps because i can't install VM Tools).

---

### Post by WutCake on 2010-03-25
nvm about those files, i just clickt cancel and it kept installing, but probably skiped something' 
but it's all fine now, Internet works :D

---

