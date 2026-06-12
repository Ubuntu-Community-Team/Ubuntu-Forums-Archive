---
title: "Dovecot GSSAPI Authentication"
date: 2016-03-13
forum: Server Platforms
---

### Post by trentsch on 2016-03-13
Hello community,

i am asking for help with configuring Kerberos authentication with a Dovecot IMAP server.

This is the system configuration:


[LIST]
[*]Ubuntu Server 15.10 (fresh install) with Dovecot 2.2.18.
[*]sssd and samba (as a member server) are installed.
[*]System is joined to a samba 4 driven domain.
[*]MIT Kerberos is used - at least i suppose this is the case since ubuntu uses MIT by default and i did not explicitly install a krb5 library. Any advice on how to check if MIT or Heimdal is used is appreciated.
[/LIST]

What is working:


[LIST]
[*]kinit DOMAINUSER
[*]getent passwd DOMAINUSER, getent group DOMAINGROUP
[*]ssh login via Kerberos
[*]login to Dovecot via PLAIN (pam used as user- and passdb with sssd using kerberos to talk to the domain controller)
[*]TLS connection to dovecot server. Connections without TLS are refused.
[/LIST]

What is not working:


[LIST]
[*]User authentication using dovecot's gssapi. I want clients to not send username and password to dovecot but rather send the kerberos ticket to the server.
[*]The authentication process fails in two different ways, depending on the userdb / passdb configuration i use:
[/LIST]

[LIST=1]
[*]userdb driver = static with not other userdb and no passdb produces the following line in the log: auth: Panic: file auth-request.c: line 743 (auth_request_is_disabled_master_user): assertion failed: (request->requested_login_user != NULL)
[*]userdb driver = passwd and passdb driver = passwd (both the only dbs) produces the following:auth: Info: gssapi(Domainuser@REALM,192.168.3.140,<cbzvKektkQDAqAOM>): User not authorized to log in as Domainuser@REALM
[/LIST]

Obviously, configuration #2 is the only configuration where PLAIN auth is working.

[B]
The Logfiles
[/B]Note: I replaced the original kerberos realm, user and its domain suffix in the logs. Case sensitivity is respected by my replacements.

Case 1: auth_mechanisms = gssapi, userdb = passwd, passdb = passwd
```
Mar 13 08:32:17 auth: Debug: Loading modules from directory: /usr/lib/dovecot/modules/authMar 13 08:32:17 auth: Debug: Loading modules from directory: /usr/lib/dovecot/modules/auth
Mar 13 08:32:17 auth: Debug: Module loaded: /usr/lib/dovecot/modules/auth/libmech_gssapi.so
Mar 13 08:32:17 auth: Warning: userdb passwd: Move templates args to override_fields setting
Mar 13 08:32:17 auth: Debug: Read auth token secret from /var/run/dovecot/auth-token-secret.dat
Mar 13 08:32:17 auth: Debug: auth client connected (pid=21161)
Mar 13 08:32:17 auth: Debug: client in: AUTH    1       GSSAPI  service=imap    secured session=cbzvKektkQDAqAOM        lip=192.168.3.16        rip=192.168.3.140       lport=993       rport=62097
Mar 13 08:32:17 auth: Debug: gssapi(?,192.168.3.140,<cbzvKektkQDAqAOM>): Using all keytab entries
Mar 13 08:32:17 auth: Debug: client passdb out: CONT    1
Mar 13 08:32:17 auth: Debug: client in: CONT<hidden>
Mar 13 08:32:17 auth: Debug: gssapi(domainuser@REALM,192.168.3.140,<cbzvKektkQDAqAOM>): security context state completed.
Mar 13 08:32:17 auth: Debug: client passdb out: CONT    1       YIGVBgkqhkiG9xIBAgICAG+BhTCBgqADAgEFoQMCAQ+idjB0oAMCAReibQRrBjbawUcGnl9uLlNFmWE61TP0qhl/Y7ES04qN9pRzXFe7eUsNwLvXNlIJEOQ63zvxr6Ey6Atvbsrvsd26gz9Y7WVnLJnHuVKPYkYskFp1SP/r9up8F$
Mar 13 08:32:17 auth: Debug: client in: CONT<hidden>
Mar 13 08:32:17 auth: Debug: gssapi(domainuser@REALM,192.168.3.140,<cbzvKektkQDAqAOM>): Negotiated security layer
Mar 13 08:32:17 auth: Debug: client passdb out: CONT    1       BQQF/wAMAAAAAAAAApmL6gH///+RQgjO5tSvrtWmjFE=
Mar 13 08:32:17 auth: Debug: client in: CONT<hidden>
Mar 13 08:32:17 auth: Debug: pam(Domainuser@realm,192.168.3.140,<cbzvKektkQDAqAOM>): passdb doesn't support credential lookups
Mar 13 08:32:17 auth: Info: gssapi(Domainuser@realm,192.168.3.140,<cbzvKektkQDAqAOM>): User not authorized to log in as Domainuser@realm
Mar 13 08:32:19 auth: Debug: client passdb out: FAIL    1       user=Domainuser@realm    original_user=domainuser@REALM
Mar 13 08:32:19 imap-login: Debug: Ignoring unknown passdb extra field: original_user
Mar 13 08:32:19 imap-login: Info: Disconnected (auth failed, 1 attempts in 2 secs): user=<Domainuser@realm>, method=GSSAPI, rip=192.168.3.140, lip=192.168.3.16, TLS, session=<cbzvKektkQDAqAOM>
```


