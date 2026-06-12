---
title: "Help with virtualization solution"
date: 2007-04-19
forum: Server Platforms
---

### Post by yagiska on 2007-04-19
Just hoping someone can help me figure out a solution.

I have three machines running Ubuntu 7.04, two laptops and a desktop used as a server. Due to college, there are times I need to run XP. Not wanting to have to leave my Linux environment, running Windows using virtualization seems to be the best solution.

However, my desktop server has much newer hardware (Core 2 Duo), therefore, I would like the server to host the virtual install of Windows, and allow the laptops to connect to the server to use Windows remotely.

However, I don't want to use the laptops as thin clients entirely. I would like to function just as if I was running Qemu locally, with Windows in it's own window inside of Gnome, except that Qemu would be running on the server and not the client.

I'm a little stumped on how to execute that however.

Thanks.

Kris

---

### Post by sjpwong on 2007-05-02
I am in the middle of setting up something very similar.

That is quite possible with qemu or kvm, you run them "headless" ie with the graphical display sent via VNC rather than locally on the server machine.  Vmware Server is also a possibility but I am yet to try that.

Look at these pages:

[https://help.ubuntu.com/community/KVM?highlight=%28kvm%29](https://help.ubuntu.com/community/KVM?highlight=%28kvm%29)
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

To do this installation on my server (that has NO X) I used:

```
kvm -no-acpi -m 512 -cdrom /dev/scd0 -boot d -vnc 192.168.8.108:0 -k en-us -localtime -redir tcp:3389::3389 windowsXP.img

```

Beware that kvm in Feisty core dumps(!) when the virtual machine reboots :( 

Good luck!

---

### Post by rickyjones on 2007-05-02
I would personally run the free Vmware server on your desktop. You can connect to it from your laptop using the client administration utility that is included and interact with the virtual machine as though it is on your laptop. Sure it's not opensource but it works quite well and is proven.

-Richard

---

### Post by sjpwong on 2007-05-02
I am literally about to try the vmware server installation.

Got any good links on creating the VM headless or should I do it on another machine with X then copy it to the target server?

---

### Post by rickyjones on 2007-05-02
> **sjpwong said:**
> I am literally about to try the vmware server installation.

Got any good links on creating the VM headless or should I do it on another machine with X then copy it to the target server?

Sorry, don't have any good links. If you follow the direction for installing VMWare server (I think there is a how to in the tips/tricks section of the forums) then it should be all console commands. You should be able to configure the VMWare Server install via SSH or local terminal access. After that install the client tools on your laptop (should be a simple download from vmware.com). Run the tools after you have them installed and select Remote Host as the VMWare server. Point it to your host and enter in a UN/PW with the correct credentials. You will then be able to create new VMs from your laptop - everything will take place on the server though.

Hope it helps!

-Richard

---

### Post by veloce on 2007-05-03
I run a number of instances of vmware server on my laptop and around the office.  Rather than use the vmware server console, I connect to the virtual machines with gnome-rdp.  It's faster and the windows work within gnome much better.  Full screen is easier to switch to / from as well. 

vmware server is running on one ubuntu server that has no gui installed. So the guis on this only work remotely.

---

### Post by garba on 2007-05-03
what about taking a look at virtualbox? it comes with a vnc server, i've been using this proggie for a while and find it lovable

---

### Post by sjpwong on 2007-05-04
> **garba said:**
> what about taking a look at virtualbox? it comes with a vnc server, i've been using this proggie for a while and find it lovable

I tried it but the binaries are not for business use.  I could compile but would rather not waste time.

I have now had a chance to use vmware server and it is unbelievable!  On my laptop (Thinkpad T60, Intel Core2 Duo T7200 2GHz) running Windows XP is like running it natively!!

For the server it can run headless too which is a benefit.

---

### Post by bcmiller on 2007-05-06
I would prefer to do this with VirtualBox

It runs perfectly and it has VNC built in plus it's opensource as well. 

My problem is that it appears to be on a different network the IP is 10.etc...  instead of my home network IP 192.168... I have not been able to find much help on the VirutalBox forum or IRC.

Does anyone know the answer?

---

### Post by garba on 2007-05-06
attach your virtual box guest os to a tap0 interface and then bridge your tap0 interface and physical eth interface together, this way your virtual machine will behave as if it were directly  connected to your lan switch, then you can vnc over to your virtual windows box... please note that you can use window's native vnc server, to which you can connect through the client for terminal servers that comes with ubuntu... does all of this make any sense to you? if it doesn't lemme know

---

### Post by bcmiller on 2007-05-06
> **garba said:**
> attach your virtual box guest os to a tap0 interface and then bridge your tap0 interface and physical eth interface together, this way your virtual machine will behave as if it were directly  connected to your lan switch, then you can vnc over to your virtual windows box... please note that you can use window's native vnc server, to which you can connect through the client for terminal servers that comes with ubuntu... does all of this make any sense to you? if it doesn't lemme know
[URL="http://virtualbox.org/wiki/Automatic_Bridge_Ubuntu"]
I tried this tutorial from the VirtualBox site[/URL]  and it gave me the error below

```
Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

I don't know what a tap0 interface is... I'd love to get that going if you can provide any additional information.

---

### Post by garba on 2007-05-07
a tap interface is a user mode network interface, gotta do some research yourself here, your tap interface will then be connected through a virtual cross table to your guest virtual machine, now to make your virtual machine accessible through eth0 you can either set up a prper routing table on your host machine or bridge tap0 and eth0 together as to form a network bridge: think of a bridge as a software switch

---

### Post by bcmiller on 2007-05-07
I'll look into it, thanks

I am looking into this howto for the tap0 interface later

for my reference and anyone else with a similar issue ;p

[http://ubuntuforums.org/showthread.php?t=179472](http://ubuntuforums.org/showthread.php?t=179472)

---

### Post by Chayak on 2007-05-09
I may be biased as I am part of VMware's core customer program but it's probably one of the most useful tools I have in my job.  I personally have an XP VM on one of my servers that I can use remote desktop or VNC to get into when I need it.  I also have a few thin clients set up on the SSBN's  I supervise for general crew use to check/write emails home that connect to VM based desktops and make life easier for the boat adminsitrators.  It's actually prevented a fail to sail for more than one strategic missile unit because of hardware failures and using the VMs on other machines.

---

### Post by Betelgeuse on 2007-05-09
Here is what I do with vmware server :

I'm using kubuntu for my daily computer needs and I have to use windows 2000 for my job. I'm a windows software developer and I have to use ms sql server and IIS to run .asp files I write. 
I have a desktop and a laptop PC and both are running Kubuntu feisty now. I've installed vmware server on both of the machines. it's now easier to install vmware server, it's in the ubuntu commercial repositories, so just enable the commercial repos in your sources list and give the command :

sudo apt-get update
sudo apt-get install vmware-server

I have a virtual machine in vmware server, it's running ms sql server and windows 2000 and IIS and ms visual studio. When I have to do job work, I just open the vmware server console and run my virtual windows machine. When I have to use my laptop, I'm running vmware server console and connect to my desktop machine and the virtual machine runs at the desktop machine and I'm using it from the laptop. When I go out, I simply copy the virtual machine files from desktop to laptop and run the virtual machine on the laptop. vmware server saves me from dual booting... :)

---

### Post by sjpwong on 2007-05-09
Good one Betelgeuse!

Tip for young players, to enable network access to your virtual machine (VM), simply edit /etc/vmware/vmnet8/nat/nat.conf and in the [incomingtcp] or even [incomingudp] add an entry for the local port you want forwarded to the virtual machine.

For example, to enable Remote Desktop (RDP) access from your LAN/Local machine to the virtual machine add:

```
[incomingtcp]
# Remote Desktop
3389 = 192.168.111.129:3389

```

Note that you need to check what IP address the VM is picking up.  I did it from within the VM.  If you want to be "smarter" look in /etc/vmware/vmnet8/dhcpd/dhcpd.leases ;-)

Enjoy!

---

### Post by Betelgeuse on 2007-05-09
I do not use NAT or host only networking on vmware server. I've said no to those when it asked me on configuration script. I'm only using bridged networking and my virtual machines are getting their IP from my dhcp server and I've reserved their MAC adresses so they always getting the same IP. 
The only issue iw when I have to use wireless networking on my laptop, I coul not bridge the virtual machines to wireless network, maybe it's because there was some kind of mac filter on the wireless network. But I do not use wireless anymore, I've dropped my laptop from my lap and my usb wireless device is now broken.

---

### Post by sjpwong on 2007-05-09
> **Betelgeuse said:**
> I do not use NAT or host only networking on vmware server. I've said no to those when it asked me on configuration script. I'm only using bridged networking and my virtual machines are getting their IP from my dhcp server and I've reserved their MAC adresses so they always getting the same IP. 

The default Feisty vmware server installation uses NAT.

> **Betelgeuse said:**
> The only issue iw when I have to use wireless networking on my laptop, I coul not bridge the virtual machines to wireless network, maybe it's because there was some kind of mac filter on the wireless network. But I do not use wireless anymore, I've dropped my laptop from my lap and my usb wireless device is now broken.

Actually I don't believe it is possible to directly bridge wireless and Ethernet network devices due to fundamental ?protocol differences.  You need to use a something that does some magic.  Not sure what though.

---

### Post by Betelgeuse on 2007-05-09
> **sjpwong said:**
> The default Feisty vmware server installation uses NAT.
I'm manually running the vmware-config.pl after the installation to disable the host only and NAT networking. I like disabling the things I do not use. :popcorn: 


> **sjpwong said:**
> 
Actually I don't believe it is possible to directly bridge wireless and Ethernet network devices due to fundamental ?protocol differences.  You need to use a something that does some magic.  Not sure what though.
The magic was breaking the wireless USB device by dropping the laptop from my lap. :(  Now I'm using and ethernet cable with may laptop and bridged networking works fine. :) I think I'll have to use some NAT networking on my wireless device but currently I have no wireless on my laptop.

---

