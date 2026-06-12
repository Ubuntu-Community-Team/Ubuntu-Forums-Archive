---
title: "Bind9"
date: 2012-08-04
forum: Server Platforms
---

### Post by gfwwzfxixg on 2012-08-04
Hi guys,

Please clarify something for me. I'm at a brick wall, the outcome is to amend my home server using bind to host the dns obviously however to point say newwebsite.local to its directory but the other machines connected to the network do not have to edit the host file.

I keep hitting searches pointing me to dyndns.org i think its called, but, personally feel this is not what I'm looking for as I'm not wanting to go out of the network (correct me if I'm wrong)

So in a nutshell,

CPU ------------------------- v
CPU ------------------------- v
SERVER -------------------- > ROUTER (Server hosts domain names, website locally, etc)

Any help is greatly appreciated, my head is now battered!

---

### Post by darkod on 2012-08-04
I think this is a fast and short tutorial. Of course, you will need to use the static IP of the server for the A records, and you can ignore the part for the mail MX records.
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

---

### Post by gfwwzfxixg on 2012-08-04
hey thanks will check this out :)

---

### Post by gfwwzfxixg on 2012-08-04
Ok done all that, 2 questions:

1. I can't remember where to add the data for the /etc/resolv.conf file, I'm on 12.04 (Sorry if I did'nt advise of this previously)

2. A records is that in the /etc/networking/interfaces file? as in dns 8.8.8.8 8.8.4.4?, the current status of my interfaces file is as follows:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The host-only network interface
auto eth1
iface eth1 inet static
address 192.168.56.101
netmask 255.255.255.0
network 192.168.56.0
broadcast 192.168.56.255
```

bind config:

```

; BIND data file for intranet.local
;
$TTL 14400
@ IN SOA ns1.intranet.local. indo.intranet.local. (
201006601 ; Serial
7200 ; Refresh
120 ; Retry
2419200 ; Expire
604800) ; Default TTL
;
intranet.local. IN NS ns1.intranet.local.
intranet.local. IN NS ns2.intranet.local.

intranet.local. IN MX 10 mail.intranet.local.
intranet.local. IN A 192.168.56.101

ns1 IN A 192.168.56.101
ns2 IN A 192.168.56.101
www IN CNAME intranet.local.
mail IN A 192.168.56.101
ftp IN CNAME intranet.local.
intranet.local. IN TXT "v=spf1 ip4:192.168.56.101 a mx ~all"
mail IN TXT "v=spf1 a -all"

```

eth1 is primary to local static in Virtual hosts, testing before configuring the main server (currently being nuked as flattening the hdd!)

I'm looking to do the MX records anyway, email will be needed for sites I create in Drupal, that's not a worry, again if I've missed anything please do say so.

---

### Post by darkod on 2012-08-04
If we are talking about setting dns servers in ubuntu server 12.04 LTS, you don't do it in /etc/resolv.conf any more. In /etc/network/interfaces, below the settings for the address, netmask and gateway, you add:
```
dns-nameservers x.x.x.x y.y.y.y
```That is a permanent setting, so your server will use those dns servers to resolve names.

On the other hand, the machines on your local network will have to have their dns set as the server private IP, which seems to be 192.168.56.101. This makes the computers use your newly created dns server otherwise doing the bind config doesn't help much.

As far as the bind config is concerned, I'm not an expert, I just have that link bookmarked because it looked like an easy setup. I doubt I will be able to notice any errors.

Give it a shot and see if it works as expected for you. If it doesn't ask for help.

EDIT PS: If you were referring to the part of the tutorial saying to add your domain to /etc/resolv.conf I think this is also done in /etc/network/interfaces now with:
```
dns-search intranet.local
```
That should do it.

---

### Post by gfwwzfxixg on 2012-08-04
Ok,

So lets strip bind out of the equation. So what you're saying is no matter what setup the ip on all computers have to be static?

so let's say for instance we have the router, this brings in the internet. The server is Ethernet connected into this. There is another PC and Laptop wirelessley connected to that router.

I'm designing a website, say, website.local, email for that website [email]root@website.local[/email]. The idea, the server hosts the test website (locally only) I can connect to the router in the normal wireless fasion, in the address bar I enter website.local, there is my project hosted on the server, connected to the router. I can send test email contact form scripts to [email]root@website.local[/email] again hosted on the server, connected to the router.

I'm coming from a xampp environment (where apache is the virtual host provider), so used to that setup, however, changing to a hardware server its quicker, more stable and efficient as you can do other things obviously meditomb etc.

So what do i do next? and thank you for your current replies

---

### Post by darkod on 2012-08-04
No, you don't need static IPs on the workstation, just on the server so it never changes.

In this case, since your router dhcp is giving out the IPs, go into it's GUI in the dhcp settings, and there should be DNS fields. There you can select the dns servers the router will send to the workstations.

Make DNS1 the IP of your server, so it's always the first option.
Make DNS2 the IP of your router or a public IP of your ISP dns server.

That way, on one of the workstations when you type website.local it will ask DNS1 where is it. DNS1 is your own server with the bind config and will reply with the local IP. So, the website should open, and you don't even go out of your network.

If DNS1 (your bind) doesn't work correctly, it will ask DNS2 where is that address and that wouldn't work at all since the outside world doesn't know anything about website.local.

---

### Post by gfwwzfxixg on 2012-08-04
That makes a great deal of sense, I'll give it a whirl :D

---

### Post by Cheesemill on 2012-08-04
Instead of using BIND you could use dnsmaq. It's much easier to set up and will act as a DHCP server as well if you want it to.

[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)

---

### Post by darkod on 2012-08-04
> **Cheesemill said:**
> Instead of using BIND you could use dnsmaq. It's much easier to set up and will act as a DHCP server as well if you want it to.

[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)

But isn't that only dns forwarder? Can you set up an A record with your server ip for example?

That tutorial doesn't say anything about that. Otherwise, I have used dnsmasq as a forwarder only and it works great, much easier than setting up bind if that's the only thing you want.

---

### Post by Cheesemill on 2012-08-04
> **darkod said:**
> But isn't that only dns forwarder? Can you set up an A record with your server ip for example?

That tutorial doesn't say anything about that. Otherwise, I have used  dnsmasq as a forwarder only and it works great, much easier than setting  up bind if that's the only thing you want.Yes you can, just add an entry to the hosts file on the server running dnsmasq. The hosts file gets queried first before any external DNS servers.
Adding a new host to the hosts file is a lot easier and quicker than configuring BIND.

The tutorial that I linked to mentions this in the line directly above 'Choosing Your Interfaces'.

I've completely replaced BIND with dnsmasq on most of the networks that I administrate, I only keep BIND when I need MX records which dnsmasq can't handle.

---

### Post by darkod on 2012-08-04
> **Cheesemill said:**
> Yes you can, just add an entry to the hosts file on the server running dnsmasq. The hosts file gets queried first before any external DNS servers.
Adding a new host to the hosts file is a lot easier and quicker than configuring BIND.

The tutorial that I linked to mentions this in the line directly above 'Choosing Your Interfaces'.

I've completely replaced BIND with dnsmasq on most of the networks that I administrate, I only keep BIND when I need MX records which dnsmasq can't handle.

OK, thanks. Good to know. I agree the setup is much easier.

---

### Post by gfwwzfxixg on 2012-08-05
Much appreciated, thank you.

On DNSMasq am I still able to setup the test email as it appears for your discussion that MX records are not supported?

Would I also need to setup the router to look for IP information on its DNS setting with DNSMasq?

---

### Post by darkod on 2012-08-05
I am not sure about dnsmasq and MX. On one page I saw it says it can handle MX but I have never seen instructions how to do them.

Since you already have the bind setup from that other tutorial, you can give that a go first and think about dnsmasq only if it fails for example.

As for the router, regardless what option you use for the dns config (bind or dnsmasq), you ALWAYS need to tell your machines on the network to use your server as primary dns. Because if they use an outside dns server as primary, that server knows nothing about website.local as we already mentioned.
So, your machines using your server as primary dns is a MUST regardless how you actually do the dns config on that server.

Now, you can do that in few different ways. The easiest is to enter the router config in the options handling the dhcp server and tell it that the primary dns is the IP of your server. That info will be sent to all machines (clients) on your network.

Other option is to have manual static configuration on all machines (you already said you don't want to set up manually on all of them) in which case you enter the primary dns server manually in the network settings.

---

### Post by gfwwzfxixg on 2012-08-05
Brill,

I will report back later today, to confuse matters look like due to my setup a bridged client will be involved with DD-WRT, so need to get that completed first, edit the DNS and take it from there.

For the record (and when "website.local" :P) is ready I should be documenting this in great detail as it's quite confusing first time around.

---

### Post by gfwwzfxixg on 2012-08-06
OK, here's where I am so far, the bind9 tutorial finished but not quite going well (I presume). I've undertook a overhaul and moved the server downstairs, ethernet connection into the main router Sky F@st, with DHCP unselected and Address Reservation set to 192.168.0.4 which is the main IP for the server.

I'm running

```
dig intranet.local
```

and

```
dig @localhost intranet.local
```

The output "status: NXDOMAIN" being the culprit! not good

```
root@elite:~# dig intranet.local

; <<>> DiG 9.8.1-P1 <<>> intranet.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 23015
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;intranet.local.                        IN      A

;; AUTHORITY SECTION:
.                       10800   IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2012080601 1800 900 604800 86400

;; Query time: 51 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Mon Aug  6 19:54:44 2012
;; MSG SIZE  rcvd: 107

root@elite:~# dig @localhost intranet.local

; <<>> DiG 9.8.1-P1 <<>> @localhost intranet.local
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 42457
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;intranet.local.                        IN      A

;; AUTHORITY SECTION:
.                       10800   IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2012080601 1800 900 604800 86400

;; Query time: 124 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Aug  6 19:57:48 2012
;; MSG SIZE  rcvd: 107
```

The current setup is:

/etc/network/interfaces (I realise its still DHCP as STATIC will not work at all)

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# DHCP - The primary network interface
auto eth0
iface eth0 inet dhcp

# Bind DNS
search intranet.local
```

/etc/bind/zones/rev.3.2.1.in-addr.arpa

```
@ IN SOA intranet.local. indo.intranet.local. (
2010081401;
28800;
604800;
604800;
86400 );

IN NS ns1.intranet.local.
4 IN PTR intranet.local.
```

/etc/bind/named.conf.local

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "home.intranet.local" {
type master;
file "/etc/bind/zones/intranet.local.db";
};

zone "3.2.1.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.3.2.1.in-addr.arpa";
};


