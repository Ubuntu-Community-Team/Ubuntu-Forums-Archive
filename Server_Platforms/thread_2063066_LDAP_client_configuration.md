---
title: "LDAP client configuration"
date: 2012-09-26
forum: Server Platforms
---

### Post by eaman on 2012-09-26
I'm trying to configure a 12.04 lab with users on a LDAP server (now the clients are Karmic) and I'd like to get some light on some configuration files.

1. /etc/ldap.conf and /etc/ldap/ldap.conf
Why two files? Can I use just one?

2. /etc/libnss-ldap.conf
This one is now missing, but still I could use to declare "scope sub
bind_policy soft" . Where should I put theese?

---

### Post by eaman on 2012-09-29
Well that's what I've chosen to do  in case some one is wondering the same thing:
I keep just /etc/ldap/ldap.conf with a symbolic link as /etc/ldap.conf 'couse nscd now looks there for its things.

So now /etc/ldap/ldap.conf holds info for scope and bind_policy as well.
```

        BASE    dc=mydc
        HOST    my.very.host.tld
        URI     ldaps://my.very.host.tld
        TLS_REQCERT allow

        SIZELIMIT       12
        TIMELIMIT       15

        # TLS certificates (needed for GnuTLS)
        TLS_CACERT      /etc/ssl/certs/ca-certificates.crt 

        scope sub
        bind_policy soft
```

---

### Post by luvshines on 2012-09-30
> **eaman said:**
> 
1. /etc/ldap.conf and /etc/ldap/ldap.conf
Why two files? Can I use just one?

The /etc/ldap.conf will be the one libnss-ldap, and PAM too I think unless there is a separate /etc/pam_ldap.conf, will be referring to. The man page for this will be nss_ldap.
If your clients login with LDAP usernames/passwords then this file will give LDAP details

/etc/ldap/ldap.conf will be the one which openLDAP client commands like 'ldapsearch', 'ldapmodify', 'ldapdelete' will be referring to. If your clients issue these commands then this file will give LDAP details. You may skip this file config if you don't plan to run those commands
> 

2. /etc/libnss-ldap.conf
This one is now missing, but still I could use to declare "scope sub
bind_policy soft" . Where should I put theese?
As I said, use /etd/ldap.conf to put these

The reason why it works by creating a link of those 2 files and putting everything at one place is that the basic options like BASE,URI etc are common

---

### Post by eaman on 2012-09-30
I do confirm what Luvshines writes regarding the three files and what uses them.
As a side note I could add the Debian dosn't use /etc/ldap.conf (but Ubuntu need this).
In the next days I will deploy the OSes on some labs and I'll see if the system (PAM + NSCD + LDAP) works as expected.

As this is free - public founded project I wrote (in Italian) a short guide to implement 12.04 with my auth system for the incoming Linux Day:
- [http://garage.andreamanni.com/garage/doc/html/client_ldap_ubuntu_12.04_pangolin.html](http://garage.andreamanni.com/garage/doc/html/client_ldap_ubuntu_12.04_pangolin.html)

If there's any interest I could try to translate it in english.

---

