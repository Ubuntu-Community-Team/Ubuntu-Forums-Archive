---
title: "Configuring Bind9 problems"
date: 2011-10-30
forum: Server Platforms
---

### Post by BEaSTFX on 2011-10-30
In few words i want to set reverse dns for my existing domain from godaddy and use it as host on irc network. I followed [this]("http://www.youtube.com/watch?v=OUv03JV5SLc&feature=channel_video_title") tutorial to set the Bind9 server.

The way my network is set is this:
Internet comes to my router with the real static ip and then it comes to my linux machine.I'm not that familiar with setting dns servers so i have few questions and problems. What DNS should i set to the domain on godaddy (they are like ns1.xXX.XX) and i can't set it to my ip address.Second when I nslookup something i got this error:

```
atlantius@Lemuria:~$ nslookup lemuria
Server:		199.207.13.100
Address:	199.207.13.100#53

** server can't find lemuria: NXDOMAIN

```


This is my Bind9 config:
named.conf.local
```
#FORWARD LOOKUP ZONE - Holds A records, maps hostnames to IP's
zone "pozitivensvqt.com"
{
	type master;
	file "/etc/bind/zones/pozitivensvqt.com.db";
};




#REVERSE LOOKUP ZONE - Holds TRP records, maps IP's to hostnames
zone "0.207.199.in-addr.arpa"
{
	type master;
	file "rev.0.207.199.in-addr.arpa";
};

```

named.conf.options

```
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow multiple
	// ports to talk.  See http://www.kb.cert.org/vuls/id/800113

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	 forwarders {
	 	199.207.13.1;
		91.92.178.193;
		85.187.216.3;
		8.8.8.8;
		8.8.4.4;
	 };

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

```


pozitivensvqt.com.db

```
$TTL 3D
@	IN SOA Lemuria.pozitivensvqt.com.	admin.pozitivensvqt.com. {
2007031001;
28800;
3600;
604800;
38400
};

pozitivensvqt.com.	IN	NS	Lemuria.pozitivensvqt.com.
Lemuria			IN	A	199.207.13.100
www			IN	CNAME	Lemuria

```

rev.0.207.199.in-addr.arpa

```
$TTL 3D
@	IN	SOA	Lemuria.pozitivensvqt.com.	admin.pozitivensvqt.com. {
2007031001;
28800;
604800;
604800;
86400
};
	IN	NS	Lemuria.pozitivensvqt.com.
100	IN	PTR	Lemuria.pozitivensvqt.com.
1	IN	PTR	gw.pozitivensvqt.com.

```

If you can tell me what i did wrong with the bind9 and how to set it up right to use my real domain as host in irc it would be great.

Regards

---

### Post by Jonathan L on 2011-10-30
Dear Beast

You have three problems: 1) getting your bind server to work, 2) delegation for the forwards, 3) delegation for the reverses.

But first: are you really quite sure you need to run a nameserver?  if all you want is for your server to be visible, you put the appropriate information (through the web page) ino Go Daddy's servers.  (This will only do the forwards however, ie getting [www.pozitivensvqt.com]("http://www.pozitivensvqt.com") -> 199.207.13.100), but really that's almost certainly all you need.

It's most unusual to need to reun your own DNS, and it is frankly quite a lot of work.  If you're doing it to learn, then of course that's a good thing.  But if you want to run a server for games or web or whatever, it's unecessary.



_**Getting BIND working**_

The way you debug this is by checking /var/log/syslog every time you reload the server.

Your pozitivensvqt.com.db file has a mistake: you are using curly brackets where you should use normal brackets.  Also, you have a very strange SOA serial number, which would normally be today's date followed by a 2-digit version number.  Lastly, in the body, use either @ substitution and relative names, or absolute names which end with a dot.   You also are in a complex situation where you are wanting to put you only, single, name server inside its own domain: this is unwise, and still requires glue records at Go Daddy.

And don't forget to test
```
dig @localhost Lemuria.pozitivensvqt.com.
```_**Forwards**_