Case 2: auth_mechanisms = gssapi, userdb = static
```
Mar 13 08:42:41 auth: Debug: Loading modules from directory: /usr/lib/dovecot/modules/authMar 13 08:42:41 auth: Debug: Loading modules from directory: /usr/lib/dovecot/modules/auth
Mar 13 08:42:41 auth: Debug: Module loaded: /usr/lib/dovecot/modules/auth/libmech_gssapi.so
Mar 13 08:42:41 auth: Debug: Read auth token secret from /var/run/dovecot/auth-token-secret.dat
Mar 13 08:42:41 auth: Debug: auth client connected (pid=21749)
Mar 13 08:42:41 auth: Debug: client in: AUTH    1       GSSAPI  service=imap    secured session=ARshT+ktwgDAqAOM        lip=192.168.3.16        rip=192.168.3.140       lport=993       rport=62146
Mar 13 08:42:41 auth: Debug: gssapi(?,192.168.3.140,<ARshT+ktwgDAqAOM>): Using all keytab entries
Mar 13 08:42:41 auth: Debug: client passdb out: CONT    1
Mar 13 08:42:41 auth: Debug: client in: CONT<hidden>
Mar 13 08:42:41 auth: Debug: gssapi(domainuser@REALM,192.168.3.140,<ARshT+ktwgDAqAOM>): security context state completed.
Mar 13 08:42:41 auth: Debug: client passdb out: CONT    1       YIGVBgkqhkiG9xIBAgICAG+BhTCBgqADAgEFoQMCAQ+idjB0oAMCAReibQRrnKtC3jkA9ZfeJnO2OOcJBKOSdM+QSMak6Fcp+oi7SaDYlHx7+Mtf6OoD9lYtPDGjo5/l/8nF5+vD6jcDnvSAagBpBmuakyYa/F4BzXPN/Ogl5A4l5$
Mar 13 08:42:41 auth: Debug: client in: CONT<hidden>
Mar 13 08:42:41 auth: Debug: gssapi(domainuser@REALM,192.168.3.140,<ARshT+ktwgDAqAOM>): Negotiated security layer
Mar 13 08:42:41 auth: Debug: client passdb out: CONT    1       BQQF/wAMAAAAAAAAFDukkgH///8/EZFfyvfTWwTTagw=
Mar 13 08:42:41 auth: Debug: client in: CONT<hidden>
Mar 13 08:42:41 auth: Panic: file auth-request.c: line 743 (auth_request_is_disabled_master_user): assertion failed: (request->requested_login_user != NULL)
Mar 13 08:42:41 auth: Error: Raw backtrace: /usr/lib/dovecot/libdovecot.so.0(+0x71fe2) [0x7fbd8a484fe2] -> /usr/lib/dovecot/libdovecot.so.0(+0x720cd) [0x7fbd8a4850cd] -> /usr/lib/dovecot/libdovecot.so.0(i_fatal+0) [0x7fbd8a430fc1] -> dov$
Mar 13 08:42:42 imap-login: Warning: Auth connection closed with 1 pending requests (max 1 secs, pid=21749, EOF)
Mar 13 08:42:42 auth: Fatal: master: service(auth): child 21751 killed with signal 6 (core dumped)
Mar 13 08:42:42 imap-login: Info: Disconnected (auth process communication failure): user=<>, method=GSSAPI, rip=192.168.3.140, lip=192.168.3.16, TLS, session=<ARshT+ktwgDAqAOM>
```

