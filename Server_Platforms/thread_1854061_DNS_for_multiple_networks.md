---
title: "DNS for multiple networks"
date: 2011-10-03
forum: Server Platforms
---

### Post by The Sorrow on 2011-10-03
I have 3 network segments in my house (LAN, DMZ and WAP) with one 11.04 box running BIND9. Essentially i want to be able to go to my LAMP server with just a host name or FQDN. So lets get started with the facts.

DNS works in LAN. nslookup to thesorrow.cobra.unit replies fine. 

Host theboss.cobra.unit can contact theboss.cobra.unit over port 53

My networks are as follows:
LAN         10.10.1.0/24
LAN Gateway 10.10.1.254 

DMZ         10.10.2.0/24
DMZ Gateway 10.10.2.254

WAP         10.10.3.0/24
WAP Gateway 10.10.3.254

Map for assistance in visualizing my setup

[img]http://forums.hak5.org/index.php?app=core&module=attach&section=attach&attach_rel_module=post&attach_id=672[/img]

Here are my bind config files:

/etc/bind/zones/
|-cobra.unit.db
```
// replace example.com with your domain name. do not forget the . after the dom$
// Also, replace ns1 with the name of your DNS server
example.com. IN SOA ns1.example.com. admin.example.com. (
// Do not modify the following lines!
2007031001
28800
3600
604800
38400
)

// Replace the following line as necessary:
// ns1 = DNS Server name
// mail = mail server name
// example.com = domain name
cobra.unit = cobra.unit
cobra.unit. IN NS thesorrow.cobra.unit.
cobra.unit. IN MX 10 mail.cobra.unit.

// Replace the IP address with the right IP addresses.
thefury IN A 10.10.1.200
theend IN A 10.10.1.254
thesorrow IN A 10.10.1.250
theboss IN A 10.10.2.100
```


|-rev.1.10.10.in-addr.arpa
```
//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS serve$
@ IN SOA thesorrow.cobra.unit. admin.cobra.unit. (
2007031001;
28800;
604800;
604800;
86400
)

IN NS thesorrow.cobra.unit.
1 IN PTR cobra.unit
```

My firewall rules are as follows:

```
LAN
ALLOW access to ALL networks

DMZ
ALLOW access to LAN over port 53 for DNS
ALLOW access to ALL networks EXCEPT LAN
BLOCK access to LAN

WAP
ALLOW access to ALL networks EXCEPT LAN
BLOCK access to LAN
```

I think that covers all my bases...

---

### Post by collisionystm on 2011-10-04
Your reverse config is wrong. You need to add all host names you configure.

---

### Post by collisionystm on 2011-10-04
```
administrator@trash:/etc/bind$ cat db.Trash
$TTL 3D
@       IN      SOA     apollo.Trash.   hostmaster (
                        2011100311      ;serial number
                        8H              ;refresh
                        2H              ;retry
                        4W              ;expiration
                        1D )            ;
;
@               NS      apollo
altieaston              A       172.16.65.221
apollo          A       172.16.64.15
athena          A       172.16.64.30
backup          A       172.16.64.10
bw              A       172.16.128.1
cl              A       172.16.32.1
ea              A       172.16.64.254
hrserver                A       172.16.65.119
nds             A       172.16.64.4
pa              A       192.168.7.1
qwserver                A       172.16.66.137
ro              A       192.168.16.1
share           A       172.16.64.17
timeclock               A       172.16.64.22
va              A       172.16.192.1
waste           A       172.16.64.2
webmeet         A       172.16.64.29
wordpress               A       172.16.64.40
administrator@trash:/etc/bind$
```

I have a reverse db file for each subnet, but here is the one for my 172.16.64.0

```
administrator@trash:/etc/bind$ cat db.64.16.172
$TTL 3D
$ORIGIN 64.16.172.in-addr.arpa.
@       IN      SOA     ns.Trash.       hostmaster.Trash. (
                        2011100311      ;serial number
                        8H              ;refresh
                        2H              ;retry
                        4W              ;expiration
                        1D )            ;
;
                NS      ns.Trash.       ;nameserver
;
15      PTR     apollo.Trash.
30      PTR     athena.Trash.
10      PTR     backup.Trash.
254     PTR     ea.Trash.
4       PTR     nds.Trash.
17      PTR     share.Trash.
22      PTR     timeclock.Trash.
2       PTR     waste.Trash.
29      PTR     webmeet.Trash.
40      PTR     wordpress.Trash.
```

---

### Post by The Sorrow on 2011-10-04
So all i have to do is make sure i have my reverse lookup .dbs configured right and that my hosts can traverse the firewall to do DNS queries?

---

### Post by collisionystm on 2011-10-04
You got it.

---

### Post by The Sorrow on 2011-10-04
Well ill go fourth and tinker as soon as i can. Another question for the meantime that ive wondered is can this be my primary DNS server for all my local PCs to do WAN host DNS (I guess my question in short is can i use a local DNS for all my DNS needs). If so how can i and how dies it work?

---

### Post by collisionystm on 2011-10-04
Yes it can be a DNS for all of your PC's. All you need to do is edit your DHCP to hand out the DNS address of your server. You obviously now know how to add host records. As long as you can ping google.com from your server you will be good to go.

