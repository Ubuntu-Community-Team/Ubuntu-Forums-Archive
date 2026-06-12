---
title: "apache2 and Kerberos Authentication"
date: 2015-01-27
forum: Server Platforms
---

### Post by kas21 on 2015-01-27
I am trying to configure an apache on an Ubuntu server to support Kerberos authentication using an Active Directory backend.  I believe I have everything setup correctly, and authentication is working in most cases, however I am receiving 401 unauthorized when accessing the site from a Linux based computer.  On Windows computers, I have tested IE, FireFox, and Chrome.  All of them authenticate correctly.  On the Linux computer, I have used kinit to successfully obtain a Kerberos ticket, however, when I use Chrome or Firefox to request the site, I receive a 401.  I checked klist after trying to connect to the site and I do have additional HTTP Kerberos tickets for the site.  

Is it possible that Windows is downgrading to NTLM and not using Kerberos?  How can I test or verify this?

Here are some logs from the server:

**## Chrome on Linux - Request before getting Kerberos ticket ##**
```
 [authz_core:debug] [pid 16986] mod_authz_core.c(802): [client 192.168.1.50:56744] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 16986] mod_authz_core.c(802): [client 192.168.1.50:56744] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 16986] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56744] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
 [authz_core:debug] [pid 16986] mod_authz_core.c(802): [client 192.168.1.50:56744] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 16986] mod_authz_core.c(802): [client 192.168.1.50:56744] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 16986] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56744] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
 [authz_core:debug] [pid 16986] mod_authz_core.c(802): [client 192.168.1.50:56744] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 16986] mod_authz_core.c(802): [client 192.168.1.50:56744] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 16986] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56744] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
 [authz_core:debug] [pid 16986] mod_authz_core.c(802): [client 192.168.1.50:56744] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 16986] mod_authz_core.c(802): [client 192.168.1.50:56744] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 16986] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56744] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos

```

**## Chrome on Linux - Request after obtaining Kerberos ticket ##**
```
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56761] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56761] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1260): [client 192.168.1.50:56761] Acquiring creds for HTTP/webserver.my.domain.net
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1406): [client 192.168.1.50:56761] Verifying client data using KRB5 GSS-API with our SPNEGO lib
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1422): [client 192.168.1.50:56761] Client didn't delegate us their credential
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1441): [client 192.168.1.50:56761] GSS-API token of length 9 bytes will be sent back
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1121): [client 192.168.1.50:56761] GSS-API major_status:00010000, minor_status:00000000
 [auth_kerb:error] [pid 17031] [client 192.168.1.50:56761] gss_accept_sec_context() failed: An unsupported mechanism was requested (, Unknown error)
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56761] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56761] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56761] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1260): [client 192.168.1.50:56761] Acquiring creds for HTTP/webserver.my.domain.net
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1406): [client 192.168.1.50:56761] Verifying client data using KRB5 GSS-API with our SPNEGO lib
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1422): [client 192.168.1.50:56761] Client didn't delegate us their credential
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1441): [client 192.168.1.50:56761] GSS-API token of length 9 bytes will be sent back
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1121): [client 192.168.1.50:56761] GSS-API major_status:00010000, minor_status:00000000
 [auth_kerb:error] [pid 17031] [client 192.168.1.50:56761] gss_accept_sec_context() failed: An unsupported mechanism was requested (, Unknown error)
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 17031] mod_authz_core.c(802): [client 192.168.1.50:56761] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 17031] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56761] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos

```



**## Chrome on Windows - Success ##**
```
 [authz_core:debug] [pid 17062] mod_authz_core.c(802): [client 192.168.1.50:56902] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 17062] mod_authz_core.c(802): [client 192.168.1.50:56902] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 17062] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56902] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
 [authz_core:debug] [pid 17062] mod_authz_core.c(802): [client 192.168.1.50:56902] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
 [authz_core:debug] [pid 17062] mod_authz_core.c(802): [client 192.168.1.50:56902] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
 [auth_kerb:debug] [pid 17062] src/mod_auth_kerb.c(1652): [client 192.168.1.50:56902] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
 [auth_kerb:debug] [pid 17062] src/mod_auth_kerb.c(1260): [client 192.168.1.50:56902] Acquiring creds for HTTP/webserver.my.domain.net
 [auth_kerb:debug] [pid 17062] src/mod_auth_kerb.c(1406): [client 192.168.1.50:56902] Verifying client data using KRB5 GSS-API with our SPNEGO lib
 [auth_kerb:debug] [pid 17062] src/mod_auth_kerb.c(1422): [client 192.168.1.50:56902] Client didn't delegate us their credential
 [auth_kerb:debug] [pid 17062] src/mod_auth_kerb.c(1441): [client 192.168.1.50:56902] GSS-API token of length 181 bytes will be sent back
 [authz_core:debug] [pid 17062] mod_authz_core.c(802): [client 192.168.1.50:56902] AH01626: authorization result of Require valid-user : granted
 [authz_core:debug] [pid 17062] mod_authz_core.c(802): [client 192.168.1.50:56902] AH01626: authorization result of <RequireAny>: granted

```

---

