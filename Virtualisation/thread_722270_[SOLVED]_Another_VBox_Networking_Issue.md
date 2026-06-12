---
title: "[SOLVED] Another VBox Networking Issue"
date: 2008-03-12
forum: Virtualisation
---

### Post by Live-Dimension on 2008-03-12
I've spent a few days trying to figure this out with no avail.

Basically this is my setup.

Ubuntu Gutsy Desktop.
VirtualBox Closed-Source, Latest.
Windows XP Pro, GuestOS.
Wireless Connection to router.

What I used to be able to do on WinXP was use VPC2007(VM software) to make a mini-testing server. Instead of doing one fix, uploading to the server, testing, it was almost instant at due to it all being done on the same machine/network.

I've been unsuccessful with doing the same now that I've moved to Ubuntu. I however need access to my programs (Photoshop, Dreamweaver, etc). I've setup apache, php, etc on the Guest.

What I want to do is give the GuestOS it's own IP. I've gone though the instructions a good 6-8 times. The best I've been able to do is nuke my wireless somehow, thankfully a restart tends to fix it.

Also the tricky thing - the router I''m connecting to uses MAC filtering - so the router needs to see that my machine is using the wireless card's MAC number, or I'll never be able to connect. ATM I've left it as clean as I can till someone can help me sort this out.

