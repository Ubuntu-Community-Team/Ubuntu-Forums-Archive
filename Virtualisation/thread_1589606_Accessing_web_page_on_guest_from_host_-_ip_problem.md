---
title: "Accessing web page on guest from host - ip problem"
date: 2010-10-06
forum: Virtualisation
---

### Post by pablopancho on 2010-10-06
Hi

I have a strange problem with Virtualbox. I searched forums but I didn't find answers.

The host: Ubuntu Lucid Desktop x64
The guest Ubuntu Lucid Server x64 - LAMP

I'm using bridged networking. The guest server is getting IP address from DHCP on my O2 wireless box.

The ip address of the guest changed from 192.168.1.72 to 192.168.1.73.

When I'm typing in firefox address bar on host "192.168.1.[COLOR="Red"]73[/COLOR]" the browser responds that 192.168.1.[COLOR="Red"]72[/COLOR] is not available. The same happens when I use Opera.

Why browsers change to old ip address? How to repair/prevent it?

Thanks

---

### Post by SeijiSensei on 2010-10-06
I just diagnosed the same problem myself last night.  I have Ubuntu server as a VB guest within a Ubuntu host.

For me the solution was to put the guest NIC into "Host-only mode" which created a virtual interface on the guest and assigned both it and its own interface to private addresses.  I can now open a web page inside the guest using a browser on the host with the guest's IP.

I haven't tried connecting to the guest from other machines around the network because this machine is isolated behind a router.  I'd guess that with correcting routing established you should be able to see the guest from outside the host.

---

### Post by pablopancho on 2010-10-06
Thanks SeijiSensei, I suppose this should work.

However I really would like to know what causes this problem.

I should add that I can ping 192.168.1.73 from the host without any problem so it isn't really a connection issue - it seems to be a browser(s) issue.

---

### Post by SeijiSensei on 2010-10-06
In bridged mode the guest has the same IP as the host.  I'm not sure how a request for a webserver running on the guest using the bridged IP would be handled in this case.  I can confirm that in bridged mode I couldn't open a web page on the guest from the host using the shared IP.

I never use bridging, only IP routing.

However I can confirm that if I set up the guest in host-only mode, then add a default route in the host using the guest's IP on the VB interface vboxnet0 as the gateway, I can see the guest from outside the host.  I have to enable IP forwarding on the host, of course, by setting /proc/sys/net/ipv4/ip_forward to 1 using the net.ipv4.ip_forward directive in /etc/sysctl.conf.  I also needed to add a static route on my main router to the private VBox network address using the VB host's external IP address as the gateway.

---

### Post by pablopancho on 2010-10-06
> **SeijiSensei said:**
> In bridged mode the guest has the same IP as the host.  I'm not sure how a request for a webserver running on the guest using the bridged IP would be handled in this case.  I can confirm that in bridged mode I couldn't open a web page on the guest from the host using the shared IP.

Sorry, you lost me here :confused:

As I understand it, in bridged mode my guest machine asked for a seperate ip address from DHCP. My host is on the 192.168.1.0/24 network and so is the guest and the wireless router. When I log in to the router I can see the guest as a seperate computer with seperate ip address.

Normally I don't have any problem because I set up a static address on guest so it doesn't change. However this time I forgot to do it and after some time DHCP assigned different ip address than before. The guest still has connection to the internet, everything is fine, ping works, the only problem is when I try to view a page from host's browser. As if there was a cache somewhere that tells browser to look for that page at 192.168.1.72 and not at 192.168.1.73. Really weird.

The only thing that would work is to give the guest previous ip address. But that wouldn't give me the explanation :(

---

### Post by SeijiSensei on 2010-10-06
OK, here's what I think is happening. 

I put my VB guest into bridged mode and rebooted.  I get a different IP address (192.168.1.3) than my host has (192.168.1.2).  I can ping the host from the guest *but not vice versa*.  That's because traffic for everything in 192.168.1.0/24 is sent to the router.  The router will look for the guest on its own network; it won't know that 192.168.1.3 is behind my host.  

I'm not sure I really understand the issue you reported.  Can you ping the guest from the host in bridged mode?  When you use a static IP on the guest, do you give it an address in the same address block as the host?  For instance, if the host is 192.168.1.20, do you give the guest an address like 192.168.1.21, or do you give it an address in an entirely different range like 192.168.2.1?  That approach might work because then the traffic for the guest isn't sent to the router.

Anyway I'm sticking with host mode because I understand how to get the routing set up correctly to make that work.  In host mode it's just as if I had two network cards in the host, one connected to the Internet router and one connected to another PC running as the guest.  As long as all the machines along the way know what to do with packets intended for the guest's IP address, everything works the way I expect it to.

---

### Post by pablopancho on 2010-10-07
Everything is fine - I can ping in both directions, I can use ftp server on a guest, I can ssh to the guest, the only problem is apache server.

---

### Post by pablopancho on 2010-10-08
BUMP!

Anyone had similar problem? Any solutions/ideas?

---

