---
title: "ldap with postix and dovecot"
date: 2011-12-27
forum: Server Platforms
---

### Post by learnbash on 2011-12-27
First of all i am i tell you about setup. Ldap authentication with dovecot not working, i am not able to reterive emails.
 

1. i have install 389 server, that is working fine.

 

my hostname is server1.example.com

dc=example,dc=com

 

2. i have configure dovecot.conf and conf.d/10-auth.conf configure properly but dovecot-ldap.conf having problem.

 

Below is my /etc/dovecot.conf

 

auth_verbose = yes
mail_debug = no

base_dir = /var/run/dovecot/
protocols = imap imaps pop3 pop3s
protocol lda {
  mail_plugins = quota
  postmaster_address = [EMAIL="postmaster@example.com"]postmaster@example.com[/EMAIL]
  auth_socket_path = /var/run/dovecot/auth-master
  }
listen = *
shutdown_clients = yes
log_timestamp = "%b %d %H:%M:%S "
syslog_facility = mail
disable_plaintext_auth = no
login_chroot = yes
login_user = postfix
login_process_per_connection = yes
login_processes_count = 2
login_max_processes_count = 128
login_max_connections = 256
login_greeting = Welcome to Dovecot eMail Server.
login_log_format_elements = user=<%u> method=%m rip=%r lip=%l %c
login_log_format = %$: %s
#default_mail_env = maildir:/home/vmail/%d/%u
mail_location = maildir:/var/vmail/%d/%u
first_valid_uid = 108 # REMEBER THIS MUST BE CHANGED TO YOUR UID FOR "postfix" FROM /etc/passwd
mail_uid = 5000
mail_gid = 5000
pop3_uidl_format = %08Xu%08Xv
auth default {
    mechanisms = PLAIN LOGIN
    passdb ldap {
        args = /etc/dovecot/dovecot-ldap.conf
    }
    userdb ldap {
        args = /etc/dovecot/dovecot-ldap.conf
    }
socket listen {
                master {
                        path = /var/run/dovecot/auth-master
                                mode = 0600
                        user = vmail
                        group = vmail
                }
                client {
                        path = /var/spool/postfix/private/auth
                        mode = 0660
                        user = postfix
                        group = postfix
                }
        }
        user = vmail
}

 

/etc/dovecot/dovecot-ldap.conf

 

hosts = server1.example.com
auth_bind = yes
auth_bind_userdn = mail=%u,ou=People,dc=example,dc=com
ldap_version = 3
base = ou=People,dc=example,dc=com
dn = cn="Directory Manager,dc=example,dc=com"
dnpass = mypassword
#deref = never
scope = subtree
user_attrs = quota=quota=maildir:storage
user_filter = (&(objectClass=VirtualMailAccount)(accountActive=T  RUE)(mail=%u))
pass_attrs = mail,userPassword
pass_filter = (&(objectClass=VirtualMailAccount)(accountActive=T  RUE)(mail=%u))
default_pass_scheme = MD5

 

When i use configuration and checking pop for [EMAIL="chris@example.com"]chris@example.com[/EMAIL] which have password 123. But it is not working, it is giving me error.

 

Dec 27 22:35:24 server1 dovecot: auth: Error: LDAP: binding failed (dn cn="Directory Manager,dc=example,dc=com"): No such object
Dec 27 22:35:24 server1 dovecot: auth: Error: LDAP: binding failed (dn cn="Directory Manager,dc=example,dc=com"): No such object

———————————————————————————————————

Below is postfix entry for chris user

 

# chris, Groups, example.com
dn: cn=chris,ou=Groups,dc=example,dc=com
objectClass: posixGroup
objectClass: top
cn: chris
gidNumber: 5051
userPassword:: e1NTSEF9TzdzbjNMejViWnI5N1RZbGNMenZEMXZIR1kzLy9iVj  k=

# chris, People, example.com
dn: uid=chris,ou=People,dc=example,dc=com
mailMessageStore: /var/vmail/example.com/chris
mail: [EMAIL="chris@example.com"]chris@example.com[/EMAIL]
givenName: chris
sn: chris
uidNumber: 5051
gidNumber: 5051
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetorgperson
objectClass: shadowaccount
objectClass: posixaccount
objectClass: mailrecipient
uid: chris
cn: chris chris
homeDirectory: /home/chris
userPassword:: e1NTSEF9RUgwNm11MmplVEtINGZjWisweWY2OTI1MU0vYmxaY0  s=

Please help me out where i am doing mistake. After fixing it i will go  to postfix part, one thing, /var/vmail/example.com/chris directory not  exist. Should i create it manually.

---

### Post by learnbash on 2011-12-28
Now directory server properly bind with dovecot but /var/log/maillog show password problem while password is fine. there is no error in access log of directory server. Please see maillog and access log


>  maillog

Dec 28 12:03:51 server1 dovecot: pop3-login: Disconnected (auth failed, 3 attempts): user=<chris@example.com>, method=PLAIN, rip=192.168.15.52, lip=192.168.15.52, secured



