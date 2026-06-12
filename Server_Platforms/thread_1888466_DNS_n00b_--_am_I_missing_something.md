---
title: "DNS n00b -- am I missing something?"
date: 2011-11-29
forum: Server Platforms
---

### Post by kr651129 on 2011-11-29
I'm not really sure how to explain what my question is because that is half the question, I don't know enough DNS vocab. to know how to explain what I need, so I'll try my best and hope to learn a lot.

I have a server at home Ubuntu 11.10 32bit running a RAID0 on an old Dell machine.  Basiclly this server holds all of my media, music, video, etc.

I've created a drupal webpage and added an html5 media player so I can stream all of this media to my android, iOS, Wii, and other devices that support HTML5.

I want to create a DNS so that every time I go to my intranet homepage I don't need the IP, I can just type in [http://headless/](http://headless/)

I've followed all of the DNS tutorials out there and from what I've gathered I need to set up forwarding?  I'm also a little confused about if I need to adjust any settings on my router.

Even if I don't learn what I'm trying to do just knowing the right words to google will go a long way for me.

Thanks for the help!

---

### Post by mikegior on 2011-11-29
Where are you setting up this DNS record? From the sounds of it, you want what is called an "A" record which simply "attaches" and IP address to a hostname.

Example: 192.168.0.100 is your media server

A RECORD for that IP address will be "mediaserver"

That's what allows you to do [http://mediaserver/](http://mediaserver/). When DNS looks up that name, it will find that A record and know that "mediaserver" points to 192.168.0.100 for instance.

**EDIT: **do you have a DNS server on your network where you can add this record, unless of course someone puts out a probably easier method?

---

### Post by kr651129 on 2011-11-29
Thanks for the reply!

My server WAS running as a DNS server but I reinstalled the OS to put the RAID together.  It's installed just not configured.

---

### Post by kr651129 on 2011-11-29
Ok, so maybe you can tell me from my config what I'm doing wrong?

named.conf.local
```

zone "mediaserver" {
              type master;
              file "/etc/bind/db.mediaserver.com";
         };   

Reverse Zone File   

zone "0.168.192.in-addr.arpa" {
         type master;
         notify no;
         file "/etc/bind/db.192";
};

```

db.mediaserver.com
```

$TTL	604800
@	IN	SOA	ns.mediaserver.com.	root.mediaserver.com.	{
			1			; Serial
			604800			; Refresh
			86400			; Retry
			2419200			; Expire
			604800 )		; Negative Cache TTL
;

@	IN	NS	ns.mediaserver.com.	
@	IN	A	192.168.0.101
box	IN	A	192.168.0.101

```

db.192
```

$TTL	604800
@	IN	SOA	ns.mediaserver.com.	root.mediaserver.com.	{
			2			; Serial
			604800			; Refresh
			86400			; Retry
			2419200			; Expire
			604800 );		; Negative Cache TTL
;
@	IN	NS	ns.
10	IN	PTR	ns.mediaserver.com.	

```

---

### Post by Doug S on 2011-11-29
I think your forward and reverse lookups don't match, as one seems to be 192.168.0.101 and the other seems to be 192.168.0.10.
Rather then me re-typing everything (which I will do, if it comes to it), maybe look at these recent threads: [http://ubuntuforums.org/showthread.php?t=1884267](http://ubuntuforums.org/showthread.php?t=1884267) [http://ubuntuforums.org/showthread.php?t=1885824](http://ubuntuforums.org/showthread.php?t=1885824) 
Summary: Myself, I would drop the ns. from the SOA record in the forward stuff.

---

### Post by kr651129 on 2011-11-29
Thank you, DNS is such a simple concept but for some reason it's verry hard for me to wrap my head around configuring it.  I think it's because I don't understand all of the commands and how everything works.

Let me ask you this, in db.mediaserver.com...line two.  I have ns.mediaserve.com. if I droped the .com. and instead put ns.mediaserver. would this give me the [http://mediaserver/](http://mediaserver/) without needing my .com?

Secondly, I'm starting to understand a little more, however not fully.  I am moding a config I found online to match my needs so what does

```

box	IN	A	192.168.0.101

```

mean?  Could I drop it and just keep

```

@	IN	A	192.168.0.101

```

And then my last question is, do I need to change DNS settings in the router for my server box to pick up the DNS request and forward me to the right webpage on my box?

---

### Post by Doug S on 2011-11-29
> in db.mediaserver.com...line two. I have ns.mediaserve.com. if I droped the .com. and instead put ns.mediaserver. would this give me the [[COLOR=#000000]http://mediaserver/[/COLOR]]("http://mediaserver/") without needing my .com?
Yes, I think so. Also see posting #8 (and the reply that it worked) in one of the links I gave you earlier: [http://ubuntuforums.org/showpost.php?p=11478018&postcount=8](http://ubuntuforums.org/showpost.php?p=11478018&postcount=8) 
I would still drop the ns. from that line, and also notice carefully the A record line without the @ at the start.
 
The "box" A record is merely another mapping to the same IP address. You can have more than 1 and/or CNAME records, see posting #10 in the same above reference.
 
> do I need to change DNS settings in the router for my server box to pick up the DNS request and forward me to the right webpage on my box?Yes. (My main Ubuntu server box is also my router, so our systems are a little different) You would want your LAN computers to go to your local DNS first, yes. Your local DNS should have forwarders setup to go to the name server your ISP provides. On my DHCP server, I have added my DNS as the first one to check, the other two are as given by my ISP. Therefore computers on my LAN get the following:
```

C:\Users\Doug\C>ipconfig /all
...
Wireless LAN adapter Wireless Network Connection:
   Connection-specific DNS Suffix  . : smythies.com
   Description . . . . . . . . . . . : Dell Wireless 1505 Draft 802.11n WLAN Mini-Card
   Physical Address. . . . . . . . . : ............
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.111.100(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : November-12-2011 14:08:52
   Lease Expires . . . . . . . . . . : November-30-2011 03:30:13
   Default Gateway . . . . . . . . . : 192.168.111.1
   DHCP Server . . . . . . . . . . . : 192.168.111.1
   [COLOR=red]DNS Servers . . . . . . . . . . . : 192.168.111.1[/COLOR]
[COLOR=red]                                      75.154.133.68[/COLOR]
[COLOR=red]                                      75.154.133.100[/COLOR]

```
I did this with this line in dhcpd.conf:
```
 
option domain-name-servers 192.168.111.1, 75.154.133.68, 75.154.133.100;

```
If you have a hardware router, I tihnk you can also force the list of name servers.
I hope this helps.

---

### Post by kr651129 on 2011-11-29
Wow, thank you for all of the help, I'm slowly starting to *understand* rather than randomly plugging in my own network data.  Eventually I will want this box to be my router too but one thing at a time.  Right now I have a hardware router and this is to sever my intranet only so the devices connected to this router wirelesly do not have internet access because I want to limit all of the possible errors while I'm setting this up.

---

