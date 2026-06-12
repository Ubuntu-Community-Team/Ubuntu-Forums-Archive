---
title: "mod_ldap or mod_authnz_ldap hangs when connecting to ldap server"
date: 2008-09-24
forum: Server Platforms
---

### Post by MikeBenza on 2008-09-24
Hey everyone,

I've an apache2 server running on Hardy.  I've a <Location> in a certain site that needs to be ldap authenticated.  It doesn't get authenticated.  Here is the location:

```

<Location /blah>
  AuthzLDAPAuthoritative Off
  AuthName "EWB Documents"
  AuthType Basic
  AuthBasicProvider ldap
  AuthLDAPBindDN "cn=ewb,ou=Service Accounts,dc=rice,dc=edu"
  AuthLDAPBindPassword *********
  AuthLDAPURL "ldaps://ldap.rice.edu:636/ou=People,dc=rice,dc=edu?uid"

  <Limit GET POST PROPFIND OPTIONS REPORT>
     Require valid-user
  </Limit>
</Location>

```When I browse to [http://site/blah](http://site/blah), I get prompted for my username and password.  I've confirmed that this <Location> configuration is causing that, since when I remove the <Location>, I don't get prompted for a username and password.  After I type my username and password in and click OK, nothing happens on the browser side.  I can watch my browser send my credentials back the server, and I can see the beginning of an LDAP conversation using wireshark on the server.  However, after the conversation begins, it abruptly stops, and nothing happens.  It just sits there.

I tested logging into the LDAP with a variation of the following (using a hostname and port, but I don't remember the format and switches now):
```
ldapsearch -x -W -D "cn=ewb,ou=service accounts,dc=rice,dc=edu" -b "ou=People,dc=rice,dc=edu" '(uid=XYZ)'
```
It prompts me for my password (the ***s in the above apache configuration), then finds the user named XYZ.

So, in summary I can connect via ldaps and lookup a user at the command line, but somewhere, apache fails.

I turned logging in apache to debug, and discovered that ldap doesn't log much:
```

[Wed Sep 17 20:07:10 2008] [error] (2)No such file or directory: mod_mime_magic: can't read magic file /etc/apache2/conf/magic
[Wed Sep 17 20:07:10 2008] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Wed Sep 17 20:07:10 2008] [info] Init: Seeding PRNG with 256 bytes of entropy
[Wed Sep 17 20:07:10 2008] [info] Init: Generating temporary RSA private keys (512/1024 bits)
[Wed Sep 17 20:07:10 2008] [info] Init: Generating temporary DH parameters (512/1024 bits)
[Wed Sep 17 20:07:10 2008] [info] Init: Initializing (virtual) servers for SSL
[Wed Sep 17 20:07:10 2008] [info] mod_ssl/2.2.8 compiled against Server: Apache/2.2.8, Library: OpenSSL/0.9.8g
[Wed Sep 17 20:07:10 2008] [error] (2)No such file or directory: mod_mime_magic: can't read magic file /etc/apache2/conf/magic
[Wed Sep 17 20:07:10 2008] [notice] Digest: generating secret for digest authentication ...
[Wed Sep 17 20:07:10 2008] [notice] Digest: done
[Wed Sep 17 20:07:10 2008] [debug] util_ldap.c(1977): LDAP merging Shared Cache conf: shm=0x80f2188 rmm=0x80f21b8 for VHOST: ewb.rice.edu
[Wed Sep 17 20:07:10 2008] [debug] util_ldap.c(1977): LDAP merging Shared Cache conf: shm=0x80f2188 rmm=0x80f21b8 for VHOST: wiki.ewb.rice.edu
[Wed Sep 17 20:07:10 2008] [debug] util_ldap.c(1977): LDAP merging Shared Cache conf: shm=0x80f2188 rmm=0x80f21b8 for VHOST: ewb.rice.edu
[Wed Sep 17 20:07:10 2008] [info] APR LDAP: Built with OpenLDAP LDAP SDK
[Wed Sep 17 20:07:10 2008] [info] LDAP: SSL support available
[Wed Sep 17 20:07:10 2008] [info] Init: Seeding PRNG with 256 bytes of entropy
[Wed Sep 17 20:07:10 2008] [info] Init: Generating temporary RSA private keys (512/1024 bits)
[Wed Sep 17 20:07:10 2008] [info] Init: Generating temporary DH parameters (512/1024 bits)
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(374): shmcb_init allocated 512000 bytes of shared memory
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(554): entered shmcb_init_memory()
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(576): for 512000 bytes, recommending 4266 indexes
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(619): shmcb_init_memory choices follow
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(621): division_mask = 0x1F
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(623): division_offset = 64
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(625): division_size = 15998
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(627): queue_size = 1604
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(629): index_num = 133
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(631): index_offset = 8
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(633): index_size = 12
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(635): cache_data_offset = 8
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(637): cache_data_size = 14386
[Wed Sep 17 20:07:10 2008] [debug] ssl_scache_shmcb.c(650): leaving shmcb_init_memory()
[Wed Sep 17 20:07:10 2008] [info] Shared memory session cache initialised
[Wed Sep 17 20:07:10 2008] [info] Init: Initializing (virtual) servers for SSL
[Wed Sep 17 20:07:10 2008] [info] mod_ssl/2.2.8 compiled against Server: Apache/2.2.8, Library: OpenSSL/0.9.8g
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1670): proxy: grabbed scoreboard slot 0 in child 24788 for worker proxy:reverse
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1778): proxy: initialized single connection worker 0 in child 24788 for (*)
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1670): proxy: grabbed scoreboard slot 0 in child 24789 for worker proxy:reverse
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1689): proxy: worker proxy:reverse already initialized
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1778): proxy: initialized single connection worker 0 in child 24789 for (*)
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1670): proxy: grabbed scoreboard slot 0 in child 24790 for worker proxy:reverse
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1689): proxy: worker proxy:reverse already initialized
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1778): proxy: initialized single connection worker 0 in child 24790 for (*)
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1670): proxy: grabbed scoreboard slot 0 in child 24791 for worker proxy:reverse
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1689): proxy: worker proxy:reverse already initialized
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1778): proxy: initialized single connection worker 0 in child 24791 for (*)
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1670): proxy: grabbed scoreboard slot 0 in child 24792 for worker proxy:reverse
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1689): proxy: worker proxy:reverse already initialized
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1778): proxy: initialized single connection worker 0 in child 24792 for (*)
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1670): proxy: grabbed scoreboard slot 0 in child 24793 for worker proxy:reverse
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1689): proxy: worker proxy:reverse already initialized
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1778): proxy: initialized single connection worker 0 in child 24793 for (*)
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1670): proxy: grabbed scoreboard slot 0 in child 24794 for worker proxy:reverse
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1689): proxy: worker proxy:reverse already initialized
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1778): proxy: initialized single connection worker 0 in child 24794 for (*)
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1670): proxy: grabbed scoreboard slot 0 in child 24795 for worker proxy:reverse
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1689): proxy: worker proxy:reverse already initialized
[Wed Sep 17 20:07:10 2008] [debug] proxy_util.c(1778): proxy: initialized single connection worker 0 in child 24795 for (*)
[Wed Sep 17 20:07:10 2008] [notice] Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g mod_perl/2.0.3 Perl/v5.8.8 configu
red -- resuming normal operations

```Nothing is logged in the error log when I try to load the page requiring my username and password.

Has anyone had problems like this?  Please help me.  I can't find anyone who knows enough about apache and ldap.  I've been working at this for days now.  Thank you.

- Mike Benza

---

### Post by Joeb454 on 2008-10-06
Moved to Server Platforms

---

### Post by lykwydchykyn on 2008-10-06
I have messed with this some, and have some intranet sites at work that authenticate against our ldap (eDirectory).  It took a lot of fiddling, and I believe what I ended up doing is checking to see that the user logging in was a member of a group.  It didn't work to just check against the user's existence.  It was pretty brittle altogether, and took me a while to get the magic combination of directives that worked.

When I can get to my stuff (I'm off today and my remote access is down for some reason) I'll post what I did and maybe it will help you.

---

