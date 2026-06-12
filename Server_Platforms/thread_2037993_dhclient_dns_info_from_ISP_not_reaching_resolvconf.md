---
title: "dhclient dns info from ISP not reaching resolvconf"
date: 2012-08-05
forum: Server Platforms
---

### Post by ahardy66 on 2012-08-05
I have 12.04 on a gateway machine with 2 interfaces and eth0 gets its IP address and the DNS server IP addresses for the whole LAN from the ISP via the ADSL modem. 

I want dhclient from isc-dhcp-client to pass the ISP DNS info to resolvconf to put into the /etc/resolv.conf but this isn't happening. 

I know the DNS IPs are coming in from the modem at DHCP time because I put some debugging into /etc/dhcp/dhclient-enter-hooks.d/resolvconf and I can see them coming through. The IP addresses just never make it into /etc/resolv.conf. 

Up until now, I've been using another machine as the lan's gateway with debian etch and I want to get it running on this new machine with ubuntu. 

I installed the standard ubuntu and it had network-manager installed, so I de-installed that since I'll be using this box with no changes to the network in the long term.

I've dpkg-reconfigured both isc-dhcp-client and resolvconf but still no joy. 

My guess is that the issue is either a) due to removal of network-manager or (b) a missing line of config somewhere, or (c) something interfering from another package - I have installed dnsmasq for instance (default ubuntu package)

Have searched up and down the internet and can only find other problems with resolvconf, never this one. 

Any help massively appreciated!

---

### Post by ahardy66 on 2012-08-07
75 views so far but no ideas - not a good sign! I was thinking of just re-installing the whole OS - but that's such a Microsoft-style way to go, I can't bring myself to do it.

---

### Post by bakegoodz on 2012-08-12
I usually just manually edit resolv.conf on Ubuntu server
```
nameserver 4.2.2.2
```
If you have dnsmasq setup correctly on that machine you can just point it to 127.0.0.1 and get the cached DNS and local DNS you can setup too.

---

### Post by ahardy66 on 2012-08-12
yes, thats what i was doing with my old machine. it'd be good to get this new resolvconf program going, but it looks like its foobarred.

---

### Post by ahardy66 on 2012-08-12
After googling a bit more just now, I decided to remove and purge dnsmasq and now resolvconf works - the DNS server from my ISP is in there. 

Cool but not that cool - I need dnsmasq. Hmmm. Maybe it will all magically start working when I re-install it. :guitar: That looks like correct usage of that smilie.

---

### Post by ahardy66 on 2012-08-12
Rats. Re-installing dnsmasq just brought back the problem. dnsmasq puts 127.0.0.1 into resolv.conf and chucks out the actual DNS server. 

I guess it's a dnsmasq issue so I'll do some more googling on dnsmasq and start a new thread if I still can't solve it.

---

### Post by bakegoodz on 2012-08-12
What are using dnsmasq for? Why do you not want it for DNS? How do you have this option set in dnsmasq.conf? > # Change this line if you want dns to get its upstream servers from
# somewhere other that /etc/resolv.conf
resolv-file=/etc/dnsmasqupstreamservers

---

### Post by ahardy66 on 2012-08-12
i need dnsmasq as the dhcp server for my lan. it's the easiest i've come across - although at the moment i'm defaulting to it, haven't looked for a better one recently. maybe i should. or maybe i should de-install resolvconf - don't really need it that bad.

but i dont understand your question. this is a gateway machine. eth0 is getting its ip address & dns from the ISP. 

dnsmasq serves dhcp to the rest of the lan on eth1 and gives them the gateway machine and I figured it passes on the DNS info from the resolv.conf. 

So why is it overwriting the resolv.conf? I'll look into it but I'm going to post this msg now so i can reconfigure it all and try out that dnsmasq option you mention

---

### Post by papibe on 2012-08-12
Hi ahardy66.

My first guess is that you are using the Desktop Edition.

12.04 introduced a [dnsmasq plugin]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/") for Network-Manager. It works great for is intended to do, but it is incompatible with other DNS packages like dnsmasq and bind (read [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/959037")).

If you are committed to use the Desktop Edition, you would need to unisntall Network-Manager and manage the network using config files.

On the other hand, the server edition does not have this problem.

Let us know how it goes.
Regards.

---

### Post by ahardy66 on 2012-08-12
1 step forward, 2 steps back. 

