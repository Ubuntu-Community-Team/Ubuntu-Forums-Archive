---
title: "automount of user /home directories setup issue"
date: 2023-05-09
forum: Server Platforms
---

### Post by nahebm on 2023-05-09
I want to set up my Ubuntu server so that when I ssh to it, it automatically mounts my home directory (/home/mike) and logs me in.  I have this set up on other servers already, but there's something missing that I can't figure out and I'm hoping someone in this community can point it out to me.

The system in question:
- Ubuntu 20.04
- I used adcli to join this server to a realm
- server has sssd and nslcd running as well as autofs

Notable settings in files:
- /etc/autofs.conf
          master_map_name = /etc/auto.master
          browse_mode = no
          mount_nfs_default_protocol = 4
- /etc/autofs_ldap_auth.conf
        <autofs_ldap_sasl_conf
          usetls="yes"
          tlsrequired="no"
          authrequired="simple"
          authtype="LOGIN"
          user="username"
          secret="password"
/>

# the username/password values DO work

- /etc/nsswitch.conf
       passwd:  files sss ldap
       shadow:  files sss
       group:  files sss
       hosts:  files dns myhostname
       automount: files sss ldap
       aliases:  files sss

- /etc/sssd/sssd.conf

[sssd]
debug_level = 2
config_file_version = 2
reconnection_retries = 3
services = nss,pam,autofs
domains = my.company.com

[autofs]
debug_level = 9
ldap_autofs_entry_key = keyname
ldap_autofs_object_class = nisObject
ldap_autofs_entry_value = nisMapEntry
ldap_autofs_map_name = nisMap
ldap_autofs_map_object_class = nisMapName
ldap_autofs_search_base = cn=LdapUser,dc=my,dc=company,dc=com

[nss]
debug_level = 2
fallback_homedir = /home/%u
filter_users = root,nagios
override_shell = /bin/bash
reconnection_retries = 3
debug_level = 2

root@server ~# dpkg -l |grep ldap 
ii autofs-ldap        5.1.6-2ubuntu0.1
ii ldap-auth-client  0.5.4
ii ldap-auth-config 0.5.4
ii ldap-utils            2.4.49+dfsg-2ubuntu1.9
ii libldap-2.4-2:amd 2.4.49+dfsg-2ubuntu1.9
ii libldap-common    2.4.49+dfsg-2ubuntu1.9
ii libnss-ldap:amd64 265-5ubuntu1
ii libpam-ldap:amd64 186-4ubuntu1
ii sssd-ldap             2.2.3-3ubuntu0.8

root@server ~# dpkg -l |grep autofs
ii autofs 5.1.6-2ubuntu0.1

I also tried editing /etc/sssd/sssd.conf with nothing under the [autofs] section, because a guide I found says to remove this and let the program(s) rebuild the entry, but that's what I've seen on my other working systems.

Thanks,
Mike

---

