---
title: "ldap_sasl_interactive_bind_s: GSSAPI Error: An invalid name was supplied"
date: 2015-02-16
forum: Security
---

### Post by peridian on 2015-02-16
Hi, (Ubuntu 14.04, krb5)

Why do I get "An invalid name was supplied" from GSSAPI when performing ldapsearch?  What have I not setup correctly?  (configs below)

Also, does the saslauthd daemon have to be running on the local machine for this to work?  When mine installed it gave an error and said I have to set "START=yes" in the /etc/default script.

Checklist

[LIST]
[*]openldap is installed and working correctly.  Tested using ldapsearch (both local and remote) on both ldaps and ldap+starttls using a binddn.
[*]kerberos is installed and working correctly.  Tested using kinit/kadmin (both local and remote) using principals created in kadmin.local.
[*]krb5.keytab file correctly populated on client machine.
[*]Can bind kerberos attributes to existing LDAP Posix users when creating principals.
[*]sasl2 + GSSAPI modules installed.
[*]Have inspected the debugging output from ldapsearch -d 255; can see the ldap/fqdn@DOMAIN user is being used in the exchange.
[/LIST]

Here's what happens:

```

user@hostname:/$ sudo klist -k
Keytab name: FILE:/etc/krb5.keytab
KVNO Principal
---- --------------------------------------------------------------------------
   2 host/hostname@DOMAIN
   2 ldap/hostname@DOMAIN
   2 host/fqdn@DOMAIN
   2 ldap/fqdn@DOMAIN


user@hostname:/$ sudo klist -f
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: user@DOMAIN


Valid starting     Expires            Service principal
16/02/15 16:53:45  17/02/15 04:53:45  krbtgt/DOMAIN@DOMAIN
    renew until 17/02/15 16:53:45, Flags: PRI
16/02/15 16:55:35  17/02/15 04:53:45  ldap/fqdn@DOMAIN
    renew until 17/02/15 16:53:45, Flags: PRT


user@hostname:/$ sudo ldapsearch -LLL -H ldaps://fqdn:636/ -s sub "(objectclass=*)"
SASL/GSSAPI authentication started
ldap_sasl_interactive_bind_s: Other (e.g., implementation specific) error (80)
    additional info: SASL(-1): generic failure: GSSAPI Error: An invalid name was supplied (Permission denied)

```

Some debugging shows:

```

ldap_sasl_interactive_bind: server supports: GS2-IAKERB GS2-KRB5 SCRAM-SHA-1 GSSAPI DIGEST-MD5 NTLM CRAM-MD5 LOGIN PLAIN
ldap_int_sasl_bind: GS2-IAKERB GS2-KRB5 SCRAM-SHA-1 GSSAPI DIGEST-MD5 NTLM CRAM-MD5 LOGIN PLAIN
ldap_int_sasl_open: host=hostname.domain
SASL/GSSAPI authentication started
ldap_sasl_bind

```

/etc/ldap/ldap.conf

```

URI ldaps://fqdn/
PORT 636
BASE dc=hostnam,dc=domain
TLS_CACERT /usr/share/ca-certificates/extra/cacert.crt
TLS_REQCERT demand

```

/etc/krb5kdc/kdc.conf

```

[kdcdefaults]
        kdc_ports = 88


[realms]
DOMAIN = {
        kadmind_port = 1088
        max_life = 12h 0m 0s
        max_renewable_life = 2d 0h 0m 0s
        supported_enctypes = aes256-cts-hmac-sha1-96:normal
}


[logging]
        kdc = FILE:/var/log/krb5kdc/kdc.log
        admin_server = FILE:/var/log/krb5kdc/kadmin.log


[dbdefaults]
        ldap_kerberos_container_dn = cn=Kerberos,dc=hostname,dc=domain


[dbmodules]
DOMAIN = {
        db_library = kldap
        disable_last_success = true
        ldap_kdc_dn = "cn=kerberos,ou=Admins,dc=hostname,dc=domain"
        ldap_kadmind_dn = "cn=kerberos,ou=Admins,dc=hostname,dc=domain"
        ldap_service_password_file = /etc/krb5kdc/bind.key
        ldap_servers = ldaps://fqdn/
        ldap_conns_per_server = 2
}

```

/etc/krb5.conf

```

[libdefaults]
        default_realm = DOMAIN


[realms]
DOMAIN = {
        admin_server = fqdn:1088
        default_domain = DOMAIN
        kdc = fqdn
}


[domain_realm]
        domain = DOMAIN
        .domain = DOMAIN

```

