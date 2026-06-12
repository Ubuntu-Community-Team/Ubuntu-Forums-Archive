---
title: "ETH0 internet connection drops when connecting ETH1 to internal network"
date: 2012-07-30
forum: Server Platforms
---

### Post by duplex50 on 2012-07-30
Hello there! This is my first post to any forum, EVER!

I have been working with Ubuntu linux for several months now. I have already successfully configured a Snort box for intrusion detection.

Currently, I am working to configure a Poweredge 2650 as a Firewall for my home network. Installed is Ubuntu Server 12. I have two NICs, ETH0 and ETH1. ETH0 is the external interface and is configured with a static address (192.168.254.2) on 192.168.254.0/24 network. ETH0 is connected directly to the DSL modem. ETH1 is the internal interface and configured with a static address (192.168.1.23) on 192.168.1.0/24 network.

While SUCCESSFULLY pinging out to the internet ([www.google.com]("http://www.google.com/")) on ETH0, as soon as I connect ETH1 to the switch on my internal network, the connection drops (MSG: Operation not permitted). I can then ping internal network IPs, but can no longer get out to the internet on ETH0. Default gw route added for ETH0. Default gateway (DSL modem) 192.168.254.254.

NetworkManager.conf is currently set to manager network connections.

What am I missing? Why does connecting ETH1 to internal network cause ETH0 to drop out?

I can provide any information needed for suggestions on resolving this issue.

Thanks in advance!

While ETH0 is successfully pinging google.com, route command shows the default gw for ETH0 as the DSL modem's name: speedstream.domain. When connecting ETH1 to switch, route command shows that the default gw for ETH0 is now just it's IP address: 192.168.254.254. DNS issue?

---

### Post by darkod on 2012-07-30
You seem to know IPs and subnetting, but I have to ask this: Is the DSL modem really only a modem or modem/router?

Because if I'm not mistaken only a modem will pass the connection to the machine connected to its port and the public IP will be on that machine. But you seem to be sure that the modem has a private interface 192.168.254.254 so I believe you.

Otherwise, your setup looks OK. Just in case, have you tried using eth1 with a network different from 192.x.x.x, for example like 10.0.0.1/24? Will that drop the eth0 connection too?

---

### Post by The Cog on 2012-07-30
It would be interesting to see the output of the commands 
```
route -n
cat /etc/resolv.conf
```both before and after connecting the internal network. But if the ongoing ping to google breaks, then I guess it's a routing issue rather than a DNS issue. 

My first guess would be that bringing up the internal interface is replacing the default gateway with an internal one but I'd like to see the route printed just to be sure.

---

### Post by duplex50 on 2012-07-30
Hi there!  Thanks for your reply.  Yes, the modem is a Speedstream 4300 DSL router.  It's interface is indeed accessed by 192.168.254.254:80.

I have not yet tried to use a different another network class for ETH1.  I can try that, but I do not think that this is the issue.

Ultimately, I want to change the default gateway setting on all internal network clients to point to ETH1 so that any traffic from the clients goes through ETH1, through IPTABLES rules, and then out ETH0, and vise-versa.
 
For some reason I still have a feeling that it is some stupid auto-default setting in Ubuntu or a neglected route setting in Ubuntu.
 
If anyone has any further questions, suggestions, I would be happy to provide Ubuntu output information.
 
THANKYOU EVERYONE!

---

### Post by duplex50 on 2012-07-30
Hi Cog,
 
Last night I was lookin at the routes before and after ETH1 was connected.
I have a default route in the /etc/network/interfaces file for ETH0.
Slightly different in interfaces file, but same as: 
sudo route add default gw 192.168.254.254 eth0
I also have two nameservers defined in Resolv.conf:
nameserver 192.168.254.254 (DSL Modem)
nameserver 4.2.2.2 (Public DNS)
I will have to go home to provide the exact output, but I know that before ETH1 is connected, default gw for ETH0 resolves to speedstream.domain which is my DSL modem.
After ETH1 is connected default gw for ETH0 just shows it's IP of 192.168.254.254.
 
Keep the questions coming!  I will post command outputs tonight.
 
THANKS!

