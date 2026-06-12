---
title: "Setting up DNS"
date: 2012-06-20
forum: Server Platforms
---

### Post by computerfox on 2012-06-20
Hello all,

I want to try and set up my own DNS because I'm fed up with third party services.  

Specs: I have Ubuntu Server.  I use Webmin for management.  I opened up port 53.

I also set up bind9 following these instructions:[http://forums.devshed.com/dns-36/setting-up-dns-using-webmin-406190.html](http://forums.devshed.com/dns-36/setting-up-dns-using-webmin-406190.html)

What else do I have to do in order to have my own DNS server?

-FOX

---

### Post by rukiaEnix on 2012-06-20
But what else do you want? Make it public? What you have already done should be fine.

---

### Post by computerfox on 2012-06-20
> **rukiaEnix said:**
> But what else do you want? Make it public? What you have already done should be fine.

HAHA!  Thanks for the reply rukia.  Yes, I would like to make it public and some how use it with my registrar.  When I was trying to do it last night, it said it was invalid.  This could be just because it still needed to propagate, but I just wanted to make sure that I didn't need to register it with the registrar.  That would be kind of counterintuitive, I think, and plus FatCow doesn't allow me to do that at the moment.

---

### Post by SeijiSensei on 2012-06-20
You'll need to tell your registrar that your server is authoritative for the domain and set up a complete zone file on your server for your domain.

However there's a basic flaw in your model.  You won't have the [mandatory secondary nameserver]("http://ohse.de/uwe/rfc/rfc1912.html#2.8").  It's possible you can arrange for the registrar to host your secondary.  Otherwise you need another server, and preferably one not in the same network subnet as yours to provide fault-tolerance.

As RFC 1912 says at the outset, "Running a nameserver is not a trivial task. There are many things that can go wrong, and many decisions have to be made about what data to put in the DNS and how to set up servers."  Note the plural in the word "servers."

---

### Post by computerfox on 2012-06-20
> **SeijiSensei said:**
> You'll need to tell your registrar that your server is authoritative for the domain and set up a complete zone file on your server for your domain.

However there's a basic flaw in your model.  You won't have the [mandatory secondary nameserver]("http://ohse.de/uwe/rfc/rfc1912.html#2.8").  It's possible you can arrange for the registrar to host your secondary.  Otherwise you need another server, and preferably one not in the same network subnet as yours to provide fault-tolerance.

As RFC 1912 says at the outset, "Running a nameserver is not a trivial task. There are many things that can go wrong, and many decisions have to be made about what data to put in the DNS and how to set up servers."  Note the plural in the word "servers."

Yes, I am aware that if you want to run personal DNS you NEED 2 different IP addresses and I could probably call up Verizon to arrange that, but I believe that will cost me an arm and a leg.

---

### Post by gregor171 on 2012-06-20
I'm working on that problem right now and there are basically many solutions to the problem:

1. I have a server with 3 IP addresses (we get them here for free) and they are all conected to the same server. They say that You can even configure BIND9 to be a Caching and Primary Master DNS server simultaneously, a Caching and a Secondary Master server or...
Link: [URL="https://help.ubuntu.com/community/BIND9ServerHowto"]
https://help.ubuntu.com/community/BIND9ServerHowto[/URL]

So if someone finds the solution how to set up a box to be a Primary and secondary master at the same time without using Virtualbox. Setting up a second machine as a virtualbox would be a way to do it...

2. You can set your secondary DNS on one of free DNS providers like [http://xname.org/]("http://xname.org/") or [http://freedns.afraid.org/]("http://freedns.afraid.org/").
Free DNS are OK for non pro environment. They don't work 247. There was a time when xname was down for 3 days. 

3. You can rent a cloud server that would cost you around 200$ per year. Thats less than arm and a leg ))

And I have a question about that. If I set a third server and point records to another IPs (backup IP), could this work if my ISP is down?

Some more links:
[http://www.tldp.org/HOWTO/DNS-HOWTO.html]("http://www.tldp.org/HOWTO/DNS-HOWTO.html")
[http://linux.justinhartman.com/DNS_Installation_and_Setup_using_BIND9]("http://linux.justinhartman.com/DNS_Installation_and_Setup_using_BIND9")

---

### Post by stmiller on 2012-06-20
SeijiSensei has wise advice...

---

### Post by computerfox on 2012-06-20
> **gregor171 said:**
> I'm working on that problem right now and there are basically many solutions to the problem:

1. I have a server with 3 IP addresses (we get them here for free) and they are all conected to the same server. They say that You can even configure BIND9 to be a Caching and Primary Master DNS server simultaneously, a Caching and a Secondary Master server or...
Link: [URL="https://help.ubuntu.com/community/BIND9ServerHowto"]
https://help.ubuntu.com/community/BIND9ServerHowto[/URL]

So if someone finds the solution how to set up a box to be a Primary and secondary master at the same time without using Virtualbox. Setting up a second machine as a virtualbox would be a way to do it...

2. You can set your secondary DNS on one of free DNS providers like [http://xname.org/]("http://xname.org/") or [http://freedns.afraid.org/]("http://freedns.afraid.org/").
Free DNS are OK for non pro environment. They don't work 247. There was a time when xname was down for 3 days. 

3. You can rent a cloud server that would cost you around 200$ per year. Thats less than arm and a leg ))

And I have a question about that. If I set a third server and point records to another IPs (backup IP), could this work if my ISP is down?

Some more links:
[http://www.tldp.org/HOWTO/DNS-HOWTO.html]("http://www.tldp.org/HOWTO/DNS-HOWTO.html")
[http://linux.justinhartman.com/DNS_Installation_and_Setup_using_BIND9]("http://linux.justinhartman.com/DNS_Installation_and_Setup_using_BIND9")


Yes, I use afraid.org for my client's domains, but like you said it's not always on.  I used zonomi for a while, but it wasn't working out too well.  Looks like I might have to just stick with afraid.org for the time being.

---

### Post by rukiaEnix on 2012-06-21
You need two domains.

One for your nameservers.
And the other for your own domain.

---

