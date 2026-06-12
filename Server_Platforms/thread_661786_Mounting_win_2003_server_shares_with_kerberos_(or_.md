---
title: "Mounting win 2003 server shares with kerberos (or other?)"
date: 2008-01-08
forum: Server Platforms
---

### Post by r-mo on 2008-01-08
I've got my ubuntu box authenticating on a windows 2003 server domain using kerberos and winbind and I'm wondering if it's possible to mount network shares in a login script either using the kerberos ticket or the username and password supplied in gdm.  I  tried to smbmount with -o krb but I get

```

Warning: kerberos support will only work for samba servers
ads_krb5_mk_req: krb5_get_credentials failed for dc$@domain (Cannot find ticket for requested realm)
cli_session_setup_kerberos: spnego_gen_negTokenTarg failed: Cannot find ticket for requested realm
Anonymous login successful
6990: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```

I'm guessing the 'kerberos will only work for samba servers' means that this won't work with a 2003 server atm thanks to ms only just releasing the specs for the smb protocol.  Or is there a way of getting this working?

I can mount using smbmount -o username=<username>,password=<password> so can I use the username and password from gdm to script this?

---

### Post by Cerebus on 2008-01-15
If you comment out the following from /etc/krb5.conf from section [libdefaults]:

default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc

It'll work.  

Removing these will mean you're using arcfour-hmac-md5 and the enctype.  I'm not sure why this works yet and what a better replacement would be. 

-- C

---

