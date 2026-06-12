---
title: "Why does ssh ignore 'default_ccache_name'"
date: 2016-10-18
forum: Server Platforms
---

### Post by macduke on 2016-10-18
I got a problem with ssh and forwarded kerberos tickets. When I login the first time, without a ticket, the system asked for my password and I get a kerberos ticket. The "KEYRING ticket cache" is uses from the variable "default_ccache_name" of "/etc/krb5.conf".  

```
    doejo@mybox:~$ klist 
    Ticket cache: KEYRING:persistent:10001:krb_ccache_qZOkiaw 
    Default principal: doejo@EXAMPLE.LOCAL 
 
    Valid starting       Expires              Service principal 
    18.10.2016 18:48:11  19.10.2016 18:47:56  host/mybox.example.local@EXAMPLE.LOCAL 
            renew until 28.10.2016 18:47:56 
    18.10.2016 18:47:56  19.10.2016 18:47:56  krbtgt/EXAMPLE.LOCAL@EXAMPLE.LOCAL 
            renew until 28.10.2016 18:47:56 
```
 
When I now connect to another (or the same host) with ssh the KRB5CCNAME environment variable get changed and I end up with a file based ticket cache. 
 
```
    doejo@mybox:~$ ssh -K doejo@mysecbox -p 2222 
    Last login: Tue Oct 18 18:48:05 2016 from 10.0.0.23 
    debug1: Setting KRB5CCNAME to FILE:/tmp/krb5cc_10001_oDUjjkPclI 
    debug3: Copy environment: KRB5CCNAME=FILE:/tmp/krb5cc_10001_oDUjjkPclI 
    Environment: 
      KRB5CCNAME=FILE:/tmp/krb5cc_10001_oDUjjkPclI 
      LANG=de_DE.UTF-8 
      USER=doejo 
      LOGNAME=doejo 
      HOME=/home/doejo 
      PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games 
      MAIL=/var/mail/doejo 
      SHELL=/bin/bash 
      SSH_CLIENT=10.0.0.23 53986 2222 
      SSH_CONNECTION=10.0.0.23 53986 10.0.0.97 2222 
      SSH_TTY=/dev/pts/1 
      TERM=xterm 

    doejo@mysecbox:~$ klist 
    Ticket cache: FILE:/tmp/krb5cc_10001_oDUjjkPclI 
    Default principal: doejo@EXAMPLE.LOCAL 
 
    Valid starting     Expires            Service principal 
    10/18/16 18:49:44  10/19/16 18:47:56  krbtgt/EXAMPLE.LOCAL@EXAMPLE.LOCAL 
            renew until 10/28/16 18:47:56 
    doejo@mysecbox:~$ 
```
 
I don&#8217;t know why or what is changing the KRB5CCNAME variable to the default? Maybe anyone can give me a hint.  

My /etc/krb5.conf file:
```
 
[libdefaults] 
  default_realm = EXAMPLE.LOCAL 
  default_ccache_name = KEYRING:persistent:%{uid} 
  default_keytab_name = FILE:/etc/krb5.keytab 
  allow_weak_crypto = false 
  # Do not set this unless required 
  #default_tkt_enctypes = aes256-cts-hmac-sha1-96 
  #default_tgs_enctypes = aes256-cts-hmac-sha1-96 
  # rc4-hmac is needed for samba / Windows 
  permitted_enctypes = aes256-cts-hmac-sha1-96 
  kdc_timesync = 1 
  ccache_type = 4 
  clockskew = 300 
  forwardable = true 
  proxiable = true 
  ticket_lifetime = 1d 0h 0m 0s 
  renew_lifetime = 7d 0h 0m 0s 
  dns_canonicalize_hostname = true 
  dns_lookup_kdc = true 
  dns_lookup_realm = false 
  rdns = true 
  canonicalize = true 
  ccache_type = 4 
  clockskew = 3 
  noaddresses = true 
 
[realms] 
  EXAMPLE.LOCAL = { 
    kdc = mybox.example.local 
    kdc = mysecbox.example.local 
    admin_server = mybox.example.local 
    kpasswd_server = mybox.example.local 
  } 
 
[domain_realm] 
  .example.local = EXAMPLE.LOCAL 
  example.local = EXAMPLE.LOCAL 
 
[login] 
  krb5_get_tickets = true 
  krb4_convert = false 
  krb4_get_tickets = false 

```

---

