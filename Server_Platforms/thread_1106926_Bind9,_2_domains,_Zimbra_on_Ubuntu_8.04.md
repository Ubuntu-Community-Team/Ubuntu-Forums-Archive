---
title: "Bind9, 2 domains, Zimbra on Ubuntu 8.04"
date: 2009-03-26
forum: Server Platforms
---

### Post by primaxx on 2009-03-26
Hello,

I must just admit, the more I work with networking, the more difficult I find it...

I know I have asked a more or less similar question earlier, but I never got the answer I needed, so I try again.

What I desperately need someone to tell me is how to configure /etc/hosts and the zone-files /etc/bind/db.test.no and /etc/bind/db.example.no given the following scenario:

[list]
[*]One public, static ip 100.200.300.400
[*]test.no and example.no are pointed to this ip-address (100.200.300.400)
[*]IMAP, smtp and such services are routed to 192.1.2.3 in the local network
[*]Zimbra will be installed on 192.1.2.3, (hostname: ubuntubox) and will serve the mail for both test.no and example.no. Even though all the computers in my network uses the public dns-servers 100.200.0.100 and 100.200.0.200, this machine (the ubuntubox) needs to have a local dns-server running. This is because I need the result of when I run **nslookup mail.test.no**, or **nslookup mail.example.no*** to be the local ip 192.1.2.3*, and *not *the public 100.200.300.400.
(If you understood that you are probably a professor in linguistics... :P)
[/list]
This is my /etc/hosts today:
```
127.0.0.1 localhost.localdomain localhost
127.0.1.1 ubuntubox.test.no ubuntubox ubuntubox.example.no
192.1.2.3	mail.test.no mail mail.example.no mail
100.200.300.400 mail.test.no mail mail.example.no mail
```,

and this is one of my dns zone-files (/etc/bind/db.test.no):```
;
; BIND data file for test.no
;
$TTL    604800
@       IN      SOA     mail.test.no. webmaster.test.no. (
                         2009032502         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      mail
        IN      MX      10 mail
        IN      A       192.1.2.3
mail    IN      A       192.1.2.3
```

The Zimbra-installation fails, and I do believe my problem is related to this:
When running nslookup test.no (from 192.1.2.3) the response is **192.1.2.3** (which is what I want it to be.)
When running nslookup mail.test.no (from 192.1.2.3) the response is **Host mail.test.no not found 3(NXDOMAIN)**.

Are there any samaritans here who understand my problem and can help me with this?

Thanks upfront! :-)
(Says one who easily understand the concept of dns, but find it incredibly hard to configure......)

---

### Post by BkkBonanza on 2009-03-26
IP addresses can only go up to 255 - so without having looked over the rest of your text, for starters you need to change the 100.200.300.400 to something valid.

Next, you can't assign names to more than one ip in /etc/hosts. That would make no sense. A name points to one and only one IP. 

For your local address you should use a net space designated for private networks. Not 192.1.2.3 but perhaps 192.168.2.3

You do not need a local dns for your names. You use your public dns for public names and the local names should be easy to do from your router. It's dhcp program will usually allow for resolving local names. Also you can use /etc/hosts for that but it's manual.

/etc/hosts overrides the dns server - so any name lookups that are found in your hosts file are not even asking the dns server. Likely your dns server is misconfigured. Any requests for a name it doesn't know need to relay on to the external dns server. But your public ip isn't valid so it's impossible that that ip would actually have been accepted by any dns server.

---

### Post by primaxx on 2009-03-26
> **BkkBonaza said:**
> IP addresses can only go up to 255 - so without having looked over the rest of your text, for starters you need to change the 100.200.300.400 to something valid.

I know that, the addresses used in this post are just to illustrate my situation. The domain-names i refer to are also not. test.no and example.no...

Thanks for the reply, anyway! :-)

---

### Post by primaxx on 2009-03-28
This is now solved. I just had to change /etc/hosts from this```
127.0.0.1 localhost.localdomain localhost
127.0.1.1 ubuntubox.test.no ubuntubox ubuntubox.example.no
192.1.2.3	mail.test.no mail mail.example.no mail
100.200.300.400 mail.test.no mail mail.example.no mail
``` to this:```
127.0.0.1 localhost.localdomain localhost
127.0.1.1 ubuntubox.test.no ubuntubox ubuntubox.example.no
192.1.2.3	mail.test.no mail mail.example.no mail
```
(In case anyone ever wonders...)

---

### Post by windependence on 2009-03-28
Yes, I have one customer where I had to set up local DNS to get the mail to resolve correctly but in your case I don't think you need to run Bind at all. Zimbra is picky about DNS but their community support is great. Glad you got it fixed.

-Tim

---

### Post by primaxx on 2009-03-28
> **windependence said:**
> Yes, I have one customer where I had to set up local DNS to get the mail to resolve correctly but in your case I don't think you need to run Bind at all. Zimbra is picky about DNS but their community support is great. Glad you got it fixed.

-Tim

That's interesting!
-Because (and this probably more a question than a statement) even though you don't have Bind installed, it will still check the /etc/hosts before asking dns. -as long as you have this in your /etc/nsswitch.conf:```
hosts:	files dns
```Then you just have to add your local ip-address in your /etc/hosts like this:```

192.1.2.3	mail.test.no mail mail.example.no mail
```

I needed the peace of Earth Hour to understand this... :-)

-Oh, and by the way, for those of you who ever plan to install Zimbra, remember to do it on a computer where you have not yet installed Apache and MySQL!

Yes, I have seen the forum for Zimbra, but somehow it feels safer to ask questions here...

Primaxx
[SIZE="1"]Always learning by doing, and always the hard way...[/SIZE]

---

### Post by windependence on 2009-03-30
Yeah, normally /etc/hosts would be fine, but in this case, the setup was much more complicated than that.  If you are interested in why, do a search for "split DNS" and you'll see what I mean. This machine was also hosted on a rather complex VMware ESXi setup. /etc/hosts just didn't do it. Trust me, I avoid Bind at all costs. One mistake and the whole machine can get buggered up from DNS problems.

-Tim

---