---

### Post by BkkBonanza on 2012-07-30
Your'e setting up a firewall/router box. So remove networkmanager and configure manually. Network Manager will bugger up anything you do manually with multiple interfaces. 

sudo apt-get remove networkmanager

After that you can configure your interfaces and they won't flip about on you like that. For your use you'll need to configure ip_forwarding and some NAT rules. See near the bottom of this page,

[https://help.ubuntu.com/community/Router/](https://help.ubuntu.com/community/Router/)


Please use names eth0 eth1 not the upper case names as linux is case sensitive and using the wrong names is confusing... and wrong.

---

### Post by duplex50 on 2012-07-30
route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         speedstream.dom 0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.254.0   *               255.255.255.0   U     1      0        0 eth0

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.254.254 0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.254.0   0.0.0.0 

/etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet static
        address 192.168.254.2
        network 192.168.254.0
        netmask 255.255.255.0
        broadcast 192.168.254.255

dns-nameservers 192.168.254.254

iface eth1 inet static
        address 192.168.1.23
        network 192.168.1.0
        netmask 255.255.255.0

---

### Post by duplex50 on 2012-07-30
ABOVE IS JUST ETH0 UP, With a valid connection to the internet.

BELOW IS HOW THE routing table changes when connecting ETH1 to the local network.

route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.254.254 0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
localnet        *               255.255.255.0   U     1      0        0 eth1
192.168.254.0   *               255.255.255.0   U     1      0        0 eth0

ALSO

/etc/resolv.conf

nameserver 192.168.254.254
nameserver 4.2.2.2

How do you make the nameservers permanent?

My issue persists.  As soon as I connect ETH1 to local network via Cisco Catalyst 2980G, ETH0 drops internet connection.

---

### Post by BkkBonanza on 2012-07-30
Hello,
Did you see my response above. REMOVE networkmanager. It is designed for managing a SINGLE interface only so it will bring down the interfaces it thinks are not wanted.

To make resolv.conf permanent under 12.04 you need to add a file in /etc/resolvconf/resolv.conf.d/ directory with your entries.

---

### Post by duplex50 on 2012-07-30
Thank you very much for your reply Bonanza.

I have uninstalled Network Manager via:
sudo apt-get remove --purge network-manager-gnome

After uninstalling and rebooting, I tested.  Same issue.  As soon as eth1 is connected to switch, connection on eth0 dies.

I then added resolv.conf file to /etc/resolvconf/ with DNS entries:
nameserver 192.168.254.254
nameserver 4.2.2.2

I rebooted, confirmed that this file was still there and tested.  Same issue.

Is the /etc/resolv.conf file suppose to change by adding the same file with the above entries to /etc/resolvconf?  The one that says "DO NOT EDIT THIS FILE BY HAND".

Once again, same issue.  

Routes are the same as previously posted after connecting eth1.

Thank you all again for your replies.

Regards,


64 bytes from yh-in-f104.1e100.net (74.125.137.104): icmp_req=6 ttl=47 time=40.2 ms
64 bytes from yh-in-f104.1e100.net (74.125.137.104): icmp_req=7 ttl=47 time=40.2 ms
64 bytes from yh-in-f104.1e100.net (74.125.137.104): icmp_req=8 ttl=47 time=39.2 ms
64 bytes from yh-in-f104.1e100.net (74.125.137.104): icmp_req=9 ttl=47 time=39.0 ms
64 bytes from yh-in-f104.1e100.net (74.125.137.104): icmp_req=10 ttl=47 time=40.0 ms
64 bytes from 74.125.137.104: icmp_req=11 ttl=47 time=38.9 ms
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

---

### Post by duplex50 on 2012-07-30
I also created a separate VLAN on my Cisco Catalyst 2980G and plugged in eth1 there.  To my dismay, the same behavior occured.

---

### Post by BkkBonanza on 2012-07-30
Make sure you remove network-manager not just network-manager-gnome. That is just the gnome gui interface. So network-manager would still be running. Check **ps afx** output and see if it's running.

Re-read what I said about resolv.conf.d directory not resolv.conf file. Put your entries in a file such as, /etc/resolvconf/resolv.conf.d/main

Seriously, interfaces don't just go up and down unless something is trying to manage them. I have machines with 3 interfaces here all active at once. Get rid of all network-manager junk fully.

aptitude search network-manager

and make sure all have status "p" or "c".

---

### Post by darkod on 2012-07-31
For the DNS entries use the dns-nameservers option in /etc/network/interfaces. That is permanent. You can have more than one server configured of course:
dns-nameservers x.x.x.x y.y.y.y z.z.z.z etc

Not sure if network-manager is also doing something funny about your DNS, as already mentioned. It's best to use only /etc/network/interfaces for the network settings.

I also noticed in your post #7 that you don't have a gateway configured for eth0 in your /etc/network/interfaces.

Below the IP address and the netmask you should have something like:
gateway 192.168.254.254

One more thing, with Cisco you have to be careful about something called spanning tree. Not sure if your switch has the options, but basically it can detect if you somehow create a loop and disconnect one connection. So, while doing your tests with two internal interfaces (with private IPs although you consider one interfaces to be external), make sure you are not creating some loop and the Cisco spanning is killing the connection.

And definitely purge all network-manager related. :)

