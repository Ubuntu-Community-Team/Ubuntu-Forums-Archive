---
title: "Client login via LDAP not working"
date: 2012-09-18
forum: Server Platforms
---

### Post by oguzy on 2012-09-18
I have an LDAP server installed and running. At my client machine, i can run the ldapsearch and get the results as below:

```

# ldapsearch -D cn=admin,dc=foo,dc=edu,dc=tr -W -h 192.168.1.250 -x -b dc=foo,dc=edu,dc=tr

# extended LDIF
#
# LDAPv3
# base <dc=foo,dc=edu,dc=tr> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# foo.edu.tr
dn: dc=foo,dc=edu,dc=tr
objectClass: top
objectClass: dcObject
objectClass: organization
o: foo
dc: foo

# admin, foo.edu.tr
dn: cn=admin,dc=foo,dc=edu,dc=tr
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword:: some_password_data

# people, foo.edu.tr
dn: ou=people,dc=foo,dc=edu,dc=tr
objectClass: organizationalUnit
objectClass: top
ou: people

# student, people, foo.edu.tr
dn: ou=student,ou=people,dc=foo,dc=edu,dc=tr
objectClass: organizationalUnit
objectClass: top
ou: student

# personel, people, foo.edu.tr
dn: ou=personel,ou=people,dc=foo,dc=edu,dc=tr
objectClass: organizationalUnit
objectClass: top
ou: personel

# [email]foomaster@foo.edu.tr[/email], student, people, foo.edu.tr
dn: mail=foomaster@foo.edu.tr,ou=student,ou=people,dc=foo,dc=edu,dc=tr
objectClass: organizationalPerson
objectClass: person
objectClass: inetOrgPerson
mail: [email]060401026@foo.edu.tr[/email]
userPassword:: NDM4Njc1NQ==
uid: 060401026
cn: Foo Master
sn: FooMaster
givenName: 060401026

# [email]foo2master@foo.edu.tr[/email], personel, people, foo.edu.tr
dn: mail=foo2emaster@foo.edu.tr,ou=personel,ou=people,dc=foo,dc=edu,dc=tr
cn: Foo2  Master
objectClass: organizationalPerson
objectClass: person
objectClass: inetOrgPerson
sn: Master
mail: [email]foo2master@foo.edu.tr[/email]
givenName:: Foo2
userPassword:: dDJabmNW

```

At the client side i tried to set the LDAP authentication when logging in. I followed the instructions mentioned [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) address.

I am attaching the files from the client machine: /etc/ldap.conf, /etc/nsswitch.conf, /etc/nscd.conf, /etc/security/group.conf /etc/pam.d/common-session, /etc/pam.d/common-auth, /etc/pam.d/common-account and /etc/pam.d/common-password

When i enter getent passwd i dont get the entries from my ldapserver but some ldap related messages. 