Case 3 (everything working as expected, PLAIN): auth_mechanisms = plain gssapi, userdb = passwd, passdb = passwd
```
Mar 13 06:43:50 auth: Debug: Loading modules from directory: /usr/lib/dovecot/modules/authMar 13 06:43:50 auth: Debug: Loading modules from directory: /usr/lib/dovecot/modules/auth
Mar 13 06:43:50 auth: Debug: Module loaded: /usr/lib/dovecot/modules/auth/libmech_gssapi.so
Mar 13 06:43:50 auth: Warning: userdb passwd: Move templates args to override_fields setting
Mar 13 06:43:50 auth: Debug: Read auth token secret from /var/run/dovecot/auth-token-secret.dat
Mar 13 06:43:50 auth: Debug: auth client connected (pid=16434)
Mar 13 06:43:54 auth: Debug: client in: AUTH    1       PLAIN   service=imap    secured session=cUtPpuctuQDAqAOM        lip=192.168.3.16        rip=192.168.3.140       lport=993       rport=61369
Mar 13 06:43:54 auth: Debug: client passdb out: CONT    1
Mar 13 06:43:54 auth: Debug: client in: CONT<hidden>
Mar 13 06:43:54 auth-worker(16438): Debug: Loading modules from directory: /usr/lib/dovecot/modules/auth
Mar 13 06:43:54 auth-worker(16438): Debug: Loading modules from directory: /usr/lib/dovecot/modules/auth
Mar 13 06:43:54 auth-worker(16438): Debug: Module loaded: /usr/lib/dovecot/modules/auth/libmech_gssapi.so
Mar 13 06:43:54 auth-worker(16438): Warning: userdb passwd: Move templates args to override_fields setting
Mar 13 06:43:54 auth-worker(16438): Debug: pam(Domainuser@realm,192.168.3.140): lookup service=dovecot
Mar 13 06:43:54 auth-worker(16438): Debug: pam(Domainuser@realm,192.168.3.140): #1/1 style=1 msg=Password:
Mar 13 06:43:55 auth: Debug: client passdb out: OK      1       user=Domainuser@realm
Mar 13 06:43:55 auth: Debug: master in: REQUEST 1562247169      16434   1       521a8501f17769e25bd225579a527c72        session_pid=16446       request_auth_token
Mar 13 06:43:55 auth: Debug: passwd(Domainuser@realm,192.168.3.140,<cUtPpuctuQDAqAOM>): lookup
Mar 13 06:43:55 auth: Debug: passwd(Domainuser@realm,192.168.3.140,<cUtPpuctuQDAqAOM>): username changed Domainuser@realm -> domainuser
Mar 13 06:43:55 auth: Debug: master userdb out: USER    1562247169      domainuser    quota_rule=*:storage=1G system_groups_user=domainuser uid=710601125   gid=710600513   home=/home/domainuser username_format=domainuser    auth_token=80d25a31455b26cab98fc8421e$
Mar 13 06:43:55 imap-login: Info: Login: user=<Domainuser@realm>, method=PLAIN, rip=192.168.3.140, lip=192.168.3.16, mpid=16446, TLS, session=<cUtPpuctuQDAqAOM>
```


**The config files**