If it is a windows network, you will want to enable WINS. You do by installing samba and editing your smb.conf

In your DHCP change your WINS to point to your server. Windows likes to use netbios. This provides it.

---

### Post by The Sorrow on 2011-10-04
So your setup will resolve WAN addresses like google.com and yahoo.com?

And here is the setup i have formulated thus far

/etc/bind/cobra.unit.db
```
$TTL 3D
@       IN      SOA     thesorrow.cobra.unit.   admin (
                        2011100311              ;serial number
                        8H                      ;refresh
                        2H                      ;retry
                        4W                      ;expiration
                        1D )                    ;
;
@               NS      thesorrow
thepain         A       10.10.1.251
thesorrow       A       10.10.1.250
thefury         A       10.10.1.200
theboss         A       10.10.2.100
theend          A       10.10.1.254
theend          A       10.10.2.254
theend          A       10.10.3.254
```


rev.1.10.10.in-addr.arpa
```
$TTL 3D
$ORIGIN 1.10.10.in-addr.arpa.
@       IN      SOA     thesorrow.cobra.unit.       admin.cobra.unit. (
                        2011100311      ;serial number
                        8H              ;refresh
                        2H              ;retry
                        4W              ;expiration
                        1D )            ;
;
                NS      thesorrow.cobra.unit.       ;thesorrow
;
100      PTR     thefury.cobra.unit.
251      PTR     thepain.cobra.unit.
254      PTR     theend.cobra.unit.
250      PTR     thesorrow.cobra.unit

```

rev.2.10.10.in-addr.arpa
```
$TTL 3D
$ORIGIN 1.10.10.in-addr.arpa.
@       IN      SOA     thesorrow.cobra.unit.       admin.cobra.unit. (
                        2011100311      ;serial number
                        8H              ;refresh
                        2H              ;retry
                        4W              ;expiration
                        1D )            ;
;
                NS      thesorrow.cobra.unit.       ;thesorrow
;
100      PTR     theboss.cobra.unit
```

---

### Post by collisionystm on 2011-10-05
So can you successfully ping your local hostnames?

And yes, you will be able to resolve and ping google.com etc...

Look at /etc/bind/db.root

That is the file that holds the IP's of all the official name servers you are reaching out to when you resolve entries that cannot be found in your server.

---

### Post by The Sorrow on 2011-10-05
this far i can ping every hostname in the LAN network. However, I cannot ping to the DMZ network via hostname.

---

### Post by The Sorrow on 2011-10-10
Still no guesses? Like i said, LAN DNS is fantastic but DMZ/WAP cannot look at 10.10.1.250 for DNS...

---

### Post by Doug S on 2011-10-10
Is it just a typo that "rev.2.10.10.in-addr.arpa" says "$ORIGIN 1.10.10.in-addr.arpa."?
Shouldn't it say "$ORIGIN 2.10.10.in-addr.arpa."?
Also, from post #1 "Map for assistance in visualizing my setup": the link doesn't work. I was thinking about routing, and the map would help.

---

### Post by The Sorrow on 2011-10-11
> **Doug S said:**
> Is it just a typo that "rev.2.10.10.in-addr.arpa" says "$ORIGIN 1.10.10.in-addr.arpa."?
Shouldn't it say "$ORIGIN 2.10.10.in-addr.arpa."?
Also, from post #1 "Map for assistance in visualizing my setup": the link doesn't work. I was thinking about routing, and the map would help.

[ATTACH]204011[/ATTACH]

Here ya go. As far as i know routing shouldn't be an issue... that typo may be the issue though...

---

### Post by Doug S on 2011-10-11
We'll wait to hear about any changes to the issue with the typo fixed.
> LAN DNS is fantastic but DMZ/WAP cannot look at 10.10.1.250 for DNS...
Based on your firewall rules (post #1), yes, I would expect WAP to not be able to use 10.10.1.250 for DNS.
Are you able to look into the iptables details of what those firewall rules translate into? [Edit: Since I wrote the post, I did some reading about pfsense and I now realize that question doesn't make sense, as iptables is not involved] For a quick test I would suggest to change the DMZ rules to ALLOW the LAN. If you are worried about it, maybe just unplug the Cox Modem cable during the test.
By the way, I am pretty sure in post #1 here:> Host theboss.cobra.unit can contact theboss.cobra.unit over port 53You meant to say:> Host theboss.cobra.unit can contact TheSorrow.cobra.unit over port 53

---

### Post by The Sorrow on 2011-10-12
We'll wait to hear about any changes to the issue with the typo fixed.
> 
Based on your firewall rules (post #1), yes, I would expect WAP to not be able to use 10.10.1.250 for DNS.

Ive recently added an allow rule for DNS to point to 10.10.1.250 from WAP.

> Are you able to look into the iptables details of what those firewall rules translate into? [Edit: Since I wrote the post, I did some reading about pfsense and I now realize that question doesn't make sense, as iptables is not involved] For a quick test I would suggest to change the DMZ rules to ALLOW the LAN. If you are worried about it, maybe just unplug the Cox Modem cable during the test.

not terribly worried. just gives me something to do if someone decides to try anything ;)


> You meant to say: Host theboss.cobra.unit can contact TheSorrow.cobra.unit over port 53 

Aye, you found a fluke in my writings. your correction is what i mean to say.

---

