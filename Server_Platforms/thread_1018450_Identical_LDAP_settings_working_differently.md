---
title: "Identical LDAP settings working differently?"
date: 2008-12-22
forum: Server Platforms
---

### Post by calle.kabo on 2008-12-22
Hi,

I've set up an LDAP-server and two other machines acting as LDAP-clients.

Here's what I did client side on both clients:
# apt-get install auth-client-config ldap-auth-client ldap-auth-config libnss-db libnss-ldap libpam-ldap nscd nss-updatedb libpam-foreground sudo-ldap
# rm /etc/ldap/ldap.conf; ln -s /etc/ldap.conf /etc/ldap/ldap.conf
# auth-client-config -a -p lac_ldap
# nss_updatedb ldap
# getent passwd (to make sure I get the info from the LDAP-server)

Here's my problem:
On one machine I can log in and everything's dandy.
On the other machine... different story :(
Here's what my auth.log says when I try to log in with my user on the bad machine:
```

Dec 22 10:17:40 badmachine sshd[10113]: Invalid user ckabo from 192.168.100.183
Dec 22 10:17:40 badmachine sshd[10113]: Failed none for invalid user ckabo from 192.168.100.183 port 51292 ssh2
Dec 22 10:17:42 badmachine sshd[10113]: pam_ldap: error trying to bind as user "uid=ckabo,ou=people,dc=xxx,dc=com" (Invalid credentials)
Dec 22 10:17:42 badmachine sshd[10113]: pam_unix(sshd:auth): check pass; user unknown
Dec 22 10:17:42 badmachine sshd[10113]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.100.183 
Dec 22 10:17:44 badmachine sshd[10113]: Failed password for invalid user ckabo from 192.168.100.183 port 51292 ssh2

```

Auth.log on the good machine:
```

Dec 22 10:25:38 goodmachine sshd[25927]: Accepted password for ckabo from 192.168.100.183 port 51301 ssh2
Dec 22 10:25:38 goodmachine sshd[25933]: pam_unix(sshd:session): session opened for user ckabo by (uid=0)

```

When logged in as root on the bad machine I get the correct entries from 'getent passwd'.
But I still can't log in as my user.

Here's what I get when running 'slapd -d 1'.
When logging in on the good machine:
```


slap_listener_activate(8): 
>>> slap_listener(ldap:///)
connection_get(17): got connid=10
connection_read(17): checking for input on id=10
ber_get_next
ber_get_next: tag 0x30 len 45 contents:
ber_get_next
conn=10 op=0 do_bind
ber_scanf fmt ({imt) ber:
ber_scanf fmt (m}) ber:
>>> dnPrettyNormal: <cn=manager,dc=xxx,dc=com>
<<< dnPrettyNormal: <cn=manager,dc=xxx,dc=com>, <cn=manager,dc=xxx,dc=com>
do_bind: version=3 dn="cn=manager,dc=xxx,dc=com" method=128
do_bind: v3 bind: "cn=manager,dc=xxx,dc=com" to "cn=manager,dc=xxx,dc=com"
send_ldap_result: conn=10 op=0 p=3
send_ldap_response: msgid=1 tag=97 err=0
ber_flush2: 14 bytes to sd 17
connection_get(17): got connid=10
connection_read(17): checking for input on id=10
ber_get_next
ber_get_next: tag 0x30 len 139 contents:
ber_get_next
conn=10 op=1 do_search
ber_scanf fmt ({miiiib) ber:
>>> dnPrettyNormal: <dc=xxx,dc=com>
<<< dnPrettyNormal: <dc=xxx,dc=com>, <dc=xxx,dc=com>
ber_scanf fmt ({mm}) ber:
ber_scanf fmt ({mm}) ber:
ber_scanf fmt ({M}}) ber:
=> get_ctrls
ber_scanf fmt ({m) ber:
ber_scanf fmt (m) ber:
=> get_ctrls: oid="1.2.840.113556.1.4.319" (noncritical)
ber_scanf fmt ({im}) ber:
<= get_ctrls: n=1 rc=0 err=""
=> hdb_search
bdb_dn2entry("dc=xxx,dc=com")
search_candidates: base="dc=xxx,dc=com" (0x00000001) scope=2
=> hdb_dn2idl("dc=xxx,dc=com")
=> bdb_equality_candidates (objectClass)
=> key_read
<= bdb_index_read: failed (-30990)
<= bdb_equality_candidates: id=0, first=0, last=0
=> bdb_equality_candidates (objectClass)
=> key_read
<= bdb_index_read 1 candidates
<= bdb_equality_candidates: id=1, first=8, last=8
=> bdb_equality_candidates (memberUid)
<= bdb_equality_candidates: (memberUid) not indexed
bdb_search_candidates: id=1 first=8 last=8
hdb_search: 8 does not match filter
send_ldap_result: conn=10 op=1 p=3
send_ldap_response: msgid=2 tag=101 err=0
ber_flush2: 51 bytes to sd 17

```

When trying to log in on the bad machine:
```
slap_listener_activate(8): 
>>> slap_listener(ldap:///)
connection_get(18): got connid=12
connection_read(18): checking for input on id=12
ber_get_next
ber_get_next: tag 0x30 len 45 contents:
ber_get_next
conn=12 op=0 do_bind
ber_scanf fmt ({imt) ber:
ber_scanf fmt (m}) ber:
>>> dnPrettyNormal: <cn=manager,dc=xxx,dc=com>
<<< dnPrettyNormal: <cn=manager,dc=xxx,dc=com>, <cn=manager,dc=xxx,dc=com>
do_bind: version=3 dn="cn=manager,dc=xxx,dc=com" method=128
do_bind: v3 bind: "cn=manager,dc=xxx,dc=com" to "cn=manager,dc=xxx,dc=com"
send_ldap_result: conn=12 op=0 p=3
send_ldap_response: msgid=1 tag=97 err=0
ber_flush2: 14 bytes to sd 18
connection_get(18): got connid=12
connection_read(18): checking for input on id=12
ber_get_next
ber_get_next: tag 0x30 len 54 contents:
ber_get_next
conn=12 op=1 do_search
ber_scanf fmt ({miiiib) ber:
>>> dnPrettyNormal: <dc=xxx,dc=com>
<<< dnPrettyNormal: <dc=xxx,dc=com>, <dc=xxx,dc=com>
ber_scanf fmt ({mm}) ber:
ber_scanf fmt ({M}}) ber:
=> hdb_search
bdb_dn2entry("dc=xxx,dc=com")
search_candidates: base="dc=xxx,dc=com" (0x00000001) scope=2
=> hdb_dn2idl("dc=xxx,dc=com")
=> bdb_equality_candidates (objectClass)
=> key_read
<= bdb_index_read: failed (-30990)
<= bdb_equality_candidates: id=0, first=0, last=0
=> bdb_equality_candidates (uid)
<= bdb_equality_candidates: (uid) not indexed
bdb_search_candidates: id=-1 first=1 last=10
hdb_search: 1 does not match filter
hdb_search: 2 does not match filter
hdb_search: 3 does not match filter
hdb_search: 4 does not match filter
=> send_search_entry: conn 12 dn="uid=ckabo,ou=people,dc=xxx,dc=com"
ber_flush2: 724 bytes to sd 18
<= send_search_entry: conn 12 exit.
hdb_search: 6 does not match filter
hdb_search: 7 does not match filter
hdb_search: 8 does not match filter
hdb_search: 9 does not match filter
hdb_search: 10 does not match filter
send_ldap_result: conn=12 op=1 p=3
send_ldap_response: msgid=2 tag=101 err=0
ber_flush2: 14 bytes to sd 18
connection_get(18): got connid=12
connection_read(18): checking for input on id=12
ber_get_next
ber_get_next: tag 0x30 len 61 contents:
ber_get_next
conn=12 op=2 do_bind
ber_scanf fmt ({imt) ber:
ber_scanf fmt (m}) ber:
>>> dnPrettyNormal: <uid=ckabo,ou=people,dc=xxx,dc=com>
<<< dnPrettyNormal: <uid=ckabo,ou=people,dc=xxx,dc=com>, <uid=ckabo,ou=people,dc=xxx,dc=com>
do_bind: version=3 dn="uid=ckabo,ou=people,dc=xxx,dc=com" method=128
bdb_dn2entry("uid=ckabo,ou=people,dc=xxx,dc=com")
send_ldap_result: conn=12 op=2 p=3
send_ldap_response: msgid=3 tag=97 err=49
ber_flush2: 14 bytes to sd 18
connection_get(18): got connid=12
connection_read(18): checking for input on id=12
ber_get_next
ber_get_next: tag 0x30 len 45 contents:
ber_get_next
conn=12 op=3 do_bind
ber_scanf fmt ({imt) ber:
ber_scanf fmt (m}) ber:
>>> dnPrettyNormal: <cn=manager,dc=xxx,dc=com>
<<< dnPrettyNormal: <cn=manager,dc=xxx,dc=com>, <cn=manager,dc=xxx,dc=com>
do_bind: version=3 dn="cn=manager,dc=xxx,dc=com" method=128
do_bind: v3 bind: "cn=manager,dc=xxx,dc=com" to "cn=manager,dc=xxx,dc=com"
send_ldap_result: conn=12 op=3 p=3
send_ldap_response: msgid=4 tag=97 err=0
ber_flush2: 14 bytes to sd 18

```


As far as I can see I'm using the exact same settings on both machines.
Tried rebooting.
Can anybody see what might be the issue?
Thanks!

---

### Post by calle.kabo on 2008-12-22
Heh, I solved it!

```

/etc/init.d/nscd restart

```
on the bad machine did the trick ;)

---