This all started because I was trying to hook up nslcd service to Kerberos/LDAP setup, but although the nslcd service starts without a problem, whenever it tries to access the entities (e.g. getent), it gave errors similar to this one.

/etc/nslcd.conf

```

uid nslcd
gid nslcd
uri ldap://fqdn/
base dc=hostname,dc=domain
ssl start_tls
tls_reqcert demand
tls_cacertfile /usr/share/ca-certificates/extra/cacert.crt
sasl_mech GSSAPI
krb5_ccname FILE:/tmp/host.tkt

```


/etc/nsswitch.conf

```

passwd:         compat ldap
group:          compat ldap
shadow:         compat ldap


hosts:          files dns
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis

```

Any help would be appreciated.

Regards,
Rob.

---

### Post by peridian on 2015-02-17
> **peridian said:**
> Hi, (Ubuntu 14.04, krb5)
Also, does the saslauthd daemon have to be running on the local machine for this to work?  When mine installed it gave an error and said I have to set "START=yes" in the /etc/default script.


Indeed it does, so I have configured and started this service.  It also appears I missed some steps in setting up openldap to work with SASL, namely the olcSasl* attributes, and pointing explicitly at the keytab with the ldap/fqdn@DOMAIN ticket in.

Despite all my attempts however, I am still getting the same error.  I have realised that the problem appears to be "Permission Denied" which makes me think it is not managing to map my Kerberos credentials to a valid LDAP user.

However, I get the exact same error if I run a simple "ldapwhoami" command.

Regards,
Rob.

LDIF changes to cn=config:

```

olcAuthzRegexp: {0}uid=(.*),cn=domain,cn=gssapi,cn=auth cn=$1,ou=Users,dc=hostname,dc=domain
olcAuthzRegexp: {1}uid=(.*),cn=DOMAIN,cn=gssapi,cn=auth cn=$1,ou=Users,dc=hostname,dc=domain
olcAuthzRegexp: {2}uid=(.*),cn=gssapi,cn=auth cn=$1,ou=Users,dc=hostname,dc=domain
olcSaslHost:: {encrypted}hostname.domain
olcSaslRealm: DOMAIN

```

/etc/default/saslauthd

```

START=yes
DESC="SASL Authentication Daemon"
NAME="saslauthd"
MECHANISMS="kerberos5"
MECH_OPTIONS=""
THREADS=5
OPTIONS="-c -m /var/run/saslauthd"

```

Added to /etc/default/slapd:

```

export KRB5_KTNAME=/etc/ldap/ldap.keytab

```

Added to /etc/ldap/ldap.conf:

```

SASL_MECH GSSAPI

```

---

### Post by peridian on 2015-02-22
The exodus continues, I seem to be banging my head against a wall.

I discovered that I was missing a file at /etc/ldap/sasl2/slapd.conf (see below).  I deliberately changed the pwcheck_method to saslauthd, since I have been successful in configuring that service.  I can successfully use the testsaslauthd and sasl-sample-{client|server} tests with Kerberos, so I'm still happy that krb5 and saslauthd are correct.

```

mech_list: gssapi
keytab: /etc/ldap/ldap.keytab
pwcheck_method: saslauthd

```

I also double checked LDAPs support mechanisms:

```

user@hostname:~$ sudo ldapsearch -x -D "cn=admin,cn=config" -W -b "" -s base supportedSASLMechanisms
Enter LDAP Password: 
# extended LDIF
#
# LDAPv3
# base <> with scope baseObject
# filter: (objectclass=*)
# requesting: supportedSASLMechanisms 
#


#
dn:
supportedSASLMechanisms: GSSAPI


# search result
search: 2
result: 0 Success


# numResponses: 2
# numEntries: 1

```


One thing I have discovered is there is a difference between running the command with sudo, and without it.  This is not unexpected, as sudo changes your user principal, and if I am reading the below correctly, the difference is to do with whether the executable can access local resources or not.

What's interesting is that both errors state "Permission Denied"

With sudo:

