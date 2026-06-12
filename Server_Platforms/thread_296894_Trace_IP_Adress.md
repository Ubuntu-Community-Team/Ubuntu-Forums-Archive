---
title: "Trace IP Adress"
date: 2006-11-10
forum: Server Platforms
---

### Post by Steve S. on 2006-11-10
Is there a way to trace an ip address hit on your firewall?

I'm sorry if this should be posted somewhere else, or it has been answered, but I don't even know the terminology on a "trace."

I run firestarter on a wireless pc run through a router (Linksys).  I have noticed that recently I'm getting a lot more blocked hits.  I want to know if there is some type of software, in Synaptic or otherwise, that can trace these and tell me what that ip address is.

Thanks for any terms or ideas you have on this.

---

### Post by an.echte.trilingue on 2006-11-10
The command is called whois.

For example, I have one of googles IP addresses: 64.233.183.99

In the terminal it looks like this:

```
mat@desktop:~$ whois 64.233.183.99

OrgName:    Google Inc.
OrgID:      GOGL
Address:    1600 Amphitheatre Parkway
City:       Mountain View
StateProv:  CA
PostalCode: 94043
Country:    US

NetRange:   64.233.160.0 - 64.233.191.255
CIDR:       64.233.160.0/19
NetName:    GOOGLE
NetHandle:  NET-64-233-160-0-1
Parent:     NET-64-0-0-0-0
NetType:    Direct Allocation
NameServer: NS1.GOOGLE.COM
NameServer: NS2.GOOGLE.COM
Comment:
RegDate:    2003-08-18
Updated:    2004-03-05

RTechHandle: ZG39-ARIN
RTechName:   Google Inc.
RTechPhone:  +1-650-318-0200
RTechEmail:  arin-contact@google.com

OrgTechHandle: ZG39-ARIN
OrgTechName:   Google Inc.
OrgTechPhone:  +1-650-318-0200
OrgTechEmail:  arin-contact@google.com

# ARIN WHOIS database, last updated 2006-11-09 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.
mat@desktop:~$

```

Probably, you are getting hit by zombies.  Don't try to counter-attack, since then you will be making some poor sap's life even worse.  The best you can do is take the ISP info you get from who is and report it to them.

Take care,

-mat

---

### Post by Steve S. on 2006-11-10
Excellent!  That's just what I wanted to know...thanks, Mat.

Zombie?  Please clarify...I need to learn new stuff today.:cool: 

Oh, and can the same thing be done in Windoze?  Just curious...

---

### Post by an.echte.trilingue on 2006-11-10
A zombie is what you call a computer that has been taken over with malicious software and is used by the person who wrote the software to do things like try to crack other computers.  The people who actually own the computers have no idea that they are attacking other people, they usually just think that their computers have gotten a lot slower lately.  There are litterally millions of computers like this on the internet.  So, trying to counter attack them is neither productive, legal, nor nice.  However, usually whois will give you the abuse address/phone# of the ISP, and you can report the address.  Sometimes they do something about it, usually they won't tell you about it either way. 

I am sure that something like this exists for Windows, but I haven't used windows in like five years so I don't know what it is called or where to get it, but it is not something you should pay money for.

Take care,

-mat

---

### Post by Steve S. on 2006-11-10
> **an.echte.trilingue said:**
> A zombie is what you call a computer that has been taken over with malicious software and is used by the person who wrote the software to do things like try to crack other computers.  The people who actually own the computers have no idea that they are attacking other people, they usually just think that their computers have gotten a lot slower lately.  There are litterally millions of computers like this on the internet.  So, trying to counter attack them is neither productive, legal, nor nice.  However, usually whois will give you the abuse address/phone# of the ISP, and you can report the address.  Sometimes they do something about it, usually they won't tell you about it either way. 

I am sure that something like this exists for Windows, but I haven't used windows in like five years so I don't know what it is called or where to get it, but it is not something you should pay money for.

Take care,

-mat

Excellent...thanks, mat.  Very, very appreciated.

Anyone else know the question about the equivalent in Windoze?  Just curious.

---

### Post by MJN on 2006-11-10
There are numeours *whois* clients for Windows - just search for 'windows whois' in Google and take your pick!

Mathew

---

### Post by Steve S. on 2006-11-10
> **MJN said:**
> There are numeours *whois* clients for Windows - just search for 'windows whois' in Google and take your pick!

Mathew

Rockin'.

I checked my favorite freeware site...[this one]("http://www.snapfiles.com/get/karenwhois.html") was pretty good for NT whois program.

Thanks all.

---

### Post by koenn on 2006-11-10
[http://www.kloth.net/services/](http://www.kloth.net/services/)

web-based nslookup, dig, whois, ... 
everything you need to find out who's who, and where

---

### Post by gl0wst1ckn1nja on 2007-09-08
here are some more programs that i have found to be useful:
   ettercap (packet capture) (very easy to use)
```
matt@d4rkf0rm:~$ sudo apt-get install ettercap-gtk
```
or if you want the verbose one it would be the same without the gtk tag at the end

   another is etherape (in synaptic)
```
matt@d4rkf0rm:~$ sudo apt-get install etherape
```

   finally a very nice whois client/port scanner/info getter/reverse DNS lookup is nmapfe
```
matt@d4rkf0rm:~$ sudo apt-get install nmapfe
```

have fun and happy "reconnaissance"

---

### Post by GS2 on 2007-09-08
[http://addons.mozilla.org/firefox/addon/827?id=827](http://addons.mozilla.org/firefox/addon/827?id=827)

Firefox DnsStuff addon - everything you need :)

Packet capture could also try Wireshark (used to be etheral)

---

### Post by gl0wst1ckn1nja on 2007-10-18
here are some more. 
```
sudo apt-get install wireshark
```
```
sudo apt-get install aircrack-ng
```

or you could just get backtrack2 and either live boot or install it its got all that stuff preinstalled

---

