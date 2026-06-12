---
title: "Need dns cache-dnsmasq"
date: 2012-09-30
forum: Server Platforms
---

### Post by hawaiiman on 2012-09-30
Making server for school. ISP is PPPoe. internet-modem/router-server-WAN(eth0)-LAN(eth2)-switch-clients. eth0 is dhcp. eth2 is static 10.10.0.1 255.255.255.0.
I am attemting to use dnsmasq to create dns caching and dhcp on LAN. 
I commented out dns-dnsmasq in NM, downloaded and installed dnsmasq, and configured dnsmasq.conf, but no caching and no dhcp. If clients are set to static ip and gateway, etc. then they go to internet fine. dig shows repeated 50ms to google.com and client shows "unknown network no internet" when i re-set the properties to dhcp.

---

### Post by elico on 2012-09-30
I would suggest you to use Bind and dhcpd and also add on the way webmin and you will get a server that gives you good interface and results for your needs.

---

### Post by hawaiiman on 2012-09-30
I've been working along, and got dns caching going with Bind9, but the cache dies on reboot. DHCP is going with isc-dhcp-server and working well.
Need to get cache to persist so multiple clients on LAN can access and will persist over time.
I have tried to get webmin, but every direction fails with a broken link or unavailable source. The mirror link fails, the sourceforge link from their website gives 404 error. I did manage to download the tarball, but can't find an autorun or anything I can ./... dpkg tries to find it online and fails. Frustrating, it sounds great.

---

### Post by hawaiiman on 2012-09-30
Where there's a will...webmin up and running.

---

### Post by hawaiiman on 2012-10-18
Sorry, but it's got to be dnsmasq. Server is working, but not caching. Removed dhcp3-server, ufw and bind9. I really don't like the idea of webmin.

---

### Post by hawaiiman on 2012-10-20
Update: Getting online from client, getting dhcp assignment, but no caching (it was not forwarding. Added POSTROUTING command to /etc/rc.local) This is dnsmasq, supposedly cache by default. I did go for webmin. No ufw, no NM,no bind9

---

### Post by darkod on 2012-10-20
Are you using the server version, or the desktop? Network Manager is not installed by default in the server version as far as I know. So I don't understand why are you mentioning it. Did you install it?

On another note, setting up dnsmasq for dns caching is very easy. And for dhcp too.

Open the /etc/dnsmasq.conf file and find the line:
#interface=

Remove the # symbol and add the interface you want it to serve dns to, for example:
interface=eth1

That should be the interface leading to the clients (local LAN).

As for dhcp, it's disabled by default so find the line that says like:
#dhcp-range=......

Change it to:
dhcp-range=eth1,192.168.1.100,192.168.1.200,7d

The subnet I used is just an example, change it to the range that you want to issue with the dhcp. You can see that you can also specify the interface where you want the dhcp to be served.

That should be it. Restart the server and check if it's working.

---

### Post by hawaiiman on 2012-10-20
That's exactly what's been done. Apparently the gnome package put NM back in. This is the server 64bit LTS with gnome added. Everythings works great, thanks to your prior help. It just doesn't cache, however. When I ping google.com from the client I get the same 83 ms as many times as I want to bother. Since we last exchanged I formatted and re-installed one last time due to a screw up with permissions and passwords I created. I was very carefull to do as little as possible as far as configuration goes, as I had heard the caching is supposed to be a default. I'm not losing sleep over it, but I would like to get it going, and hopefully learn something too.

---

### Post by darkod on 2012-10-20
Yeah, but what dns are the clients using? Remember that you need to tell dnsmasq dhcp to send that info to the clients like you needed to do with the router IP.

If you clients are windows, what does ipconfig /all say for dns server? Is it the ubuntu server IP?

PS. Why are you adding gnome to a server, for GUI?

---

### Post by hawaiiman on 2012-10-20
windows clients say dns is 10.10.0.1. There are several reasons I added gnome, but mostly a gui. I've got a fair amount of hdd room (500 gb) ram is 2 gb, so I think I can live with it. One reason is I'm partly disabled and my right hand is missing some parts. I get tired of typing with my thumb. I plan on developing a website hosted on this server and wanted gimp, kompozer, etc.

---

### Post by darkod on 2012-10-20
In that case it looks set up correctly. I don't know what could be the issue, I don't see anything.

---

### Post by Doug S on 2012-10-20
In post #8 above when you said:> When I ping google.com from the client I get the same 83 ms as many times as I want to bother.Did you mean to say "dig" instead of "ping", as in post #1? Caching or not will not influence "ping" but will repeated "dig"s.

---

