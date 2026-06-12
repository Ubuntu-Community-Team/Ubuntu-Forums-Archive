---
title: "LDAP client would not connect to server (10.10)"
date: 2011-03-16
forum: Server Platforms
---

### Post by Jean-Michel C. on 2011-03-16
Hi there,
I am still grinding my teeth on my little Ubuntu set up at home and the topic of the week has been LDAP authentication.

So I installed OpenLDAP on my 10.10 server following steps [here]("https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html") in the official documentation.
From the server, it looks OK... LDAP utils scripts work and do send back meaningful information (as far as I can say).

I then turned towards my Ubuntu desktop to set up the client LDAP  authentication. I followed the step from the documentation but it was  going nowhere and failing miserably to login the LDAP user.

In order to understand what was going on, I uninstalled the libdnss-ldap and auth-client-config packages and installed ldapscipts.

Now, when I issue a :
[FONT=Courier New][COLOR=Navy]sudo ldapsearch -LLL -W -H ldaps://ubuntu-srv-1.kzo-corp.com -b ldapsearch -xLLL -b "dc=kzo-corp,dc=com" uid=antoine[/COLOR][/FONT]

I get:
[FONT=Courier New][COLOR=Red]ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)[/COLOR][/FONT]

Obviousky I can ping the server. I have no idea where to start looking and any help will be much appreciated.

Many thanks,

---

### Post by Jean-Michel C. on 2011-03-16
Forgot to mention that I do have the same reply when using ldapi instead of ldaps and I made sure the ldap daemon was running on the server.

Thanks in advance for your help.

---

### Post by Jean-Michel C. on 2011-03-17
OK, after cleaning my eyes and looking thru my shell history, I realised that my CLI ldapsearch was a bit stupid (and possibly this is why I did not get any replies ;)...

So I started again with a cleaner command and in debug mode...

Here is what I have...

For:
[FONT=Courier New][COLOR=Blue]sudo ldapsearch -LLL -W -H ldapi://ubuntu-srv-1 -d1 -b "dc=kzo-corp,dc=com"[/COLOR][/FONT]