```

ldap_create
ldap_url_parse_ext(ldap://192.168.1.250)
ldap_simple_bind
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP 192.168.1.250:389
ldap_new_socket: 5
ldap_prepare_socket: 5
ldap_connect_to_host: Trying 192.168.1.250:389
ldap_pvt_connect: fd: 5 tm: 30 async: 0
ldap_ndelay_on: 5
ldap_int_poll: fd: 5 tm: 30
ldap_is_sock_ready: 5
ldap_ndelay_off: 5
ldap_pvt_connect: 0
ldap_open_defconn: successful
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({i) ber:
ber_flush2: 14 bytes to sd 5
ldap_result ld 0x967e7d0 msgid 1
wait4msg ld 0x967e7d0 msgid 1 (timeout 30000000 usec)
wait4msg continue ld 0x967e7d0 msgid 1 all 0
** ld 0x967e7d0 Connections:
* host: 192.168.1.250  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Tue Sep 18 11:06:02 2012


** ld 0x967e7d0 Outstanding Requests:
 * msgid 1,  origid 1, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x967e7d0 request count 1 (abandoned 0)
** ld 0x967e7d0 Response Queue:
   Empty
  ld 0x967e7d0 response count 0
ldap_chkResponseList ld 0x967e7d0 msgid 1 all 0
ldap_chkResponseList returns ld 0x967e7d0 NULL
ldap_int_select
read1msg: ld 0x967e7d0 msgid 1 all 0
ber_get_next
ber_get_next: tag 0x30 len 12 contents:
read1msg: ld 0x967e7d0 msgid 1 message type bind
ber_scanf fmt ({eAA) ber:
read1msg: ld 0x967e7d0 0 new referrals
read1msg:  mark request completed, ld 0x967e7d0 msgid 1
request done: ld 0x967e7d0 msgid 1
res_errno: 0, res_error: <>, res_matched: <>
ldap_free_request (origid 1, msgid 1)
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt (}) ber:
ldap_msgfree
ldap_search_ext
put_filter: "(objectClass=posixAccount)"
put_filter: simple
put_simple_filter: "objectClass=posixAccount"
ldap_send_initial_request
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({) ber:
ber_flush2: 230 bytes to sd 5
ldap_result ld 0x967e7d0 msgid 2
wait4msg ld 0x967e7d0 msgid 2 (timeout 30000000 usec)
wait4msg continue ld 0x967e7d0 msgid 2 all 0
** ld 0x967e7d0 Connections:
* host: 192.168.1.250  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Tue Sep 18 11:06:02 2012


** ld 0x967e7d0 Outstanding Requests:
 * msgid 2,  origid 2, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x967e7d0 request count 1 (abandoned 0)
** ld 0x967e7d0 Response Queue:
   Empty
  ld 0x967e7d0 response count 0
ldap_chkResponseList ld 0x967e7d0 msgid 2 all 0
ldap_chkResponseList returns ld 0x967e7d0 NULL
ldap_int_select
read1msg: ld 0x967e7d0 msgid 2 all 0
ber_get_next
ber_get_next: tag 0x30 len 49 contents:
read1msg: ld 0x967e7d0 msgid 2 message type search-result
ber_scanf fmt ({eAA) ber:
read1msg: ld 0x967e7d0 0 new referrals
read1msg:  mark request completed, ld 0x967e7d0 msgid 2
request done: ld 0x967e7d0 msgid 2
res_errno: 0, res_error: <>, res_matched: <>
ldap_free_request (origid 2, msgid 2)
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt ({a) ber:
ber_scanf fmt (o) ber:
ber_scanf fmt (}) ber:
ldap_msgfree
ber_scanf fmt ({io}) ber:
ldap_unbind
ldap_free_connection 1 1
ldap_send_unbind
ber_flush2: 7 bytes to sd 5
ldap_free_connection: actually freed
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
colord:x:103:108:colord colour management daemon,,,:/var/lib/colord:/bin/false
lightdm:x:104:111:Light Display Manager:/var/lib/lightdm:/bin/false
whoopsie:x:105:114::/nonexistent:/bin/false
avahi-autoipd:x:106:117:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:107:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:108:46:usbmux daemon,,,:/home/usbmux:/bin/false
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:110:119:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:111:122:RealtimeKit,,,:/proc:/bin/false
speech-dispatcher:x:112:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
hplip:x:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:114:123::/home/saned:/bin/false
oguz:x:1000:1000:oguz,,,:/home/oguz:/bin/bash
vboxadd:x:999:1::/var/run/vboxadd:/bin/false
openldap:x:115:125:OpenLDAP Server Account,,,:/var/lib/ldap:/bin/false
tomcat7:x:116:126::/usr/share/tomcat7:/bin/false

```

What am i doing wrong?

---

### Post by luvshines on 2012-09-18
From your setup I would check following couple of things for user lookup (not yet talking about the authentication part/PAM configs):

1. The default config would want to use 'uid' attribute for users
Since you want to use 'mail' I think you'll need something like
```
nss_map_attribute uid mail
``` which would tell nss_ldap to consider mail

2. You have mentioned nss_base_passwd with 'one' level but your actual entries lie 2 level below the ou=people. That is under student or personnel. To check this, try running the ldapsearch with "-s one" and "-b ou=people,dc=foo,dc=edu,dc=tr" and see if it returns the entries. If not, then you will need 'sub' instead of 'one' in ldap.conf

3. From the entries you have posted here, the mail in the dn is different from what is there in the user para.
Eg.
dn: mail=foomaster@foo.edu.tr ...
...
mail: [email]060401026@foo.edu.tr[/email]
...

dn: mail=foo2emaster@foo.edu.tr
...
mail: [email]foo2master@foo.edu.tr[/email]
...

Now if it's just a typo or your entries are actually defined like this. The mail in the dn and one that has been defined below shud match

---

