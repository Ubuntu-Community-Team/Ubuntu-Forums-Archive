---
title: "FreeIPA Client Ubuntu 12.04+ Server/Desktop"
date: 2014-02-25
forum: Server Platforms
---

### Post by Lee_Machine on 2014-02-25
I'm in the process of setting up an isolated Linux only network with RHEL5/6 Fedora 18/19/20 and Ubuntu 12.04+ and would like to use FreeIPA client. It works just fine on RHEL and Fedora but not Ubuntu. 

I'm tempted to just setup a Windows Server DC and continue using PBIS to login with Windows Domain credentials like we are now but the idea is a Linux only network and having a Windows Server for Linux Identity management is very laughable. :D

I don't have to time to dive into the nuts and bolts of setting up openLDAP and Kerberos whereas IPA is supposed to do all the work for me.

---

### Post by Lee_Machine on 2014-02-26
After much tinkering and rebooting I got it to work but the ipa-client process crashes sometimes.

I'll have to reproduce and document.

---

### Post by kill4killin on 2014-04-01
I realize this thread is a few weeks old now but hopefully by posting this someone, maybe OP, will see this and find it useful...

I'm running FreeIPA on a Redhat server and authenticating a mix of clients: Redhat, Fedora and Ubuntu. I've gotten this to work on Ubuntu using the following configuration files (sensitive information redacted).

/etc/sssd/sssd.conf:
The majority of this file was generated using the "ipa-client-install" command. I then modified the "ipa_server" line to remove "_srv_," and added the "ipa_hostname =" line.
```

[domain/example.domain.com]

cache_credentials = True
krb5_store_password_if_offline = True
ipa_domain = example.domain.com
id_provider = ipa
auth_provider = ipa
access_provider = ipa
ipa_hostname = hostname.example.domain.com
chpass_provider = ipa
ipa_server = ipaserver.example.domain.com
ldap_tls_cacert = /etc/ipa/ca.crt
[sssd]
services = nss, pam, ssh
config_file_version = 2

domains = example.domain.com
[nss]

[pam]

[sudo]

[autofs]

[ssh]

```

/etc/nsswitch.conf:
The below file is incomplete and probably still contains a lot of unecessary information since I'm still working on migrating from our old LDAP server to IPA but the above file is currently in production and working.
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

# pre_auth-client-config # passwd:         compat
passwd: files sss
#passwd: files ldap [NOTFOUND=return] db
# pre_auth-client-config # group:          compat
group: files sss
#group: files ldap  [NOTFOUND=return] db
# pre_auth-client-config # shadow:         compat
shadow: files ldap [NOTFOUND=return] db

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

# pre_auth-client-config # netgroup:       nis
netgroup: nis sss

```

If there are any other file examples that might be useful to anyone trying to solve this issue, I'm happy to post them. I believe these are the only really relevant ones. I've also got the following ldap/ipa/auth packages installed, not all of them may be necessary as I'm currently migrating from using openLDAP to IPA:

[LIST]
[*] freeipa-client
[*] nscd
[*] nslcd
[*] libnss-ldapd
[*] libpam-ldapd
[*] nss-updatedb
[*] libnss-db
[*] libpam-ccreds
[/LIST]

EDIT:
OH! I also forgot to mention that we have the following line in /etc/pam.d/common-account:
```
session required pam_mkhomedir.so skel=/etc/skel/ umask=0022
```
and the a file in /usr/share/pam-configs/my_mkhomedir containing the following:
```

Name: activate mkhomedir
Default: yes 
Priority: 900 
Session-Type: Additional
Session:
    required        pam_mkhomedir.so umask=0022 skel=/etc/skel

```

EDIT2:
Some additional notes...
After further testing, it looks like the ipa-client-install does not properly modify the pam.d/common-* files. You need to make sure that each file is calling "pam_sss.so". I've included the pam_sss.so lines from my files below for reference:

/etc/pam.d/common-auth:
```
auth    [success=4 default=ignore]                      pam_sss.so use_first_pass
```

/etc/pam.d/common-account (NOTE, this file also had a "pam_localuser.so" line which I've included for completeness):
```
account sufficient                                      pam_localuser.so
account [default=bad success=ok user_unknown=ignore]    pam_sss.so
```

/etc/pam.d/common-password:
```
password        sufficient                                      pam_sss.so
```

/etc/pam.d/common-session:
```
session optional                                        pam_sss.so
```

---

### Post by Lee_Machine on 2014-04-08
Thank you for the helpful reply. 

I put the Ubuntu clients on the backburner since most of the Linux clients I support run RHEL or CentOS. IPA client on those work just fine (most of the time) but the Ubuntu client seems to be full of bugs.

On my test environment at home, Ubuntu 14.04 seems to be able to join IPA domains just fine.

I'm going to the RedHat Summit next week and if given the chance im going to ask about official support for the IPA-Client on Ubuntu.

-Brandon

---

