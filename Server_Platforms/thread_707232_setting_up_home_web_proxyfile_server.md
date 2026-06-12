---
title: "setting up home web proxy/file server"
date: 2008-02-25
forum: Server Platforms
---

### Post by mike_frost on 2008-02-25
Hi all,
My first post here, after doing a lot of trying things out, configuring and not getting there!  I got a spare PC and set up a home server with MS SBS2003, which was pretty easy, but I really prefer to use Ubuntu and come to grips with it; I've been using Edubuntu as my main workstation for a year now and love it.  My background is software development, not IT, so networking is only something I'm learning.  I've spent a few days trying different how-to's and different variations but don't seem to be getting there with the server setup.  I have Ubuntu 7.10 correctly installed with LAMP and Samba installed (tho not configured yet).  First priority was getting the network working.

My goal is for the home server to be used for file sharing (with some fine grained control) and as a web proxy so that I can limit/filter access to the internet for one of the LAN users (my son!).  

My proposed setup looks something like this:

ISP/Internet -- Router1 -- eth0 / first NIC - SERVER  - eth1 / second NIC -- Router2 -- Clients (Windows, Ubuntu & a network printer)

(As you can see I've got two NICs in the server, which I am putting on different subnets for security)

Software:  Ubuntu 7.10 server, Squid, Dansguardian
I've installed Ubuntu7.10 server + Squid.  Not configured squid yet as I was trying to get basic network working first.

Router IPs are set as follows:
Router1 IP: 192.168.1.254
Router2 IP: 192.168.100.254

And my interfaces file is as follows:
```
# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet static
	address 192.168.1.1
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.254

auto eth1
iface eth1 inet static
	address 192.168.100.1
	netmask 255.255.255.0
	network 192.168.100.0
	broadcast 192.168.100.255
#	gateway 192.168.1.1
```

Notice I've commented out the last line, which doesn't work as the gateway's on a different subnet.  Not sure if I need to set gateway for eth1?

So first, is my interfaces file ok?

Next, how do I bridge (if that's the right term) connections on eth1 to eth0 so that LAN users can get to the internet via the server (ultimately through squid/dansguardian)?  I've tried brctl but wasn't able to get it working; I deleted my bridge so back with clean slate.

By default the routers have DHCP on, I can turn it on or off.
I notice that when using DHCP, router2 gives clients a gateway address of itself (192.168.100.254), and that I can't change that.  However I would assume that LAN clients should instead use the server's eth1 address as the gateway?  

Maybe I have to turn off DHCP on router 2 and set up the Ubuntu server as a  DHCP server?  Or I could manually set my client PCs since I only have a few of them.

Current state of affairs is that I have internet access on the server but not on clients.

My route table, which I haven't altered, looks like this at the moment:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.254   0.0.0.0         UG    100    0        0 eth0

```

This doesn't seem right - don't I need a default route for the LAN to go to eth1?  At the moment it seems to be saying that everything for the WAN goes to 192.168.1.254 (router1), but how can the LAN (on a different subnet) reach that without going through the server?

If you can recommend a good how-to that would take me through the steps needed to get this up and running, or can advise on next steps that would be great..

Thanks  for any / all help!

---

### Post by mike_frost on 2008-02-26
well once i got squid running and set the proxy settings in the client browser i was able to use the web from my clients.

i realise that i also need to access email through the server - just pop/smtp from the client out to the internet, the ubuntu server wont have any email server software.

so i've been trying to get the firewall configured and i can get as far as my thunderbird email client (on an XP Pro machine with windows firewall turned off for now) says it is connected to the mail server on the internet, but it says the mail server is rejecting the password.  now i've checked and the password is correct so this error isnt accurate.  i set up firestarter on the server and told it to share connections; it does show the pop connection as active when i try to access email from the client, and doesnt show any packets being rejected (except SMB).  i even tried adding a reject rule for POP to see if it would show up but it didnt.

so how can i set up the server to let SMTP/POP traffic from the LAN through, and what settings do the clients need?

---

