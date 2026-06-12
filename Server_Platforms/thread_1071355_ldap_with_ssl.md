---
title: "ldap with ssl"
date: 2009-02-16
forum: Server Platforms
---

### Post by pischta on 2009-02-16
Hi!

I would like to set up a SaMBa server with ldap, with Kerberos autentication, for which I need ssl. ldap+ssl doesn't work. I read some docs, searched the error messages, but i couldn't find the solution.
I use Ubuntu 8.10 AM64.
Here is the output of two commands:
```
**openssl s_client -connect srv4:636 -showcerts**
CONNECTED(00000003)
7326:error:140790E5:SSL routines:SSL23_WRITE:ssl handshake failure:s23_lib.c:188:

**ldapsearch -H ldaps://192.168.1.100 -b dc=valami,dc=pelda,dc=hu -x -d 255**
ldap_url_parse_ext(ldaps://192.168.1.100)
ldap_create
ldap_url_parse_ext(ldaps://192.168.1.100:636/??base)
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP 192.168.1.100:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 192.168.1.100:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
tls_write: want=93, written=93
0000: 16 03 02 00 58 01 00 00 54 03 02 49 95 64 63 ad ....X...T..I.dc.
0010: e6 3a f4 b2 4a d7 cb 5e 7f 00 7b 37 ef dd d1 49 .:..J..^..{7...I
0020: e0 53 a5 3e ba fa 0b b0 5b 00 90 00 00 24 00 00 .S.>....[x......
0030: 00 45 00 39 00 88 00 16 00 00 00 44 00 38 00 00 .E.9.......D.8..
0040: 00 13 00 66 00 2f 00 41 00 35 00 84 00 0a 00 05 ...f./.A.5......
0050: 00 04 01 00 00 07 00 09 00 03 02 00 01 .............
tls_read: want=5, got=0

TLS: can't connect: A TLS packet with unexpected length was received..
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
```

Thanks: Tamas.

---

### Post by buddyellis on 2009-03-05
I've got the same issue, the openssl command above works on several other ubuntu servers but not one particular server that was installed from jeos

openssl s_client -connect ldp.server.com:636 -showcerts gives me a tls error.  Does the openssl in hardy come built with ssl?

openssl s_client -connect ldp.server.com:636 -showcerts
CONNECTED(00000003)
16916:error:140790E5:SSL routines:SSL23_WRITE:ssl handshake failure:s23_lib.c:188:

---

