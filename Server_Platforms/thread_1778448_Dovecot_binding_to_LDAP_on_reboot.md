---
title: "Dovecot binding to LDAP on reboot"
date: 2011-06-09
forum: Server Platforms
---

### Post by ZuOverture on 2011-06-09
Hi again.

Today I'm trying to configure Postfix+Dovecot to use Samba4's LDAP database for authorisation and mail delivery. As I can see from /var/log/mail.log, Dovecot tries to bind to LDAP right after reboot , but fails:
```
pdcadmin@PDC1:~$ cat /var/log/mail.log
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_bind
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_simple_bind
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_sasl_bind
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_send_initial_request
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_new_connection 1 1 0
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_int_open_connection
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_connect_to_host: TCP mydomain.dyndns.com:389
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_connect_to_host: getaddrinfo failed: Temporary failure in name resolution
Jun  9 13:06:46 PDC1 dovecot: auth(default): LDAP: Can't connect to server: ldap://mydomain.dyndns.com
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_unbind
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_create
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_url_parse_ext(ldap://mydomain.dyndns.com)
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_bind
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_simple_bind
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_sasl_bind
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_send_initial_request
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_new_connection 1 1 0
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_int_open_connection
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_connect_to_host: TCP mydomain.dyndns.com:389
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_connect_to_host: getaddrinfo failed: Temporary failure in name resolution
Jun  9 13:06:46 PDC1 dovecot: auth(default): LDAP: Can't connect to server: ldap://mydomain.dyndns.com
Jun  9 13:06:46 PDC1 dovecot: auth(default): ldap_unbind
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_bind
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_simple_bind
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_sasl_bind
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_send_initial_request
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_new_connection 1 1 0
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_int_open_connection
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_connect_to_host: TCP mydomain.dyndns.com:389
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_connect_to_host: getaddrinfo failed: Temporary failure in name resolution
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): LDAP: Can't connect to server: ldap://mydomain.dyndns.com
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_unbind
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_create
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_url_parse_ext(ldap://mydomain.dyndns.com)
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_bind
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_simple_bind
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_sasl_bind
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_send_initial_request
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_new_connection 1 1 0
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_int_open_connection
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_connect_to_host: TCP mydomain.dyndns.com:389
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_connect_to_host: getaddrinfo failed: Temporary failure in name resolution
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): LDAP: Can't connect to server: ldap://mydomain.dyndns.com
Jun  9 13:06:46 PDC1 dovecot: auth-worker(default): ldap_unbind
```
Then I do "sudo service dovecot restart" magic, and look into mail.log again:
```
Jun  9 13:07:55 PDC1 dovecot: managesieve-login: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun  9 13:07:55 PDC1 dovecot: auth(default): Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun  9 13:07:55 PDC1 dovecot: imap-login: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun  9 13:07:55 PDC1 dovecot: managesieve-login: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun  9 13:07:55 PDC1 dovecot: pop3-login: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun  9 13:07:55 PDC1 dovecot: dovecot: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jun  9 13:07:55 PDC1 dovecot: Dovecot v1.2.15 starting up (core dumps disabled)
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_bind
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_simple_bind
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_sasl_bind
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_send_initial_request
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_new_connection 1 1 0
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_int_open_connection
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_connect_to_host: TCP mydomain.dyndns.com:389
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_new_socket: 13
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_prepare_socket: 13
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_connect_to_host: Trying 192.168.0.200:389
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_pvt_connect: fd: 13 tm: -1 async: 0
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_open_defconn: successful
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_send_server_request
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_bind
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_simple_bind
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_sasl_bind
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_send_initial_request
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_new_connection 1 1 0
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_int_open_connection
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_connect_to_host: TCP mydomain.dyndns.com:389
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_new_socket: 8
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_prepare_socket: 8
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_connect_to_host: Trying 192.168.0.200:389
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_pvt_connect: fd: 8 tm: -1 async: 0
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_open_defconn: successful
Jun  9 13:07:55 PDC1 dovecot: auth-worker(default): ldap_send_server_request
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_result ld 0x7f1d8b0b2440 msgid -1
Jun  9 13:07:55 PDC1 dovecot: auth(default): wait4msg ld 0x7f1d8b0b2440 msgid -1 (timeout 0 usec)
Jun  9 13:07:55 PDC1 dovecot: auth(default): wait4msg continue ld 0x7f1d8b0b2440 msgid -1 all 1
Jun  9 13:07:55 PDC1 dovecot: auth(default): ** ld 0x7f1d8b0b2440 Connections:
Jun  9 13:07:55 PDC1 dovecot: auth(default): * host: mydomain.dyndns.com  port: 389  (default)
Jun  9 13:07:55 PDC1 dovecot: auth(default):   refcnt: 2  status: Connected
Jun  9 13:07:55 PDC1 dovecot: auth(default):   last used: Thu Jun  9 13:07:55 2011
Jun  9 13:07:55 PDC1 dovecot: auth(default):
Jun  9 13:07:55 PDC1 dovecot: auth(default):
Jun  9 13:07:55 PDC1 dovecot: auth(default): ** ld 0x7f1d8b0b2440 Outstanding Requests:
Jun  9 13:07:55 PDC1 dovecot: auth(default):  * msgid 1,  origid 1, status InProgress
Jun  9 13:07:55 PDC1 dovecot: auth(default):    outstanding referrals 0, parent count 0
Jun  9 13:07:55 PDC1 dovecot: auth(default):   ld 0x7f1d8b0b2440 request count 1 (abandoned 0)
Jun  9 13:07:55 PDC1 dovecot: auth(default): ** ld 0x7f1d8b0b2440 Response Queue:
Jun  9 13:07:55 PDC1 dovecot: auth(default):    Empty
Jun  9 13:07:55 PDC1 dovecot: auth(default):   ld 0x7f1d8b0b2440 response count 0
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_chkResponseList ld 0x7f1d8b0b2440 msgid -1 all 1
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_chkResponseList returns ld 0x7f1d8b0b2440 NULL
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_int_select
Jun  9 13:07:55 PDC1 dovecot: auth(default): read1msg: ld 0x7f1d8b0b2440 msgid -1 all 1
Jun  9 13:07:55 PDC1 dovecot: auth(default): read1msg: ld 0x7f1d8b0b2440 msgid 1 message type bind
Jun  9 13:07:55 PDC1 dovecot: auth(default): read1msg: ld 0x7f1d8b0b2440 0 new referrals
Jun  9 13:07:55 PDC1 dovecot: auth(default): read1msg:  mark request completed, ld 0x7f1d8b0b2440 msgid 1
Jun  9 13:07:55 PDC1 dovecot: auth(default): request done: ld 0x7f1d8b0b2440 msgid 1
Jun  9 13:07:55 PDC1 dovecot: auth(default): res_errno: 0, res_error: <>, res_matched: <>
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_free_request (origid 1, msgid 1)
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_parse_result
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_msgfree
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_result ld 0x7f1d8b0b2440 msgid -1
Jun  9 13:07:55 PDC1 dovecot: auth(default): wait4msg ld 0x7f1d8b0b2440 msgid -1 (timeout 0 usec)
Jun  9 13:07:55 PDC1 dovecot: auth(default): wait4msg continue ld 0x7f1d8b0b2440 msgid -1 all 1
Jun  9 13:07:55 PDC1 dovecot: auth(default): ** ld 0x7f1d8b0b2440 Connections:
Jun  9 13:07:55 PDC1 dovecot: auth(default): * host: mydomain.dyndns.com  port: 389  (default)
Jun  9 13:07:55 PDC1 dovecot: auth(default):   refcnt: 1  status: Connected
Jun  9 13:07:55 PDC1 dovecot: auth(default):   last used: Thu Jun  9 13:07:55 2011
Jun  9 13:07:55 PDC1 dovecot: auth(default):
Jun  9 13:07:55 PDC1 dovecot: auth(default):
Jun  9 13:07:55 PDC1 dovecot: auth(default): ** ld 0x7f1d8b0b2440 Outstanding Requests:
Jun  9 13:07:55 PDC1 dovecot: auth(default):    Empty
Jun  9 13:07:55 PDC1 dovecot: auth(default):   ld 0x7f1d8b0b2440 request count 0 (abandoned 0)
Jun  9 13:07:55 PDC1 dovecot: auth(default): ** ld 0x7f1d8b0b2440 Response Queue:
Jun  9 13:07:55 PDC1 dovecot: auth(default):    Empty
Jun  9 13:07:55 PDC1 dovecot: auth(default):   ld 0x7f1d8b0b2440 response count 0
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_chkResponseList ld 0x7f1d8b0b2440 msgid -1 all 1
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_chkResponseList returns ld 0x7f1d8b0b2440 NULL
Jun  9 13:07:55 PDC1 dovecot: auth(default): ldap_int_select
```
Believing this to be a sign of succesfull bind, I couldn't understand the reason behind it. Why do I need to restart or reload dovecot service to make it work (though it fails on the next step with "dict_ldap_lookup: Search error 1: Operations error" and "451 4.3.0 ... Temporary lookup failure")?

---

### Post by ZuOverture on 2011-06-10
I suppose, this forum is useless... :???:

---

### Post by ZuOverture on 2011-06-10
Solved.
Filtering out LDAP queries in pass_filter and user_filter was wrong.

---

