---
title: "Bind9 DNS Entries for LDAP/Samba Authentication for Windows"
date: 2009-04-27
forum: Server Platforms
---

### Post by vasoq on 2009-04-27
I need to put some entries in like this:

_ldap._tcp.example.com. SRV 0 0 389 dc1.example.com.
_kerberos._tcp.example.com. SRV 0 0 88 dc1.example.com.
_ldap._tcp.dc._msdcs.example.com. SRV 0 0 389 dc1.example.com.
_kerberos._tcp.dc._msdcs.example.com. SRV 0 0 88 dc1.example.com.

I'm using the latest version of bind9 dns server available on 8.04. Can someone please help me figure out where these entries go and if they're the right format? I googled a lot but with no luck. I don't even know what config files to put in this, so please ask for something if you need it.

---

### Post by andrejonker on 2012-04-16
> **vasoq said:**
> I need to put some entries in like this:

_ldap._tcp.example.com. SRV 0 0 389 dc1.example.com.
_kerberos._tcp.example.com. SRV 0 0 88 dc1.example.com.
_ldap._tcp.dc._msdcs.example.com. SRV 0 0 389 dc1.example.com.
_kerberos._tcp.dc._msdcs.example.com. SRV 0 0 88 dc1.example.com.

I'm using the latest version of bind9 dns server available on 8.04. Can someone please help me figure out where these entries go and if they're the right format? I googled a lot but with no luck. I don't even know what config files to put in this, so please ask for something if you need it.

The information on this is so scattered. Please share if you have found an authoritative source for a default SAMBA DC config on Ubuntu - with Bind9.

---

### Post by hawkmage on 2012-04-16
Those entries would go into the DNS Zone file for the example.com domain.  

Here is a good reference for the SRV records in a Bind zone file: [http://www.zytrax.com/books/dns/ch8/srv.html](http://www.zytrax.com/books/dns/ch8/srv.html)

---

### Post by andrejonker on 2012-06-13
Thanks. I ended up installing [[http://www.zentyal.com/]](http://www.zentyal.com/]) which seems to work without this. Still trying to figure out how Zentyal's method works, or which way is better.

---

