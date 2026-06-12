---
title: "LDAP and cached credentials"
date: 2010-09-30
forum: Server Platforms
---

### Post by druhboruch on 2010-09-30
I have been struggling with LDAP authentication when LDAP server is not accessible.

This is what happens:

When laptop user logs in and LDAP server is available everything is OK.
Then she goes home and doesn't have the internet or LDAP is not available and she needs to authenticate but can't.

I've tried to implement outdated howto 
[https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto) .

The message says that cached credentials are being used, but then login fails.

I would like to get this working.  In Maverick SSSD is supposed to do just that, but I was unable to find any references.

I would greatly appreciate any suggestions.

---

### Post by luvshines on 2010-10-03
Are you trying to authenticate(at home) with LDAP user but without LDAP server ?? OR the local user itself fails to authenticate ?

For the cached credentials thing, see if NSCD service is running. If it is, shut it down when you are logged in, then disconnect and try to login without internet/LDAP server (as you said)

---

### Post by nr1c0re on 2010-10-03
try to set "debug" near pam_ccreds.so and pam_ldap.so in pam.d and see what happens in logs

---

### Post by druhboruch on 2010-10-05
Finally I managed to get it to work.
This is what I have done on fresh Maverick RC installation on a notebook:
Here are the steps:

```
apt-get install sssd libnss-sss libpam-sss
apt-get install auth-client-config
apt-get install ldap-utils

```

```
#/etc/ldap/ldap.conf:

URI ldap://ldap.example.com/
TLS_CACERT /etc/ssl/certs/cacert.pem

```

Now make sure that TLS works:
```
ldapsearch -x -h ldap.example.com -ZZ -b dc=example,dc=com
```

Update domain section in /etc/sssd/sssd.conf

```

#/etc/sssd/sssd.conf
domains = LDAP

[domain/LDAP]
id_provider = ldap
auth_provider = ldap
ldap_uri = ldap://ldap.example.com
ldap_search_base = dc=example,dc=com
ldap_user_search_base = ou=people,dc=example,dc=com
ldap_group_search_base = ou=groups,dc=example,dc=com
ldap_user_object_class = inetOrgPerson
ldap_user_name = uid
ldap_user_uid_number = uidNumber
ldap_user_gid_number = gidNumber
ldap_user_home_directory = homeDirectory
ldap_user_shell = loginShell
ldap_tls_reqcert = demand
ldap_tls_cacert = /etc/ssl/certs/cacert.pem 
cache_credentials = true
enumerate = true

```

Now create file /etc/auth-client-config/profile.d/acc-sssd
```

[sssd]
nss_passwd=     passwd:         compat sss
nss_group=      group:          compat sss
nss_shadow=     shadow:         compat
nss_netgroup=   netgroup:       nis

pam_auth=       auth    [success=3 default=ignore]      pam_unix.so nullok_secure try_first_pass
                auth    requisite                       pam_succeed_if.so uid >= 500 quiet
                auth    [success=1 default=ignore]      pam_sss.so use_first_pass
                auth    requisite                       pam_deny.so
                auth    required                        pam_permit.so

pam_account=    account required                                        pam_unix.so
                account sufficient                                      pam_localuser.so
                account sufficient                                      pam_succeed_if.so uid < 500 quiet
                account [default=bad success=ok user_unknown=ignore]    pam_sss.so
                account required                                        pam_permit.so

pam_password=   password        sufficient      pam_unix.so obscure sha512
                password        sufficient      pam_sss.so use_authtok
                password        required        pam_deny.so

pam_session=    session required                        pam_mkhomedir.so skel=/etc/skel/ umask=0077
                session optional                        pam_keyinit.so revoke
                session required                        pam_limits.so
                session [success=1 default=ignore]      pam_sss.so
                session required                        pam_unix.so
```

And finally apply the profile:
```
auth-client-config -a -p sssd
```

Test with getent or login to your computer with credentials from LDAP.

---

### Post by nickpiggott on 2011-01-08
> **druhboruch said:**
> 
I've tried to implement outdated howto 
[https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto) .

The message says that cached credentials are being used, but then login fails.


I started with that How To, but ended up using pam-auth-update to recreate the necessary files in /etc/pam.d/common-*

That got me to the state where it was saying:
```
You have been logged on using cached credentials

Authentication Failed

```To fix that, I had to amend the /etc/pam.d/common-account file created by pam-auth-update

The line:

```
account    [success=1 default=ignore]    pam_ldap.so
```
 
will always fail, because if the machine is off-line, it cannot contact the LDAP server.

I have amended that line in my common-account to read:

```
account    [success=1 authinfo_unavail=1 default=ignore]    pam_ldap.so
```
 
If the LDAP server cannot be reached, it now proceeds as if it had succeeded.

There are some potential dangers to this approach, but it's a working solution for me

---

### Post by druhboruch on 2011-04-30
sssd is broken in natty:
[https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/746981](https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/746981)

Let's hope it is fixed soon.

---

