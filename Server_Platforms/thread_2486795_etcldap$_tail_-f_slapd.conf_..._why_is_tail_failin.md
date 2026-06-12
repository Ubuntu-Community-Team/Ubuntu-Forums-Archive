---
title: "/etc/ldap$ tail -f slapd.conf ... why is tail failing!?"
date: 2023-05-11
forum: Server Platforms
---

### Post by civilpolisen on 2023-05-11
```
jakob@lynx:/etc/ldap$ tail -f slapd.conf 

# TLS certificates (needed for GnuTLS)
#TLS_CACERT    /etc/ssl/certs/ca-certificates.crt

LOCAL4.*        /var/log/openldap/slapd.log
# Additions to default conf (Removed: We are doing it it FD if we can): 
# https://www.openldap.org/doc/admin26/tls.html
#TLSCACertificateFile    /etc/letsencrypt/live/fd.domain.se/fullchain.pem
#TLSCertificateFile    /etc/letsencrypt/live/fd.domain.se/cert.pem
#TLSCertificateKeyFile    /etc/letsencrypt/live/fd.domain.se/privkey.pem


```

The tail is not moving! Fusion Directory is running on this server and when changes are made at the server changes would also appear in the log, in the tail! I was expecting...!
I try to connect using LDAP to a server with sssd running... this server / client is connecting successfully to the FD-server...

[B]I've been looking at these pages for inspiration about slapd and tail.
[/B][https://manpages.ubuntu.com/manpages/trusty/man5/slapd.conf.5.html](https://manpages.ubuntu.com/manpages/trusty/man5/slapd.conf.5.html)

[https://manpages.ubuntu.com/manpages/bionic/man1/tail.1.html](https://manpages.ubuntu.com/manpages/bionic/man1/tail.1.html)

---

### Post by TheFu on 2023-05-11
slapd.conf is a config file, not a log file.  It shouldn't be changing. If it doesn't change, then nothing will be displayed on the screen.
From the manpage for tail:
```
       -f, --follow[={name|descriptor}]
              output appended data as the file grows;
```
manpages are our friends.

---

