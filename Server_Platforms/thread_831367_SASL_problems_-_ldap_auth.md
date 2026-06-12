---
title: "SASL problems? - ldap auth"
date: 2008-06-16
forum: Server Platforms
---

### Post by iskatyel on 2008-06-16
SASL has me ready to scream.  I am attempting to do ldap auth and it will not work with GSSAPI.
I do a kinit, then klist to verify everything checks out.  Then I run ldapwhoami and I get the following:
```
SASL/GSSAPI authentication started
ldap_sasl_interactive_bind_s: Invalid credentials (49)
```
Testing further I open two terminals to use the sasl sample-client/server test with these commands:
```
root@carrot:/home/klis# sasl-sample-server -d KRB5_REALM -s ldap
root@carrot:/home/klis# sasl-sample-client -s ldap -n FQDN -u username
```
I copy and paste once to the client and then once to the server before it outputs the following:
```
got 'GSSAPI'
sasl-sample-server: SASL Other: GSSAPI Error:  An unsupported mechanism was requested (unknown mech-code 0 for mech unknown)
sasl-sample-server: Starting SASL negotiation: authentication failure (authentication failure)
```
testsaslauthd -u username -p password works fine, ldap simple bind queries accept my username and password and kerberos will grant tickets as expected.  The whole problem seems to be GSSAPI auth so I assume I have a config file or permissions problem.
I have run strace looking for any missing files and from what I can see all the missing files are appropriate.
saslauthd.conf reads:
```
ldap_servers: ldap://127.0.0.1
ldap_port: 389
ldap_version: 3
ldap_referrals: no
ldap_search_base: dc=domainprefix,dc=mydomain,dc=com
```
and /usr/lib/sasl2/slapd.conf reads:
```
pwcheck_method: saslauthd
saslauthd_path: /var/state/saslauthd/mux
```

Any and all suggestions welcome!

I have mostly followed the howto out at [http://www.diegolima.org/slk/index.php?title=Heimdal_Kerberos_+_Samba_PDC_+_OpenLDAP_+_Squid_no_Debian_Etch](http://www.diegolima.org/slk/index.php?title=Heimdal_Kerberos_+_Samba_PDC_+_OpenLDAP_+_Squid_no_Debian_Etch)
It is in Portuguese and I have a full translation ready in English that I am adapting for Ubuntu 8.04 and this seems to be the only real hangup (kind of a big one, though).  I intend to post this for everyone in the tips and tutorials after it works.

---

