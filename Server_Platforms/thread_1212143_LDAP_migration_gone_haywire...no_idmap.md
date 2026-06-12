---
title: "LDAP migration gone haywire...no idmap"
date: 2009-07-13
forum: Server Platforms
---

### Post by AsGF2MX on 2009-07-13
My domain PDC is a debian box running samba with openldap. Initially it was running off a tdbsam backend but I migrated it across to ldap over a year ago.

Now since then no users/machines were added/modified. I now have a few machines to add but can't.

Looking in samba logs shows no results except:

[2009/06/28 19:45:32, 2] smbd/reply.c:reply_tcon_and_X(711)
  Serving IPC$ as a Dfs root
Argument "" isn't numeric in addition (+) at /usr/share/perl5/Net/LDAP.pm line 406.
Could not find base dn, to get next uidNumber at /usr/share/perl5/smbldap_tools.pm line 1046.
[2009/06/28 19:45:45, 0] passdb/pdb_interface.c:pdb_default_create_user(368)
  _samr_create_user: Running the command `/usr/sbin/smbldap-useradd -w "ubutest$"' gave 127

Ubutest is a test box with ubuntu 9.10 on it. What can I do?

---

