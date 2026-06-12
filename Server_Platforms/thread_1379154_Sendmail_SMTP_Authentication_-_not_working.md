---
title: "Sendmail SMTP Authentication - not working"
date: 2010-01-12
forum: Server Platforms
---

### Post by trawler on 2010-01-12
We're setting up a testing environment for a software with a built-in email client. The client does not support TLS, so we need to set up sendmail to require SMTP authentication, based on openLDAP.
We used for this purpose Ubuntu server 8.04.

So far, LDAP is set up correctly, so that even the pop3 server is able to authenticate with it. I also set up Cyrus-SASL to authenticate against LDAP successfully.
I used every tutorial and help guide I could find to get Sendmail to authenticate the users, but so far it's still possible to send emails with this server, unauthenticated.

**Output of testsaslauthd:**
```
root@myserver:~# testsaslauthd -u user1 -p password1
[COLOR="Red"]0: OK "Success."[/COLOR]
```

**/etc/saslauthd.conf:**
```
ldap_servers: ldap://localhost/
ldap_bind_dn: cn=admin, dc=mydomain, dc=com
ldap_bind_pw: password
ldap_version: 3
ldap_search_base: dc=mydomain, dc=com
ldap_verbose: on
ldap_debug: 3
```

**/etc/mail/sendmail.mc:**
```
divert(-1)dnl
define(`_USE_ETC_MAIL_')dnl
include(`/usr/share/sendmail/cf/m4/cf.m4')dnl
VERSIONID(`$Id: sendmail.mc, v 8.14.2-2build1 2008-01-24 14:29:57 cowboy Exp $')
OSTYPE(`debian')dnl
DOMAIN(`debian-mta')dnl
undefine(`confHOST_STATUS_DIRECTORY')dnl        #DAEMON_HOSTSTATS=
FEATURE(`no_default_msa')dnl
DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=0.0.0.0')dnl
DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, Addr=0.0.0.0')dnl
define(`confPRIVACY_FLAGS',dnl
`needmailhelo,needexpnhelo,needvrfyhelo,restrictqrun,restrictexpand,nobodyreturn,authwarnings')dnl
define(`confCONNECTION_RATE_THROTTLE', `1500')dnl
define(`confCONNECTION_RATE_WINDOW_SIZE',`100m')dnl
FEATURE(`use_cw_file')dnl
[COLOR="Red"]FEATURE(promiscuous_relay)dnl[/COLOR]
FEATURE(`access_db', , `skip')dnl
FEATURE(`greet_pause', `1000')dnl 1 seconds
FEATURE(`delay_checks', `friend', `n')dnl
FEATURE(`conncontrol', `nodelay', `terminate')dnl
FEATURE(`ratecontrol', `nodelay', `terminate')dnl
[COLOR="Red"]TRUST_AUTH_MECH(`LOGIN PLAIN')dnl
define(`confAUTH_MECHANISMS', `LOGIN PLAIN')dnl[/COLOR]
include(`/etc/mail/m4/dialup.m4')dnl
include(`/etc/mail/m4/provider.m4')dnl
FEATURE(local_procmail)dnl
MAILER_DEFINITIONS
MAILER(`local')dnl
MAILER(`smtp')dnl
define(`sm_enable_tls', `no')dnl
```

As you can see, we've opened up this server to be an open relay mailer, since it is a closed environment and we didn't initially want to bother with it.

I've tried many many options to get Sendmail to require authentication, but so far none worked. Most of the howto's I found, however, required TLS for the authentication to work, and as I mentioned above, we need the authentication process to be un-encrypted.

Any idea what could be wrong with this configuration?
Your help is appreciated.

---

