---
title: "OpenLDAP + Dovecot login issues (on 11.04)"
date: 2011-08-09
forum: Server Platforms
---

### Post by 0x01 on 2011-08-09
(repost from general area as it was probably the wrong place for it.)

Morning all,  I've managed to work my self into a corner and hoping someone can help me
out

I have OpenLDAP and Dovecot installed based on the following documents.
 
[LIST]
[*][DovecotLDAP]("https://help.ubuntu.com/community/DovecotLDAP")
[*][OpenLDAPServer]("https://help.ubuntu.com/community/OpenLDAPServer") (using RTC)
[/LIST]
 When Dovecot is set up to log in with out using LDAP connections work fine.  However as
soon as I change the dovecot.conf to use ldap I get the following error when trying to log 
in:

```

dovecot: auth(default): ldap(myuser,10.10.10.10): [COLOR=Red]invalid credentials (given password: myuserpasswd)[/COLOR]
dovecot: auth(default): client out: FAIL#0112#011user=myuser

```I have checked via phpLDAPadmin that the password I am entering matches what is in the
LDAP database, so from what I can the issue lies in how Dovecot is passing the password to openLDAP.


Is anyone able to shed some light on what may be going wrong?




*Server Setup and Dovecot Config*

Ubuntu Server 11.04

```
# uname -a
Linux base 2.6.38-10-server #46-Ubuntu SMP Tue Jun 28 16:31:00 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

```

# slapd -V
@(#) $OpenLDAP: slapd 2.4.23 (Apr  7 2011 18:00:55) $
```

```
# dovecot --version
1.2.15
```

Dovecot.conf
```
base_dir = /var/run/dovecot/
protocols = imaps imap
listen = *
disable_plaintext_auth = no
shutdown_clients = yes
log_timestamp = "%Y-%m-%d %H:%M:%S "
###ssl_disable = no
ssl_cert_file = /etc/ssl/private/mail_mydomain_com.crt
ssl_key_file = /etc/ssl/private/mail_mydomain_com.key
ssl_ca_file = /etc/ssl/private/ca-bundle.crt
mail_location = maildir:/home/MAIL/%n
mail_privileged_group = mail
mail_debug = yes
protocol imap {
###  login_greeting_capability = yes
  imap_client_workarounds = tb-extra-mailbox-sep
}
protocol lda {
  postmaster_address = postmaster@mydomain.com
  hostname = base
  auth_socket_path = /var/run/dovecot/auth-master
  mail_plugins = cmusieve
}
auth_verbose = no
auth_debug = yes
auth_debug_passwords = yes
auth default {
  mechanisms = plain
  passdb ldap {
    args = /etc/dovecot/dovecot-ldap.conf
  }
#  passdb passwd-file {
#     args = /etc/dovecot/passwd
#  }
  userdb static {
    args = uid=vmail gid=vmail home=/home/MAIL/%n allow_all_users=yes
  }
  user = vmail
  socket listen {
     master {
            path = /var/run/dovecot/auth-master
       mode = 0600
       user = vmail # User running Dovecot LDA
       group = vmail # Or alternatively mode 0660 + LDA user in this group
     }
  }
}
dict {
}
plugin {
}
```

dovecot-ldap.conf (with a number of commented out lines removed

```

# Space separated list of LDAP hosts to use. host:port is allowed too.
hosts= localhost

# Distinguished Name - the username used to login to the LDAP server
dn= cn=admin,dc=mydomain

# Password for LDAP server
dnpass = alongpasswd

auth_bind = yes

auth_bind_userdn = uid=%u,ou=Users,dc=mydomain

# LDAP protocol version to use. Likely 2 or 3.
ldap_version = 3

# LDAP base. %variables can be used here.
base = ou=Users,dc=mydomain

# Dereference: never, searching, finding, always
deref = never

# Search scope: base, onelevel, subtree
scope = subtree

user_attrs = mail=uid

user_filter = (&(objectClass=posixAccount)(uid=%n))

# Password checking attributes:
pass_attrs = uid=user,userPassword=password
###,homeDirectory=userdb_home,uidNumber=userdb_uid,gidNumber=userdb_gid

# Filter for password lookups
pass_filter = (&(objectClass=posixAccount)(uid=%n))

# Default password scheme. "{scheme}" before password overrides this.
# List of supported schemes is in: http://wiki.dovecot.org/Authentication
default_pass_scheme = MD5

```

---