---

### Post by duplex50 on 2012-07-31
Good Morning.

Bonanza, you were correct in that I had only uninstalled the gui portion of network manager.  I completed the uninstallation and network manager is no more.
When I load up Ubuntu no interfaces are brought up and my routes are empty.  
sudo ifconfig eth0 up  brings up the interface, but assigns no IP and my routes are still empty.  I assume this is because network manager does all this for you and it has since been blown away.  What should I use now to configure/load my interfaces at Ubuntu startup? I was reading that netcfg is good for multiple interfaces.  Any thoughts?

Thank you for your reply darkod.  I took a look at my /etc/network interfaces file and found that I do have my modem set as a name server.  

dns-nameservers 192.168.254.254, 4.2.2.2

I also added public DNS server.

Please correct me if I am wrong, but it appears that you only need to worry about the /etc/network/interfaces file when network manager is running.  As stated above, I no longer have interfaces configuring themselves at startup.  Since removing network manager, I need to configure something to take care of the interfaces automatically at startup.  Any suggestions are very appreciated.


Regards,

---

### Post by darkod on 2012-07-31
On the contrary, you use /etc/network/interfaces without network-manager which shouldn't have been there in the first place.

If you tried to configure the network through NM purging it might have deleted all info from /etc/network/interfaces. Simply edit the file as root, and add the info.
sudo nano /etc/network/interfaces

Something like:
```
auto eth0
iface eth0 inet static
       address 192.168.254.2
       netmask 255.255.255.0
       gateway 192.168.254.254
       dns-nameservers 192.168.254.254 8.8.8.8
```If the loopback interface is also missing, above eth0 settings add also:
```
auto lo
iface lo inet loopback
```That should configure the first interface and give you internet access. If that works we can talk about the second one later.

PS. The line with 'auto' tells it to bring the interface up at boot, so after you save those changes and reboot the interfaces lo and eth0 will be activated on boot. You will do a similat setup for eth1 later, lets see how this works first.

---

### Post by duplex50 on 2012-07-31
You guys are awesome.
 
After completely disabling network manager last night and manually configuring interfaces via command line this morning before work, I am now able to get a valid internet connection on eth0 and connect eth1 to internal network without dropping connection.  I can now successfully ping externally on eth0 while pinging internally on eth1.  Thank you very much Bonanza for your excellent advise and information.
 
Darkod, that makes sense now.  I thought initialy the scope of the /etc/network/interfaces file was beyond that of just network manager, but I was not sure.  

I do indeed have my interfaces file configured, but I never added "auto" to each interface so that it would come up on boot.  I didn't know what adding "auto" did!  Now I do!  I will do that as soon as I get home.
 
Thanks again for everyone's contributions!  This has been an excellent first experience with forums!  You guys are great!
 
 
Kind Regards!

---

### Post by darkod on 2012-07-31
You are welcome. Glad you got it going.

Please mark the thread as Solved, you can do this in Thread Tools above the first post.

---

