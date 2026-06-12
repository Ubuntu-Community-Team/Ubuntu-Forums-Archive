---
title: "sub domain"
date: 2007-08-20
forum: Server Platforms
---

### Post by md5hash on 2007-08-20
how can i make a local subdomain i created accessible to my network using only 1 IP address?

---

### Post by southernman on 2007-08-20
[https://help.ubuntu.com/community/LocalhostSubdomain]("https://help.ubuntu.com/community/LocalhostSubdomain")

That should get you started in the right direction. If you have trouble with that post back and we'll help sort it out.

---

### Post by pofigster on 2007-08-20
What software are you using to run your server?  Apache2?

---

### Post by Mr. C. on 2007-08-20
Sub-domains and domains - all the same.  They are simply names which eventually are translated into IP addresses.

To answer correctly, you're going to have to explain what services you are referring to and how you will access them.  Adding an entry in /etc/hosts will be sufficient for some services, but insufficient for others.

Please clarify.
MrC

---

### Post by md5hash on 2007-08-21
> **pofigster said:**
> What software are you using to run your server?  Apache2?

Ubuntu Server + Apache2

---

### Post by md5hash on 2007-08-21
> **Mr. C. said:**
> Sub-domains and domains - all the same.  They are simply names which eventually are translated into IP addresses.

To answer correctly, you're going to have to explain what services you are referring to and how you will access them.  Adding an entry in /etc/hosts will be sufficient for some services, but insufficient for others.

Please clarify.
MrC

I have here a intranet site [http://iportal](http://iportal) i want my development site to be accessible from this url [http://beta.iportal](http://beta.iportal), this is not working when i try to access it from another pc

i added this to my /etc/hosts.. what is wrong?

127.0.0.1 iportal.localhost iportal
127.0.0.2 beta.localhost beta.iportal

---

### Post by Mr. C. on 2007-08-21
1) you need host entries on the *client* PCs
2) your apache config must recognize the (sub-)domain.

Once you've added the host entries on the client, you can ping by name to verify you've configured the client correctly.  Then you can verify that apache is receiving the requests by examining your apache access and error logs.

MrC

---

### Post by md5hash on 2007-08-21
Adding entries to clients pc will be too hard for me because we 200+ employees working here. 

is there an easy way?

---

### Post by Mr. C. on 2007-08-21
I don't want to play guessing games with scant details.  You really have to describe your environment better if you want help.  Perhaps other's are willing to stab in the dark.

MrC

---

### Post by wirelessmonkey on 2007-08-22
Apache2 virtual hosts, and you'll have to configure your DNS appropriately.

---

### Post by md5hash on 2007-08-22
> **wirelessmonkey said:**
> Apache2 virtual hosts, and you'll have to configure your DNS appropriately.

is it possible to have subdomains with 1 ip address?

---

### Post by MJN on 2007-08-22
Yes, that's one of the main reasons behind the need for virtual hosting - multiple names/domains/sites being served from a single address.
 
As Mr C says you need to provide more detail to your question/circumstances if you require detailed responses. Alternatively, some Googling will have you up to speed in no time.
 
Mathew

---

### Post by md5hash on 2007-08-22
heres what i want to happen..  i have an existing intranet site with this address [http://iportal](http://iportal), i need to have a subdomain [http://beta.iportal](http://beta.iportal) for unstable version of my site and this should be accessible also from other workstation. 

[http://iportal](http://iportal) is in ubuntu server

please tell me other info you want to know.

---

### Post by MJN on 2007-08-22
As discussed above there are a number of steps required to achieve this - firstly you need a method by which clients can find the IP address of your sub-domain, and secondly when they then connect to your server the correct site is served up.
 
The first issue is solved by either a) adding a **<ip.address.of.server> beta.iportal** entry to each client, or b) adding a suitable record to a DNS that your clients can then query.
 
The second issue requires you creating another <Virtualhost> container (see the Apache docs online) specifically for your beta site (identified using a **Servername beta.iportal** directive inside this container).
 
See [http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/) for further details.
 
I appreciate it's all very daunting when you don't know where to even start, but the effort of the exploration process of searching for further info on the 'buzzwords' mentioned will pay for itself in no time.
 
Mathew

---

### Post by md5hash on 2007-08-22
Thanks alot MJN

---

