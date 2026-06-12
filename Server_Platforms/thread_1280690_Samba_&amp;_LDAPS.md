---
title: "Samba &amp; LDAPS"
date: 2009-10-02
forum: Server Platforms
---

### Post by HDave on 2009-10-02
Been banging my head against the wall for about 4 days now trying to get Samba to use LDAP authentication (using SSL).  

I think I have the smb.conf setup properly. e.g.

```
passdb backend = ldapsam:ldaps://virt-ldap-srv.mydomain.int:636/
```

However, when testing the client side (test user "eva") I keep getting:

```
tree connect failed: NT_STATUS_ACCESS_DENIED
```

Tailing the samba log file, I find several errors in succession:

```
[2009/10/02 11:22:35,  0] lib/smbldap.c:smb_ldap_start_tls(600)
  Failed to issue the StartTLS instruction: Operations error
[2009/10/02 11:22:35,  1] lib/smbldap.c:another_ldap_try(1175)
  Connection to LDAP server failed for the 1 try!
[2009/10/02 11:22:36,  1] passdb/pdb_get_set.c:pdb_set_user_sid_from_string(517)
  pdb_set_user_sid_from_string: 0-815-4711-4003 isn't a valid SID!
[2009/10/02 11:22:36,  1] passdb/pdb_ldap.c:init_sam_from_ldap(617)
  init_sam_from_ldap: no sambaSID or sambaSID attribute found for this user eva
[2009/10/02 11:22:36,  1] passdb/pdb_ldap.c:ldapsam_getsampwnam(1531)
  ldapsam_getsampwnam: init_sam_from_ldap failed for user 'eva'!
[2009/10/02 11:22:36,  0] lib/smbldap.c:smb_ldap_start_tls(600)
  Failed to issue the StartTLS instruction: Operations error
[2009/10/02 11:22:36,  1] lib/smbldap.c:another_ldap_try(1175)
  Connection to LDAP server failed for the 1 try!
[2009/10/02 11:22:37,  0] lib/smbldap.c:smb_ldap_start_tls(600)
  Failed to issue the StartTLS instruction: Operations error
[2009/10/02 11:22:37,  1] lib/smbldap.c:another_ldap_try(1175)
  Connection to LDAP server failed for the 1 try!
[2009/10/02 11:22:38,  0] smbd/service.c:make_connection_snum(740)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
```

The first error seems pretty ominous: ("Failed to issue the StartTLS instruction: Operations error").   However, I can use ldaps from the command line on the samba server (and other machines) so I don't think the problem is on the LDAP server.

All suggestions are welcome!

---

### Post by awclemen on 2009-10-02
Well, since you are looking for any suggestions, here's one out of left field

I think using TLS, you need to use port 389, not 636.

[http://www.unav.es/cti/ldap-smb/smb-ldap-3-howto.html#smb.conf.tls](http://www.unav.es/cti/ldap-smb/smb-ldap-3-howto.html#smb.conf.tls)

Good Luck!

---

### Post by HDave on 2009-10-02
You are right.  In fact, I found out that if you provide the URI as "ldaps://..." then you need to explicitly tell Samba NOT to use TLS.

The incredibly obtuse way you do this is with the following configuration in smb.conf:

```
ldap ssl = off
```

The default for ldap ssl is "Start TLS".  The values of yes, no, and on or no longer valid.

---