```

user@hostname:/$ sudo kinit -p user
Password for user@DOMAIN: 


user@hostname:/$ sudo klist -f
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: user@DOMAIN


Valid starting     Expires            Service principal
22/02/15 15:17:23  23/02/15 03:17:23  krbtgt/DOMAIN@DOMAIN
    renew until 23/02/15 15:17:23, Flags: PRI


user@hostname:/$ sudo ldapwhoami -d 165
ldap_create
ldap_sasl_interactive_bind: user selected: GSSAPI
ldap_int_sasl_bind: GSSAPI
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP fqdn:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 10.x.x.x:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
ldap_int_sasl_open: host=fqdn
SASL/GSSAPI authentication started
ldap_sasl_bind
ldap_send_initial_request
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({i) ber:
ber_flush2: 625 bytes to sd 3
ldap_msgfree
ldap_result ld 0x7f6d7dd63200 msgid 1
wait4msg ld 0x7f6d7dd63200 msgid 1 (infinite timeout)
wait4msg continue ld 0x7f6d7dd63200 msgid 1 all 1
** ld 0x7f6d7dd63200 Connections:
* host: fqdn  port: 636  (default)
  refcnt: 2  status: Connected
  last used: Sun Feb 22 15:18:41 2015




** ld 0x7f6d7dd63200 Outstanding Requests:
 * msgid 1,  origid 1, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x7f6d7dd63200 request count 1 (abandoned 0)
** ld 0x7f6d7dd63200 Response Queue:
   Empty
  ld 0x7f6d7dd63200 response count 0
ldap_chkResponseList ld 0x7f6d7dd63200 msgid 1 all 1
ldap_chkResponseList returns ld 0x7f6d7dd63200 NULL
ldap_int_select
read1msg: ld 0x7f6d7dd63200 msgid 1 all 1
ber_get_next
ber_get_next: tag 0x30 len 101 contents:
read1msg: ld 0x7f6d7dd63200 msgid 1 message type bind
ber_scanf fmt ({eAA) ber:
read1msg: ld 0x7f6d7dd63200 0 new referrals
read1msg:  mark request completed, ld 0x7f6d7dd63200 msgid 1
request done: ld 0x7f6d7dd63200 msgid 1
res_errno: 80, res_error: <SASL(-1): generic failure: GSSAPI Error: An invalid name was supplied (Permission denied)>, res_matched: <>
ldap_free_request (origid 1, msgid 1)
ldap_int_sasl_bind: <null>
ldap_parse_sasl_bind_result
ber_scanf fmt ({eAA) ber:
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt (}) ber:
ldap_msgfree
ldap_err2string
ldap_sasl_interactive_bind_s: Other (e.g., implementation specific) error (80)
    additional info: SASL(-1): generic failure: GSSAPI Error: An invalid name was supplied (Permission denied)
ldap_free_connection 1 1
ldap_send_unbind
ber_flush2: 7 bytes to sd 3
ldap_free_connection: actually freed

```

Without sudo:

```

user@hostname:/$ sudo kinit -p user
Password for user@DOMAIN: 


user@hostname:/$ sudo klist -f
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: user@DOMAIN


Valid starting     Expires            Service principal
22/02/15 15:17:23  23/02/15 03:17:23  krbtgt/DOMAIN@DOMAIN
    renew until 23/02/15 15:17:23, Flags: PRI

user@hostname:/$ ldapwhoami -d 165
ldap_create
ldap_sasl_interactive_bind: user selected: GSSAPI
ldap_int_sasl_bind: GSSAPI
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP fqdn:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 10.x.x.x:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
ldap_int_sasl_open: host=fqdn
SASL/GSSAPI authentication started
ldap_msgfree
ldap_err2string
ldap_sasl_interactive_bind_s: Local error (-2)
    additional info: SASL(-1): generic failure: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Permission denied)
ldap_free_connection 1 1
ldap_send_unbind
ber_flush2: 7 bytes to sd 3
ldap_free_connection: actually freed


```

As ever, any help would be greatly appreciated.

Regards,
Rob.

---

### Post by peridian on 2015-03-02
Finally got this working.

Managed to use strace on the slapd service in order to catch a line that does not get output in the openLDAP logs, even with full logging.

It turns out that the "Permission Denied" message comes off the back of an attempt to read the file at /etc/krb5.conf  At some point along the way, probably when I was securing the krb5.keytab file, I must have set the permissions as 640 root:root which then stops the openldap user from being able to read the file.  Doh!

I had a subsequent problem complaining about invalid credentials and gss_accept_sec_context but that just needed the random keys for the principals stored in the keytabs to be regenerated, and the keytab files to be repopulated with the new keys.

It all seems to be working now.

Regards,
Rob.

---