Now I've got rid of dnsmasq, but still dhclient isn't putting the dns info from the ISP into resolv.conf via resolvconf when the machine brings up eth0

---

### Post by bakegoodz on 2012-08-12
DNSmasq is a DNS and DHCP server. It's a pretty easy to setup DNS Caching server. Compared to BIND which has a pretty hard learning curve. I would recommend using just DHCP server if you just want DHCP. It isn't much harder to setup. I see that you removed network manager, so you will need to use the Ubuntu server's method for network settings. Which is in /etc/network/interfaces. Example:
> 
#/etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# Internet facing interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0

Reboot to update resolv.conf or do it manually
```
apt-get install isc-dhcp-server
cd /etc/dhcp/
mv dhcpd.conf dhcpd.backup
```
 edit /etc/dhcp/dhcpd.conf
> 
# /etc/dhcp/dhcpd.conf
ddns-update-style none;
default-lease-time 3600;
max-lease-time 7200;
authoritative;
log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.11 192.168.1.100;
option routers 192.168.1.1;
option domain-name-servers 8.8.8.8;
} 


So resolv.conf is only used for the server's DNS address, the clients DNS is given by the DHCP server set by dhcpd.conf under > option domain-name-servers

---

### Post by ahardy66 on 2012-08-13
> **papibe said:**
> Hi ahardy66.

My first guess is that you are using the Desktop Edition.

12.04 introduced a [dnsmasq plugin]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/") for Network-Manager. It works great for is intended to do, but it is incompatible with other DNS packages like dnsmasq and bind (read [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/959037")).

If you are committed to use the Desktop Edition, you would need to unisntall Network-Manager and manage the network using config files.

On the other hand, the server edition does not have this problem.

Let us know how it goes.
Regards.

Hi Papibe - when I downloaded ubuntu I had 2 choices IIRC, one was 'alternate CD' and I figured that wasn't what I wanted. Looking at the download page now it seems obvious now but this is my first ubuntu installation. 

I also read in various places that installing and de-installing the stuff I wanted and didn't want should be painless, and I guess up until now, it was. 

I also had the 'dnsmasq' package installed - I didn't read that it was just a plug-in for network-manager. 

Will it be worth scrapping my installation and going with the server edition? Is the package selection any more different on the basic networking front? 

I do actually use the GUI window manager quite a bit - xfce actually - since it's not just a gateway box, it's also my home media center.

---

### Post by ahardy66 on 2012-08-13
> **bakegoodz said:**
> DNSmasq is a DNS and DHCP server. It's a pretty easy to setup DNS Caching server. Compared to BIND which has a pretty hard learning curve. I would recommend using just DHCP server if you just want DHCP. It isn't much harder to setup. I see that you removed network manager, so you will need to use the Ubuntu server's method for network settings. Which is in /etc/network/interfaces. Example:

Reboot to update resolv.conf or do it manually
```
apt-get install isc-dhcp-server
cd /etc/dhcp/
mv dhcpd.conf dhcpd.backup
```

edit /etc/dhcp/dhcpd.conf
```

# /etc/dhcp/dhcpd.conf
ddns-update-style none;
default-lease-time 3600;
max-lease-time 7200;
authoritative;
log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.11 192.168.1.100;
option routers 192.168.1.1;
option domain-name-servers 8.8.8.8;
} 

```

So resolv.conf is only used for the server's DNS address, the clients DNS is given by the DHCP server set by dhcpd.conf under

```

option domain-name-servers

```



I'm slowly getting to grips with these concepts. You are saying, isc-dhcp-server gives the DNS names I enter manually into dhcpd.conf to the clients on the LAN when it's configured with that option. 

I'm not sitting at my server now so I can't check, but on my old machine, dnsmasq (like you call it, a DNS caching server) catered for the DNS requests from the LAN clients. I want to do that now on my new box as well. 

When I first found dnsmasq 5 years ago and started using it, I liked it compared to the other options available but figured that it would probably become redundant as linux brought out simpler DNS and DHCP servers - is that what has happened? Or am I still looking at dnsmasq as the best option here?

I see you favour the google dns. Me too - that and OpenDNS.

---

### Post by ahardy66 on 2012-08-13
I'm not at home right now but despite getting excited by the possible answers you guys have given, I just realised that neither actually helps the problem I've got right now - 

I'm not running dnsmasq and apart from a brief period of a couple of hours over the weekend, dhclient is not able to pass the ISP's DNS info into resolvconf. Something is blocking it. 