### Post by hawaiiman on 2012-10-20
Hmm, I have been using ping as a test on the client machine. I thought dig was a linux command. In any case I just did dig to google on the server and no evidence of caching. I believe the problem is one of configuration of nameserver listing. dnsmasq default goes to resolv.conf for list of recursive nameservers. The tutorial ends with adding several. Having tried this, I notice that on re-boot, the list is purged and the only one appearing is 192.168.1.1 which it is picking up automatically. There seem to be ways to adjust this. There is a choice to enter a list in dnsmasq.conf and comment out resolv.conf, for example. I wanted to get the basic setup working before adding variables, so now I can try adjusting, and see what happens.

---

### Post by hawaiiman on 2012-10-21
I saw a man page for resolvconf in ubuntu that stated that dnsmasq would go to resolv.conf for nameservers (added s for resolvconf) and that would look to those listed in /etc/network/interfaces. It gave an example of a single nic server with a static ip. So my first attempt was to list nemerser xx.xx.xx.xx under eth1 as it had a staic ip. This killed outside access. `dig google.com' `no servers could be reached' So removed those entries. 
After trying several variations, I found that dnsmasq default goes to /etc/resolv.conf for a list of nameservers. resolv.conf queries /etc/network/interfaces and will add those listed there. If eth0 is static, then all is good, but if eth0 is dhcp, then there is no way to configure effectively using this approach.
[http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html)
This seems to discuss this, but is beyond my level of understanding at this point. I may be wrong but it appears that dnsmasq doesn't fully support caching in the case where eth0 is dynamic rather than static. I will continue to experiment.

---

### Post by darkod on 2012-10-21
Why do you have dhcp on eth0? Is that a requirement from the ISP of the interface is directly on the internet, or it's connected to your router?

If it's connected to your router set up static IP which you should always do with servers on all interfaces. That way you are sure it will never change. Just use an IP outside of the router dhcp range. And when using static you can add the setting for eth0:
dns-nameservers x.x.x.x y.y.y.y

That way the server (and dnsmasq) will use those nameservers.

---

### Post by hawaiiman on 2012-10-21
Great idea! Only problem: at home I can't change settings on the router/modem. At school, I believe there is some flexibility as it's a near enterprise sort of thing. I don't recall, but I believe it may not allow a static ip either. As I recall, I set the dhcp range to one ip number, that must have been the reason. School starts in about 10 days for teachers, and I'll have some student free days to make adjustments. As I said, not caching isn't the end of the world. Having the samba file server should be a huge hit with the staff. That's working well.

---

### Post by darkod on 2012-10-21
For using static IP on the server you don't need to do anything on the router end. It helps to know the range it is issuing but you can try. So, having complete access to the router config is not always needed.

For example, when the router is 192.168.1.1 usually it doesn't start issuing addresses right away from 192.168.1.2. Usually they start at 192.168.1.30 or 192.168.1.100, etc.

So, you can use 192.168.1.2 as a static IP for the server for example, and see how it works.

But if you need to do some port forwarding or similar on the router, to enable some kind of outside access, that might be a problem if you don't have full access.

---

### Post by hawaiiman on 2012-10-21
So if i set the eth0 in network/interfaces to static and assign something in range, that will work? Interesting. Sounds good. Then I can list nameserver xx.xx.xx.xx under eth0 and it should work. For some reason, I had the idea that the dhcp of the router would force eth0 to whatever ip the router wanted to assign it.Yes the router at home is totally locked. I tried re-flashing the firmware to get around that, but ended up with a bigger problem. The one at school has access to port forwarding, filtering, etc. That's why I don't really need an in server firewall.

---

### Post by darkod on 2012-10-21
Correct, it will receive an automatic IP only if the network card of the client is set to use automatic dhcp. If it's on static, it ignores any dhcp servers running on the network.

And just a reminder, the command you need in /etc/network/interfaces is not nameserver, it's:
dns-nameservers x.x.x.x y.y.y.y

So it will look something like:
```
auto eth0
iface eth0 inet static
   address 192.168.1.2
   netmask 255.255.255.0
   gateway 192.168.1.1
   dns-nameservers x.x.x.x y.y.y.y
```

---

### Post by hawaiiman on 2012-10-21
Ok, do I list the loopback? Do I list 192.168.1.1, or start out with the outside servers like the isp's and some others like the other isp's (home and school are not same) and opendns, google, etc?

---

### Post by darkod on 2012-10-21
I would start by listing the ISP nameservers, not the router.
As for the loopback address, I'm not sure if it would help. Investigate a little if it helps dnsmasq with caching, otherwise if it doesn't, no need to list it I think.

---

