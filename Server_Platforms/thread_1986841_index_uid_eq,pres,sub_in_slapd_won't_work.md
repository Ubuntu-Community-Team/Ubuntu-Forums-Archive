---
title: "index uid eq,pres,sub in slapd won't work"
date: 2012-05-25
forum: Server Platforms
---

### Post by natomb on 2012-05-25
Hello,

I have a small Linux server where I want to use LDAP for central user authentication for various services, including samba, radius, web login, unix and windows, and much more. Yet, I face two problems.

1) when strictly following the manuals, i.e. for samba, LDAP will not authenticate any user.
2) groups are rarely resolved.

For 1) in particular adding the following line to slapd.conf will result in a situation where no user in LDAP can login to the system:```
index           uid eq,pres,sub
```When I remove the line, users can login to the system. Yet in the syslog I continuously get the following 'warning':
```
May 25 07:59:13 ldap slapd[24791]: <= bdb_equality_candidates: (uid) not indexed
```(of course, I commented the index out).

My question: how I have to write the index such that the 'warning' disappears while login of users registered in LDAP is still possible?


For 2) I have a number of groups registered in LDAP. But most of the times, the group name for those gid cannot be resolved. This also includes complaining about unknown groups when log in as user with groups from LDAP. Surprisingly, very few times it works. It does not matter whether to reboot the server. I had a situation where user a attempted to log in three times in a row and only the third log in resulted in a successful group lookup. Then, in another situation user b attempted to log in three times in a row while groups could not be looked up first and third time but second time groups could be looked up.


For analysis, I will tell you what I did. For the ldap configuration I used the "old school" way of slapd.conf file, instead of config database. Configuration files are attached.


```
 sudo apt-get install apparmor-utils slapd ldap-utils samba-doc ldapscripts pwgen
  sudo gunzip /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz
 sudo cp /usr/share/doc/samba-doc/examples/LDAP/samba.schema /etc/ldap/schema
 
```Configure /etc/ldap/slapd.conf file.
Configure /etc/default/slapd.conf file.
Creating files /etc/ldap/aktiviere_slapd.conf.sh, /etc/ldap/base.ldif, /etc/ldap/init.ldif and /etc/ldap/samba.ldif .
Configure /etc/ldap/ldap.conf file.

Executed the following statements:
```
sudo chown root:openldap /etc/ldap/slapd.conf /etc/ldap/ldap.conf /etc/ldap/base.ldif /etc/ldap/init.ldif /etc/ldap/aktiviere_slapd.conf.sh /etc/ldap/ldap.key
 sudo chmod o-rwx /etc/ldap/slapd.conf /etc/ldap/ldap.conf /etc/ldap/base.ldif /etc/ldap/init.ldif /etc/ldap/ldap.key
 sudo chmod ug+x /etc/ldap/aktiviere_slapd.conf.sh
 sudo aa-complain /usr/sbin/slapd
 sudo /etc/ldap/aktiviere_slapd.conf.sh
 sudo aa-logprof
 sudo ldapadd -x -h ldaps://ldap.example.org -p 636 -W -D cn=admin,dc=example,dc=org -f /etc/ldap/base.ldif
 sudo ldapadd -x -h ldaps://ldap.example.org -p 636 -W -D cn=admin,dc=example,dc=org -f /etc/ldap/init.ldif
 
```Create file /etc/ldapscripts/ldapscripts.passwd with password for ldap administrator account.
Configure /etc/ldapscripts/ldapscripts.conf file.

Add some groups and users with ldapaddgroup and ldapadduser scripts.

Setup LDAP client authentication.
```
sudo apt-get install libnss-ldapd libpam-ldapd auth-client-config ldap-auth-client ldap-auth-config nslcd nscd
  
```Parameters for ldap-auth-config (dpkg-reconfigure ldap-auth-config):

```
LDAP server URI: ldaps://ldap.example.org:636
 DN of search base: dc=example,dc=org
 LDAP version: 3
 Make local root DB admin: yes
 Does the LDAP DB require login: no
 LDAP account for root: cn=admin,dc=example,dc=org
 LDAP root account password: ...
 LDAP suffix: dc=example,dc=org
 Services für LDAP-Lookup: group, passwd, shadow
 
```Execute the following commands:

```
sudo auth-client-config -t nss -p lac_ldap  
 sudo pam-auth-update
 
```Select: UNIX & LDAP

Adjusted /etc/nslcd.conf and added:
```
tls_cacertfile /etc/ssl/certs/ldap.crt
```
Invoking 'getent group' and 'getent passwd' returns all groups and users, including the ones in UNIX /etc/group file as well as LDAP, including their gid and name.


I am lost what I can do. According to the numerous guides and how-to's I set up everything appropriately apart from the line "index uid eq,pres,sub". Yet, when I put in this line into slapd.conf, then nothing is working.


Thank you for your assistance.
  Bjoern

---

### Post by natomb on 2012-05-28
News on this topic.

I found the config lines resulting in the problem. In /etc/ldap/slapd.conf I have to comment the following two lines so those indexes are not created / used:

```

#index gidNumber eq
#index default sub

```

Yet, I do not understand why I have to do this. I even do not understand this because those lines are present in dozens of tutorials. If they are in the tutorials, I think it shall work. But why it does not work for me?

Any ideas?


Thanks
  Bjoern

---

### Post by natomb on 2012-06-02
Ok, found the problem by myself. For some reason slapd is creating "just some" of the index defined.

So, I had to execute "slapindex -f /etc/ldap/slapd.conf" and then everything (on linux side) works as expected, including the indexes.

---

