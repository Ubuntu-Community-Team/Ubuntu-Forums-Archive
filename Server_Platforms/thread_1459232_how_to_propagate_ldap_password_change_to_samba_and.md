---
title: "how to propagate ldap password change to samba and unix user account"
date: 2010-04-21
forum: Server Platforms
---

### Post by macpraveen on 2010-04-21
Hello
I setup openldap and samba on 9.10. The ubuntu desktop client gets authenticated successfully with the server.

But when I do a passwd on the client, only the ldap passwd is getting changed but not in the samba and the unix user account.

My smb.conf

   ```

   passdb backend = ldapsam:ldap://192.168.3.100
   ldap suffix = dc=example,dc=local
   ldap user suffix = ou=People
   ldap group suffix = ou=Groups
   ldap admin dn = cn=admin,dc=example,dc=local
   ldap ssl = no
   ldap passwd sync = yes

   add machine script = sudo /usr/sbin/smbldap-useradd -t 0 -w "%u"

   obey pam restrictions = yes

   unix password sync = no

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes


```When I do a passwd, I get,

Enter login(LDAP) password:
New password:
Re-enter new password:
LDAP password information changed for username
passwd: password updated successfully

But only the ldap password is getting changed and not in the samba and unix user account.

I tried 
  unix password sync = yes 
but same result.

Am I missing something?

Thanks

---

### Post by macpraveen on 2010-04-21
any help from any one?

---

