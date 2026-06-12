---
title: "FreeRadius+OpenLdap+WIFI AP"
date: 2016-07-07
forum: Server Platforms
---

### Post by Eloge_Bapfunya on 2016-07-07
Hi all,
I am about to finalize set up of my freeradius server to use Ldap directory as source of identity. I configured my WIFI AP to use WPA2 Enterprise connected to radius server for authentication. When I try to get connected from my Windows 7 to the WIFI AP, it prompt me to type username and password and I get this error from my radius server logs:
Thu Jul  7 11:47:05 2016 : Error: TLS Alert read:fatal:unknown CA
Thu Jul  7 11:47:05 2016 : Error:     TLS_accept: failed in SSLv3 read client certificate A
Thu Jul  7 11:47:05 2016 : Error: rlm_eap: SSL error error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Thu Jul  7 11:47:05 2016 : Error: SSL: SSL_read failed inside of TLS (-1), TLS session fails.

Is there anyway I should bypass the verification of the certification as I have around thousands of devices that will be connected through this process and I can't set up certifcate on all devices.
Thank you in advance for your help.

Eloge

---

