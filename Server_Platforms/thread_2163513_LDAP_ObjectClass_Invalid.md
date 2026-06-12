---
title: "LDAP ObjectClass Invalid"
date: 2013-07-18
forum: Server Platforms
---

### Post by sandyd on 2013-07-18
I have been working on syncrepl to create a slave LDAP server to speed up LDAP queries on a remote machine.

So far, everything works except for an issue with the slave not recognizing an object class.

Any easy way I can find what it is choking on, and identify the correct schema to add?

debug log below
```
** ld 0x7fa7bc108f50 Outstanding Requests:
 * msgid 1,  origid 1, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x7fa7bc108f50 request count 1 (abandoned 0)
** ld 0x7fa7bc108f50 Response Queue:
   Empty
  ld 0x7fa7bc108f50 response count 0
ldap_chkResponseList ld 0x7fa7bc108f50 msgid 1 all 1
ldap_chkResponseList returns ld 0x7fa7bc108f50 NULL
ldap_int_select
51e83440 >>> slap_listener(ldap:///)
51e83440 connection_get(12): got connid=1000
51e83440 connection_read(12): checking for input on id=1000
ber_get_next
ber_get_next: tag 0x30 len 74 contents:
51e83440 op tag 0x60, time 1374172224
ber_get_next
51e83440 conn=1000 op=0 do_bind
ber_scanf fmt ({imt) ber:
ber_scanf fmt (m}) ber:
51e83440 >>> dnPrettyNormal: <cn=bind bind,ou=people,dc=sandydpnet,dc=me>
51e83440 <<< dnPrettyNormal: <cn=bind bind,ou=people,dc=sandydpnet,dc=me>, <cn=bind bind,ou=people,dc=sandydpnet,dc=me>
51e83440 do_bind: version=3 dn="cn=bind bind,ou=people,dc=sandydpnet,dc=me" method=128
51e83440 send_ldap_result: conn=1000 op=0 p=3
51e83440 send_ldap_response: msgid=1 tag=97 err=49
ber_flush2: 14 bytes to sd 12
read1msg: ld 0x7fa7bc108f50 msgid 1 all 1
ber_get_next
ber_get_next: tag 0x30 len 12 contents:
read1msg: ld 0x7fa7bc108f50 msgid 1 message type bind
ber_scanf fmt ({eAA) ber:
read1msg: ld 0x7fa7bc108f50 0 new referrals
read1msg:  mark request completed, ld 0x7fa7bc108f50 msgid 1
request done: ld 0x7fa7bc108f50 msgid 1
res_errno: 49, res_error: <>, res_matched: <>
ldap_free_request (origid 1, msgid 1)
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt (}) ber:
ldap_msgfree
ldap_search_ext
put_filter: "(objectclass=*)"
put_filter: simple
put_simple_filter: "objectclass=*"
ldap_send_initial_request
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({) ber:
ber_flush2: 144 bytes to sd 10
51e83440 =>do_syncrep2 rid=001
ldap_result ld 0x7fa7bc100910 msgid 2
wait4msg ld 0x7fa7bc100910 msgid 2 (infinite timeout)
wait4msg continue ld 0x7fa7bc100910 msgid 2 all 0
** ld 0x7fa7bc100910 Connections:
* host: 172.16.1.104  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Thu Jul 18 22:30:24 2013


** ld 0x7fa7bc100910 Outstanding Requests:
 * msgid 2,  origid 2, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x7fa7bc100910 request count 1 (abandoned 0)
** ld 0x7fa7bc100910 Response Queue:
   Empty
  ld 0x7fa7bc100910 response count 0
ldap_chkResponseList ld 0x7fa7bc100910 msgid 2 all 0
ldap_chkResponseList returns ld 0x7fa7bc100910 NULL
ldap_int_select
read1msg: ld 0x7fa7bc100910 msgid 2 all 0
ber_get_next
wait4msg continue ld 0x7fa7bc100910 msgid 2 all 0
** ld 0x7fa7bc100910 Connections:
* host: 172.16.1.104  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Thu Jul 18 22:30:24 2013


** ld 0x7fa7bc100910 Outstanding Requests:
 * msgid 2,  origid 2, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x7fa7bc100910 request count 1 (abandoned 0)
** ld 0x7fa7bc100910 Response Queue:
   Empty
  ld 0x7fa7bc100910 response count 0
ldap_chkResponseList ld 0x7fa7bc100910 msgid 2 all 0
ldap_chkResponseList returns ld 0x7fa7bc100910 NULL
ldap_int_select
read1msg: ld 0x7fa7bc100910 msgid 2 all 0
ber_get_next
ber_get_next: tag 0x30 len 2680 contents:
read1msg: ld 0x7fa7bc100910 msgid 2 message type search-entry
ber_scanf fmt ({xx) ber:
ber_scanf fmt ({a) ber:
ber_scanf fmt (o) ber:
ldap_get_dn_ber
ber_scanf fmt ({ml{) ber:
ber_scanf fmt ({em) ber:
ldap_get_dn_ber
ber_scanf fmt ({ml{) ber:
51e83440 >>> dnPrettyNormal: <dc=sandydpnet,dc=me>
51e83440 <<< dnPrettyNormal: <dc=sandydpnet,dc=me>, <dc=sandydpnet,dc=me>
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
51e83440 >>> dnPretty: <cn=admin,dc=sandydpnet,dc=me>
51e83440 <<< dnPretty: <cn=admin,dc=sandydpnet,dc=me>
51e83440 >>> dnNormalize: <cn=admin,dc=sandydpnet,dc=me>
51e83440 <<< dnNormalize: <cn=admin,dc=sandydpnet,dc=me>
51e83440 syncrepl_message_to_entry: rid=001 mods check (objectClass: value #0 invalid per syntax)
ldap_msgfree
ldap_free_request (origid 2, msgid 2)
ldap_free_connection 1 1
ldap_send_unbind
ber_flush2: 7 bytes to sd 10
ldap_free_connection: actually freed
51e83440 do_syncrepl: rid=001 rc 21 retrying (4 retries left)
51e83445 =>do_syncrepl rid=001
ldap_create
ldap_url_parse_ext(ldap://172.16.1.104:389/)
ldap_sasl_bind_s
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP 172.16.1.104:389
ldap_new_socket: 10
ldap_prepare_socket: 10
ldap_connect_to_host: Trying 172.16.1.104:389
ldap_pvt_connect: fd: 10 tm: -1 async: 0
ldap_open_defconn: successful
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({i) ber:
ber_flush2: 76 bytes to sd 10
ldap_result ld 0x7fa7b8000a80 msgid 1
wait4msg ld 0x7fa7b8000a80 msgid 1 (infinite timeout)
wait4msg continue ld 0x7fa7b8000a80 msgid 1 all 1
** ld 0x7fa7b8000a80 Connections:
* host: 172.16.1.104  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Thu Jul 18 22:30:29 2013


** ld 0x7fa7b8000a80 Outstanding Requests:
 * msgid 1,  origid 1, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x7fa7b8000a80 request count 1 (abandoned 0)
** ld 0x7fa7b8000a80 Response Queue:
   Empty
  ld 0x7fa7b8000a80 response count 0
ldap_chkResponseList ld 0x7fa7b8000a80 msgid 1 all 1
ldap_chkResponseList returns ld 0x7fa7b8000a80 NULL
ldap_int_select
read1msg: ld 0x7fa7b8000a80 msgid 1 all 1
ber_get_next
ber_get_next: tag 0x30 len 12 contents:
read1msg: ld 0x7fa7b8000a80 msgid 1 message type bind
ber_scanf fmt ({eAA) ber:
read1msg: ld 0x7fa7b8000a80 0 new referrals
read1msg:  mark request completed, ld 0x7fa7b8000a80 msgid 1
request done: ld 0x7fa7b8000a80 msgid 1
res_errno: 0, res_error: <>, res_matched: <>
ldap_free_request (origid 1, msgid 1)
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt (}) ber:
ldap_msgfree
51e83445 =>ldap_back_getconn: conn 0x7fa7bc108ed0 fetched refcnt=1.
ldap_sasl_bind
ldap_send_initial_request
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({i) ber:
ber_flush2: 76 bytes to sd 11
ldap_result ld 0x7fa7bc108f50 msgid 2
wait4msg ld 0x7fa7bc108f50 msgid 2 (timeout 100000 usec)
wait4msg continue ld 0x7fa7bc108f50 msgid 2 all 1
** ld 0x7fa7bc108f50 Connections:
* host: localhost  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Thu Jul 18 22:30:29 2013


** ld 0x7fa7bc108f50 Outstanding Requests:
 * msgid 2,  origid 2, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x7fa7bc108f50 request count 1 (abandoned 0)
** ld 0x7fa7bc108f50 Response Queue:
   Empty
  ld 0x7fa7bc108f50 response count 0
ldap_chkResponseList ld 0x7fa7bc108f50 msgid 2 all 1
ldap_chkResponseList returns ld 0x7fa7bc108f50 NULL
ldap_int_select
51e83445 connection_get(12): got connid=1000
51e83445 connection_read(12): checking for input on id=1000
ber_get_next
ber_get_next: tag 0x30 len 74 contents:
51e83445 op tag 0x60, time 1374172229
ber_get_next
51e83445 conn=1000 op=1 do_bind
ber_scanf fmt ({imt) ber:
ber_scanf fmt (m}) ber:
51e83445 >>> dnPrettyNormal: <cn=bind bind,ou=people,dc=sandydpnet,dc=me>
51e83445 <<< dnPrettyNormal: <cn=bind bind,ou=people,dc=sandydpnet,dc=me>, <cn=bind bind,ou=people,dc=sandydpnet,dc=me>
51e83445 do_bind: version=3 dn="cn=bind bind,ou=people,dc=sandydpnet,dc=me" method=128
51e83445 send_ldap_result: conn=1000 op=1 p=3
51e83445 send_ldap_response: msgid=2 tag=97 err=49
ber_flush2: 14 bytes to sd 12
read1msg: ld 0x7fa7bc108f50 msgid 2 all 1
ber_get_next
ber_get_next: tag 0x30 len 12 contents:
read1msg: ld 0x7fa7bc108f50 msgid 2 message type bind
ber_scanf fmt ({eAA) ber:
read1msg: ld 0x7fa7bc108f50 0 new referrals
read1msg:  mark request completed, ld 0x7fa7bc108f50 msgid 2
request done: ld 0x7fa7bc108f50 msgid 2
res_errno: 49, res_error: <>, res_matched: <>
ldap_free_request (origid 2, msgid 2)
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt (}) ber:
ldap_msgfree
ldap_search_ext
put_filter: "(objectclass=*)"
put_filter: simple
put_simple_filter: "objectclass=*"
ldap_send_initial_request
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({) ber:
ber_flush2: 144 bytes to sd 10
51e83445 =>do_syncrep2 rid=001
ldap_result ld 0x7fa7b8000a80 msgid 2
wait4msg ld 0x7fa7b8000a80 msgid 2 (infinite timeout)
wait4msg continue ld 0x7fa7b8000a80 msgid 2 all 0
** ld 0x7fa7b8000a80 Connections:
* host: 172.16.1.104  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Thu Jul 18 22:30:29 2013


** ld 0x7fa7b8000a80 Outstanding Requests:
 * msgid 2,  origid 2, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x7fa7b8000a80 request count 1 (abandoned 0)
** ld 0x7fa7b8000a80 Response Queue:
   Empty
  ld 0x7fa7b8000a80 response count 0
ldap_chkResponseList ld 0x7fa7b8000a80 msgid 2 all 0
ldap_chkResponseList returns ld 0x7fa7b8000a80 NULL
ldap_int_select
read1msg: ld 0x7fa7b8000a80 msgid 2 all 0
ber_get_next
ber_get_next: tag 0x30 len 2680 contents:
read1msg: ld 0x7fa7b8000a80 msgid 2 message type search-entry
ber_scanf fmt ({xx) ber:
ber_scanf fmt ({a) ber:
ber_scanf fmt (o) ber:
ldap_get_dn_ber
ber_scanf fmt ({ml{) ber:
ber_scanf fmt ({em) ber:
ldap_get_dn_ber
ber_scanf fmt ({ml{) ber:
51e83445 >>> dnPrettyNormal: <dc=sandydpnet,dc=me>
51e83445 <<< dnPrettyNormal: <dc=sandydpnet,dc=me>, <dc=sandydpnet,dc=me>
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
ber_scanf fmt ({mW}) ber:
51e83445 >>> dnPretty: <cn=admin,dc=sandydpnet,dc=me>
51e83445 <<< dnPretty: <cn=admin,dc=sandydpnet,dc=me>
51e83445 >>> dnNormalize: <cn=admin,dc=sandydpnet,dc=me>
51e83445 <<< dnNormalize: <cn=admin,dc=sandydpnet,dc=me>
51e83445 syncrepl_message_to_entry: rid=001 mods check (objectClass: value #0 invalid per syntax)
ldap_msgfree
ldap_free_request (origid 2, msgid 2)
ldap_free_connection 1 1
ldap_send_unbind
ber_flush2: 7 bytes to sd 10
ldap_free_connection: actually freed
51e83445 do_syncrepl: rid=001 rc 21 retrying (3 retries left)
^C51e83446 daemon: shutdown requested and initiated.
51e83446 connection_close: conn=1000 sd=12
51e83446 =>ldap_back_conn_destroy: fetching conn 1000
51e83446 slapd shutdown: waiting for 0 operations/tasks to finish
51e83446 slapd shutdown: initiated
51e83446 slapd destroy: freeing system resources.
51e83446 syncinfo_free: rid=001
ldap_free_connection 1 1
ldap_send_unbind
ber_flush2: 7 bytes to sd 11
ldap_free_connection: actually freed
51e83446 slapd stopped.
```

---