dovecot -n
```
# 2.2.18: /etc/dovecot/dovecot.conf
# Pigeonhole version 0.4.8 (0c4ae064f307+)
# OS: Linux 4.2.0-30-generic x86_64 Ubuntu 15.10 ext4
auth_debug = yes
auth_default_realm = REALM
auth_gssapi_hostname = $ALL
auth_krb5_keytab = /etc/dovecot/imap.keytab
auth_mechanisms = gssapi
auth_realms = REALM realm
auth_username_format = %u
auth_verbose = yes
auth_worker_max_count = 5
default_client_limit = 50
default_process_limit = 10
default_vsz_limit = 128 M
disable_plaintext_auth = no
listen = *
log_path = /var/log/dovecot.log
login_greeting = Servus
mail_location = maildir:/var/mail/%u
namespace inbox {
  inbox = yes
  location = 
  mailbox Drafts {
    special_use = \Drafts
  }
  mailbox Junk {
    special_use = \Junk
  }
  mailbox Sent {
    special_use = \Sent
  }
  mailbox "Sent Messages" {
    special_use = \Sent
  }
  mailbox Trash {
    special_use = \Trash
  }
  prefix = 
}
passdb {
  args = session=yes failure_show_msg=yes max_requests=10 dovecot
  driver = pam
}
protocols = " imap"
service auth-worker {
  user = root
}
service imap-login {
  inet_listener imaps {
    port = 993
    ssl = yes
  }
  process_min_avail = 0
  service_count = 1
}
service imap {
  process_limit = 128
}
ssl_cert = </etc/dovecot/certificate.pem
ssl_dh_parameters_length = 2048
ssl_key = </etc/dovecot/private/certificate.key
ssl_prefer_server_ciphers = yes
userdb {
  args = blocking=no username_format=%n
  default_fields = quota_rule=*:storage=1G
  driver = passwd
  override_fields = home=/home/%u
}
userdb {
  driver = passwd
}
# In case 2) the following is the only userdb, passdb is not used.
#userdb {
#  driver = static
#  args = uid=dovecot gid=mailusers home=/home/%u
#}
```


krb5.conf
```
[libdefaults]
        default_realm = REALM
        rdns = false
        dns_lookup_kdc = true
        dns_lookup_realm = false
# The following krb5.conf variables are only for MIT Kerberos.
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true


# The following libdefaults parameters are only for Heimdal Kerberos.
        v4_instance_resolve = false
        v4_name_convert = {
                host = {
                        rcmd = host
                        ftp = ftp
                }
                plain = {
                        something = something-else
                }
        }
        fcc-mit-ticketflags = true


[realms]
        REALM = {
                kdc = kdc1.realm
                kdc = kdc2.realm
                admin_server = kdc1.realm
                default_domain = realm
        }


[domain_realm]
        .realm = REALM
        realm = REALM
[login]
        krb4_convert = true
        krb4_get_tickets = false
```

Note: /etc/dovecot/imap.keytab contains imap/fqdn@REALM, /etc/krb5.keytab contains host/fqdn@REALM


sssd.conf
```
[sssd]
services = nss, pam
config_file_version = 2
domains = realm
# 3 Logs error from critical to minor
debug_level = 3


[nss]


[pam]


[domain/int.rentsch.bayern]
id_provider = ad
access_provider = ad
auth_provider = ad
override_homedir = /home/%u
ldap_id_mapping = true
```


/etc/pam.d/dovecot
```
#%PAM-1.0


auth required pam_sss.so


account required pam_sss.so


#@include common-auth
#@include common-account
@include common-session
```


The goal is to allow authentication using gssapi and plain simultaneously for the same users. Users inside the private network should be able to login using kerberos (and thus benefit from SSO), users outside the network should be able to login using plain.
If using userdb and passdb driver = passwd (so pam is used) it seams to me that dovecot cannot verify the kerberos user is contained in the userdb. But using userdb = static should allow all users that succeeded with gssapi to authenticate, shouldn't it? :confused: I am completly stuck with this topic since weeks. :( Hopefully i am missing something obvious.

Any help is greatly appreciated. Thank you!

---

### Post by trentsch on 2016-03-14
Answering my own Question in case someone else encounters the same problem:

The above configuration is correct. The solution is unbelievably simple: The E-Mail client must use lowercase username (and lowercase realm extension, if specified). Thus specifying "user" or "user@realm" is working, whereas "User" or "User@REALM" or even "user@REALM" is not. Note that the setting ```
auth_username_format = %u
``` actually does not matter. I've tried %u, %Lu, %n, %Ln. It doesn't seem to affect gssapi authentication at all. PAM (for using PLAIN auth) does seem to cope with different settings very well (at least with my setup). Another good news is that the static userdb not needed. passwd (pam) as userdb does work perfectly for gssapi auth.

---