I get:
[FONT=Courier New][COLOR=Red]ldap_url_parse_ext(ldapi://ubuntu-srv-1)
ldap_create
ldap_url_parse_ext(ldapi://ubuntu-srv-1/??base)
Enter LDAP Password: 
ldap_pvt_sasl_getmech
ldap_search
put_filter: "(objectclass=*)"
put_filter: simple
put_simple_filter: "objectclass=*"
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_path
ldap_new_socket: 3
ldap_connect_to_path: Trying ubuntu-srv-1
ldap_connect_timeout: fd: 3 tm: -1 async: 0
ldap_ndelay_on: 3
ldap_close_socket: 3
ldap_err2string
_**ldap_sasl_interactive_bind_s: Can't contact LDAP server (-1)**_[/COLOR][/FONT][FONT=Courier New][COLOR=Red]

[/COLOR][/FONT]It seems it cannot find the server...
But if I use the -h option instead of -H, ([COLOR=Blue]sudo ldapsearch -LLL -W -h 192.168.0.6 -d1 -b "dc=kzo-corp,dc=com"[/COLOR]), it seems to go a bit further, it finds the server, but fail to authenticate (find) a user:[FONT=Courier New][COLOR=Red]
ldap_create
ldap_url_parse_ext(ldap://192.168.0.6)
Enter LDAP Password: 
ldap_pvt_sasl_getmech
ldap_search
put_filter: "(objectclass=*)"
put_filter: simple
put_simple_filter: "objectclass=*"
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP 192.168.0.6:389
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 192.168.0.6:389
ldap_pvt_connect: fd: 3 tm: -1 async: 0
ldap_open_defconn: successful
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({) ber:
ber_flush2: 64 bytes to sd 3
ldap_result ld 0x214890c8 msgid 1
wait4msg ld 0x214890c8 msgid 1 (infinite timeout)
wait4msg continue ld 0x214890c8 msgid 1 all 1
** ld 0x214890c8 Connections:
* host: 192.168.0.6  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Thu Mar 17 14:12:52 2011


** ld 0x214890c8 Outstanding Requests:
 * msgid 1,  origid 1, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x214890c8 request count 1 (abandoned 0)
** ld 0x214890c8 Response Queue:
   Empty
  ld 0x214890c8 response count 0
ldap_chkResponseList ld 0x214890c8 msgid 1 all 1
ldap_chkResponseList returns ld 0x214890c8 NULL
ldap_int_select
read1msg: ld 0x214890c8 msgid 1 all 1
ber_get_next
ber_get_next: tag 0x30 len 66 contents:
read1msg: ld 0x214890c8 msgid 1 message type search-entry
wait4msg continue ld 0x214890c8 msgid 1 all 1
** ld 0x214890c8 Connections:
* host: 192.168.0.6  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Thu Mar 17 14:12:52 2011


** ld 0x214890c8 Outstanding Requests:
 * msgid 1,  origid 1, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x214890c8 request count 1 (abandoned 0)
** ld 0x214890c8 Response Queue:
 * msgid 1,  type 100
  ld 0x214890c8 response count 1
ldap_chkResponseList ld 0x214890c8 msgid 1 all 1
ldap_chkResponseList returns ld 0x214890c8 NULL
ldap_int_select
read1msg: ld 0x214890c8 msgid 1 all 1
ber_get_next
ber_get_next: tag 0x30 len 12 contents:
read1msg: ld 0x214890c8 msgid 1 message type search-result
ber_scanf fmt ({eAA) ber:
read1msg: ld 0x214890c8 0 new referrals
read1msg:  mark request completed, ld 0x214890c8 msgid 1
request done: ld 0x214890c8 msgid 1
res_errno: 0, res_error: <>, res_matched: <>
ldap_free_request (origid 1, msgid 1)
adding response ld 0x214890c8 msgid 1 type 101:
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt (}) ber:
ldap_get_values
ber_scanf fmt ({x{{a) ber:
ber_scanf fmt ([v]) ber:
ldap_msgfree
ldap_sasl_interactive_bind_s: server supports: DIGEST-MD5 NTLM CRAM-MD5
ldap_int_sasl_bind: DIGEST-MD5 NTLM CRAM-MD5
ldap_int_sasl_open: host=ubuntu-srv-1.kzo-corp.com
SASL/DIGEST-MD5 authentication started
ldap_sasl_bind_s
ldap_sasl_bind
ldap_send_initial_request
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({i) ber:
ber_flush2: 26 bytes to sd 3
ldap_result ld 0x214890c8 msgid 2
wait4msg ld 0x214890c8 msgid 2 (infinite timeout)
wait4msg continue ld 0x214890c8 msgid 2 all 1
** ld 0x214890c8 Connections:
* host: 192.168.0.6  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Thu Mar 17 14:12:52 2011


** ld 0x214890c8 Outstanding Requests:
 * msgid 2,  origid 2, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x214890c8 request count 1 (abandoned 0)
** ld 0x214890c8 Response Queue:
   Empty
  ld 0x214890c8 response count 0
ldap_chkResponseList ld 0x214890c8 msgid 2 all 1
ldap_chkResponseList returns ld 0x214890c8 NULL
ldap_int_select
read1msg: ld 0x214890c8 msgid 2 all 1
ber_get_next
ber_get_next: tag 0x30 len 266 contents:
read1msg: ld 0x214890c8 msgid 2 message type bind
ber_scanf fmt ({eAA) ber:
read1msg: ld 0x214890c8 0 new referrals
read1msg:  mark request completed, ld 0x214890c8 msgid 2
request done: ld 0x214890c8 msgid 2
res_errno: 14, res_error: <SASL(0): successful result: security flags do not match required>, res_matched: <>
ldap_free_request (origid 2, msgid 2)
ldap_parse_sasl_bind_result
ber_scanf fmt ({eAA) ber:
ber_scanf fmt (O) ber:
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt (x) ber:
ber_scanf fmt (}) ber:
ldap_msgfree
sasl_client_step: 2
sasl_client_step: 1
ldap_sasl_bind_s
ldap_sasl_bind
ldap_send_initial_request
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({i) ber:
ber_flush2: 318 bytes to sd 3
ldap_result ld 0x214890c8 msgid 3
wait4msg ld 0x214890c8 msgid 3 (infinite timeout)
wait4msg continue ld 0x214890c8 msgid 3 all 1
** ld 0x214890c8 Connections:
* host: 192.168.0.6  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Thu Mar 17 14:12:52 2011


** ld 0x214890c8 Outstanding Requests:
 * msgid 3,  origid 3, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x214890c8 request count 1 (abandoned 0)
** ld 0x214890c8 Response Queue:
   Empty
  ld 0x214890c8 response count 0
ldap_chkResponseList ld 0x214890c8 msgid 3 all 1
ldap_chkResponseList returns ld 0x214890c8 NULL
ldap_int_select
read1msg: ld 0x214890c8 msgid 3 all 1
ber_get_next
ber_get_next: tag 0x30 len 60 contents:
read1msg: ld 0x214890c8 msgid 3 message type bind
ber_scanf fmt ({eAA) ber:
read1msg: ld 0x214890c8 0 new referrals
read1msg:  mark request completed, ld 0x214890c8 msgid 3
request done: ld 0x214890c8 msgid 3
res_errno: 49, res_error: <SASL(-13): user not found: no secret in database>, res_matched: <>
ldap_free_request (origid 3, msgid 3)
ldap_parse_sasl_bind_result
ber_scanf fmt ({eAA) ber:
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt (}) ber:
ldap_msgfree
ldap_err2string
[U][B]ldap_sasl_interactive_bind_s: Invalid credentials (49)
    additional info: SASL(-13): user not found: no secret in database[/B][/U][/COLOR][/FONT]

I will probably re-install ldap on the server side and reconfigure from scratch, but I woul still like to understand what is going on...

As well, where are the slapd logs on the server side?

Thanks in advance for your help...

Jean-Michel

---

### Post by Jean-Michel C. on 2011-03-18
OK, I did reinstall everything and realised my mistake.

I stupidly had a different password for the LDAP root user in teh frontend and backend ldif files. Now that this is correct, I can ldapsearch (the so connect) to my LDAP server from the client...

I still cannot authenticate though, but as it is a different issue, I will open another thread.

---

