---
title: "OpenDKIM help please"
date: 2010-10-14
forum: Server Platforms
---

### Post by clegends on 2010-10-14
Hi people, I'm having problems setting up dkim with opendkim. Could someone take a look at my db files below, and config file for opendkim to see that I'm getting this right? When I try and send an email to [email]check-auth@verifier.port25.com[/email] I get back 'perm Error', domainkey not found. Have I made a mistake? My domain is curiouslegends.com.au and I'm running ubuntu 10.04.1 64x.

db.curiouslegends.com.au
```


;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     curiouslegends.com.au. curiouser.curiouslegends.com.au. 
(
                      2010101402        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.curiouslegends.com.au.
@       IN      A       124.254.118.5
@       IN      AAAA    ::1
ns      IN      A       124.254.118.5
www     IN      A       124.254.118.5 
@       IN      MX 1    mail.curiouslegends.com.au.
mail    IN      A       124.254.118.5
curiouslegends.com.au.  IN      NS      ns0.xname.org.
curiouslegends.com.au.  IN      NS      ns1.xname.org.
curiouslegends.com.au.  IN      NS      ns2.xname.org.
curiouslegends.com.au.  IN      TXT     "v=spf1 a mx ~all"

2010._domainkey.curiouslegends.com.au.  IN      TXT "k=rsa; p=(key, not posted)"
mail._domainkey.curiouslegends.com.au.  IN      TXT     "k=rsa; p=(key, not posted)"
(END) 

```

db.124 (reverse dns)

```


;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA curiouslegends.com.au. curiouser@curiouslegends.com.au. (
                       2010101402       ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.curiouslegends.com.au.
1.0.0   IN      PTR     curiouslegends.com.au.
1.0.0   IN      PTR     www.curiouslegends.com.au.
1.0.0   IN      PTR     mail.curiouslegends.com.au.
/etc/bind/db.124 (END) 

```

My config file for opendkims:


```

# This is a basic configuration that can easily be adapted to suit a standard
# installation. For more advanced options, see opendkim.conf(5) and/or
# /usr/share/doc/opendkim/examples/opendkim.conf.sample.

# Log to syslog
Syslog                  yes
# Required to use local socket with MTAs that access the socket as a non-
# privileged user (e.g. Postfix)
UMask                   002

# Sign for example.com with key in /etc/mail/dkim.key using
# selector '2007' (e.g. 2007._domainkey.example.com)
Domain                  curiouslegends.com.au
KeyFile                 /etc/mail/dkim.key
Selector                2010

# Commonly-used options; the commented-out versions show the defaults.
#Canonicalization       simple
#Mode                   sv
SubDomains              yes
#ADSPDiscard            no
ReportAddress           [email]curiouser@curiouslegends.com.au[/email]
/etc/opendkim.conf (END) 

```

I appreciate your help in advance. Cheers.

---

### Post by clegends on 2010-10-14
Bump. Anyone able to help please?

---

### Post by clegends on 2010-10-15
Another bump...

---

### Post by clegends on 2010-10-20
Mods, can you please close & delete this thread? I've been getting help over at the Opendkim guid thread, and would rather not have 2 running. Cheers. Other thread is here: [http://ubuntuforums.org/showthread.php?p=10002682#post10002682](http://ubuntuforums.org/showthread.php?p=10002682#post10002682)

---