```

/etc/bind/zones/intranet.local.db

```

; BIND data file for intranet.local
;
$TTL 14400
@ IN SOA ns1.intranet.local. indo.intranet.local. (
201006601 ; Serial
7200 ; Refresh
120 ; Retry
2419200 ; Expire
604800) ; Default TTL
;
intranet.local. IN NS ns1.intranet.local.
intranet.local. IN NS ns2.intranet.local.

intranet.local. IN MX 10 mail.intranet.local.
intranet.local. IN A 192.168.0.4

ns1 IN A 192.168.0.4
ns2 IN A 192.168.0.4
www IN CNAME intranet.local.
mail IN A 192.168.0.4
ftp IN CNAME intranet.local.
intranet.local. IN TXT "v=spf1 ip4:192.168.0.4 a mx ~all"
mail IN TXT "v=spf1 a -all"

```

/etc/bind/zones/intranet.local.db

```

; BIND data file for intranet.local
;
$TTL 14400
@ IN SOA ns1.intranet.local. indo.intranet.local. (
201006601 ; Serial
7200 ; Refresh
120 ; Retry
2419200 ; Expire
604800) ; Default TTL
;
intranet.local. IN NS ns1.intranet.local.
intranet.local. IN NS ns2.intranet.local.

intranet.local. IN MX 10 mail.intranet.local.
intranet.local. IN A 192.168.0.4

