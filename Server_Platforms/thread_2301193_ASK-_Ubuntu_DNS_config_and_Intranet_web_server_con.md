---
title: "ASK- Ubuntu DNS config and Intranet web server config"
date: 2015-10-31
forum: Server Platforms
---

### Post by david457 on 2015-10-31
Hi guys. i'm new in Ubuntu
I'm sorry i dont know how to type properly and create a spoiler for the picts.

My cases are:
[B]1. Configure primary and secondary DNS server
2. Configure 3 intranet(internal) apache web server[/B]
-intranet.unn.co.uk/~username (unn.co.uk zone)
-A12345678.tech.co.uk (tech.co.uk zone)
-ws.staff.co.uk (staff.co.uk zone)


Primary DNS server address is 192.168.133.134
Secondary server ip add is 192.168.133.135




I have 3 zones for my DNS which are unn.co.uk, tech.co.uk, and staff.co.uk

this are the zone pict
[spoiler] [IMG]http://i65.tinypic.com/4l3yxf.jpg[/IMG] [/spoiler]

and my db.unn.co.uk 
[spoiler][IMG]http://i65.tinypic.com/15mgw34.jpg[/IMG][/spoiler]

result
[spoiler][IMG]http://i63.tinypic.com/rhrevr.jpg[/IMG][/spoiler]


and i tried the same method for my tech.co.uk but it does'nt work
[spoiler][IMG]http://i64.tinypic.com/dxol92.jpg[/IMG][/spoiler]


this is the configuration inside /etc/apache2/sites-available name tech.conf 
[spoiler][IMG]http://i63.tinypic.com/r85tn4.jpg[/IMG][/spoiler]


[B]Question: Is it possible my primary DNS holding 3 web server ? if yes what are my mistake? or do I need another 2 ubuntu for hosting my apache server ?

[/B]

Desperately need a mentor to guide me finish my project (configure primary & sec DNS, web server and mysql database.
PM me if interested
Thank you
Regards

David

---

### Post by darkod on 2015-10-31
There are few errors...

1. The db.unn.co.uk in the IN SOA line has "intranet" as the domain. It should be the domain with a traling dot, and of course the web admin email after it. Like:
```
@   IN   SOA   unn.co.uk. admin.unn.co.uk.   (
```

Also the trailing dot is missing in the IN SOA of db.tech.co.uk.

2. In all three zones, you should have IN NS records with your nameservers FQDN. Like:
```
@   IN   NS   ns1.unn.co.uk.
@   IN   NS   ns2.unn.co.uk.
```

You have different IN NS in db.unn.co.uk and db.tech.co.uk. Also the nameservers FQDN has to exist as A record in the corresponding zone (depending in which domain you want to place your nameservers).

3. When you create IN A records in the zones, on the left you don't put the full FQDN like you did. You just put the short prefix. Like:
```
david   IN   A   192.168.133.134
```

The domain zone already knows the domain and it adds it to the A record. What you did might add the domain twice. The left side of IN A should not contain the domain.

Make those changes and restart bind, see if that helps.

---

### Post by david457 on 2015-10-31
> **darkod said:**
> 

2. In all three zones, you should have IN NS records with your nameservers FQDN. Like:
```
@   IN   NS   ns1.unn.co.uk.
@   IN   NS   ns2.unn.co.uk.
```

You have different IN NS in db.unn.co.uk and db.tech.co.uk. Also the nameservers FQDN has to exist as A record in the corresponding zone (depending in which domain you want to place your nameservers).



I don't really understand this part.
do you mean in my db.unn.co.uk like this
```
@       IN    NS    intranet.co.uk.
@       IN    NS    A12345678.tech.co.uk.
intranet   IN   A 192.168.133.134
```

and my db.tech.co.uk like this?
```
@       IN    NS    A12345678.tech.co.uk.
@       IN    NS    intranet.co.uk.
A12345678   IN   A 192.168.133.135
```


should I use the same IP ?

---

### Post by darkod on 2015-10-31
You don't switch nameserver names according to domain. The DNS servers names are fixed, according to what you named them. On your DNS servers, if you run this:
```
hostname -f
```

What's the output?

Also, are the apache servers three separate machines, of you will have apache on the DNS servers? Are we talking about 5 machines, or 3 in total?

PS. Which hostnames have you assigned to your dns servers? intranet and a12345678? Those are not really hostnames most people would use... You can call your servers what ever you want, but you need to create some sort of logic in your infrastructure. For example, literary ns1 and ns2 are good dns names. You don't need much...

I would never call a server 'intranet', that's very confusing. intranet refers to a whole internal network, not to a specific machine on it.

---

### Post by david457 on 2015-10-31
the output for hostname -f is ubuntu

Well that's my doubt, so i can't use 1 ubuntu machine for my primary DNS include 3 apache server? now I'm doing with 2 ubuntu machine only. 1 for primary and  3 apache server and another one for secondary server.

For best practice which one should i use ? 5 ubuntu, 4 or 3 ?

For the hostnames I have no choice, cause that's what i need to create based from my assignment paper.
and for the a12345678 i need to make ex. a12345678 IN CNAME finance.tech.co.uk

---

### Post by darkod on 2015-10-31
Hmm, it's one thing to have a network named intranet (or a subdomain), but calling the server that is different.

You can have only one server that will be single dns and it will have apache web server on it. Inside apache you can have as many sites as you want. So, we are talking about 3 sites, not 3 servers.

Best practice is to have at least 2 dns servers for redundancy, if one fails. But one is enough to work.

So, you can set up all this on single machine and it will work.

For the records you are mentioning as part of the assignment, be careful that you understand it correctly. Making a record in the dns zone is one thing, calling the server 'intranet' or 'a12345678' is another. You can still call your server ns1 for example and have many A records in the dns zones.

Did you read the basic dns help from the ubuntu server manual? That's the place to start. [https://help.ubuntu.com/lts/serverguide/dns-configuration.html](https://help.ubuntu.com/lts/serverguide/dns-configuration.html)

That should sort out your dns part. Apache is different topic but included in the help guide too.

---