From previous experience I'd say I've probably foobar'd it myself in the config, but if I have, it's sure as ever not obvious.

---

### Post by bakegoodz on 2012-08-13
The main difference between Ubuntu Desktop and Server is that Desktop has a graphical manger and server does not. You can setup any server package on the desktop version. It used to be that Network Manager modified /etc/network/interfaces file, but now it works independently. So Ubuntu has 2 ways to configure network settings and some programs are only compatible with one of the configuration methods. Which is why if you use Ubuntu Desktop for server packages you may have to uninstall Network Manger.

You can get DNS from anywhere, unless you have a crazy ISP that blocks port 53. The DHCP client or Network Manger will set the /etc/resolv.conf DHCP Server will tell the DHCP clients to use any DNS server that you set in dhcpd.conf, it doesn't care what the server is using. You don't have to get DNS from your ISP, all DNS servers get their updates either directly from the Root Servers or update from another DNS server. There are reasons to be particular, for instance using OpenDNS's filtering feature, or you have special needs to have custom DNS for your LAN. For instance my wireless router runs DNSmasq and I can reach my computers by private DNS name instead of by IP address. My routers DHCP server tells DHCP clients to use the routers IP address for DNS and the router gets DNS updates from OpenDNS.

---

### Post by ahardy66 on 2012-08-14
> **bakegoodz said:**
> The main difference between Ubuntu Desktop and Server is that Desktop has a graphical manger and server does not. You can setup any server package on the desktop version. It used to be that Network Manager modified /etc/network/interfaces file, but now it works independently. So Ubuntu has 2 ways to configure network settings and some programs are only compatible with one of the configuration methods. Which is why if you use Ubuntu Desktop for server packages you may have to uninstall Network Manger.

You can get DNS from anywhere, unless you have a crazy ISP that blocks port 53. The DHCP client or Network Manger will set the /etc/resolv.conf DHCP Server will tell the DHCP clients to use any DNS server that you set in dhcpd.conf, it doesn't care what the server is using. You don't have to get DNS from your ISP, all DNS servers get their updates either directly from the Root Servers or update from another DNS server. There are reasons to be particular, for instance using OpenDNS's filtering feature, or you have special needs to have custom DNS for your LAN. For instance my wireless router runs DNSmasq and I can reach my computers by private DNS name instead of by IP address. My routers DHCP server tells DHCP clients to use the routers IP address for DNS and the router gets DNS updates from OpenDNS.

OK. Well, my ISP is good - no ports blocked. It's British Telecom. Their name servers have a really bad reputation though, so at the end of the day, I might not use them. 

However dhclient/DHCP is still not working with resolvconf and I'm not happy just going with it when I know it's foobard. 

I have de-installed network-manager, and dnsmasq. 

I don't think I have any other packages interfering with it, but maybe I don't know what to look for. 

I also edited /etc/hosts and /etc/network/interfaces but in a sane way as I had them on my debian box earlier to provide the same setup and they look like they should according to what you've said too.

I mean, let's forget about the LAN on eth1 for the moment - I just want to get eth0 up and running getting it's config sorted via DHCP from the dsl modem and the ISP, and fix whatever spanner is currently in the works.

---

### Post by bakegoodz on 2012-08-14
Honestly I'm a little perplex by resolv.conf update mechanism sometimes, I've had it not work right too. I know how to set it statically, if you edit /etc/resolvconf/resolv.conf.d/head it will set /etc/resolv.conf from the name server from that file.

---

### Post by ahardy66 on 2012-08-19
I just got back to my server and figured I'd give it a last ditch attempt to resolve the resolv.conf crisis ;)

I hadn't done a reconfigure of the resolvconf package after removing the dnsmasq package. 

Just did and it sorted the problem out, why, I don't know.

Have to re-install dnsmasq now and hope it doesn't go belly-up again.

---

### Post by ahardy66 on 2012-08-19
> **papibe said:**
> Hi ahardy66.

My first guess is that you are using the Desktop Edition.

12.04 introduced a [dnsmasq plugin]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/") for Network-Manager. It works great for is intended to do, but it is incompatible with other DNS packages like dnsmasq and bind (read [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/959037")).

If you are committed to use the Desktop Edition, you would need to unisntall Network-Manager and manage the network using config files.

On the other hand, the server edition does not have this problem.

Let us know how it goes.
Regards.

Hi @papibe

i cant find anything to distinguish the full dnsmasq from the plug-in dnsmasq for network-manager that you mention. 