>  access log of directory server

[28/Dec/2011:12:03:29 +0500] conn=101 op=18 UNBIND
[28/Dec/2011:12:03:29 +0500] conn=101 op=18 fd=69 closed - U1
[28/Dec/2011:12:03:34 +0500] conn=104 fd=65 slot=65 connection from 127.0.0.1 to 127.0.0.1
[28/Dec/2011:12:03:34 +0500] conn=104 op=0 BIND dn="cn=Directory Manager" method=128 version=3
[28/Dec/2011:12:03:34 +0500] conn=104 op=0 RESULT err=0 tag=97 nentries=0 etime=0 dn="cn=directory manager"
[28/Dec/2011:12:03:34 +0500] conn=104 op=1 SRCH base="dc=example,dc=com" scope=2 filter="(&(objectClass=posixAccount)(uid=chris@example.com))" attrs="uid userPassword"
[28/Dec/2011:12:03:34 +0500] conn=104 op=1 RESULT err=0 tag=101 nentries=0 etime=0
[28/Dec/2011:12:03:39 +0500] conn=104 op=2 SRCH base="dc=example,dc=com" scope=2 filter="(&(objectClass=posixAccount)(uid=chris@example.com))" attrs="uid userPassword"
[28/Dec/2011:12:03:39 +0500] conn=104 op=2 RESULT err=0 tag=101 nentries=0 etime=0
[28/Dec/2011:12:03:45 +0500] conn=104 op=3 SRCH base="dc=example,dc=com" scope=2 filter="(&(objectClass=posixAccount)(uid=chris@example.com))" attrs="uid userPassword"
[28/Dec/2011:12:03:45 +0500] conn=104 op=3 RESULT err=0 tag=101 nentries=0 etime=0
[28/Dec/2011:12:04:01 +0500] conn=105 fd=66 slot=66 connection from 192.168.15.52 to 192.168.15.52
[28/Dec/2011:12:04:01 +0500] conn=105 op=0 BIND dn="" method=128 version=3
[28/Dec/2011:12:04:01 +0500] conn=105 op=0 RESULT err=0 tag=97 nentries=0 etime=0 dn=""
[28/Dec/2011:12:04:01 +0500] conn=105 op=1 SRCH base="dc=example,dc=com" scope=2 filter="(&(objectClass=posixGroup)(cn=pulse-rt))" attrs="cn userPassword memberUid uniqueMember gidNumber"
[28/Dec/2011:12:04:01 +0500] conn=105 op=1 RESULT err=0 tag=101 nentries=0 etime=0
[28/Dec/2011:12:04:01 +0500] conn=105 op=2 SRCH base="dc=example,dc=com" scope=2 filter="(&(objectClass=posixGroup)(cn=pulse-rt))" attrs="cn userPassword memberUid uniqueMember gidNumber"
[28/Dec/2011:12:04:01 +0500] conn=105 op=2 RESULT err=0 tag=101 nentries=0 etime=0
[28/Dec/2011:12:04:01 +0500] conn=105 op=-1 fd=66 closed - B1



---

### Post by wineman on 2011-12-28
hi learnbash

the only problem that i can see (according to your logs) is localed here in your dovecot-ldap.conf file.
> **learnbash said:**
> 
#/etc/dovecot/dovecot-ldap.conf
hosts = server1.example.com
auth_bind = yes
auth_bind_userdn = mail=%u,ou=People,dc=example,dc=com
ldap_version = 3
base = ou=People,dc=example,dc=com
**dn = cn="Directory Manager,dc=example,dc=com"**
dnpass = mypassword
#deref = never
scope = subtree
user_attrs = quota=quota=maildir:storage
user_filter = (&(objectClass=VirtualMailAccount)(accountActive=T  RUE)(mail=%u))
pass_attrs = mail,userPassword
pass_filter = (&(objectClass=VirtualMailAccount)(accountActive=T  RUE)(mail=%u))
default_pass_scheme = MD5
#EOF


basically what its doing is authenticating into LDAP off a non-existant admin dn. the line should read as follows:

```
dn = cn="Directory Manager",dc=example,dc=com
```
it will auth your postfix system as the "Directory Manager" account in LDAP, instead of as "Directory Manager,dc=example,dc=com". Remeber that everything in LDAP inside of double inverted commas is viewed as a single term, and so the term you passed wouldn't have worked.

Aso, check you pass_filter and user_filter in your doevcot config, the biggest thing that messed up auth is a lack of queried terms (ie you set dovecot up to ask for a property of the user that doesn't exist).

HTH

wineman

---

### Post by learnbash on 2011-12-28
Dear sir, 

my following files screw up thats why problem is coming. After alot effort i found that. if someone have that and help me in setting up, its so kind of him, it really give me headache, ldap authentication problem resolved.


1. /etc/dovecot/dovecot.conf
2. /etc/dovecot/dovecot-ldap.conf.ext
3. /etc/dovecot/conf.d/auth-ldap.conf.ext

---

