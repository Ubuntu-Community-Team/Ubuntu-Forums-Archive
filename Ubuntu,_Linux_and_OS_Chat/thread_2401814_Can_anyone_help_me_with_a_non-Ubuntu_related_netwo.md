---
title: "Can anyone help me with a non-Ubuntu related networking problem?"
date: 2018-09-22
forum: Ubuntu, Linux and OS Chat
---

### Post by SagaciousKJB on 2018-09-22
Okay to this is a weird use case and will take a little bit of reading to understand.

I have a DNS server I've put on a local machine at 192.168.1.43 that I would like all my local devices to use.  To do so I edited the DNS IP settings in my router's configuration.  However when I dig my *subdomain*.ddns.net I set custom records for, I get back the wrong record.  However, if I dig the 192.168.1.43 address directly, I get the expected record.

I get back the external IP address that any DNS server would serve up when I dig 192.168.1.1, where as I've configured my local DNS server to instead provide local addresses for the subdomain. *mysubdomain.ddns.net* points to my server (with a few web services on it) 192.168.1.43, *desktop.*ddns.net points to my desktop 192.168.1.2, and so on. (I have a couple IP Cameras I want to make ipcam1.ddns.net, ipcam2.ddns.net, etc. but that was just miscellaneous)  The reason I need this done is the router is too inferior to know that if I am trying to connect to my external IP from a local IP address, that it should route to whatever local IP that port is forwarded to (192.168.1.43 for 80 for instance); instead it just tries to connect to the actual router itself on that port.  The end result it is makes my subdomain unusable from within my own network.

My hope was that by setting *mysubdomain*.ddns.net  to be the local IP addresses of the servers I needed, they would resolve the domain to internal IPs and connect to them without need for routing.  Then when I was connected abroad, it would use whatever DNS server was configured for whatever WiFi network I ended up connecting to, and would connect to the external IP it resolved just fine.  In the meantime, I also configured my custom DNS server to act as a caching server with forwarders to Google so that I could resolve every other address normally. I only had custom records for *mysubdomain*.ddns.net

Well, it was working for a day or two, but then my tablet stopped resolving the internal IP and would only resolve the external one.  I checked my logs for bind, and I couldn't even see that it was querying my server (so it wasn't just being forwarded), and then when I checked out Google Chrome's settings on my tablet (chrome://net-internals/#dns) , I found that it was using some IPV6 addresses for my IPS as the nameservers instead of either my local DNS server, or the Google DNS I had set as an alternative server in my router's configuration and as forwarders on my custom DNS server.  It seemed to have randomly decided its own DNS settings to use completely different from any that I'd specified.

To add to that mysterious behavior, when I go into my Android settings and manually configure the DNS address, the tablet still ignores the settings and resolves the external IP address through my ISP's nameservers.  The only way I can get it to respect my DNS settings now is to use a DNS-changer app that routes it through a VPN tunnel.

I believe the only reason that it is working flawlessly between my local Linux computers is because I manually changed the nameservers in /etc/resolv.conf to point to my local DNS server 192.168.1.43.  Otherwise if I were to rely on DHCP I believe it would still just be pointing towards my router at 192.168.1.1 which dig shows is producing the wrong records as well.

I'm not really sure what to think about this.  Are my router and my Android BOTH doing something suspiciously user-unfriendly by refusing to use the DNS settings I specify, or is there something else going on?  Having both my Linux PCs /etc/resolv.conf pointed directly toward the local DNS has been working flawlessly for them, but between my Android tablet and my router there's something unexpected going on.

My Router: Welcome to Sagemcom F@st 5260
My Android Tablet: Galaxy Tab A6
My DNS Server: Ubuntu 16.04.5 TLS with bind9
My ISP: Charter Spectrum

---

### Post by TheFu on 2018-09-23
Most people use internal domain names for internal use and use public domain names for internet use.
.net is public.
.local or .lan or .foo or **any** non-TLD would be internal.

I use a VPN running at home to access my LAN from the outside world. This prevents all sorts of other security problems, like having to trust some 3rd party to get remote access.  Most VPNs work on any networked OS.  

BTW, android releases 6.x and later ignore DNS and always use 8.8.8.8.  Thank google for that. [https://www.androidpolice.com/2018/04/20/make-android-use-dns-server-choice/](https://www.androidpolice.com/2018/04/20/make-android-use-dns-server-choice/)  In theory, Android-P will provide a viable workaround to the problem that wasn't a problem before Google screwed with it.

I know nothing about IPv6 except that is has caused issues with many services, connections and has security implications I'm not equipped to handle. For those reasons, I disabled it on all my servers, routers, and desktops.  Only 1 service on 1 server has seen that as an issue and there was a config option to disable any attempted use of IPv6 for that service.  Not having it on the system wasn't enough.

---

### Post by SagaciousKJB on 2018-09-23
> **TheFu said:**
> Most people use internal domain names for internal use and use public domain names for internet use.
.net is public.
.local or .lan or .foo or **any** non-TLD would be internal.

I use a VPN running at home to access my LAN from the outside world. This prevents all sorts of other security problems, like having to trust some 3rd party to get remote access.  Most VPNs work on any networked OS.  

BTW, android releases 6.x and later ignore DNS and always use 8.8.8.8.  Thank google for that. [https://www.androidpolice.com/2018/04/20/make-android-use-dns-server-choice/](https://www.androidpolice.com/2018/04/20/make-android-use-dns-server-choice/)  In theory, Android-P will provide a viable workaround to the problem that wasn't a problem before Google screwed with it.

I know nothing about IPv6 except that is has caused issues with many services, connections and has security implications I'm not equipped to handle. For those reasons, I disabled it on all my servers, routers, and desktops.  Only 1 service on 1 server has seen that as an issue and there was a config option to disable any attempted use of IPv6 for that service.  Not having it on the system wasn't enough.

Yeah I realize it's unorthodox but I couldn't think of a better solution. Right now *mysubdomain*.ddns.net needs to be the singular host name which I can connect to regardless of network. Before, I couldn't use anything but local IPs if I was connected on my own LAN, so I was constantly having to go change my configuration files to be a local IP or my subdomain name based on if I was home or not.

I'm not so much worried about accessing my LAN from the outside world since I only really need to check security cameras remotely, but the services I run at home are heavily networked and Web based so I essentially just want to stop having to connect to  a local IP to view my cameras at home, and would rather use the same URL I connect to to monitor them abroad.

Well that is interesting about them forcing the use of Google... But mine is running 5.1.1 so that makes it a little confusing still.

---

