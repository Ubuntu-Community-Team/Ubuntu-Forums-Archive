---
title: "LDAP installed, running but can't connect remotely"
date: 2011-03-17
forum: Server Platforms
---

### Post by casey.jordan@jorsek.com on 2011-03-17
Hi all,

I installed LDAP on my ubuntu 10.10 system, using the tutorial found here: [https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html)

Everything seems to be working well, when logged into the server via ssh I can run commands like:

> ldapsearch -xLLL -b "dc=easydita,dc=com" uid=john sn givenName cn

dn: uid=john,ou=people,dc=easydita,dc=com
sn: Doe
givenName: John
cn: John Doe

So I think that's a good sign that things are working well.

However I have had zero luck connecting to the server remotely via GUI tools or command line. I have tied JXplorer, and LDAP administration tool.

Running commands like this:

>  ldapsearch -xLLL -W -H ldap://ice.rit.edu -d1  "dc=easydita,dc=com"


ldap_url_parse_ext(ldap://ice.rit.edu)
ldap_create
ldap_url_parse_ext(ldap://ice.rit.edu:389/??base)
Enter LDAP Password: 
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP ice.rit.edu:389
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 127.0.0.1:389
ldap_pvt_connect: fd: 3 tm: -1 async: 0
ldap_open_defconn: successful
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({i) ber:
ber_flush2: 34 bytes to sd 3
ldap_result ld 0xb8940170 msgid 1
wait4msg ld 0xb8940170 msgid 1 (infinite timeout)
wait4msg continue ld 0xb8940170 msgid 1 all 1
** ld 0xb8940170 Connections:
* host: ice.rit.edu  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Thu Mar 17 19:42:29 2011


** ld 0xb8940170 Outstanding Requests:
 * msgid 1,  origid 1, status InProgress
   outstanding referrals 0, parent count 0
  ld 0xb8940170 request count 1 (abandoned 0)
** ld 0xb8940170 Response Queue:
   Empty
  ld 0xb8940170 response count 0
ldap_chkResponseList ld 0xb8940170 msgid 1 all 1
ldap_chkResponseList returns ld 0xb8940170 NULL
ldap_int_select
read1msg: ld 0xb8940170 msgid 1 all 1
ber_get_next
ber_get_next: tag 0x30 len 16 contents:
read1msg: ld 0xb8940170 msgid 1 message type bind
ber_scanf fmt ({eAA) ber:
read1msg: ld 0xb8940170 0 new referrals
read1msg:  mark request completed, ld 0xb8940170 msgid 1
request done: ld 0xb8940170 msgid 1
res_errno: 49, res_error: <>, res_matched: <>
ldap_free_request (origid 1, msgid 1)
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt (}) ber:
ldap_msgfree
ldap_err2string
**ldap_bind: Invalid credentials (49)**

I am pretty sure that I set up the admin password correctly, but the tutorial was not very specific about that. (Also could not find instructions on how to reset admin password.)

Given that it seems I have this *almost* set up correctly is there any steps I can take to correct this?

Thanks,

Casey

---

### Post by casey.jordan@jorsek.com on 2011-03-17
Additional info: I was told that this file might hold important information so I will post it:

/etc/ldap/slapd.d/cn=config/olcDatabase={0}config.ldif

dn: olcDatabase={0}config
objectClass: olcDatabaseConfig
olcDatabase: {0}config
olcAccess: {0}to * by dn.exact=cn=localroot,cn=config manage by * break
olcRootDN: cn=admin,cn=config
structuralObjectClass: olcDatabaseConfig
entryUUID: eca09490-e524-102f-87c5-17d7a82e8985
creatorsName: cn=config
createTimestamp: 20110317205733Z
entryCSN: 20110317205733.193089Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20110317205733Z

---

### Post by casey.jordan@jorsek.com on 2011-03-18
[Solved]

This was an error in my syntax not the ldap server itself.

Thanks

---

