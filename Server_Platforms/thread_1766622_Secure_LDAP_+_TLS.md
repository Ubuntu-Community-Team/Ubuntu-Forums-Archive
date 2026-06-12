---
title: "Secure LDAP + TLS"
date: 2011-05-24
forum: Server Platforms
---

### Post by mayankraj on 2011-05-24
I have got LDAP server running on Ubuntu 10.04 and configured according to community documentation.

When I have the following configuration in my /etc/default/slapd
SLAPD_SERVICES="ldap:/// ldapi:/// ldaps:///" 

ldapsearch -x -h ldap-server-name -ZZ -b dc=example,dc=edu
It works correctly and returns me back the results

But when I want the ldap server to run only ldaps services, i.e.
SLAPD_SERVICES="ldaps://ldap-server-name

ldapsearch -d -1 -x -h ldap-server-name -ZZ -b dc=example,dc=edu

ldap_create
ldap_url_parse_ext(ldap://ldap-server-name)
ldap_extended_operation_s
ldap_extended_operation
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP ldap-server-name:389
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying ldap-server-ip-address:389
ldap_pvt_connect: fd: 3 tm: -1 async: 0
ldap_close_socket: 3
ldap_err2string
ldap_start_tls: Can't contact LDAP server (-1)

Why is it trying to connect to on port 389. Shouldn't it connect on port 636 for secure ldap connection. In the first config it succeeded when forcing the TLS connection to start. So shouldn't it work with only secure ldap enabled.

Am I missing something??

Thanks
Mayank

---

### Post by mayankraj on 2011-05-24
Ok maybe I need to make the server to listen to port 389
SLAPD_SERVICES="ldaps://ldap-server-name:389

with ldapsearch -d -1 -x -h ldap-server-name -ZZ -b dc=example,dc=edu

I get the following error

ldap_create
ldap_url_parse_ext(ldap://ldap-server-name)
ldap_extended_operation_s
ldap_extended_operation
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP tldap-server-name:389
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying ldap-serverip-address:389
ldap_pvt_connect: fd: 3 tm: -1 async: 0
ldap_open_defconn: successful
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_dump: buf=0xb8edcea8 ptr=0xb8edcea8 end=0xb8edcec7 len=31
  0000:  30 1d 02 01 01 77 18 80  16 31 2e 33 2e 36 2e 31   0....w...1.3.6.1  
  0010:  2e 34 2e 31 2e 31 34 36  36 2e 32 30 30 33 37      .4.1.1466.20037   
ber_scanf fmt ({) ber:
ber_dump: buf=0xb8edcea8 ptr=0xb8edcead end=0xb8edcec7 len=26
  0000:  77 18 80 16 31 2e 33 2e  36 2e 31 2e 34 2e 31 2e   w...1.3.6.1.4.1.  
  0010:  31 34 36 36 2e 32 30 30  33 37                     1466.20037        
ber_flush2: 31 bytes to sd 3
  0000:  30 1d 02 01 01 77 18 80  16 31 2e 33 2e 36 2e 31   0....w...1.3.6.1  
  0010:  2e 34 2e 31 2e 31 34 36  36 2e 32 30 30 33 37      .4.1.1466.20037   
ldap_write: want=31, written=31
  0000:  30 1d 02 01 01 77 18 80  16 31 2e 33 2e 36 2e 31   0....w...1.3.6.1  
  0010:  2e 34 2e 31 2e 31 34 36  36 2e 32 30 30 33 37      .4.1.1466.20037   
ldap_result ld 0xb8ed4d28 msgid 1
wait4msg ld 0xb8ed4d28 msgid 1 (infinite timeout)
wait4msg continue ld 0xb8ed4d28 msgid 1 all 1
** ld 0xb8ed4d28 Connections:
* host: ldap-server-name  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Tue May 24 15:46:04 2011


** ld 0xb8ed4d28 Outstanding Requests:
 * msgid 1,  origid 1, status InProgress
   outstanding referrals 0, parent count 0
  ld 0xb8ed4d28 request count 1 (abandoned 0)
** ld 0xb8ed4d28 Response Queue:
   Empty
  ld 0xb8ed4d28 response count 0
ldap_chkResponseList ld 0xb8ed4d28 msgid 1 all 1
ldap_chkResponseList returns ld 0xb8ed4d28 NULL
ldap_int_select
read1msg: ld 0xb8ed4d28 msgid 1 all 1
ber_get_next
ldap_read: want=8, got=0

ber_get_next failed.
ldap_err2string
ldap_start_tls: Can't contact LDAP server (-1)

---

### Post by luvshines on 2011-06-14
What does it say if you let the ldaps run on default port 636 and modify the ldapsearch command as:
```
ldapsearch -d -1 -x -H ldaps://ldap-server-name -b dc=example,dc=edu 
```

---