To me it looks like you've not got the delegation correct at Go Daddy.

The chain of delegation works correctly down to here:
```
$ dig @a.gtld-servers.net. pozitivensvqt.com. ns
...
pozitivensvqt.com.    172800    IN    NS    ns73.superhosting.bg.
pozitivensvqt.com.    172800    IN    NS    ns74.superhosting.bg.
...
```But 
```
$ dig @ns73.superhosting.bg. pozitivensvqt.com. ns

; <<>> DiG 9.7.0-P1 <<>> @ns73.superhosting.bg. pozitivensvqt.com. ns
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: [COLOR=Red]REFUSED[/COLOR], id: 42010
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
...

```First get your bind working, as above, then get it delegated at Go Daddy.  But I just want to say: it's almost always easier just to use their servers in the first place.

_**Reverse**_

You need the full pathname for the file in named.conf.local; and your address is 199.207.13.100 but you defined 199.207.0.100.  Once you have it working, you need to speak with your ISP about the reverse mapping.  In real life you almost always only need this for sending mail.

_**Files**_

Files named.conf.local: note changed filenames

```
zone "pozitivensvqt.com"
{
    type master;
    file "/etc/bind/pozitivensvqt.com.db";
};

zone "13.207.199.in-addr.arpa"
{
    type master;
    file "/etc/bind/rev.13.207.199.in-addr.arpa";

};

```Following is pozitivensvqt.com.db, not round brackets, serial, and relative references

```
$TTL 3D
@    IN SOA Lemuria.pozitivensvqt.com.    admin.pozitivensvqt.com.[COLOR=Red] ([/COLOR]
    [COLOR=Red]2011103002[/COLOR];
    28800;
    3600;
    604800;
    38400
[COLOR=Red])[/COLOR];

@        IN    NS       Lemuria
Lemuria  IN    A        199.207.13.100
www      IN    CNAME    Lemuria
```This is  rev.13.207.199.in-addr.arpa; not round brackets and serial number

```
$TTL 3D
@    IN    SOA    Lemuria.pozitivensvqt.com.    admin.pozitivensvqt.com.[COLOR=Red] ([/COLOR]
[COLOR=Red]2011103001[/COLOR];
28800;
604800;
604800;
86400
[COLOR=Red])[/COLOR];
@    IN    NS     Lemuria.pozitivensvqt.com.
100  IN    PTR    Lemuria.pozitivensvqt.com.
1    IN    PTR    gw.pozitivensvqt.com.

```Kind regards, hope that's helpful.

Jonathan.

---

### Post by elico on 2011-10-30
i found it really nice and easy to manage bind using webmin.
so you can install webmin just for that and turn it on and off.

---

### Post by BEaSTFX on 2011-10-30
First of all thank you for the great reply, Jonathan L!
I know it is easier to use godaddys dns server for my web server but I really wanted to create and manager my own. I wanted to create reverse DNS to use my domain name as virtual host in the IRC networks and etc. Primary it is really interesting for me :)

**1. I changed the delegation**

```
$ dig @a.gtld-servers.net. pozitivensvqt.com. ns 
;; AUTHORITY SECTION:
pozitivensvqt.com.	172800	IN	NS	lemuria.pozitivensvqt.com.
pozitivensvqt.com.	172800	IN	NS	admin.pozitivensvqt.com.

```

```
$ dig @lemuria.pozitivensvqt.com. pozitivensvqt.com.

; <<>> DiG 9.7.3 <<>> @lemuria.pozitivensvqt.com. pozitivensvqt.com.
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 46125
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;pozitivensvqt.com.		IN	A

;; AUTHORITY SECTION:
pozitivensvqt.com.	38400	IN	SOA	Lemuria.pozitivensvqt.com. admin.pozitivensvqt.com. 2011103002 28800 3600 604800 38400

;; Query time: 1 msec
;; SERVER: 199.207.13.100#53(199.207.13.100)
;; WHEN: Sun Oct 30 16:27:42 2011
;; MSG SIZE  rcvd: 85

```