ns1 IN A 192.168.0.4
ns2 IN A 192.168.0.4
www IN CNAME intranet.local.
mail IN A 192.168.0.4
ftp IN CNAME intranet.local.
intranet.local. IN TXT "v=spf1 ip4:192.168.0.4 a mx ~all"
mail IN TXT "v=spf1 a -all"

```

Now I'm lost haha!

---

### Post by darkod on 2012-08-07
And the most important question we discussed so far: What is the dns issued by the dhcp?

If it's a public dns, that might be a reason not recognizing your local domain.

On another note, what do you mean it doesn't work with static? Try something like:
```
auto eth0
iface eth0 inet static
   address 192.168.0.4
   netmask 255.255.255.0
   gateway 192.168.0.1 (assuming your router is 192.168.0.1)
   dns-nameservers 192.168.0.4 x.x.x.x (put one public dns too for the public domains)
   dns-search intranet.local
```Restart networking (or the whole server):
sudo /etc/init.d/networking restart

---

### Post by gfwwzfxixg on 2012-08-14
Sorry for the delay!

It may appear to be my sagecom f@st router as provided by sky, It's so locked down you can't even disable its DNS server, and, they will plummet me if I change it to a custom (as so I'm told).

Any way around this? - I've meant to admit that I'm pretty new to DHCP & DNS, probably knew that anyway! ha.

Thanks

---

