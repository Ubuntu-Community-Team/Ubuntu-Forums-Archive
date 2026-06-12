---
title: "Confused about name server, can someone break this down for me"
date: 2008-02-12
forum: Server Platforms
---

### Post by ade234uk on 2008-02-12
Ok when I purchased my dedicated server I was given two ip addresses
example 

234.232.123.78 and 234.232.123.79

So I set up an account on here called ubuntu and also set up the domain name ubuntu.co.uk and map this to the ubuntu account

So that when someone enters ubuntu.co.uk the webpages come up on the ubuntu account.

This is where I get confused between dns and nameservers.

Lets say my domain name is located @ 123reg which some of them are.
I would log into 123 reg and goto ubuntu.co.uk and click the change dns link

I am then presented with the following fields

@                  A          238.343.212.001
www            A          238.343.212.001

At the moment the domain is sitting on 123reg server. I want to change these settings to point to the dedicated server.

Now I presume I would enter the ip address of the server in these boxes but what number would I add. Would it the primary ip address or secondrary ip address.

How would you go about doing this, what steps would you take, so that when someone enter ubuntu.co.uk it takes them to the website?

---

### Post by ikonia on 2008-02-12
you are getting confused

Lets break this down.

1.) dns / namesservers - same thing.

2.) I assume you have apache setup using the "mod_user" module so that [www.ubuntu.co.uk](www.ubuntu.co.uk) points to /home/ubuntu/public_html 

3.) the name server stuff, you have 2 options, 

a.) use the 123-reg name servers to point the domain RECORD at your box (the best option) you need to use the 123-reg control pannel to add an A record for ubuntu.co.uk ---> your_ip_address

b.) change the name servers AWAY from ubuntu to point the DOMAIN not the record at your box - this requires you to be running your own TWO dns server on seperate IP address, then you create and manage your own records - I strongly advise against this unless you know exactly what your doing.

---

### Post by ade234uk on 2008-02-12
Ok I now understand the above. So I point the domain name to the ip of the box.

So would I then enter nslookup ubuntu.co.uk, would this not give me the ip address of where I need to point the domain name too in the A fields in 123reg?

I am learning so much and really pleased for the help.

---

### Post by ikonia on 2008-02-12
nslookup will query the dns record of ubuntu.co.uk 

eg: where is CURRENTLY pointing, in your example case, 123-reg's webservers.

you need to create an A record that points at YOUR server's ip address, then wait 24/48 hours for that change to propogate around the internet.

then when you do nslookup [www.ubuntu.co.uk](www.ubuntu.co.uk) you'll see your ip address

---

### Post by Rmantingh on 2008-03-29
If it helps....here are my settings for my domain at 123-reg.
I do not use my own DNS servers.

A, CNAME and TXT records
Name	Type	Content
@	A	62.44.79.226
ftp	CNAME	energyforge.com.
mail	A	62.44.79.226
www	CNAME	energyforge.com.

MX Records
Name	Priority
mail.energyforge.com	10

NB: Please note the extra dot after the CNAMEs !

---

### Post by Mr. C. on 2008-03-30
Rmantingh,

```
A, CNAME and TXT records
Name Type Content
@ A 62.44.79.226
```

This @ symbol is for the bare domain name (eg. mydoman.com  vs. host.mydomain.com).

The IP address should be that of your server.  DNS hosting companies default to using their services until you override them with your own.

```

ftp CNAME energyforge.com.
mail A 62.44.79.226
www CNAME energyforge.com.
```
These are common service aliases (www, ftp), and a mail record (which should not be a CNAME).  You can replace them as you see fit.

```
MX Records
Name Priority
mail.energyforge.com 10
```

Mail exchange records - this is where email for your domain will be sent.

Question: do you own the domain "ubuntu.co.uk", or are you just using it because you think you can.  You  must own that domain, and can't just use any name you choose.

Here's what you need to do:
1) Create an A record at your DNS provider's site, that specifies the IP address that reaches your server.  Your provider gave you two IP addresses - you'll have to determine which one(s) reach your server.  Perhaps both do, and this allows you to use IP-based hosting.  Start with the first one, and if that works, use it until you understand more about how all this stuff works (or when you need the second IP).  Your A record needs to be a hostname mapping to an IP address, the IP address of your server.  Eg: [www.mydomain.com](www.mydomain.com) ==> xxx.xxx.xxx.xxx (an ip).

2) Create additional A records if you want additional names to reach your server (Eg. host2.mydomain.com, host3.mydomain.com).

3) Alternatively, create CNAMEs instead of names in (2) above.

4) Set the bare domain record (@) to your server's IP, if you want to be reachable with just your domain name (Eg: [http://mydomain.com](http://mydomain.com))

5) Create the catch all (*) A record if you want to be reached by all other names (Eg. anything.mydomain.com)

If this doesn't resolve your questions/confusion,  please be as specific as possible with your immediate questions/concerns.

---