**2. Then I tested the Bind:**

```
$ dig @localhost Lemuria.pozitivensvqt.com.

; <<>> DiG 9.7.3 <<>> @localhost Lemuria.pozitivensvqt.com.
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29797
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;Lemuria.pozitivensvqt.com.	IN	A

;; ANSWER SECTION:
Lemuria.pozitivensvqt.com. 259200 IN	A	199.207.13.100

;; AUTHORITY SECTION:
pozitivensvqt.com.	259200	IN	NS	Lemuria.pozitivensvqt.com.

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Oct 30 16:32:45 2011
;; MSG SIZE  rcvd: 73

```

It seems to work okay, except in IRC:

```
* *** Looking up your hostname...
* *** Checking Ident
* *** Couldn't look up your hostname
* *** No Ident response
```

As you see I am not that familiar with DNS server so forgive me for asking so much questions, but what exactly do I need to contact my ISP for, and what should I ask them?

Regards

---

### Post by SeijiSensei on 2011-10-30
You have no control over reverse-DNS resolution for public IP addresses provided by an ISP.  The ISP is responsible for that.  If you need reverse DNS, contact the ISP.

---

### Post by BEaSTFX on 2011-10-30
I don't understand one thing, do they give me control to set up the reverse dns or do i have to give them ip and domain and they set it up?

---

### Post by SeijiSensei on 2011-10-30
It varies, but for a single IP address, usually the latter.  However if you're a residential customer, the chances are good they won't do this for you.  Most of the time this is a service provided to people with business accounts.

If you were provided with an IP subnet from your ISP, it's possible the ISP will enable RFC 2317 "[delegation]("http://www.ietf.org/rfc/rfc2317.txt")" for the subnet. Delegation lets the subscriber manage the reverse domain for the subnet. Again this is usually a service for business subscribers.

---

### Post by Jonathan L on 2011-10-30
>  Primary it is really interesting for me :)Perfectly good reason!

**_Delegation_**

Your delegation looks good: I see this:

```
dig @a.gtld-servers.net. pozitivensvqt.com. ns
...
;; AUTHORITY SECTION:
pozitivensvqt.com.    172800    IN    NS    lemuria.pozitivensvqt.com.
pozitivensvqt.com.    172800    IN    NS    admin.pozitivensvqt.com.
...
;; ADDITIONAL SECTION:
lemuria.pozitivensvqt.com. 172800 IN    A    91.92.178.202
lemuria.pozitivensvqt.com. 172800 IN    A    199.207.13.100
admin.pozitivensvqt.com. 172800    IN    A    91.92.178.202
admin.pozitivensvqt.com. 172800    IN    A    199.207.13.100


```I see you have the glue records (the A records) there, which are required because your name server is inside the domain it serves.  But seems  you've put the same two addresses for both admin and lemuria, which looks a  little strange.  But it shouldn't stop things working.

And I see your local dig looks good:

```
$ dig @localhost Lemuria.pozitivensvqt.com.
...
Lemuria.pozitivensvqt.com. 259200 IN    A    199.207.13.100
...
```[B][U]Problem Accessing

