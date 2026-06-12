---
title: "openLDAP and libnss and Unix accounts"
date: 2009-05-21
forum: Security
---

### Post by matthewboh on 2009-05-21
Okay - I've been slogging through installing openLDAP with Samba - but I'm running into some issues.

Basically, I am able to test out the LDAP with an ldapsearch, able to add users with the webmin module for LDAP users and groups or add them through the smbldap-adduser command line.

However, it doesn't appear to create a Unix account.  Is that needed?  I would prefer not to have Unix accounts. Here's the results from the Samba logs after I created the user 'alex'

```
[2009/05/23 13:57:20, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/alex failed. Permission denied
[2009/05/23 13:57:20, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/alex failed. No such file or directory
[2009/05/23 13:57:20, 0] smbd/service.c:make_connection(1191)
  mlb-laptop (192.168.1.101) couldn't find service alex
[2009/05/23 13:57:26, 1] passdb/pdb_get_set.c:pdb_set_user_sid_from_string(526)
  pdb_set_user_sid_from_string: -3024 isn't a valid SID!
[2009/05/23 13:57:26, 1] passdb/pdb_ldap.c:init_sam_from_ldap(575)
  init_sam_from_ldap: no sambaSID or sambaSID attribute found for this user alex
[2009/05/23 13:57:26, 1] passdb/pdb_ldap.c:ldapsam_getsampwnam(1413)
  ldapsam_getsampwnam: init_sam_from_ldap failed for user 'alex'!
[2009/05/23 13:57:26, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/alex failed. Permission denied
[2009/05/23 13:57:26, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/alex failed. No such file or directory
[2009/05/23 13:57:26, 0] smbd/service.c:make_connection(1191)
  mlb-laptop (192.168.1.101) couldn't find service alex
```

Any ideas of where to start?

Thanks,

Thanks

---

### Post by matthewboh on 2009-05-23
Bump

---

