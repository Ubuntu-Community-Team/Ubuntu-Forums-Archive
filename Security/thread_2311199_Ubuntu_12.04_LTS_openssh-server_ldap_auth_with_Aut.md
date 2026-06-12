---
title: "Ubuntu 12.04 LTS openssh-server ldap auth with AuthorizedKey problem."
date: 2016-01-25
forum: Security
---

### Post by Lorand on 2016-01-25
HI All !

  I am trying to set up said server(s) running 12.04 LTS and openssh-server Version: 1:5.9p1-5ubuntu1.8 to use ldap authetntication with Authorized keys.

  The normal password based authentication is working with libpam-ldap and nslcd - users can log in, home directories are cretaed etc. This only for password based authentication. 

 If I would like to make the next step and store public keys in LDAP - Which I did already, and the /usr/local/bin/ssh-ldap-pubkey-wrapper utility is pulling the right public keys for any user from the LDAP - and ask openssh to pull the key from LDAP for key based auth I am getting an error:

$> /usr/sbin/sshd -f /etc/ssh/sshd-ldap_config -ddd
[----]
  /etc/ssh/sshd-ldap_config: line 35: Bad configuration option: AuthorizedKeysCommand
debug3: /etc/ssh/sshd-ldap_config:35 setting AuthorizedKeysCommand /usr/local/bin/ssh-ldap-pubkey-wrapper
/etc/ssh/sshd-ldap_config: line 36: Bad configuration option: AuthorizedKeysCommandUser
debug3: /etc/ssh/sshd-ldap_config:36 setting AuthorizedKeysCommandUser root

  Is this option not supported and what other options I have for autheticating against and LDAP server via ssh authorised keys? 

  Thanks in advance for your support !

Lorand

---

