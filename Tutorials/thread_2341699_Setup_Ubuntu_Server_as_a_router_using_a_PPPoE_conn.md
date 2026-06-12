---
title: "Setup Ubuntu Server as a router using a PPPoE connection"
date: 2016-10-30
forum: Tutorials
---

### Post by js_muyo on 2016-10-30
Let me start off by saying that I am extremely new to Linux. I didn't even know you could create a linux router until I read the article by Jim Salter on Ars.

[http://arstechnica.com/gadgets/2016/01/numbers-dont-lie-its-time-to-build-your-own-router/](http://arstechnica.com/gadgets/2016/01/numbers-dont-lie-its-time-to-build-your-own-router/)

Once I read his follow up article I knew I had to do this for myself.

[http://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](http://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/)

I ordered a small "router like" fanless pc, added a SSD and RAM and got to work. Unfortunately I could never get my Ubuntu Server router to work like his did. The main reason is because my ISP requires PPPoE authentication. This is the same type of login that a DSL connection would require (I'm on a fiber connection but for some reason it still uses PPPoE). My old Netgear WNDR3700 had a spot in its configuration to put in the username and password and it would magically connect and I would get internet. This didn't happen on my new Linux router. I couldn't get it to work with a PPPoE connection.

After many weeks of internet searching and forum reading I am happy to say I finally got it working and learned a lot about MTU, MSS (this dang thing took me a whole week to figure out) and PPPoE in the process. I am hoping this post will help anyone else trying to set up a Ubuntu Server router using a PPPoE connection. For the most part I follow Jim's second article, but I had to do quite a few modifications to get it to work on my system. I will always put links to the sites where I found the information in each section.

For some reason my Ubuntu Server USB installation media always required me to be connected to the internet. I don't recommend connecting this box directly to the internet without a firewall in place between this router and the outside. Since I had my Netgear WNDR3700 already working, I connected this router into one of the network ports so it was behind a firewall. Once I got through the installation (which always required me to be online for some reason) I rebooted, made the modifications to GRUB and installed all the necessary software required for this tutorial. Once that was done I unplugged the router from the Netgear and completed the rest of the setup completely offline. This way I wouldn't get any DHCP issues on my current network while setting this up. Once everything was completed and I verified that iptables was functioning, I would connect it directly to the modem and verify everything worked. Once I verified everything I replaced my Netgear with this new router.

Here is what I did.

**------Install Ubuntu Server------**

I decided to install the Ubuntu Server 16.04.1 LTS because of the 4 years of support and it is a 64-bit only release.

This part is pretty self explanatory, just install it and get to a command prompt. I elected to have security updates installed automatically as per Jim's article. For everything else I just used the default settings. I didn't install any additional software during the install. We will install all we need in the next few steps.

[https://www.ubuntu.com/download/server](https://www.ubuntu.com/download/server)

**------Make changes to GRUB------**

One thing I didn't like about a fresh install of Ubuntu Server is you can't see the OS boot up with OK or FAIL as it initialized each component. Being able to see all this during boot up really helped me troubleshoot quite a few things so I immediately turn the "quiet splash" feature off so I can see all that boot information. You might not even get a command prompt on your initial boot of the system. You might just get a blinking cursor in the upper left corner of your screen or just a completely blank screen. If you find that on your first boot you are sitting there staring at a blank screen, hit Ctrl + Alt + F1. This will remove the blank screen and give you your login prompt. When we disable quiet splash this blank screen will go away.

The next thing that is a bit frustrating is renaming the network cards to something other than the standard eth0 and eth1. So in this step we take care of both the quiet splash and getting the network cards named back to their old names.

Delete the quiet splash so you can see what is happening when Ubuntu boots up.

```
sudo nano /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
remove the quiet splash to make it look like this:
GRUB_CMDLINE_LINUX_DEFAULT=""

GRUB_CMDLINE_LINUX=""
Edit this line to get your network cards back to their original names.
GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0"
```

Be sure to update GRUB once you make these changes. The grub config file resides on a different partition than the actual GRUB software. So when you update the config you have to push those changes to the software on the other partition using this command.

```
sudo update-grub
```

Now that GRUB has been updated you need to edit your interfaces file and change the names of your network cards back to their normal eth0 and eth1.

```
sudo nano /etc/network/interfaces
```

Reboot for the changes to kick in.

[https://askubuntu.com/questions/6122/how-to-see-whats-going-on-during-shutdown](https://askubuntu.com/questions/6122/how-to-see-whats-going-on-during-shutdown) - Remove quite boot
[http://www.itzgeek.com/how-tos/mini-howtos/change-default-network-name-ens33-to-old-eth0-on-ubuntu-16-04.html](http://www.itzgeek.com/how-tos/mini-howtos/change-default-network-name-ens33-to-old-eth0-on-ubuntu-16-04.html) - Old network interface names.

**------Install your software------**

This will install the DNS, DHCP, OpenSSL and PPPoE software required to complete the rest of the setup offline.

```
sudo apt-get install bind9 isc-dhcp-server openssl pppoeconf
```

Reboot

*It is at this point I remove this router from my local network and continue the rest of the setup completely offline.*

**------Setting up PPPoE------**

With pppoeconf installed we can now setup the PPP login. First we need to edit the chap-secrets file with your username and password provided to you buy your ISP. The PPPoE software will use this information during the authentication process to connect to your ISP.

```
sudo nano /etc/ppp/chap-secrets
```

Put in your username and password and be sure to surround them with ""'s. Use a * for the server name and in most cases you can leave the IP address section blank unless your ISP assigned you an IP address. Here is what your chap-secrets file should look like once finished.

```
# Secrets for authentication using CHAP
# client            server        secret            IP addresses
"yourusername"        *            "yourpassword"
```

Now we need to create a peers file for the PPPoE connection. These files are located in **/etc/ppp/peers** directory. There will already be a default file called "provider" located in this directory. You can either edit that file or create your own. I elected to create my own file to make sure there was nothing in there I didn't need. Since my ISP is Centurylink I created a centurylink file using the command below.

```
sudo nano /etc/ppp/peers/centurylink
```

Here is what my centurylink file looks like once I was done editing it. You will notice the line second from the bottom where it references eth0. This is where you want to put the name of the interface you are using for your WAN connection that connects to the outside world. In this case my WAN connection is using eth0.

I put a link below for what most of these commands do.

```
# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
noauth
persist
plugin rp-pppoe.so eth0
user "yourusername"
```

With this file now created and configured, if I run the "pon centurylink" command it will connect to my ISP using the information from the centurylink peers and chap-secrets file. Once it is connected if you do an "ifconfig" you will notice a new network interface called ppp0 (atleast that is what mine is named). It is this new interface that we will need to reference in a few other files later on in the tutorial.

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE) - Great PPPoE tutorial
[https://ppp.samba.org/pppd.html](https://ppp.samba.org/pppd.html) - PPPoE options explaination

**------MTU------**

Now we need to setup the MTU on the ppp0 interface. The normal MTU used in LAN connections is usually 1500. If you do an ifconfig you will notice the MTU of all your interface cards is set to 1500, this is pretty standard. But because we are using a PPPoE connection the highest MTU we can get is 1492. And your ISP might not even go that high. The highest I could get mine was 1484. If the MTU setting of your ppp0 interface isn't correct you will probably have issues with web sites not loading. 

Here is an excellent post I used to determine my maximum MTU setting

[https://ubuntuforums.org/showthread.php?t=872346](https://ubuntuforums.org/showthread.php?t=872346)

Now that we have determined the maximum MTU for your ppp0 interface we need to make sure that value gets assigned to it every time the server boots up. To do this you need to edit the **/etc/ppp/ip-up** file to set the MTU of the ppp0 interface with your maximum MTU setting. Put this at the very bottom of the file.

```
/sbin/ifconfig ppp0 mtu 1484
```

Please note that 1484 is my optimal MTU setting, yours might be different.

Now when the server boots up, it will read this command and set the MTU of the ppp0 connection every time. Keep this file open as we will add some DNS servers here in the next step.

[https://ubuntuforums.org/showthread.php?t=872346](https://ubuntuforums.org/showthread.php?t=872346) - Find your optimal MTU setting
[https://philio.me/setting-mtu-size-for-pptp-server-solves-windows-browsing-issues/](https://philio.me/setting-mtu-size-for-pptp-server-solves-windows-browsing-issues/) - How to set your MTU on every boot

**------DNS------**

You will notice in the /etc/ppp/peers/centurylink peers file I didn't use the option of usepeerdns.

[I]**usepeerdns**
    Ask the peer for up to 2 DNS server addresses. The addresses supplied by the peer (if any) are passed to the /etc/ppp/ip-up script in the environment variables DNS1 and DNS2, and the environment variable USEPEERDNS will be set to 1. In addition, pppd will create an /etc/ppp/resolv.conf file containing one or two nameserver lines with the address(es) supplied by the peer.
    [https://ppp.samba.org/pppd.html](https://ppp.samba.org/pppd.html)[/I]

This is because I want to use my own DNS servers, not the ones my ISP assigns. In order to do this you need to add the following lines in the same **/etc/ppp/ip-up** file where we edited our MTU settings. Just add them below the command where you set the MTU.

```
echo "nameserver 208.67.222.222" > /etc/resolv.conf
echo "nameserver 208.67.220.220" >> /etc/resolv.conf
echo "nameserver 208.67.222.222" > /etc/ppp/resolv.conf
echo "nameserver 208.67.220.220" >> /etc/ppp/resolv.conf
```

I believe the **/etc/resolv.conf** and **/etc/ppp/resolv.conf** files are overwritten everytime the server reboots or the PPPoE connection is established. The usepeerdns command would normally grab the ISP DNS servers and place them there. But since we aren't using that command you have to put in the echo commands to have it write your DNS servers to that file every time. This is the only work around I could figure out to get my custom DNS servers to be used and get them to stick after a reboot.

[http://puppylinuxfaq.org/freeware/34-files/110-custom-dns.html](http://puppylinuxfaq.org/freeware/34-files/110-custom-dns.html) - Helped me figure out how to get this working.

**------Network Interfaces------**

Now we need to setup our network interfaces file **/etc/network/interfaces**. You will notice that I have the eth0 (WAN) connection set to manual instead of dhcp like most tutorials say. This is because of the PPPoE connection. The manual setting was needed to get this working for me. This is where you can put in how the interface will be used or how it connects. I have eth0 set as the WAN interface and eth1 as the LAN interface.

Edit the interfaces file.

```
sudo nano /etc/network/interfaces
```

Here is how mine looks.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The WAN network interface
auto eth0
iface eth0 inet manual

# The LAN network interface
auto eth1
iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
```

[https://help.ubuntu.com/community/ADSLPPPoE#Boot_issues](https://help.ubuntu.com/community/ADSLPPPoE#Boot_issues) - This helped me troubleshoot my connection issues.

**------Packet Forwarding------**

Now we need to enable packet forwarding. Without packet forwarding your router isn't a router and won't be able to forward packets between interfaces.  We need to edit the **/etc/sysctl.conf** file and remove the "#" in front of the net.ipv4.ip_forward=1 line. Save the file once completed.

```
sudo nano /etc/sysctl.conf
```

It should look like this.

```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1
```

**------Startup script------**

Next we need to create the iptables startup script to initialize iptables even before the network cards are brought online. This tip came from Jim's article mentioned at the beginning of this tutorial. Since iptables is the main firewall in Linux it is always good to have this running before the router connects to the ISP. This ensures that at no time are the network cards ever connected to the internet without iptables being loaded, not even for a split second.

Edit this file

```
sudo nano /etc/network/if-pre-up.d/iptables
```

Add the following lines.

```
#!/bin/sh
/sbin/iptables-restore < /etc/network/iptables
```

Once the file is edited you need to change the permissions on it. I could only get this to work by doing a sudo -i command and applying it that way.

```
sudo -i

chown root /etc/network/if-pre-up.d/iptables ; chmod 755 /etc/network/if-pre-up.d/iptables
```

Once the permissions are applied type "exit" and hit Enter to exit the elevated permissions.

**------DHCP Setup------**

Now we need to setup the DHCP server. Edit the **/etc/dhcp/dhcpd.conf** file with the settings you wish to use for your LAN. You can put this anywhere in the file as everything else is commented out by default.

```
sudo nano /etc/dhcp/dhcpd.conf
```

Here is how mine looks.

```
subnet 192.168.99.0 netmask 255.255.255.0 {
    range 192.168.99.100 192.168.99.199;
    option routers 192.168.99.1;
    option domain-name-servers 192.168.99.1;
    option broadcast-address 192.168.99.255;
}
```

That's it. Save and close the file and you are done with DHCP setup.

**------iptables------**

Now we need to edit our **/etc/network/iptables** file with our rules. Iptables is the firewall we will be using for Ubuntu Server. This is the part that gave me a bit of a headache. You will notice in my iptables file I reference the ppp0 interface instead of the eth0 interface like most tutorials suggest (Jim's tutorial uses eth0 for example). This is because of our PPPoE connection. We want to route the traffic to this ppp0 connection which will then take care of routing it through the eth0 interface. We set this up earlier in our PPPoE configuration with the line "plugin rp-pppoe.so eth0" in our **/etc/ppp/peers/centurylink** configuration file. If we route directly to the eth0 interface (like in Jim's article)we will miss all the PPPoE configuration and the connection won't work.

You will also notice the first Forwarding rule is a new rule different from Jim's main iptables config. 

```
# Clamp the MSS to MTU size
-A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
```

This little rule caused me the most pain throughout the whole tutorial. Without this rule I would get webpages that would half-load, not load at all, or time out. This is because my MSS (Maximum Segment Size) was bigger than my MTU (Maximum Transmit Size) so anything larger than a 1484 segment size would be lost. This rule clamps the MSS (1500 in my case) to my largest MTU size of 1484. Once I put in this rule and restarted iptables, the whole internet lit up and everything finally started working.

[https://bugs.launchpad.net/auto-package-testing/+bug/1572026](https://bugs.launchpad.net/auto-package-testing/+bug/1572026) - This is where I found the rule to clamp the MSS to MTU size.

If you want to specify your MSS size so there is no guessing involved, you can use this rule instead.

```
# Specify MSS size
-A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --set-mss 1436
```

You can determine your MSS value by taking your MTU, subtracting the PPPoE header, the IP header and the TCP header. The end result is your MSS size.

MTU = 1484
PPPoE header = 20
IP header = 20
TCP header = 8
MSS = 1436

1484 - 20 - 20 - 8 = 1436

This site gives a great explaination on how this all works and the calculations.
[https://samuel.kadolph.com/2015/02/mtu-and-tcp-mss-when-using-pppoe-2](https://samuel.kadolph.com/2015/02/mtu-and-tcp-mss-when-using-pppoe-2)

Edit the iptables file.

```
sudo nano /etc/network/iptables
```

This is how my full iptables rules look.

```
*nat
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]

# eth0 is WAN interface, eth1 is LAN interface, ppp0 is the PPPoE connection
-A POSTROUTING -o ppp0 -j MASQUERADE

COMMIT

*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]


# Service rules

# basic global accept rules - ICMP, loopback, traceroute, established all accepted
-A INPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -i lo -j ACCEPT
# -A INPUT -p icmp -j ACCEPT
-A INPUT -m state --state ESTABLISHED -j ACCEPT

# enable traceroute rejections to get sent out
-A INPUT -p udp -m udp --dport 33434:33523 -j REJECT --reject-with icmp-port-unreachable

# DNS - accept from LAN
-A INPUT -i eth1 -p tcp --dport 53 -j ACCEPT
-A INPUT -i eth1 -p udp --dport 53 -j ACCEPT

# SSH - accept from LAN
-A INPUT -i eth1 -p tcp --syn --dport 22 -j ACCEPT

# DHCP client requests - accept from LAN
-A INPUT -i eth1 -p udp --dport 67:68 -j ACCEPT

# drop all other inbound traffic
-A INPUT -j DROP


# Forwarding rules

# Clamp the MSS to MTU size. Both rules work, this depends on if you specify the MSS or not.
#-A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
-A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --set-mss 1436

# forward packets along related/established connections
-A FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

# forward from LAN (eth1) to PPPoE (ppp0)
-A FORWARD -i eth1 -o ppp0 -j ACCEPT

# drop all other forwarded traffic
-A FORWARD -j DROP

COMMIT
```

Almost all these rules came from Jim's article in Ars, but I had to modify a few things to get it working for me. I had to modify the SSH service rule and add the "--syn" option to finally allow SSH to this router from another computer on the LAN. I also commented out the ICMP service rule to not reply to pings. This made my computer fully stealth according to a Shields up scan.

[https://www.grc.com/shieldsup](https://www.grc.com/shieldsup) - Security port scanning

**------System Startup Scripts------**

I noticed sometimes, for reasons I couldn't figure out, that not all of my interfaces or PPPoE connections would connect when I booted up the router. My eth1 interface connection was especially problematic. So I created a small startup script to make sure all my interfaces and PPPoE connections were up when the system booted. This added 6 seconds to my boot time but it is totally worth it to me. To run commands after the system has fully booted but before you log in you need to edit the **/etc/rc.local** file.

```
sudo nano /etc/rc.local
```

Here are the commands I added.

```
sleep 2
ifup eth0
sleep 2
ifup eth1
sleep 2
pon centurylink
```

What this basically does is after the system is competely booted up but before I log in, it runs the ifup and pon commands on my connections. If the connection is already up and running then nothing happens and it moves to the next one. But if one of my connections isn't up this script will catch it and make sure it is initialized. I have the pon centurylink command last because it relies on the eth0 and eth1 interfaces being up. So I placed it at the end in this chain.

Now if you reboot you should have a fully functioning Ubuntu Server router.

If you have any comments or suggestions please post them here. I don't mean for this tutorial to be the only way to get this working, or even the most optimal. But for me, a person with very little Linux experience, this is how I was able to successfully get it working.

I love my new Linux router and will never buy a pre-built router again.

Here are some other commands or file locations I found out while researching all this. These helped me troubleshoot all the issues I had trying to get this to work.

**------References------**

Apply new iptables configuration:
```
sudo /etc/network/if-pre-up.d/iptables
```

check status of iptables:
```
sudo iptables-L
```

Reboot and Shutdown:
```
sudo shutdown -r now
sudo poweroff
```

Remove package:
```
sudo apt-get remove package
```

Find all interface connections, even ones that are not up:
```
ifconfig -a
```

Enable a interface connection:
```
sudo ifup eth1
```

Add or delete VLAN interface:
```
sudo vconfig add eth0 201 
```
```
sudo vconfig delete eth0 201 
```

Reset network interfaces:
```
sudo /etc/init.d/networking restart
```

DNS config file location:
**/etc/resolv.conf**

BIND9 config file location:
**/etc/bind/named.conf.options**

DHCP config file location:
**/etc/default/isc-dhcp-server**

**------BONUS Stuff------**

My "special" promotion with CenturyLink is due to expire in about two months. Once that happens I will have to start leasing a modem from them or purchase my own. Since I didn't want to lease one I started researching the options to purchase my own device. The modem/router I am leasing now is a Zyxel C1100Z. So I looked on Amazon for that model. In the reviews for it someone linked a site talking about how the modem/router was completely worthless and can be bypassed.

[http://kmwoley.com/blog/bypassing-needless-centurylink-wireless-router-on-gigabit-fiber/](http://kmwoley.com/blog/bypassing-needless-centurylink-wireless-router-on-gigabit-fiber/)

Like the example on the website I am also on CenturyLink with a fiber connection. So I wanted to see if I could bypass my current Zyxel modem/router with this Ubuntu Server setup like he did with his Netgear router. The good news is I was able to successfully bypass the Zyxel device and speed up my connection a bit. One less device standing between me and the internet means one less device that slows down the connection, could fail, you have to pay for and sucks up power. It was a win win situation.

**Setup VLAN tagging**

It turns out that the entire nationwide CenturyLink fiber network is running on VLAN 201. So the first thing I had to do was setup VLAN tagging on my eth0 interface.

Download the vlan software

```
sudo apt-get install vlan
```

Once the software is downloaded and installed load the 8021q module

```
sudo modprobe 8021q
```

Now we need to add the 8021q module to **/etc/modules** like in the example below. This will make sure the VLAN module loads when the system reboots.

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
8021q
```

Now we need to manually add the new VLAN. The last 3 numbers in this command is the number of the VLAN. So in my case I am going to use 201 since this is what CenturyLink uses for their nationwide fiber network.

```
sudo vconfig add eth0 201
```

Now we need to edit the **/etc/network/interfaces** to configure our new VLAN interface. Here is what I added to my interface file:

```
# The VLAN 201 network interface
auto eth0.201
iface eth0.201 inet manual
vlan_raw_device eth0
```

Now if you run the **sudo ifup eth0.201** command the interface should now be online. You can see it by running a **ifconfig** command.

In order to get our PPPoE connection to use this VLAN connection instead of the normal eth0 connection to route the traffic, we have to edit our peers file and point it to eth0.201.

```
sudo nano /etc/ppp/peers/centurylink
```

Here is what mine looks like now.

```
noipdefault
defaultroute
replacedefaultroute
hide-password
noauth
persist
# plugin rp-pppoe.so eth0
plugin rp-pppoe.so eth0.201
user "yourusername"
```

You can see that I commented out the old line linking rp-pppoe.so to eth0 and instead linked it to eth0.201. Now all the PPPoE traffic will be routed through the eth0.201 VLAN instead of eth0.

I put all these settings in place and rebooted, but had some issues with my eth0 and eth1 adapters coming online at boot. I put a few commands in my **/etc/rc.local** to bring them up at the end of the boot process, but this caused a few issues for me with this new setup. So using the tip from Coseus (please see his post below) I added the **allow-hotplug** to my **/etc/network/interfaces** file. So now my file looks like this.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The WAN network interface
# auto eth0
allow-hotplug eth0
iface eth0 inet manual

# The VLAN 201 network interface
auto eth0.201
iface eth0.201 inet manual
vlan_raw_device eth0

# The LAN network interface
auto eth1
iface eth1 inet static
    address 192.168.1.1
    netmask 255.255.255.0
```

You can see from my file that I commented out the old **auto eth0** and replaced it with **allow-hotplug eth0**. This fixed my issues with the eth0 adapter, but I still left the commands in there to bring up eth1 and the Centurylink PPPoE connection. Now my **/etc/rc.local** looks like this.

```
# sleep 2
# ifup eth0
# sleep 2
ifup eth1
sleep 2
pon centurylink
```

You can see that I commented out the command to bring up the eth0 interface since it is no longer needed with the allow-hotplug declaration in my interfaces file.

Now with all these settings in place, I was able to successfully bypass the Zyxel modem/router.

---

### Post by coseus on 2017-01-02
Thanks for this tutorial.
I had a problem with the network interface , a delay at startup and the ppp connection not starting. I resolved it with the "allow-hotplug eth0" not "auto eth0" in etc/network/interfaces
I have Ubuntu 16.10.

---

### Post by js_muyo on 2017-01-06
> **coseus said:**
> Thanks for this tutorial. I had a problem with the network interface , a delay at startup and the ppp connection not starting. I resolved it with the "allow-hotplug eth0" not "auto eth0" in etc/network/interfaces I have Ubuntu 16.10.  Thank you for the tip. Are you hooking into a modem supplied by your ISP or are you going straight out using the Ubuntu router. I'm asking because I am on CenturyLink fiber which uses an Optical Network Terminator (ONT) and then connects to a Zyxel C1100Z router and then my Ubuntu Server router is hooked into that. So my Ubuntu Server router is 3rd in the chain. The Zyxel is setup in bypass mode but there is still some configuration in there that connects it to the CenturyLink network. I've been reading that it is possible to bypass this useless Zyxel router/modem since the ONT box is taking care of converting the fiber signal to a Ethernet signal. I did a quick test last night to see if I could go straight in and it didn't work. I'm wondering if your setup is the same. 

My next step on this tutorial is to try and bypass the Zyxel box and go straight into the ONT. I've seen a few threads on this, but most of them are in Seattle WA. I'm wondering if the settings would be the same for where I live. If I can successfully bypass it, I will update the tutorial. 

[http://kmwoley.com/blog/bypassing-needless-centurylink-wireless-router-on-gigabit-fiber/](http://kmwoley.com/blog/bypassing-needless-centurylink-wireless-router-on-gigabit-fiber/)
[https://gist.github.com/blakerohde/267519833ea1abe417759cdb9b9af0d2](https://gist.github.com/blakerohde/267519833ea1abe417759cdb9b9af0d2)
[http://www.snbforums.com/threads/secure-reliable-wireless-router-for-centurylink-fiber-home-network.33726/](http://www.snbforums.com/threads/secure-reliable-wireless-router-for-centurylink-fiber-home-network.33726/)

---

### Post by js_muyo on 2017-01-15
I was able to successfully bypass my CenturyLink router. I had to set up a few extra things on the Ubuntu Server router to get it working properly. I have updated the tutorial with a new **BONUS** section that explains what I had to do. If anyone else is able to use this information to bypass their router please reply and let me know if you did anything different or have any helpful tips.

These were the items my Ubuntu Server router needed to do to be able to bypass the Zyxel router. I made a call to CenturLink technical support and surprisingly got someone very knowledgeable and confirmed my information.

1. You must be able to connect using a VLAN 201. The entire CenturyLink fiber network runs on VLAN 201.
2. Your device must be GPON (Gigabit Passive Optical Network) compatible. It turns out I had no issue with this using Ubuntu Server. I don't know if this has to do with the OS or because I am using a Intel NIC in my router.
3. You must be able to push your login and password credentials. We were able to accomplish this very early in the tutorial.

Another bit of useful information, because my Zyxel modem was in bridged mode they couldn't even see its MAC address. On their network they don't read MAC addresses, so their was no need to change the MAC address of your eth0 adapter. This is much different from a cable modem where everything relies on the MAC address of the modem. I'm betting they know the MAC address of the ONT device converting the fiber signal to Ethernet. Luckily they don't charge for this device. It is automatically provided once you sign up for fiber service.

---

### Post by patrick-stalvord on 2017-03-28
Nice tutorial! You can also start the pppoe connection in /etc/network/interfaces:


```

auto centurylink
iface centurylink inet ppp
        pre-up ifconfig eth1 up
        provider centurylink

```

---

### Post by lensman3 on 2017-04-24
An excellent thread.  I have CenturyLink DSL, but CL's fiber has just been introduced to the area.  (I am currently not using the 201 vlan tag, but I will shortly add it).

I would suggest that the MTU be set to 1412.  For this info check the man page of pppoe "man pppoe" and search to the very bottom.  Once I found this warning of 1412, I have not had any troubles.  Prior to this, there were strange youtube, hulu and netflix drop outs in the middle of movies).

I use dnsmasq as my nameserver and one of the options is when a client asks for an IP address the MTU is supplied. This includes IP numbers for cells phones, iphones and Ipads.

---