**edit** I need the ability for other computers (especially my host, if other pc's aren't possible it's ok) to connect to my guest, which is impossible until this is solved.

---

### Post by Hero of Time on 2008-03-12
What you need is Bridging. Read chapter 6, 6.3 and 6.5 of the user manual to know how to set up bridging. Simply put, you need to apt-get install bridge-utils, create a bridge interface, put your wlan in it, create a vbox0 interface for host interface to function with your virtual machine, put that in the bridge too and you're done. Set up the correct IP address and it should work. If it doesn't, then you might need to add the virtual mac address to your router. I haven't tried this bridging with wireless but it should work. You might want to check the VirtualBox forums for more info on this subject.

---

### Post by Live-Dimension on 2008-03-12
I've done that 6-8 times :P But I can never get it working?

In the attachment is the details, if anyone can help me get the right IP from that?

And no I can't change the router =\
Does VMWare have the same issue with its products?

---

### Post by Hero of Time on 2008-03-12
What doesn't work? Getting the bridge up, adding interfaces to the bridge, create the vbox0 interface and set it to your VM, get the proper connection? What you need to do is set your wlan0 ip configuration to the bridge and leave the wlan0 for as it is (it should be auto wlan0, iface wlan0 inet manual in the interfaces file). Also, do you use network manager for your wireless? Do you get any scanning results if you scan for wireless networks on your bridge?

Google for some tutorials, I will try to get it working too somehow with my own setup. If I have it working, I will report here.

---

### Post by Live-Dimension on 2008-03-12
Just the connection would never work.
I've downloaded and installed VMware Workstation trial, and I must say its actually working o.o

Even at the price difference ($200/free) it will save me alot in the long run being a developer. I'll keep the trial on and look around from time to time, see if a fix can be found for vbox I guess.

Thanks for the help.

**edit** The more and more I use VMware, the more and more I dislike it, and prefer VBox. It was the same with XP too :P.
Guess I'll just play with vbox more.

**edit2** This error always shows when I go and restart the network with 
sudo /etc/init.d/networking restart

*Waiting for br0 to get ready (MAXWAIT is 32 seconds)*

But nothign seems to happen (But i must check if it times out in 32 seconds, or if its like, 25 seconds then finnishes)

---

### Post by siepo on 2008-03-12
You don't actually need a bridge. You can simply create a virtual network interface:

tunctl -t tap0 -u <username>
ifconfig tap0 <some ip number>

You could put this in /etc/rc.local if you want it to come up every time. Don't put anything in /etc/network/interfaces since this is a strictly internal affair.

The big difference between VB and VMware is that VB doesn't involve the host in the virtual networks it creates, so you have to do that by other means. But once it has been set up, it is less of a hassle.

---

### Post by Live-Dimension on 2008-03-12
ok Here is my interfaces file

```

auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
    bridge_ports wlan0
```

And following the first set of instructions, the terminal data
```

chris@chris-ubuntu:~$ sudo /etc/init.d/networking restart
[sudo] password for chris:
 * Reconfiguring network interfaces...                                          
Waiting for br0 to get ready (MAXWAIT is 32 seconds).
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/br0/00:0e:2e:85:8d:a7
Sending on   LPF/br0/00:0e:2e:85:8d:a7
Sending on   Socket/fallback
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 10.1.1.1
DHCPREQUEST on br0 to 255.255.255.255 port 67
DHCPACK from 10.1.1.1
bound to 10.1.1.105 -- renewal in 1409 seconds.
                                                                         [ OK ]
chris@chris-ubuntu:~$ sudo VBoxAddIF vbox0 chris br0
VirtualBox host networking interface creation utility, version 1.5.6
(C) 2005-2007 innotek GmbH
All rights reserved.

Creating the permanent host networking interface "vbox0" for user chris.
chris@chris-ubuntu:~$ 

```

From the Guest, I can ping the host but not the router.
It makes these connections on these devices

wlan0 - IP6.
vbox0 - IP6
br0 - IP6 + IP4 (with the address my router should send)

I'll ask at VBox forums after work today..

**edit** siepo - You got in before I posted this :P
I tried that, but it still doesn't work. As far as I can tell, your doing *exactly* what vbox says to do, creating a virtual adapter, just without bridging it. Which doesn't actually make much sence, since, where does the adapter "tap0" connect to? Isn't that what the bridge with wlan0 is ment for?

---

### Post by siepo on 2008-03-13
Tap0 is the host end of the interface. In VB's network configuration, you can configure up to 4 network adapters of the guest machine. Hook one of these up to tap0.

As to bridging: I would rather have called it bundling: you make several interfaces act as one. It is not about connecting one point to another.

---

### Post by Hero of Time on 2008-03-13
So, you have internet with the bridge working in your host. Then the next thing is the correct IP address in your guest OS. Creating the bridge is necessary, else the guest can't communicate with the outside world. Perhaps you need to add the virtual adapter mac address to your router.

---

### Post by siepo on 2008-03-13
Without bridge and just a tap/tun interface, guest and host can still communicate. I understood that that was the main requirement.

---

### Post by Live-Dimension on 2008-03-13
I see siepo and hero. I'm slightly getting myself confused here :P

I can't try (again) now but the networks never seem to work for the guestOS, and every time it does seem to work, it kills my wireless.

I had the same issue with VMWorkstation but a simple user-made patch fixed it =\.

Thanks for the help though. I just think I gotta keep trying thigns out till it works.

> Then the next thing is the correct IP address in your guest OS
Wouldnt happen to know what the correct IP is?

---

### Post by Hero of Time on 2008-03-13
> Wouldn't happen to know what the correct IP is?
Simple, it's the same as your network, as you want to connect to your network. I have tried a few things myself, but somehow I can't seem to get the the wifi working inside the bridge. When I'm at home, I can try there as I have static addresses there and now I'm at school with DHCP addresses. If static works, then that is also your solution. I will look into this matter further. The main problem is wifi and bridge equals no network. That has to be fixed somehow.

---

### Post by Live-Dimension on 2008-03-13
> **Hero of Time said:**
> Simple, it's the same as your network, as you want to connect to your network. I have tried a few things myself, but somehow I can't seem to get the the wifi working inside the bridge. When I'm at home, I can try there as I have static addresses there and now I'm at school with DHCP addresses. If static works, then that is also your solution. I will look into this matter further. The main problem is wifi and bridge equals no network. That has to be fixed somehow.

Finally you see my problem :)
It's all setup "right" yet the wireless just doesn't seem to connect/authenticate.
Thanks for the length your going to with helping me with this. Now I know this is a wireless issue, it should help to narrow those search results down.

**edit** I remember reading somewhere that using a different wireless/network connection manager solves this problem. Pity I didn't keep a link to the post... but apparently from what I picked up*, nm-applet* is alright, but there's better out there. Maybe ther others are more complex, hence why *nm-applet *is chosen as starnded.

---

### Post by Hero of Time on 2008-03-13
I've done some more research and found a commandline solution. This doesn't involve a bridge, but does use the Host Interface.

