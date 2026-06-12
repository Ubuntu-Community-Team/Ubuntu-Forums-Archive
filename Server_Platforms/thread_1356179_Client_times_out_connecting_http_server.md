---
title: "Client times out connecting http server"
date: 2009-12-15
forum: Server Platforms
---

### Post by wiseguy12851 on 2009-12-15
I am running Ubuntu Server on a VMware computer with a NAT ip.
 
I am an advanced software engineer in all common computer languages but have never stepped foot in linux territory so I am learning very quick and have set up an HTTP server and downloaded my website from online server using FTP
 
Linux and the host computer connect instantly, hence the host computer is Windows Vista -- Cold Shiver --, When I get the IP address through linux (The one the host connects to within microseconds) all other computers completely time out (All windows). Even the command prompt displays request timed out.
 
I have hardly scratched the surface of linux and don't know how to access logs and such but another important detail to note is that the only steps I took to setting up the HTTP server was installing the packages and placing the website from online in the default directory allowing the loop-back address in linux and the given NAT address for Vista to access without any problems.
 
My ultimate goal is to setup test server for HTTP with a domain, nothing serious like dedicated speed and uptime, and to get to explorer Linux's network capabilities which Linux is built upon.
 
Any help with this timeout error, and should I do some more configuring

---

### Post by BkkBonanza on 2009-12-15
You cannot use NAT mode interface for external access.
Unfortunately I don't use VMware so I can't tell you the name of the correct mode.
I use VirtualBox, which is similar, and they have "Bridged" mode that makes the VM look like another machine on the LAN for connections. VMWare no doubt has a similar type of network adapter.

With NAT mode your host machine acts as a router / NAT for the guest. You would have to create some special forwarding routes to get connections through to the guest.

---

### Post by wiseguy12851 on 2009-12-15
I've tried everything I could do with bridged, releasing ip, renewing, Double checking setup. As far as I can gather linux is unabe to connect to the network and cannot detect anywhere to connect to, if bridge is selected.

That brings me down to play around (and probably mess up) the vista routing table, or spend all of my time trying to get bridged working.

I was considering getting some sort of proxy software on my computer to do the routing for me but it would be a lot easier if I could just get bridged working and get a real connection to my actual hardware and nothing virtualized.

I want to switch to ubuntu but I'm not going to dedicate just yet until I can get around a lot better. Which means this needs to be setup.

---

### Post by BkkBonanza on 2009-12-15
Ok. Take this as just generic guessing because as mentioned I use VirtualBox. This is just in case someone with specific VMWare knowledge doesn't post. (You may be better asking this question on a vmware specific forum that has a lot more vmware experts or even in the Virtualization board here where it will get viewed by people using that).

With Bridged mode the ip address is likely assigned by your dhcp server on your LAN. So if you're not setup so that your router will do dhcp that could prevent the bridged adapter from getting an ip and it would be unconnectable.

I believe using bridged mode should be easy with no hacks and routing changes to function. If it's that hard on vmware then I'd recommend VirtualBox where this works easily by default. But even on VB it needs to get assigned it's own ip by the dhcp server on the LAN. It doesn't know what ip to use otherwise.

Another thought - if you have a firewall on your host machine (Vista?) then it will block any connections to your guest as well. So make sure to open the port needed. eg. 80 for http.

---

### Post by wiseguy12851 on 2009-12-15
That's a good guess but my router has been configured to distribute DHCP addresses and is already doing this for multiple PC's. I'm having the same problem with other routers in other locations as well. Even my copy of vista receives an IP from whatever router it's connected to.

on a side note: Is virtual box free?

---

### Post by BkkBonanza on 2009-12-15
There is both an open source version (totally free) and a non open version that is free (as in beer). So yes, free to use without payment. It works very, very well for running test servers. I do all my web development locally in a guest Ubuntu machine embedded within my Ubuntu host. Then when it's ready I just type an rsync command (or script I made) that udpates it all to the real live server out on the web.

Also VB has an integrated desktop mode where apps from both Linux and windows can show up on the same desktop. I don't usually use that but it was pretty cool when I tried it. VB was started by a smaller company but bought by Sun Microsystems some time ago.

Double check the firewall issue - sometimes people forget about it and get hung up there.

---