### Post by hawaiiman on 2012-10-21
That broke everything. I remember long before in this process trying to get eth0 going as static and couldn't. Server is off line and ifconfig shows neither eth0 or eth1 getting an ip address. Of course that eliminates the client as well. BTW I tried it without change to resolve.conf and with adding a line ` search myname.no-ip.org' , although it's set for 10 minute refresh, so maybe I should wait (?). I don't remember the suggested format for the nameserver entries there, seems like it was something with / instead of- or .

---

### Post by hawaiiman on 2012-10-27
So, I'm right where I started, except I guess I'll give up on caching with a dhcp eth0. Funny too as the router is assigning a single ip to eth0 and yet if I set eth0 to static, it falls over. Everything else is going good. The new term starts the 29th (Oct.) and I'll have it at school with a better router. See what happens then.  I have read in tutorials for other caching packages that static ip is a necessity.

---

### Post by jdthood on 2012-10-29
> **hawaiiman said:**
> I saw a man page for resolvconf in ubuntu that stated that dnsmasq would go to resolv.conf for nameservers (added s for resolvconf) and that would look to those listed in /etc/network/interfaces. [...] After trying several variations, I found that dnsmasq default goes to /etc/resolv.conf for a list of nameservers.

When resolvconf and dnsmasq are installed, dnsmasq obtains its list of forwarder nameserver addresses from resolvconf's database instead of from /etc/resolv.conf.

> **hawaiiman said:**
> resolv.conf queries /etc/network/interfaces and will add those listed there.

What happens, more precisely, is that resolvconf generates resolv.conf from information that comes from /etc/network/interfaces, among other sources. See the resolvconf man page for details.

---

### Post by jdthood on 2012-10-29
Dnsmasq's cache size is controlled using the cache-size option either on the command line or in one of dnsmasq's configuration files. Make sure that the cache size is larger than zero. You may want to set the size to a three- or four-digit number.

---

### Post by hawaiiman on 2012-11-08
I realize that. Cache set to 300 previously. 
As I said previously, the problem seems to arise from /etc/resolv.conf looking for a list of nameservers in the information listed in /etc/network/interfaces this is all fine with a machine with a static ip on the wan side. Unfortunately, this eth0 is dynamic, and thus no nameservers are listed for eth0. /etcf/resolv.conf deletes all entries at reboot and defaults to the router as the nameserver, which seems to prevent caching.

---

### Post by jdthood on 2012-11-12
> **hawaiiman said:**
> As I said previously, the problem seems to arise from /etc/resolv.conf looking for a list of nameservers in the information listed in /etc/network/interfaces  [T]his is all fine with a machine with a static ip on the wan side. Unfortunately, this eth0 is dynamic, and thus no nameservers are listed for eth0. /etc/resolv.conf deletes all entries at reboot and defaults to the router as the nameserver, which seems to prevent caching.

Your posts would be easier to read if you distinguished between resolvconf, a program, and /etc/resolv.conf, a file.

If I understand correctly, if you have the following in /etc/network/interfaces

```
iface eth0 inet static
        address 192.168.1.99
        ...
        dns-nameservers w.x.y.z
```

then dnsmasq uses w.x.y.z as its upstream recursive nameserver and dnsmasq caches the replies; all is well.

However, if you have the following in /etc/network/interfaces

```
iface eth0 inet dhcp
```

then dnsmasq uses the router's nameserver as its upstream recursive nameserver and does not cache.

My guess is that the router's nameserver sends out results with TTL=0, causing dnsmasq not to cache them. I don't know of any way to cause dnsmasq to override TTL values coming from upstream.

I'll assume that the problem is to be solved by using nameserver w.x.y.z in preference to the router nameserver. Do the following. (1) In /etc/network/interfaces add a "dns-nameservers" line to the "iface eth0" stanza.

```
iface eth0 inet dhcp
        dns-nameservers w.x.y.z
```

(2) In /etc/resolvconf/interface-order add a line "eth0.dhcp" before the line "eth*". This will cause the nameserver address w.x.y.z to be prioritized over the address provided via DHCP (which has the record name "eth0.dhclient").

```
$ diff -u interface-order_ORIG interface-order
--- interface-order_ORIG	2012-11-12 21:04:51.341700438 +0100
+++ interface-order	2012-11-12 21:05:37.569702413 +0100
@@ -9,6 +9,7 @@
 hso*
 em+([0-9])?(_+([0-9]))*
 p+([0-9])p+([0-9])?(_+([0-9]))*
+eth0.dhcp
 eth*
 ath*
 wlan*
```

(3) Do the following in a terminal

```
sudo ifdown eth0
sudo ifup eth0
```

In /etc/resolv.conf you should now have only one "nameserver" line, the following.

```
nameserver 127.0.0.1
```

To see what nameserver address(es) dnsmasq is forwarding to, look in /var/run/dnsmasq/resolv.conf.

---

