---
title: "Seeking advice on completing application for fixed IP"
date: 2006-12-22
forum: Server Platforms
---

### Post by satimis on 2006-12-22
Hi folks,

I'm now completing following form for applying broadband installation with fixed IP address.  (I haven't registered a domain yet.  I'll register it later). 
```

Private IP address [ ] have Private IP	[ ] 10.__.__.__   to  10.__.__.__
					[ ] 172.__.__.__  to  172.__.__.__
					[ ] 192.168.__.__ to  192.168.__.__
					[ ] 192.168.0.10 to 192.168.0.60 (default)

		   [ ] have no Private IP address



Gateway IP:[ ] defaul: 192.168.0.1  [ ] different from default range:(range:__.__.__.__)


Subnet Mask: [ ] default: 255.255.255.192  [ ] different from default range:(range:__.__.__.__)


NAT	[ ] NAT applied		[ ] no NAT applied (default)


DHCP	[ ] DHCP applied (default for BBB Xtra and SBB Xtra	
	[ ] no DHCP applied (default for BBB X2, LL, MBB, NBB, SBB and LBS)
	[ ] range: 192.168.0.10-60 (default)
	[ ] different from default range: (range:__.__.__.__)


Internet IP address [ ] self owned Internet IP address	  IP address: ______
		    [ ] ISP owned Internet IP address	  IP address: ______
		    [ ] have no Internet IP address (default)


Firewall or proxy   [ ] have firewall or proxy separate network from Internet
		    [ ] no firewall or proxy (default)

```
The above information is for ISP to preset the router which will be supplied free of charge.


Could you please giving me some advice on completing the said form.  TIA


Merry X'mas and Happy New Year.


B.R.
satimis

---

### Post by kidders on 2006-12-22
Hi there,

You'll have to give us some indication of the composition of your network first ... there is no way for someone to guess the answers to these questions :-(

**Edit:**

If it were me, my answers might be:

**Private IP range: 192.168.5.1 - 192.168.5.254**
This is the address space used by my network.

**Gateway: 192.168.5.100**
This is the IP of the network node connected to the internet. (A Gentoo box, in my case.)

**Subnet mask: 255.255.255.0**
Part of the internal address space specification, used by network devices to decide which IP bits are significant in terms of routing packets.

**NAT applied**
Am I using (or would I like to use) NAT to share a single internet connection with my network?

**DHCP applied (Range 192.168.5.200 - 192.168.5.220)**
What part of the LAN address space is for use by DHCP clients?

**Have no internet IP address**
Isn't that the point in applying for one? :-? (Although my ISP owns mine.)

**Have firewall or proxy**
Should your router come with a built-in firewall or proxy?

---

### Post by satimis on 2006-12-22
Hi kidders,

> 
You'll have to give us some indication of the composition of your network first ... 

Whether you meant the kind of server?

It is a web, dns and email server.  Tks.

B.R.
satimis

---

### Post by chrisfay on 2006-12-22
> Whether you meant the kind of server?


I think he means your actual network layout. We couldn't give you guidance without knowing your LAN architecture.

---

### Post by satimis on 2006-12-22
Hi chrisfay,

> 
We couldn't give you guidance without knowing your LAN architecture.

I have no LAN architecture yet.  This is to continue my test overcoming the difficulty on running dynamic IP.

I'm going to register a domain with 'goddady'
[https://www.godaddy.com/gdshop/registrar/search.asp?se=%2B&ci=414](https://www.godaddy.com/gdshop/registrar/search.asp?se=%2B&ci=414)

Any comment and suggestion?  TIA


B.R.
satimis

---

### Post by kidders on 2006-12-22
> I think he means your actual network layout. We couldn't give you guidance without knowing your LAN architecture.
[COLOR="Silver"]Yep, exactly ...

If you are actually using the network at the moment, many of the answers will be obvious to you (eg what your subnet mask is). Others depend entirely on what your personal taste is.[/COLOR]

> I have no LAN architecture yet.Oh. Well, in that case, imagine you did ... how would you like it to work? If it were me, I'd opt for as dumb a router as possible, and implement most of its functionality in software ... perhaps with Ubuntu. But that's just the way _I'd_ like it.

---

### Post by satimis on 2006-12-22
Hi kidders,

> 
If it were me, I'd opt for as dumb a router as possible, and implement most of its functionality in software ... perhaps with Ubuntu. But that's just the way _I'd_ like it.
I have no knowledge on the free router supplied by ISP.  I agreed with your view to have a router without presettings, only possible to connect ISP and to access Internet.  What will be the basic requirement on the router?  Pls shed me some light to talk to ISP.  TIA.


B.R.
satimis

---

