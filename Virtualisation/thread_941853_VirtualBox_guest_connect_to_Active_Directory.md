---
title: "VirtualBox guest connect to Active Directory"
date: 2008-10-08
forum: Virtualisation
---

### Post by shahgols on 2008-10-08
Hi everyone,

I have posted a message in the Networking section and seeing as nobody has responded there, I suppose that perhaps it would have been more appropriate to have posted it here.  This is the thread that I have posted:

[http://ubuntuforums.org/showthread.php?t=941738]("http://ubuntuforums.org/showthread.php?t=941738")

Basically, my question is about how to allow the guest OS, which is an XP Pro, to join my domain.  The host OS, Ubuntu, is connected using DHCP, but it  is not joined to the domain.  I have been able to successfully join XP to the domain in mvware, but vmware is so slow, it's intolerable.  Thanks in advance.

---

### Post by b0b138 on 2008-10-08
If I'm not mistaken, it has to do with the virtual networking. By default, vbox uses nat, which gives your guest an address of 10.x.x.x. VMware uses host/bridged networking so your ip comes from the dhcp server like any other physical computer. It seems the nat doesn't pass along all protocols properly.

You can setup vbox to use a host interface, but unfortunately is not as simple as vmware. I found a thread once with some working directions to set it up, but did not bookmark it. If I can find it I'll post it here for you.

---

### Post by shahgols on 2008-10-08
Thanks Bob, your clear explanation actually is great, since it gives me a hint as to what I should be looking for.  I'll look at virtualbox documentation to see if I can find anything.  If I am able to make this work, I'll post here so that others can benefit as well.

---

### Post by b0b138 on 2008-10-08
start here [http://ubuntuforums.org/showthread.php?t=346185](http://ubuntuforums.org/showthread.php?t=346185)

---

### Post by b0b138 on 2008-10-08
this one looks very useful too  [http://spinczyk.net/blog/2008/03/05/setting-up-a-bridged-network-for-virtualbox-on-ubuntu-linux/](http://spinczyk.net/blog/2008/03/05/setting-up-a-bridged-network-for-virtualbox-on-ubuntu-linux/)

---

### Post by shahgols on 2008-10-08
Bob, thanks a mill, greatly appreciate it.  I'll go through these articles and get back to you about the results tomorrow.

---

### Post by b0b138 on 2008-10-08
The instructions at that second link mostly work. Some of it goes over my head and this way is probably slighly different than what I've done before, but it works.

In a nutshell, you use a script to setup some bridging and tunneling "stuff". Here's mine currently, edited from the original to allow 2 vm's running at the same time using host networking. Each vm must call a different tap device.

```

#!/bin/bash
brctl addbr br0
ifconfig eth0 0.0.0.0
brctl addif br0 eth0

#if you have a dhcp-server uncomment this line:
dhclient3 br0

#If you have a static IP uncomment the following lines and
#change the IP accordingly to your subnet:
#ifconfig br0 192.168.178.5 up
#route add default gw 192.168.178.1

#Now we will create the tap device for the vm,!
# change your username accordingly
tunctl -t tap0 -u username
#Create another for each VM. This is only necessary for
#multiple VM's running at the same time.
tunctl -t tap1 -u username

#Now add the tap-device to the bridge:
ifconfig tap0 up
brctl addif br0 tap0
#Add more for each additional tap-device.
ifconfig tap1 up
brctl addif br0 tap1

```

According to the website, you should be able to reference the start and stop scripts from vbox, but i could not get that to work. I'm not sure if having the bridge and tap devices setup all the time would have any side effects for any other applications. If not the easiest thing to do would probably set the start script to run at systim boot to avoid having to run that then run vbox.

---

### Post by shahgols on 2008-10-09
Hi Bob, good news!  :)

The script from the second link worked like a charm for me.  All that I changed was to put my username in the right place, and uncomment the commands for dhcp and it worked on first try!  Thank you so much dude, and cheers to you.

Peace.

---

### Post by shahgols on 2008-11-14
Just wanted to post this here, just in case the web site (second link posted by Bob) is no more.  



setting up a bridged network for virtualbox on ubuntu linux (Host Interface)
by simon
linux, ubuntu

In order for this to run, you will most likely need a wired network connection, since most wireless-adapters won’t support bridged networking! This description is intended to be used with VirtualBox >= 1.4.0, since earlier versions handle the virtual networking differently due to kernel changes in 2.6.18 and later.

First of all, you’ll have to check the permissions on the device /dev/net/tun . The user running VirtualBox with bridged networking needs to have access to this device. The easiest way to do this is by chown’ing the group vboxusers to it:

sudo chown :vboxusers /dev/net/tun
sudo chmod 0660 /dev/net/tun

You will also have to install the package bridge-utils and uml-utilities:

sudo apt-get install bridge-utils uml-utilities

Now we will create 2 scripts which are executed when the virtual machine starts/stops. I will create those scripts in my home dir. Here is the start script, I called it starttun.sh:

#!/bin/bash
brctl addbr br0
ifconfig eth0 0.0.0.0
brctl addif br0 eth0

#if you have a dhcp-server uncomment this line:
#dhclient3 br0

#If you have a static IP uncomment the following lines and

#change the IP accordingly to your subnet:
#ifconfig br0 192.168.178.5 up
#route add default gw 192.168.178.1

#Now we will create the tap device for the vm,!

# change your username accordingly
tunctl -t tap0 -u simon

#Now add the tap-device to the bridge:
ifconfig tap0 up
brctl addif br0 tap0

Now you’ll have to create the stop script, i called it stoptun.sh ;)

#!/bin/bash
#bring the interfaces down
ifconfig tap0 down
ifconfig br0 down
brctl delif br0 tap0
brctl delbr br0

#now setup your network-interface again
#for dhcp uncomment the following line
#dhclient3 eth0

#For a static IP uncomment the following lines and change them accordingly:
#ifconfig eth0 192.168.178.5
#route add default gw 192.168.178.1 dev eth0

Finally you’ll have to make the scripts executable:

sudo chmod ug+x starttun.sh
sudo chmod ug+x stoptun.sh

It’s time to set up VirtualBox to use the interface. For this go to the SetUp of your Virtual Machine under Network and tell VirtualBox to start/stop thescripts, when the VM is started/stopped. To do this, select “Host Interface” under Attached To. As Interface Name you use “tap0&#8243; and for the startscript you use:

“gksudo /home/YOURHOMEDIR/starttun.sh”

For the stopscript accordingly:

“gksudo /home/YOURHOMEDIR/stoptun.sh”

Note: If you use KDE, you’ll have to use kdesu instead of gksudo

---

### Post by Urinemachine on 2008-11-21
i followed shahgols instructions but I get:


Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}


