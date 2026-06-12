---
title: "Problems with Samba and LDAP"
date: 2009-01-05
forum: Server Platforms
---

### Post by constchar* on 2009-01-05
Hello everybody!
I am currently dealing with an issue for an employer involving Samba that I cannot figure out.
The issue at hand is that Samba must be configured properly to authenticate using LDAP, however, it is not functioning properly.
I did not originally setup the server, someone else did, and from what I can tell everything seems to be properly configured but despite that I am unable to login to a share.

I get the following error messages when connecting to Samba, and trying to authenticate to access a share:
```

[2009/01/05 16:18:20, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2009/01/05 16:18:20, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2009/01/05 16:18:24, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2009/01/05 16:18:24, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2009/01/05 16:18:36, 1] passdb/pdb_get_set.c:pdb_set_user_sid_from_string(526)
  pdb_set_user_sid_from_string: -3032 isn't a valid SID!
[2009/01/05 16:18:36, 1] passdb/pdb_ldap.c:init_sam_from_ldap(575)
  init_sam_from_ldap: no sambaSID or sambaSID attribute found for this user james.kelly
[2009/01/05 16:18:36, 1] passdb/pdb_ldap.c:ldapsam_getsampwnam(1413)

```

After much searching and double-checking I am led to believe that the problem lies with an incorrect sambaSID, as the log suggests, and all of the users on a server have a similar sambaSID (A number in the format of -30xx).

The global section of the Samba configuration:
```

        obey pam restrictions = no
        dns proxy = no
        workgroup = WORKGROUP
        os level = 20
        printcap name = /usr/share/doc/samba-doc/examples/printer-accounting/printcap
        usershare allow guests = yes
        max log size = 1000
        log file = /var/log/samba/log.%m
        socket options = TCP_NODELAY
        winbind trusted domains only = yes
        encrypt passwords = true
        wins support = true
        server string = %h server (Samba, Ubuntu)
        path = /Storage
        unix password sync = yes
        logon path =
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        pam password change = yes

        passdb backend = ldapsam:ldap://127.0.0.1/
        idmap backend = ldap:ldap://127.0.0.1:389

        ldap admin dn = cn=admin,dc=domain,dc=com
        ldap suffix = dc=domain,dc=com
        ldap group suffix = ou=Groups
        ldap user suffix = ou=Users
        ldap machine suffix = ou=Computers
        ldap idmap suffix = ou=Users
        ldap passwd sync = Yes

        passwd program = /usr/sbin/smbldap-passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        add user script = /usr/sbin/smbldap-useradd -m "%u"
        ldap delete dn = Yes
        delete user script = /usr/sbin/smbldap-userdel "%u"
        add machine script = /usr/sbin/smbldap-useradd -m "%u"
        add group script = /usr/sbin/smbldap-groupadd -p "%g"
        delete group script = /usr/sbin/smbldap-groupdel "%g"
        add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
        delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
        set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
        domain logons = yes

```

And the share I am attempting to access:
```

        path = /tmp
;       public = yes
        browsable = yes
        wide links = no
        delete readonly = yes
        writeable = yes
        valid users = @"Domain Users"
;       write list = @"Domain Users"
;       force group = Domain Users

```

And, finally, here is the original post of my employer:
[http://lists.samba.org/archive/samba/2008-November/144794.html](http://lists.samba.org/archive/samba/2008-November/144794.html)

Also, it is noteworthy to mention that the LDAP server already functions perfectly with other services such as OpenVPN.

Any help would be greatly appreciated.

---

### Post by HermanAB on 2009-01-05
Hmm, try the "Official Howto" on the Samba web site.  It explains everything Samba related.

Hope that helps!

Herman

---

### Post by constchar* on 2009-01-06
> **HermanAB said:**
> Hmm, try the "Official Howto" on the Samba web site.  It explains everything Samba related.

Hope that helps!

Herman

I've been all over the documentation and several how-to's trying to pin-point the problem.
I encounter this problem whenever I try to use smbpasswd as well:

```

smbpasswd -e james.kelly
pdb_set_user_sid_from_string: -3032 isn't a valid SID!
init_sam_from_ldap: no sambaSID or sambaSID attribute found for this user james.kelly
ldapsam_getsampwnam: init_sam_from_ldap failed for user 'james.kelly'!
Failed to find user james.kelly in passdb backend.

```

Its obviously apparent that an invalid "sambaSID" is being assigned to the user but I do not know how it gets assigned in the first place or how to reset it to something valid.

---

### Post by nkassi on 2009-01-06
Is the proper samba schema loaded in openldap?

Samba requires the following 

include         /etc/openldap/schema/core.schema
include         /etc/openldap/schema/cosine.schema
include         /etc/openldap/schema/inetorgperson.schema
include         /etc/openldap/schema/nis.schema
include         /etc/openldap/schema/samba.schema

---

### Post by constchar* on 2009-01-06
I figured out the problem.
It all had to do with the sambaSID and after some double-checking I realized that smbldap-useradd would assign a proper SID but the same action in another tool wasn't. Turns out the other tool was not adding the the local machine's SID to the sambaSID so all I had was what appeared to be a negative number.

Thanks for the help anyway though.

---

### Post by Fireball454 on 2009-05-29
> **constchar* said:**
> I figured out the problem.
It all had to do with the sambaSID and after some double-checking I realized that smbldap-useradd would assign a proper SID but the same action in another tool wasn't. Turns out the other tool was not adding the the local machine's SID to the sambaSID so all I had was what appeared to be a negative number.

Thanks for the help anyway though.

Hey I have a similar problem but I can't find out what causes the problem...

C2N1:/usr/sbin# smbpasswd asender
New SMB password:
Retype new SMB password:
pdb_set_user_sid_from_string:  S-1-5-21-2641060762-2792719911-2107681722-3004 isn't a valid SID!
init_sam_from_ldap: no sambaSID or sambaSID attribute found for this user asender
ldapsam_getsampwnam: init_sam_from_ldap failed for user 'asender'!
Failed to find entry for user asender.
Failed to modify password entry for user asender


Can someone help me?

---

### Post by HDave on 2009-09-29
I have the same problem.  In my case, I created the users in LDAP via GOsa, an LDAP web gui.

---

