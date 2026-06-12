---
title: "Samba + LDAP + LTS 10.04 problems with special characters in password."
date: 2010-09-14
forum: Server Platforms
---

### Post by gielium on 2010-09-14
Hello all,

We have a little problem with our upgraded domain controller. We moved from an old redhat enviorment to Ubuntu 10.04 everything seems to work fine now except.....

When a user has a @^&*() in the password we get a 

[2010/09/14 12:01:50,  2] passdb/pdb_ldap.c:571(init_sam_from_ldap)
  init_sam_from_ldap: Entry found for user: xxxxx.c
[2010/09/14 12:01:50,  2] passdb/pdb_ldap.c:1199(init_ldap_from_sam)
  init_ldap_from_sam: Setting entry for user: xxxxx.c
[2010/09/14 12:01:50,  2] auth/auth.c:320(check_ntlm_password)
  check_ntlm_password:  Authentication for user [xxxxx.c] -> [xxxxx.c] FAILED with error NT_STATUS_WRONG_PASSWORD

Maybe somewhere in the password checking routine they forget to put quotes arround the password so it's being treated as a regular expression?


I'm using LTS 10.04 with Samba 3.4.7 and an ldap backend.

Hope you guys have some good idea's:)


**Solved the keyboard layout of the test client switched after we cloned it with vmware. Windows bug.**

---

