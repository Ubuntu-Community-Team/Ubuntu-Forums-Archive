---
title: "mod_unique_id stoping internal connections to apache"
date: 2007-05-24
forum: Server Platforms
---

### Post by ninocass on 2007-05-24
I followed the guide here:

[http://mdessus.free.fr/?p=7](http://mdessus.free.fr/?p=7)

for setting up mod_security with apache and it works a treat when i access my server from outside of my network.  however when i try and access it using the local ip address i get the following:

```

Bad Request

Your browser sent a request that this server could not understand.
TEST Server at 192.168.11.2 Port 443

```

i dont think its the mod security which leaves the only thing thats changed to be the unique id mod

Any ideas

Cheers

Nino

---

### Post by ninocass on 2007-05-24
heh turns out it was mod_security

```

[Thu May 24 18:41:37 2007] [error] [client 192.168.11.3] ModSecurity: Access denied with code 400 (phase 1). Pattern match "^[\\\\d\\\\.]+$" at REQUEST_HEADERS:Host. [id "960017"] [msg "Host header is a numeric IP address"] [severity "CRITICAL"] [hostname "192.168.11.2"] [uri "/torrentflux/index.php"] [unique_id "y3FLm1YDKDYAAH5zAw0AAAAB"]

```


Edit the following file:

/etc/apache2/modsecurity/modsecurity_crs_21_protocol_anomalies.conf

Comment out the last line:

# Check that the host header is not an IP address 
#
#SecRule REQUEST_HEADERS:Host "^[\d\.]+$" "deny,log,auditlog,status:400,msg:'Host header is a numeric IP address', severity:'2',id:'960017'"

---

### Post by lfsuser on 2008-01-14
U da man (or woman).
Hope you get this accolade.

I had a similar problem where human name ([http://blahblah.com](http://blahblah.com)) would work but the IPaddress ([http://1.2.3.4/](http://1.2.3.4/)) would fail with the listed error.

Your suggestion works like magic, well not really magic since I understand it and as Arthur C. Clarke says: "Any technology sufficiently advanced is indistinguishable from magic."
I understand so not really magic...

anyway, kudos for an excellent suggestion/fix.

---

