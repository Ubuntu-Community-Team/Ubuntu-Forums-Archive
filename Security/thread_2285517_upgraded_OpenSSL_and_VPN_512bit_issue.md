---
title: "upgraded OpenSSL and VPN 512bit issue"
date: 2015-07-06
forum: Security
---

### Post by xplicit-ru on 2015-07-06
After this security patch [http://www.ubuntu.com/usn/usn-2624-1/](http://www.ubuntu.com/usn/usn-2624-1/) I'm unable to connect to VPN servers which uses 512 DH keys. How can I enable back the ability to connect to VPN servers from Ubuntu (now I have to use windows machine for it, OpenVPN 2.3.7 can connect to the servers with small key).

The error from Ubuntu openvpn:

Mon Jul  6 22:35:04 2015 TLS_ERROR: BIO read tls_read_plaintext error: error:14082174:SSL routines:SSL3_CHECK_CERT_AND_ALGORITHM:dh key too small
Mon Jul  6 22:35:04 2015 TLS Error: TLS object -> incoming plaintext read error
Mon Jul  6 22:35:04 2015 TLS Error: TLS handshake failed

---