i can only see dnsmasq and dnsmasq-base as packages in the package  repositories I have setup. Should i be looking in some particular server platform repository in my sources.list ? Doesn't look to me from a quick check that the sources.list has different reposoitories for server & desktop versions.

---

### Post by cariboo on 2012-08-19
If you are using the desktop version, removing network manager, may solve your problem. Or you can download the server iso [here]("http://www.ubuntu.com/download/server"), and restart without all the extra cruft the desktop version adds.

---

### Post by ahardy66 on 2012-08-22
> **cariboo907 said:**
> If you are using the desktop version, removing network manager, may solve your problem. Or you can download the server iso [here]("http://www.ubuntu.com/download/server"), and restart without all the extra cruft the desktop version adds.

Well, the situation is that I want to use it as a desktop as well. The machine is a gateway and server for the LAN but it's also my media center in my living room :popcorn:

My innate insanity tells me to carry on trying it the hard way, rather than ditching my current installation and starting from scratch. 

More rationally, if I did have a server platform install, my guess is that I would probably then have issues with desktop stuff like sound or fonts or something. 

Anyway, that argument aside, I did remove --purge network-manager a while back. 

The current state of play is that dnsmasq is killing the dns nameserver entries in /etc/resolv.conf which dhclient puts there, one from the ISP and two (set by me) from the /etc/network/interfaces file.

Could it be something really basic like the boot sequence? Should dnsmasq come up before dhclient sets up eth0? At the moment when I start it manually with the correct nameservers already in /etc/resolv.conf, it foobars them.

---

### Post by ahardy66 on 2012-08-22
Actually just read this from [www.thekellys.org.uk:](www.thekellys.org.uk:)

> 
In the simple configuration described above, processes local to the machine will not use dnsmasq, since they get their information about which nameservers to use from /etc/resolv.conf, which is set to the upstream nameservers. To fix this, simply replace the nameserver in /etc/resolv.conf with the local address 127.0.0.1 and give the address(es) of the upstream nameserver(s) to dnsmasq directly. You can do this using either the server option, or by putting them into another file, and telling dnsmasq about its location with the resolv-file option.


so it looks like this is meant to happen. 

However I want dnsmasq to pick up the nameserver from my ISP automatically - sounds to me like an incompatibility. I will read on...

OK there is a lot here. It looks like I need to set dhclient to write the name servers to a different file from /etc/resolv.conf and tell dnsmasq to read that. 

dnsmasq integrates dns-caching with dhcp for the lan really well. It seems to me that there is a big overlap in functionality between dns and dhcp so dnsmasq really makes sense as a solution. Helps me overcome my minimalist tendencies to research whether I can find and install a light-weight DNS server and a lightweight DHCP server :)

---

### Post by mia1dolfan on 2012-08-23
Solution:

```
sudo apt-get purge dhcp3-client
```

Now instead of overwriting the /etc/resolv.conf, the symlink remains and the dhclient entry gets prepended as the top resolver between the head and tail of resolvconf.

dhcp3-client is a old transitional package to the supported isc-dhcp-client.  dhcp3-client kept it's config files under /etc/dhcp3 while isc-dhcp-client uses /etc/dhcp.  I had two dhclient.conf files on my system.  dhclient was using the wrong config.

The Ubuntu supported isc-dhcp-client package includes a hook that runs as a script to function with resolvconf, located under /etc/dhcp/dhclient-enter-hooks.d/resolvconf

---

### Post by jdthood on 2012-10-29
> **ahardy66 said:**
> Rats. Re-installing dnsmasq just brought back the problem. dnsmasq puts 127.0.0.1 into resolv.conf and chucks out the actual DNS server. 

I guess it's a dnsmasq issue so I'll do some more googling on dnsmasq and start a new thread if I still can't solve it.

I gather you wanted the DHCP-server functionality of dnsmasq but not the DNS nameserver functionality. In that case you should set

    IGNORE_RESOLVCONF=yes

in /etc/default/dnsmasq and edit /etc/dnsmasq.conf to disable DNS functionality. The following 

    port=0

should to it. After changing these settings do

    /etc/init.d/dnsmasq restart

Now the dnsmasq initscript won't submit 127.0.0.1 as a nameserver address to resolvconf, so you should see upstream nameserver addresses in resolv.conf instead.

If you still have problems please write to me directly at jdthood AT gmail DOT com.

---

