---
title: "Connecting VNC to KVM VM"
date: 2010-02-28
forum: Server Platforms
---

### Post by raghavan-jay on 2010-02-28
I am running Ubuntu 9.10 server and have enabled virtualization using KVM.

I have configured a CentOS VM and verified it is running within the server. Next I would like to connect to this VM from a Microsoft Windows VNC client. The VM image, is enabled with vnc and was configured with the networking:default option

I do not understand bridge networking and if it is needed.

My plan is to customize my VM and clone it, each exposed with a separate VNC port.

Any suggestions/guidance would help.

Thanks!

---

### Post by kiranmurari on 2010-03-02
Hi,

In order access the VM using VNC client from your windows machine, you need to start the VM with "-vnc <DISPLAY>" option.
   
To connect to the VM Using VNC client, use the IP address of the Ubuntu server followed by the display number.
Ex: A.B.C.D :1, if you have specified "-vnc :1" while starting the VM instance.
   
By default, the network mode is configured as NAT. If you want the guest to appear as another host on the LAN, 
visible to the rest of the network, you will have to use bridged networking.
For more information, please see: [https://help.ubuntu.com/community/KVM/Networking#Creating%20a%20network%20bridge%20on%20the%20host](https://help.ubuntu.com/community/KVM/Networking#Creating%20a%20network%20bridge%20on%20the%20host)
   
Hope this helps.

---

### Post by raghavan-jay on 2010-03-02
[QUOTE=kiranmurari;8904143]Hi,

In order access the VM using VNC client from your windows machine, you need to start the VM with "-vnc <DISPLAY>" option.
   
To connect to the VM Using VNC client, use the IP address of the Ubuntu server followed by the display number.
Ex: A.B.C.D :1, if you have specified "-vnc :1" while starting the VM instance.
   
By default, the network mode is configured as NAT. If you want the guest to appear as another host on the LAN, 
visible to the rest of the network, you will have to use bridged networking.

Thanks for the suggestion.

I have since enabled bridge networking. Now my host has IP a.b.c.1 and guest has IP a.b.c.2

I can ping a.b.c.2 from a.b.c.1 or anywhere in the network, but cannot even do a SSH login

How do I enable the -vnc option. I presume kvm should be started with that option?

when I do a ps aux  | grep kvm, it displays:
root      6983  8.8  4.6 3259100 381000 ?      Sl   Mar01  67:10 /usr/bin/kvm -S -M pc-0.11 -m 3000 -smp 1 -name vm02 -uuid 4a429914-4137-60d2-b7ba-1b3c0058a798 -monitor unix:/var/run/libvirt/qemu/vm02.monitor,server,nowait -boot c -drive file=/home/jay/VM/vm02.img,if=ide,index=0,boot=on -drive file=,if=ide,media=cdrom,index=2 -net nic,macaddr=54:52:00:7b:8f:6b,vlan=0,name=nic.0 -net tap,fd=17,vlan=0,name=tap.0 -serial pty -parallel none -usb -vnc 127.0.0.1:0 -k en-us -vga cirrus

when I type virsh and enter vncdisplay <vm name> I get
:0

Jay

---

### Post by raghavan-jay on 2010-03-02
I have a better understanding now.

VNC works - with localhost, ie only from the host server.

1. How do I enable my quest VM to have a static IP?
2. When I run multiple VMs - can they share the same IP?
3. How to change the default kvm startup option to use the static IP in (1)

Jay

---

### Post by kiranmurari on 2010-03-03
The following link might be helpful in understanding on how to configure static IP to the guest VM.
[http://blog.henricook.com/?p=86](http://blog.henricook.com/?p=86)

---

### Post by raghavan-jay on 2010-03-11
> **kiranmurari said:**
> The following link might be helpful in understanding on how to configure static IP to the guest VM.
[http://blog.henricook.com/?p=86](http://blog.henricook.com/?p=86)

The solution was to run a 
- VNC server in the guest
- modify iptables for the host to send/receive msgs from guest IP

Murari  - thanks for your help.

---

### Post by Cosma on 2010-03-12
Connecting to the guests VNC Server might be one way to solve this. But i think it's better to tunnel your VNC Client through SSH and then open the KVM-Servers VNC Display of the guests (in your case :0 or :5900).
 
If you want to connect from a Linux Computer then the easiest way is to use TightVNC. You can connect to your KVM-Servers localhost VNC like this:
 
vncviewer -via username@KVM-Server-IP 127.0.0.1:5900
(if you start another Guest, then virsh will show you a VNC-Display :1 which will run on localhost:5901 - you can check that with lsof -i)
 
You can do the same thing from a Microsoft Computer but then you also have to configure Putty or some other SSH Client to tunnel your VNC connection.
 
That way you don't have to install anything in your Guest-OS and can also connect to it while it is booting or while you are installing the OS. The only problem that i found with this solution is that the vncviewer connection stops as soon as the guest switches it's displayresolution (but you can just reconnect then).

---

### Post by HermanAB on 2010-03-12
Ewwww...

VNC is best avoided.  The best way to connect to servers is with SSH.  You can use Xmingw and PuTTY on Windows.

---

### Post by Cosma on 2010-03-12
> **HermanAB said:**
> Ewwww...
 
VNC is best avoided. The best way to connect to servers is with SSH. You can use Xmingw and PuTTY on Windows.
 
i think you read that wrong. it's about connecting to the display of a vm and there is nothing wrong with tunneling vnc over ssh for that purpose.

---

