---
title: "Trying to get ldapi working on Ubuntu 12.04"
date: 2012-12-19
forum: Server Platforms
---

### Post by Philip Colmer on 2012-12-19
I've followed these instructions for the server:

[https://help.ubuntu.com/12.04/serverguide/openldap-server.html](https://help.ubuntu.com/12.04/serverguide/openldap-server.html)

and these instructions for the client:

[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

I've got LDAP working in clear text but I'm unable to get TLS working.

I've tested the certificates installed on the server with:

openssl s_client -connect YOUR_LDAP_SERVER:636 -showcerts

and the client is able to connect to the server and display the certificates.

However, if I run

ldapsearch -x -H ldaps://<server>

or

ldapsearch -x -H ldapi://<server>

I get this error:

ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

If I add -d5, this is the output I get:

ldap_url_parse_ext(ldapi://<server>)
ldap_create
ldap_url_parse_ext(ldapi://<server>/??base)
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_path
ldap_new_socket: 3
ldap_connect_to_path: Trying <server>
ldap_connect_timeout: fd: 3 tm: -1 async: 0
ldap_ndelay_on: 3
ldap_close_socket: 3
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

but this doesn't seem to shed any light on what is going wrong.

Any suggestions on what I've overlooked, please?

Thanks.

Philip

---

### Post by Philip Colmer on 2012-12-20
I've managed to get ldaps working - I think I had overlooked the need to copy the LDAP server's "root CA" certificate to the client system.

However, ldapi is still failing for some reason, even though both ldap:// and ldaps:// are working.

---

### Post by Philip Colmer on 2013-01-09
> **Philip Colmer said:**
> I've managed to get ldaps working - I think I had overlooked the need to copy the LDAP server's "root CA" certificate to the client system.

However, ldapi is still failing for some reason, even though both ldap:// and ldaps:// are working.

I was misunderstanding what ldapi meant. I didn't really mean ldapi - I was only really trying to get LDAP + SSL working.

---

