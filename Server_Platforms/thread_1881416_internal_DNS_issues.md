---
title: "internal DNS issues"
date: 2011-11-15
forum: Server Platforms
---

### Post by dbecker on 2011-11-15
I have 2 internal virtual hosts setup on apache2; each are displayed when i login to webmin; site1 and site2 each on port 80, with different document root dir's. 

This is all inside LAN. 

I can access [http://site1](http://site1) perfectly fine from a browser inside LAN. The url started working after samba/winbind was installed. 

I CANNOT access [http://site2](http://site2) UNLESS i edit the client pc's hosts file. 

I installed dnsmasq on the same server, to use for local DNS resolution. I read that dnsmasq uses the /etc/hosts file, so I added restarting networking each time: 

192.168.1.137 site1 site2

no resolution when going to [http://site2](http://site2), so I tried this:

192.168.1.137 site1
192.168.1.137 site2

still no go. 

Any pointers?

---

### Post by Jonathan L on 2011-11-15
> **dbecker said:**
> I have 2 internal virtual hosts setup on apache2; each are displayed when i login to webmin; site1 and site2 each on port 80, with different document root dir's. 

This is all inside LAN. 

I can access [http://site1](http://site1) perfectly fine from a browser inside LAN. The url started working after samba/winbind was installed. 

I CANNOT access [http://site2](http://site2) UNLESS i edit the client pc's hosts file. 

I installed dnsmasq on the same server, to use for local DNS resolution. I read that dnsmasq uses the /etc/hosts file, so I added restarting networking each time: 

192.168.1.137 site1 site2

no resolution when going to [http://site2](http://site2), so I tried this:

192.168.1.137 site1
192.168.1.137 site2

still no go. 

Any pointers?

Hi Dbecker

Sounds to me like your client machines aren't using your server for name resolution.  (This is suggested by site1 working when you installed Samba, which will mean your clients are able to use local netbios name resolution, but it's not a good way to do it realy.)

1.  Test dnsmasq

On server
```
dig @localhost site2 a
```

On Client
```
dig @192.168.1.137 site2 a
```

Both should answer with 192.168.1.137

2.  Check local name server

On cleint
```
cat /etc/resolv.conf
```

Is the nameserver 192.168.1.137 or something else?  My guess is that you'll find it's something else, which was given to it by DHCP.

3.  Find your DHCP server

Is your DHCP server the router (most likely) or dnsmasq (if you installed that).  Whichever it is, check what it is giving out as the name server address to the clients.  I'm pretty sure that's where it's going wrong.

Hope that's helpful.

Kind regards,
Joanthan.

---

### Post by dbecker on 2011-11-15
thanks Joanthan!

server: dig @localhost site2 -> returns answer 192.168.1.137
windows client: dig @192.168.1.137 site2 -> returns answer 192.168.1.137

since the client is winxp, i wasn't sure how to check nameserver, other then by typing ipconfig /all in cmd prompt; here i found: DNS Servers - 192.168.1.137, which is specified in the connection/tcpip/properties section. This client has static IP set. 

My dhcp server is my router. I Also installed dnsmasq on 192.168.1.137, but i do not have dhcp enabled. 

I looked at my hyperWRT router and unchecked the small box that said "use dnsmasq for DNS" and also entered 192.168.1.137 for Static DNS 1 on router. 

still can't hit [http://site2](http://site2) from client without modifying client c/windows/drivers/etc/hosts file

?

---

### Post by Jonathan L on 2011-11-17
Hi again Dbecker

> 
server: dig @localhost site2 -> returns answer 192.168.1.137
windows client: dig @192.168.1.137 site2 -> returns answer 192.168.1.137

since the client is winxp, i wasn't sure how to check nameserver, other then by typing ipconfig /all in cmd prompt; here i found: DNS Servers - 192.168.1.137, which is specified in the connection/tcpip/properties section. This client has static IP set. 
Good.  Are you digging for full domain names or hostnames?  That is, site2.something.cmo or jus site2?

> My dhcp server is my router. I Also installed dnsmasq on 192.168.1.137, but i do not have dhcp enabled. 

I looked at my hyperWRT router and unchecked the small box that said "use dnsmasq for DNS" and also entered 192.168.1.137 for Static DNS 1 on router. 

still can't hit [http://site2](http://site2) from client without modifying client c/windows/drivers/etc/hosts file
As your client has static IP addressing, the DHCP should make no difference whatsoever, and you say it uses .137 for its DNS server.

The thing to check next is the domains that the client has for its domain search.  In ipconfig /all there should be a domain as well as a hostname, shown as "primary DNS suffix" (wee wikipedia [image]("http://upload.wikimedia.org/wikipedia/en/6/6c/Ipconfig_win_xp.png")).
Unless this matches the domain that you dig for, you won't get resolution.

**_Steps_**

1.  On client, use default DNS server (ie, no '@'):
```
dig site2
```2.  On client, check primary DNS suffix
```
ipconfig /all
```This suffix would be set by DHCP if you were using it; for a static XP machine I understand you do it as right-click My Computer > Properties > More. (see MS [document]("http://support.microsoft.com/kb/295017"))


Let us know if that helps.

Jonathan.

---

