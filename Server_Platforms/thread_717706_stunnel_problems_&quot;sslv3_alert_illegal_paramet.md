---
title: "stunnel problems: &quot;sslv3 alert illegal parameter&quot;"
date: 2008-03-07
forum: Server Platforms
---

### Post by bigoperm on 2008-03-07
I'm having trouble connecting to my stunnel server. Both the client and server are running Ubuntu stunnel4. The connection log (from the server) is as follows:

```
sshd accepted FD=8 from [censored]:35982
sshd started
FD 8 in non-blocking mode
TCP_NODELAY option set on local socket
FD 9 in non-blocking mode
FD 10 in non-blocking mode
Cleaning up the signal pipe
Connection from [censored]:35982 permitted by libwrap
sshd accepted connection from [censored]:35982
Child process 10251 finished with code 0
SSL state (accept): before/accept initialization
SSL state (accept): SSLv3 read client hello A
SSL state (accept): SSLv3 write server hello A
SSL state (accept): SSLv3 write certificate A
SSL state (accept): SSLv3 write certificate request A
SSL state (accept): SSLv3 flush data
SSL alert (read): fatal: illegal parameter
SSL_accept: 14094417: error:14094417:SSL routines:SSL3_READ_BYTES:sslv3 alert illegal parameter
Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
sshd finished (0 left)
```

Is this a handshake problem? (But I'm using the same stunnel on both sides!?!?)

The client reports the following:

```
Snagged 64 random bytes from /path/to/.rnd
Wrote 1024 new random bytes to /path/to/.rnd
RAND_status claims sufficient
entropy for the PRNG
PRNG seeded successfully
Certificate: /path/to/.stunnel/certificates/host.crt
Certificate loaded
Key file: /path/to/.stunnel/keys/host.key
Private key loaded
Loaded verify certificates
from /path/to/.stunnel/certificates/cert.crt Loaded
/path/to/.stunnel/certificates/cert.crt revocation lookup file
SSL context initialized for service stunnel
ssh_exchange_identification: Connection closed by remote host
```

*Any* insight is appreciated

---

### Post by dthacker on 2008-03-07
Just a thought... Are you sure that both machines are setup for SSL3 in the stunnel config files?

dthacker

---

### Post by bigoperm on 2008-03-11
Yes, both machines are setup for SSLv3.

The really strange part is that I can connect to the server using other, non-Ubuntu, clients. Why wouldn't two Ubuntu machines running the same stunnel/SSL version not be able to communicate?!?!

---

### Post by bigoperm on 2008-04-28
I am able to connect to my server from other locations, so I believe the problem may be firewall related. That is, once my client is not behind a firewall, things seem to be okay. After looking at the TCPDump of successful and unsuccessful connection attempts, the problem occurs during the SSL handshake.

Does this firewall theory sound plausible? Does anyone know how/why a firewall would alter the handshake?

---