Any help?

---

### Post by astrotoad on 2009-01-27
For those still having problems with this issue, I suggest trying the Personal Use and Evaluation License (non-free) version of VirtualBox (v.2.1.2).  With this update, I was able to connect my virtual XP guest to my department's domain without using the discussed bridge scripts.  Here is an excerpt from the updated manual...

> 6.5 Host Interface Networking

With Host Interface Networking, VirtualBox uses a device driver on your host system that filters data from your physical network adapter. This driver is therefore called a “net filter” driver. This allows VirtualBox to intercept data from the physical network and inject data into it, effectively creating a new network interface in software. When a guest is using such a new software interface, it looks to the host system as though the guest were physically connected to the interface using a network cable: the host can send data to the guest through that interface and receive data from it. This means that you can set up routing or bridging between the guest and the rest of your network.

For this to work, VirtualBox needs a device driver on your host system. The way Host Interface Networking works has been completely rewritten with VirtualBox 2.0 and 2.1, depending on the host operating system. From the user perspective, the main difference is that complex configuration is no longer necessary on any of the supported host operating systems.

With the new mechanism, to enable Host Interface Networking, all you need to do is to open the Settings dialog of a virtual machine, go to the “Network” page and select “Host Interface” in the drop down list for the “Attached to” field. Finally, select desired host interface from the list at the bottom of the page, which contains the physical network interfaces of your systems. On a typical MacBook, for example, this will allow you to select between “en1: AirPort” (which is the wireless interface) and “en0: Ethernet”, which represents the interface with a network cable.

Cheers.

---

### Post by sarnobat on 2011-12-28
> **b0b138 said:**
> If I'm not mistaken, it has to do with the virtual networking. By default, vbox uses nat, which gives your guest an address of 10.x.x.x. VMware uses host/bridged networking so your ip comes from the dhcp server like any other physical computer. It seems the nat doesn't pass along all protocols properly.

You can setup vbox to use a host interface, but unfortunately is not as simple as vmware. I found a thread once with some working directions to set it up, but did not bookmark it. If I can find it I'll post it here for you.

Thank you so much for the info_, _[b0b138]("http://ubuntuforums.org/member.php?u=485187"). What I couldn't solve in 2 years of insistence on VirtualBox, I solved in 1 hour by using VMWare (once I figured out that I should be using player, not server, and installed Ubuntu).

I'm hoping this will be the dawn of a new era in my computing use now that I can access my Windows files shares and I have you to thank.

---

