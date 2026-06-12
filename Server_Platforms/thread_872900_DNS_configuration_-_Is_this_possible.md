---
title: "DNS configuration - Is this possible?"
date: 2008-07-28
forum: Server Platforms
---

### Post by Xiphius on 2008-07-28
Hello,

I'm a fairly new user to setting up servers and was looking into setting up a DNS that would resolve internal addresses. I don't need to forward traffic from the outside to any internal servers so that isn't a problem.

I simply need a configuration that allows a user to type *"ftp://hostname"* into their browser and have them connect to an internal host/server. I realize that this is not a FQDN and that I can solve that problem by going to each machine and editing the default search domain to include my local domain; however I don't have that option. I also know that I could have each user type *"ftp://hostname.mydomain.lan"* but I'd like to avoid that if possible (as many of the users are not tech savvy).
 
So my question is: Is it possible to have my DNS append a domain to all queries? or to automatically search my internal domain first?

If I have to run a separate service to do this that's OK. The important part is that I'm unable to configure the hosts in any way.

Thanks for any advice/knowledge you share.

---

### Post by PraysToPan on 2008-07-28
> **Xiphius said:**
> Hello,

I'm a fairly new user to setting up servers and was looking into setting up a DNS that would resolve internal addresses. I don't need to forward traffic from the outside to any internal servers so that isn't a problem.

I simply need a configuration that allows a user to type *"ftp://hostname"* into their browser and have them connect to an internal host/server. I realize that this is not a FQDN and that I can solve that problem by going to each machine and editing the default search domain to include my local domain; however I don't have that option. I also know that I could have each user type *"ftp://hostname.mydomain.lan"* but I'd like to avoid that if possible (as many of the users are not tech savvy).
 
So my question is: Is it possible to have my DNS append a domain to all queries? or to automatically search my internal domain first?

If I have to run a separate service to do this that's OK. The important part is that I'm unable to configure the hosts in any way.

Thanks for any advice/knowledge you share.

This isn't the responsibility of the DNS server.  You configure this on the client either statically or through DHCP.  

Statically, on a Linux client, you modify /etc/resolv.conf like so:
```
search domain1.local domain2.local (...)
nameserver xxx.xxx.xxx.xxx

```

Using DHCP, you have to add a record for the subnet you want this to apply to.  For ISC DHCP, the default DHCP server on Ubuntu, it would look something like this:

```
subnet xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy {
   (all your other DHCP directives)
   option domain-name "domain1.local domain2.local (...)";
}
```

Hope this helps,
Jon

---

### Post by 47_MasoN_47 on 2008-07-28
> I realize that this is not a FQDN and that I can solve that problem by going to each machine and editing the default search domain to include my local domain; however I don't have that option.

He can't go to each client and change the configuration.  I don't know that it is possible to do with a DNS server.  I'd probably just email everyone links with detailed instructions and tell them to bookmark them for ease of access.  That's what I've done with the internal sites here anyway.  Once they get it bookmarked then they don't have to worry about it anymore.

---

### Post by songshu on 2008-07-28
depends on how the clients are configured, mine get there DNS and NTP server from the DHCP server.

so if you can get them to look at your DNS server you could set up "internal view" in bind9.

i have a fictional domain for my internal services and this works nicely.

---

### Post by Xiphius on 2008-07-28
> **songshu said:**
> depends on how the clients are configured, mine get there DNS and NTP server from the DHCP server.

so if you can get them to look at your DNS server you could set up "internal view" in bind9.

i have a fictional domain for my internal services and this works nicely.

So right now I have my router pointing each host to the DNS and that is working correctly. (anyone can come onto the network and type the FQDN and everything works properly). Should I assume that setting up an "internal view" will allow me to force all internal traffic to search my local domain?
Sorry if I sound lost, I'm still wrapping my head around this. =)

To simplify my question for future posts/readers:

"ping hostname.mydomain.lan" works.

I would like anyone on my local network to be able to:

"ping hostname"

The catch is that I am unable to configure anything on the host side beyond pointing them to a DNS and/or DHCP server.

---

### Post by koenn on 2008-07-28
> **Xiphius said:**
> So right now I have my router pointing each host to the DNS and that is working correctly. (anyone can come onto the network and type the FQDN and everything works properly). Should I assume that setting up an "internal view" will allow me to force all internal traffic to search my local domain?
Sorry if I sound lost, I'm still wrapping my head around this. =)

To simplify my question for future posts/readers:

"ping hostname.mydomain.lan" works.

I would like anyone on my local network to be able to:

"ping hostname"

The catch is that I am unable to configure anything on the host side beyond pointing them to a DNS and/or DHCP server.

you can have dhcp not only  tell the hosts what to use for dns server, but also tell them what dns-suffix to use to make simple host names into FQDN's. It's dhcp option 15, but the actual keyword used in a config file may vary. See if the router, which apparently runs a dhcp daemon, supports this. Otherwise : it's pretty simple to run a dhcp daemon on a Linux box (e.g. the same as where tour dns is running).

---

### Post by Xiphius on 2008-07-28
Ok, I have figured it out!

Jon, your comment about DHCP was actually the key. After I added the domain name "mydomain.lan" to the DHCP domain name all the hosts picked that up and will now automatically search that domain.

Thanks for all your help everyone that posted!

---