[/U][/B]Your bind works correctly from your local machine; but it doesn't appear to work from outside: both of the following simply time out:
```
dig @91.92.178.202 lemuria.pozitivensvqt.com.
dig @199.207.13.100 lemuria.pozitivensvqt.com.

```(You can use the web form at [http://www.kloth.net/services/dig.php](http://www.kloth.net/services/dig.php)  amongst many others, to test this kind of thing from outside your  network.)

As I can't even ping those addresses, my guess is either a) your own router isn't forwarding the DNS requests to your server (which is pretty likely)  and/or b) your ISP is blocked DNS packets into your network (which is very unlikely).  You should check your router for incoming DNS requests on UDP port 53, and make sure they are forwarded to your correct machine.

**_Timing_**

A thing to know about DNS: propagation can be slow.  You will see in my previous posting this afternoon
```
pozitivensvqt.com.    172800    IN    NS    ns73.superhosting.bg.
pozitivensvqt.com.    172800    IN    NS    ns74.superhosting.bg.

```The number    172800 is the amount of time any computer receiving this is allowed to cache it for.  This means any DNS queries can have the wrong answer cached for 48 hours (172800 seconds) -- which is on Tuesday.  You have to remember that changes in DNS can take a shocking amount of time to propogate, and that at any given time during a change, you will get different answers from different servers.  This is a correct and rather clever part of DNS, but it's sometimes tricky to deal with and debug.  And you'll find that it seems the only things that get cached are mistakes you've made!

**_Serial Number_**

Per comment above about caching and propogation, don't forget you _must_ update the serial number in the SOA of your domains each time you make a change, or the other servers are unlikely to notice your change.  Because all they do is look at the serial number numerically, it _must_ always go up.  Therefore edit your serial numbers extremely carefully, as it really takes a long time to recover from the situation where you accidentally add an extra digit.  Really, really, carefully!

**_Reverses_**

Just to explain slightly about reverses: there are two domains you are interested in
pozitivensvqt.com, which contains a list of A records and is used to convert names to numbers, and 
13.207.199.in-addr.arpa, which contains a list of PTR records, and is used to convert IP addresses to names.

The delegations are in different places.  pozitivensvqt.com needs a deleagation ins .com, which you've done, through your Go Daddy control panel.  But 13.207.199.in-addr.arpa needs a delegation (or PTR records) in 207.199.in-addr.arpa, which is a domain under the control of your ISP or whoever allocated you your IP addresses.  (I'm summarising the usual case here: there are in fact some complex alternatives which I'm skipping over, because I don't believe they apply in your case.)

> what exactly do I need to contact my ISP for, and what should I ask them?If you have a static IP block of addresses that is at least /24 (ie, all of 199.207.13), you ask the hostmaster of your ISP: "Dear Hostmaster, Please delegate 13.207.199.in-addr.arpa to my servers by adding the following to your DNS servers.

```
13.207.199.in-addr.arpa. NS lemuria.pozitivensvqt.com.
13.207.199.in-addr.arpa. NS admin.pozitivensvqt.com.
```If you have a smaller allocation, then you'd need different records in the delegation, in a scheme which depends on the size of your allocation.  Classless reverse naming scheme is described [http://tools.ietf.org/html/rfc2317](http://tools.ietf.org/html/rfc2317)

If you have a /24 they're pretty likely to help.  If you have something  smaller than that they're pretty unlikely to help.  If you have a single static address, they might give you a PTR record in their DNS, but it's almost certain they won't delegate.  If you have a dynamic address, it's extremely unlikely that they'll help.

In my experience. ISPs take forever in dealing with reverse delegations, typically weeks, and you have to be very insistant indeed.  If they know what they're doing they'll complain about your server being inside its own block of IP addresses (but the admin host is somewhere else, which is good.)

**_IRC_**

I have no experience running IRC servers, but I see from Wikipedia that under some circumstances you do indeed need the reverse DNS entries like you said.  But a quick look around also found that some IRC people use ident, which perhaps will solve the problem another way around.
[http://en.wikipedia.org/wiki/Ident](http://en.wikipedia.org/wiki/Ident)

Hope all of that's of some use.

DNS is a slow game: don't be in too much of a hurry!

Kind regards,
Jonathan.

---

### Post by elico on 2011-10-31
a check for a working reverse lookup is:
dig -x @<your ISP dns server>  <your internet ip address>

---

### Post by Jonathan L on 2011-11-03
[FONT=Arial][FONT=Arial][FONT=monospace]Hi Beast

I see you're working a bit!

[/FONT][/FONT][/FONT]```
dig @91.92.178.202 lemuria.pozitivensvqt.com.
```[FONT=Arial][FONT=Arial]

Is now good, and I see you have an SOA with today's serial number.

Looks like you're starting to get there.

Kind regards,[/FONT]
Jonathan.[/FONT]

---