[quote=http://www.scottro.net/vboxbridge.html]If you don't need bridged networking, the default NAT networking works quite well with wireless in my experience. However, many of us need or at least want, the guest O/S to have its own visible address on the LAN. Thanks to the Hazard's Stuff page I was able to do it quite easily. The technique is different. Rather than use a bridge, we use parprouted to connect the wireless card and tap0 and give tap0 an address.

I've done this on Fedora, Ubuntu and Arch. There are slight differences. We will need the parprouted program. One can install from source or use the rpm from the Dag repos. I used the one for RHEL 5 on Fedora 8 without problems. 

Ubuntu has a package for it--it might have a slightly different name, do apt-cache search parprouted and intall it. Archers, use the source. (See the ArchLinux section below for links and suggestions about building the package.)

With wireless and parprouted, we can eliminate the bridge. I left my ethernet card's address alone. The wireless gets its address from DHCP, which is fine. Say that eth1 is my wireless, with its address that works on my network, whether from DHCP or being set manually. 

If you skipped the earlier part of this article about wired networks, we're using a typical 192.168.1.0/24 network. In this example, my wireless card has an address of 192.168.1.105

We have to make sure that IP forwarding is enabled. You can edit /etc/sysctl.conf in Fedora, changing the variable from 0 to 1, but that requires a reboot. If you want to do it permanently, do it in sysctl.conf, if you just want the change to be temporary, you can do it with the command
```
sysctl net.ipv4.ip_forward=1
```

Now we have to create tap0. Fortunately, the VirtualBox program includes its own version of tunctl, and we can use that. The -u in the next command refers to the user who will be using VirtualBox. In this case, it's a user with the login name of john.
```
VBoxTunctl -b -u john
```

You'll see tap0 echoed to the screen. Now we bring up tap0 and give it an address. One can use ifconfig or ip--in this case, we'll use ip. Archers, please take a moment and refer to the ArchLinux section. You'll have to install the ip command (part of the iproute package) and also symlink it to /sbin. Once you've done that, return to the steps below.
```
ip link set tap0 up
ip addr add 192.168.1.108/24 dev tap0
```

We are giving tap0 an address on our LAN, which, as we discussed above is a 192.168.1.0/24 LAN. (The /24 is the same as 255.255.255.0)

Lastly, we use parprouted to bind the wireless card to tap0
```
parprouted eth1 tap0
```

Now we have the wireless card, eth1 with an address of 192.168.1.105 and the tap0 interface with an address of 192.168.1.107. After starting VirtualBox, edit the guest O/S's networking settings, just as we did in the wired setup. Once again we choose Attached to Host Interface and for the Interface Name section, we put in tap0.

Supposedly, there are iptables rules that work with this. However, so far, I have had to completely flush my iptables rules for it to be able to connect. Oddly, enough, this is only the case at times--otherwise, I can leave my default rules (Fedora defaults, pretty much, allowing ssh and nothing else) and it works. I haven't figured this out yet, nor have the many posts I've found while googling given me the solution. I'm not sure why, apparently their solutions work for the people who have posted them. The most typical one seems to be, if your card was eth1, which is what my wireless is, 
```
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```

It's quite possible I'm missing something though, my experience is more with the BSD pf filtering program. On Fedora Forums, someone pointed out that the command didn't work for him either. However, choosing system-config-firewall, clicking masquerade and then choosing his wireless card worked for him. I tried it and it worked for me as well. In my case, my card wasn't listed, but there is a place to add an interface. 

Running iptables-save with both methods shows that the difference is that when running the command the lines allowing masquerading appear at the top of the listing. When using system-config-firewall, the lines appear at the end of iptables-save. I haven't investigated this yet, when I do, I'll add the information to the page, but at any rate, it seems that you can get it working by using system-config-firewall to have the wireless card masqueraded. When you do that, it automatically does the sysctl setting for you, changing net.ipv4.ip_forward to 1. 

(To digress briefly, I recently received an email from someone who found that though this howto didn't work for them, the IP-Masquerade howto brought them success. Also, note that that howto recommends NOT using the iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE rule as default. The reader might want to try that howto's scripts for firewalling. As I'm running everything behind other firewalls, I haven't gone through that howto and tested it myself). 

When the guest O/S boots up, you will have to manually assign it an address. Give it an address on the same network, that is, in this case, something like 192.168.1.109 with a netmask of 255.255.255.0 and a default gateway of 192.168.1.1. Use whatever DNS servers you usually use on the host machine. 

When done, you can remove the various changes you've made. After shutting down the host machine, bring down the tap0 interface, remove it and change your sysctl variable back if you choose.
```
ifconfig tap0 down
VBoxTunctl -d tap0
sysctl net.ipv4.ip_forward=0
pkill parprouted
```[/quote]

That should make it work. I haven't test this. Note that you don't have to use the VBoxTunctl command, as you already have an interface, vbox0. All you have to do, is look for the interface in /etc/vbox/interfaces and remove the bridge name.

---

### Post by Live-Dimension on 2008-03-14
Woohoo! Took another two to three tries (In paticular removing vbox0 and getting the right ip for the guest) but it works.

Thankyou :)

---

