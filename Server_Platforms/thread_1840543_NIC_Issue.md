---
title: "NIC Issue"
date: 2011-09-07
forum: Server Platforms
---

### Post by Watchlord on 2011-09-07
Alright, I have an HP Proliant DL380 G3 running Ubuntu Server 11.04. I pluged in an ethernet cable and now it worked like a dream. I was able to host a proxy, website, minecraft server, and ventrilo simultaneously. I had that NIC setup with a static IP address. The HP Proliant DL380 G3 has two Broadcom NC7781 PCI-X Gigabit NICs. I wanted to utilize both cards. My idea was to split my connection to the server with a switch and assign each card a seperate IP and port forward different services to different cards. I know the ethernet bottleneck will still be there, but spreading the load over two cards wouldn't hurt.
 
Here was my setup.
 
[Router]-----[Switch]=====[Server] 
 
I was still able to use this after I plugged everything in. Everything worked fine on the first card. I was able to host and access the internet. 
 
Here is where things blew up in my face: eth0's IP is 192.168.1.20, so I decided to assign 192.168.1.21 to eth1. 
 
Now the only thing I can acess with eth1 is my router. No internet. eth0 is not not usable at all. Help. I am unable to restore my previous setup.

---

### Post by Entilza on 2011-09-07
Looks like you have to reconfigure /etc/network/interfaces.

You should be able to find some doc's on how to configure the eth0.

Afterwards you can setup ethernet bonding which does load balancing on your 2 NIC's.  I can show you how to set this up once you have your eth0 working again.

---

### Post by Watchlord on 2011-09-08
> **Entilza said:**
> Looks like you have to reconfigure /etc/network/interfaces.

You should be able to find some doc's on how to configure the eth0.

Afterwards you can setup ethernet bonding which does load balancing on your 2 NIC's.  I can show you how to set this up once you have your eth0 working again.

I deleted ifupdown eth0 somehow. I created an automatic connection (like I did the last times I tried it) and it finally worked this time. Please show me how to set up load balancing with static IP address.

I renamed my devices from the default eth0 and eth0 after fixing. This caused no problems after a reboot.
Device names: NIC1 and NIC2
Functional connections: Wired connection1 and Auto NIC2

---

### Post by Entilza on 2011-09-08
Ok I figured you'd get your computer back up.  My example will be with eth0 and eth1 so change it accordingly for the ethernet bonding.

Step 1:  sudo apt-get install ifenslave

Step 2:  Append to or create /etc/modprobe.d/aliases.conf

alias bond0 bonding
options bonding mode=0 miimon=100

Step 3:  Modify /etc/network/interfaces

Here is an example you will have to change accordingly.  Note the slaves line with eth0 eth1

auto lo
iface lo inet loopback

auto bond0
iface bond0 inet static
        address your.server.address.here
        netmask 255.255.255.0
        gateway your.gateway.address.here
        slaves eth0 eth1

Step 4: sudo /etc/init.d/networking restart

You may have to reboot to get your old network unregistered so be sure to do that.

Then once you have it running the fun test can begin by doing a ping, and unplugging one of the network cards and watch it continue to work.  Replug then unplug the other one you should see a small delay but it should continue to work.

The bonding mode=0 is important here mode=1 will offer redundancy but no performance increase. For you, I believe you should try mode=0 for load balancing to improve performance.

Anyway good luck let me know how it works.

---

### Post by Watchlord on 2011-09-08
Thank you. Curently I have Minecraft on eth0 and LAMP, glype, and Ventrilo on eth1 via port forwarding. What is the advantages and disadvantages of bonding the cards compared to the current setup. What will this do IP wise? Create a virtual single card? Sorry for the noobness.

---

### Post by Entilza on 2011-09-08
It will create a single card called bond0  which both nic's communicate with, theoretically benefitting all applications.  You can try different bonding modes.  You can read up on them just google around.

It will also give redundancy so if one card failed the other would continue.

You can always reverse it back just keep a copy of your interfaces then remove the modprobe.

---

### Post by Watchlord on 2011-09-09
Thank you, problem solved.

---

