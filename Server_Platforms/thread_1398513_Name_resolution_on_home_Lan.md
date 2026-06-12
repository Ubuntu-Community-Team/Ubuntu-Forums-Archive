---
title: "Name resolution on home Lan"
date: 2010-02-04
forum: Server Platforms
---

### Post by Demented ZA on 2010-02-04
I have the following set up:

I have an Ubuntu 9.10 server acting as a firewall/gateway/and dhcp server between local and internet.

I have some Windows, Mac and Linux pc's connected to said network.

I recently re-installed the server. Before re-installation I did not have any problems :-(

The problem i'm experiencing is that when I ping "pc1"(192.168.0.5) from another windows pc, it resolves to an ip address (e.g: 67.215.65.132) not inside my local network. 

I'm assuming the problem has something to do with dns, but I don't understand why it worked in 9.04 without configuration? Did something change with distributions?

---

### Post by doas777 on 2010-02-04
well it seems your client is getting a public dns server address. do you have a bind instance or other dns service on your server? do your clients know that it is there, and that they shoudl use it?

the easiest way if you have  a small number of pcs is to configure your hosts file, but it lacks scalability. a small bind zone that forwards to the public dns on NX, is more advanced but more reliable as the number of hosts increasses

---

### Post by terazen on 2010-02-04
Does your dhcp/firewall/gateway server find the right ip address when it looks up pc1?  Also, did you check "ipconfig /all" on your windows machines to make sure they pulled the same settings that they used to have?

---

### Post by Rich78 on 2010-02-04
Looks like you're pointing to OpenDNS

[http://www.ip-adress.com/whois/67.215.65.132](http://www.ip-adress.com/whois/67.215.65.132)

---

### Post by Iowan on 2010-02-04
Are you using **dnsmasq** for DHCP/DNS? Mine did that for awhile...

---

### Post by Demented ZA on 2010-02-04
Thanks 4 response guys!

Well I am running bind9, however its out the box and not configured. Yes, I am using OpenDNS for my nameservers. My DHCP server automatically issues OpenDNS namesevers to the DHCP clients. 

My server does not know what the address of PC1 is. 

I don't like editing the hosts file precicely because of scalability. I'm assuming my problem is that bind9 on my server is not configured? Weird thing is that it wasn't a problem before.

I'm just wondering if this is normal? Maybe I was supposed to always have set up dns, but it used to work with the default configs for my purpose. Now with then new release of Ubuntu, I have to set it up to get it to work?

If I have to set it up, I'll probably have to configure dhcp3 to update bind9 with hostnames for my domain?  I found some guides, but most of them old and not for debian. Also, dnsmasq I have tried once before, but I prefer bind9 + dhcpd3 for my own training.

---

### Post by terazen on 2010-02-04
Are the pc's pointed directly to opendns or are they pointed to your server which forwards to opendns?  If they point to your server for dns then having dhcp update bind should work.

---

### Post by lavinog on 2010-02-04
> **Demented ZA said:**
> 
I'm assuming the problem has something to do with dns, but I don't understand why it worked in 9.04 without configuration? Did something change with distributions?
You probably enabled file sharing at some point which enabled winbind (WINS)
WINS provides name resolution for networks that do not have a dns server and use dhcp.

avahi also provides automatic name resolution for local networks.  The catch is that you have to append .local to the end, and I don't know how windows computers work with this:
```
ping pc1.local
```

To install avahi on the server just install avahi-daemon:
```

sudo apt-get install avahi-daemon

```

---

### Post by noway2 on 2010-02-05
My thought was that you have lost the link between the DHCP and DNS.  You are using bind9 for your DNS.  What are you using for the DHCP?

Here is a link (below) that I found useful when setting up a DNS and linking it to the DHCP. Basically you create a special key file that will be used to authenticate between the two processes and then set the DNS and DHCP to mutually update.

Without a link between the two, DHCP will assign IP addresses, but there is no way for the DNS to know which device has which address.

[http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/](http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/)

---

### Post by Demented ZA on 2010-02-05
> **terazen said:**
> Are the pc's pointed directly to opendns or are they pointed to your server which forwards to opendns?  

DHCP assigns two dns server addresses to my clients. Primary dns is that of my firewall gateway system and secondary is that of one of the OpenDNS servers incase my own dns is not working. Is this correct?

> **terazen said:**
> If they point to your server for dns then having  dhcp update bind should work.


Thats what I thought, thanks :-)

---

### Post by Demented ZA on 2010-02-05
> **lavinog said:**
> You probably enabled file sharing at some point which enabled winbind (WINS)
WINS provides name resolution for networks that do not have a dns server and use dhcp.

avahi also provides automatic name resolution for local networks.  The catch is that you have to append .local to the end, and I don't know how windows computers work with this:
```
ping pc1.local
```To install avahi on the server just install avahi-daemon:
```

sudo apt-get install avahi-daemon

```


I think your spot on. Now that I think about it, only windows pc's were able to find each other via hostnames. mac and Linux I had to use IP's.

---

### Post by Demented ZA on 2010-02-05
> **noway2 said:**
> My thought was that you have lost the link between the DHCP and DNS.  You are using bind9 for your DNS.  What are you using for the DHCP?

I didn't lose the link between DHCP and DNS, It was never there to begin with as I never set it up before. To answer your question, I'm using bind9 for dns and dhcpd3 server for dhcp.

> **noway2 said:**
> Here is a link (below) that I found useful when setting up a DNS and linking it to the DHCP. Basically you create a special key file that will be used to authenticate between the two processes and then set the DNS and DHCP to mutually update.

Without a link between the two, DHCP will assign IP addresses, but there is no way for the DNS to know which device has which address.

[http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/](http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/)

Thank you kindly for the link. This is exactly my problem and what I was looking for. You see, the links I looked at for making DHCP and DNS talk were outdated and the problem came in setting up the keys. i also wasn't sure which were applicable to my situation.

I'll try the above and post the results back here.

---

### Post by doas777 on 2010-02-05
check out these if you want to set up your bind zone:
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
[http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml](http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml)
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

gl and hf

---

### Post by Demented ZA on 2010-02-05
Alright, I followed the guide and set up bind9 as well as made some changes to dhcpd3 for updates. 

I know that my dns is working properly. Through webmin, I can add a host e.g printserver.example.com with ip of 192.168.0.5. If I then ping that host from any of the other pc's (windows/mac/linux) it then resolves to 192.168.0.5 which is correct.

Only thing is newly connected pc's do not get added to dns records. How do I verify whether dhcpd3 server is updating bind9 and whether it succeeds or not?

I'm not sure where to check the logs etc.

Thanks in advance

---

### Post by lavinog on 2010-02-05
have you tried installing winbind?

---

### Post by Demented ZA on 2010-02-05
> **lavinog said:**
> have you tried installing winbind?

Uhm, no, i havn't.

 I don't see how that is going to solve my problem? My problem isn't windows-specific.

---

### Post by noway2 on 2010-02-05
If you followed the guide that I sent you, there will be a change to the logging.  Look in the directory /var/lib/bind.  You should see your zone file that you created, but also see two news ones that end in .jnl which are binary files.  If you look at the bind configuration files in this directory without the .jnl, you should see all of the assigned devices including the dynamic ones.  A couple of ways to know that the link is working:

1 - the fact that you are able to ping devices on the LAN by name
2 - the date time stamp the DNS configuration files in the /var/lib directory
3 - the 'extra' data that will appear in these configuration files

You can also look in the DHCP leases files, which is located in /var/lib/dhcp3.  The leases (dhcp.leases file) should list the device host name.

---

### Post by lavinog on 2010-02-05
> **Demented ZA said:**
> Uhm, no, i havn't.

 I don't see how that is going to solve my problem? My problem isn't windows-specific.

winbind isn't just for windows
it provides wins capabilities to linux systems.  It is usually installed with samba, but may not be installed on a server setup.
It works similar to avahi's name resolution, but works with windows computers on the network.

If you need to ping pc1 from a windows machine and a linux box, use winbind
If you just wish to interact with linux and macs, use avahi.

Linux boxes can utilize wins to resolve other linux boxes too.

---

### Post by Demented ZA on 2010-02-13
Ok, its been a while since I visited this thread (1 week), but thats because my server's motherboard decided to keel over (about a week ago). It was time for an upgrade anyways.... :p

So I decided to not just upgrade the motherboard, but I replaced the whole damned system. I couldn't do all this because I work during the day, so I waited untill the past Friday (yesterday). It took half a day, but it was worth it :D , I'll explain:

On a side note, I was running a Netgear DG834 (version 4) adsl router, that got a bit hot (due to our local climate and the load that gets placed on it). I've never had a router that didn't overheat :(. I decided to do something once and for all: I stripped the modem of its outside plastic, placed heatsinks on the broadcom chip as well as memory and any other component that got hot to touch. I then soldered a 12v molex to DC jack to draw power from the psu and mounted in between two Antec tricool 120mm fans inside the PC case. I also custom made backplates for the network and telephone plugs so that all looks neat and is conveniently modular. I will upload the project pics to my blog if anyone's interested.

My new system is running a 2.5GHz Core 2 Duo, 4GB 800MHz Kingston DDR2 Ram and is running off a single 160GB Seagate SATAII HDD. 2x 120mm Antec case fans, Upgraded CPU cooler and fan and 550watt Antec PSU. The system runs surprisingly quiet. 

My old system: P4 1.7 (Underclocked to 1.1GHz) with 384mb ram Running at 333MHz and a 4Gb flashdrive as storage. This PC only had 1 Fan on the PSU modded to run on 5v instead of 12v for a silent system. The PSU was mounted over the CPU.

R.I.P Old faithfull.

Back to the topic at hand, I also decided to start anew with the entire Ubuntu server system. I went through everything and set up my server as I'm used to. When it came to DNS, I was a lot wiser and it was a lot easier this time to set it up. I understand a lot more of it now, thanks to you guys.

I also learned where some of my problems with my previous server setup was:

Firstly, what I didn't know, is that there is a known Ubuntu problem with DNS not listening on port 953. The fix lies here: [http://beginlinux.com/blog/2009/06/repairing-ubuntu-904-dns/](http://beginlinux.com/blog/2009/06/repairing-ubuntu-904-dns/)

Second, I had some problems with bind not working correctly. Basically all the guides I have been following are crap and have typos with no real troubleshooting at the end. They also did not explain things very well. The solution:

For setting up bind9: [http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/](http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/)
[Credit goes to noway2 for the above link, THANKS!]

There are some changes that need to be made to the above guide to compensate for Apparmour or bind9 will not be able to update its zones or journals (.jnl files).

Third: For getting bind9 and DHCPD3 to work, [http://hubpages.com/hub/Creating-DNS-Server-with-Ubuntu-Linux-Primary-DNS-Server-with-Bind9](http://hubpages.com/hub/Creating-DNS-Server-with-Ubuntu-Linux-Primary-DNS-Server-with-Bind9)

Fourth: The reason I kept ketting wrong ip's for my hosts was due to the nameserver not working correctly, causing name queries to be sent to the secondary name server (OpenDNS).  Because I'm running adsl, my /etc/resolv.conf file gets updated by the pppd daemon, meaning that the nameservers there were incorect for my server. My server was doing dns queries to my isp's server instead of doing it to my lan's dns and having my lan dns server cache my isp or opendns's nameservers.

After correcting my /etc/resolv.conf I had to prevent changes, following this guide: [http://www.cyberciti.biz/faq/dhclient-etcresolvconf-hooks/](http://www.cyberciti.biz/faq/dhclient-etcresolvconf-hooks/)

My resolv.conf file looks like this:
```

domain example.co.za
search  example.co.za
nameserver 192.168.0.1

```
My Fith problem is that I was unsure of checking the logs for bind9 and dhcpd3-server.
Using grep to filter log files:

Usage:
 
grep -i (ignore case) SEARCH_VALUE /path/to/log

example:

```


$grep -i bind /var/logs/kern.log


```Above filters /var/log/kern.log for entries containing the word bind

Logs to search:
/var/log/kern.log
/var/log/daemon.log


At current moment, my dns is working like it should, I have entered the address of my printserver under my example.co.za.db.

Ping printserver returns:

Pinging printserver.example.co.za [192.168.0.4] with 32 bytes of data:
Reply from 192.168.0.4: bytes=32 time=67ms TTL=128
Reply from 192.168.0.4: bytes=32 time=61ms TTL=128


My problem remains however, that I can not ping dynamic hosts and have them resolve to host.example.co.za.

Upon further inspection, there are no .jnl files with my zone files. I looked under /etc/bind/zones as well as /var/lib/bind/

@noway2, According to the link you posted: [http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/](http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/)

they state that one needs to copy the zones from /etc/bind/zones to /var/lib/bind.

I know Apparmor prevents bind from writing to /etc/bind/*

I updated my /etc/bind/named.local.conf and changed the lines that pointed to the zone files at /etc/bind/zones to /var/lib/bind/.

Is that correct??

Also, there are no .jnl files being created. 

grep -i jnl /var/log/daemon.log returns :

```

Feb 13 05:25:18 box named[3206]: /etc/bind/zones/example.co.za.db.jn
l: create: permission denied

```This is apparmor's doing. I tried changing the profile to allow writing, no difference. I purged apparmor, still, no joy.

Is it a permissions problem? How do I check?

I hope the above helps others. Thanks!

---

