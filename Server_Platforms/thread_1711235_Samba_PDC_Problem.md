---
title: "Samba PDC Problem"
date: 2011-03-21
forum: Server Platforms
---

### Post by Thomas_Matthew on 2011-03-21
Hello, I've been having some trouble with Samba and turning it into a domain controller. I have all the configurations set up correctly. Its when I tell my Windows XP Pro machine attempts to join my domain it fails with the error. 
 
The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)
The query was for the SRV record for _ldap._tcp.dc._msdcs.STUSVRJPIIHS
Common causes of this error include the following:
- The DNS SRV record is not registered in DNS.
- One or more of the following zones do not include delegation to its child zone:
STUSVRJPIIHS
. (the root zone)
 
I am unable to work out what is wrong with it. I have followed this tutorial: [http://www.youtube.com/watch?v=8MWBhlaLIxQ&feature=related](http://www.youtube.com/watch?v=8MWBhlaLIxQ&feature=related) If someone could direct me the area I need to go to resolve this problem I would gladly appreciate it. Thanks! :p

---

### Post by Thomas_Matthew on 2011-03-21
Bump, anyone?

---

### Post by kevin11951 on 2011-03-21
Is your DHCP server setup to include the DNS (WINS?) information?

---

### Post by Thomas_Matthew on 2011-03-21
> **kevin11951 said:**
> Is your DHCP server setup to include the DNS (WINS?) information?
I never did that... Never got told to by this tutorial. Where could I find where todo it excatly, thanks! ;)
 
EDIT: You mean that I have to use Webmin then make records and all the things it needs to run in there don't you?

---

### Post by kevin11951 on 2011-03-21
> **Thomas_Matthew said:**
> I never did that... Never got told to by this tutorial. Where could I find where todo it excatly, thanks! ;)
 
EDIT: You mean that I have to use Webmin then make records and all the things it needs to run in there don't you?

If you are using a consumer router, then this may not be possible.  However, if you can setup a real router I recommend you use Zentyal, its an Ubuntu 10.04 based server that can act as a router/dhcp server, and it also supports the PDC role ootb...

It is the linux version of the Windows Small Business server and then some...

[http://www.zentyal.org/](http://www.zentyal.org/)

---

### Post by Thomas_Matthew on 2011-03-21
> **kevin11951 said:**
> If you are using a consumer router, then this may not be possible. However, if you can setup a real router I recommend you use Zentyal, its an Ubuntu 10.04 based server that can act as a router/dhcp server, and it also supports the PDC role ootb...
 
It is the linux version of the Windows Small Business server and then some...
 
[http://www.zentyal.org/](http://www.zentyal.org/)
 
Ah, so it's a router setting. And your correct. It doesnt support it. Just one question, will I be able to run this along side my already running DHCP server in my router?

---

### Post by kevin11951 on 2011-03-21
> **Thomas_Matthew said:**
> Ah, so it's a router setting. And your correct. It doesnt support it. Just one question, will I be able to run this along side my already running DHCP server in my router?

No.

You can place the "new" Zentyal router behind your router, and have it just make a new subnet...

For Example:

Your Current Router: 192.168.1.1 - 255.255.255.0

The Zentyal Router: 192.168.2.1 - 255.255.255.0

Then you would connect all your computers to the Zentyal router

---

### Post by Thomas_Matthew on 2011-03-21
> **kevin11951 said:**
> No.
 
You can place the "new" Zentyal router behind your router, and have it just make a new subnet...
 
For Example:
 
Your Current Router: 192.168.1.1 - 255.255.255.0
 
The Zentyal Router: 192.168.2.1 - 255.255.255.0
 
Then you would connect all your computers to the Zentyal router
 
Ah, alright thank you. Well, I've got it all worked out. Thank you for all your help! :)

---

