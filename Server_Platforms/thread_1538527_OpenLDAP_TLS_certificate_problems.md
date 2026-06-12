---
title: "OpenLDAP TLS certificate problems"
date: 2010-07-25
forum: Server Platforms
---

### Post by Shootfast on 2010-07-25
Hi,

I've been stuck for most of the day with the following issue. I'm following the guide [here]("https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html#openldap-tls") to secure my LDAP connections via TLS. Ubuntu server 10.04 64 bit.

I've got all the certificates creating correctly, and I've copied the CA certificate across to the client.

But when I change the /etc/ldap.conf file on the client from

```

base dc=example,dc=com
uri ldap://ldap/

```

to

```

base dc=example,dc=com
uri ldaps://ldap/
TLS_REQCERT demand
TLS_CACERT /etc/ssl/certs/ldap-ca-cert.pem

```

I can no longer connect :(

Running 
```
ldapsearch -d -1 -x -h ldap.example.com -ZZ -b dc=example,dc=com
```

Gives me the error:

```
TLS: peer cert untrusted or revoked (0x42)
TLS: can't connect: (unknown error code).
ldap_err2string
ldap_start_tls: Connect error (-11)
	additional info: (unknown error code)
```

Any ideas? I've got everything scripted to recreate the server, so I've started from scratch dozens of times. I've also chopped in pieces from 
[here]("http://www.opinsys.fi/en/setting-up-openldap-on-ubuntu-10-04-lucid-part2") But get the same results.

Thanks for any help you can give!

---

### Post by raghuprasad on 2010-08-04
I am facing the same problem. It seems to be a problem with gnutls library with which openldap utilities are linked to. Probably it is not able to verify the certificate provided by the server due to some reason. These problems have been reported in Debian forums too. Apparently the ldapsearch utility coming with lenny is broken while the one from etch works fine.

It is possible that the the CA certificate is not being understood correctly by the gnutls library. I have created my certificates using tinyCA2 which uses openssl. Somewhere on the web I have read that using certtool solves the problem. I have signed many certificates using my existing CA certificate. Hence I am inclined to avoid the change of CA certificate.

Anyway, I am still banging my head on this problem and any suggestions would be welcome.

Following are the relevant information in my setup (changed the identity related information everywhere):
--------------------
Input:
gnutls-cli --x509cafile /etc/ssl/certs/cacert.pem -p 636 ldap1.mydomain.co.in

Output:
Processed 1 CA certificate(s).
Resolving 'ldap1.mydomain.co.in'...
Connecting to '10.1.1.212:636'...
- Successfully sent 0 certificate(s) to server.
- Server has requested a certificate.
- Certificate type: X.509
 - Got a certificate list of 2 certificates.
  - Certificate[0] info:
    - subject `C=IN,ST=Maharashtra,L=Mumbai,O=Mydomain Technologies Pvt. Ltd.,OU=IT,CN=ldap1.mydomain.co.in,EMAIL=helpdesk@mydomain.co.in', issuer `C=IN,ST=Maharashtra,L=Mumbai,O=Mydomain Technologies Pvt. Ltd.,OU=IT,CN=Mydomain Certifying Authority,EMAIL=myemail@mydomain.co.in', RSA key 2048 bits, signed using RSA-SHA, activated `2010-07-30 10:29:05 UTC', expires `2012-07-29 10:29:05 UTC', SHA-1 fingerprint `46da833fcf2854124902f2fde8d62269eac57ddb'
     - Certificate[1] info:
       - subject `C=IN,ST=Maharashtra,L=Mumbai,O=Mydomain Technologies Pvt. Ltd.,OU=IT,CN=Mydomain Certifying Authority,EMAIL=myemail@mydomain.co.in', issuer `C=IN,ST=Maharashtra,L=Mumbai,O=Mydomain Technologies Pvt. Ltd.,OU=IT,CN=Mydomain Certifying Authority,EMAIL=myemail@mydomain.co.in', RSA key 2048 bits, signed using RSA-SHA, activated `2008-11-24 11:39:49 UTC', expires `2018-11-22 11:39:49 UTC', SHA-1 fingerprint `2f115200ea42073f3890bac52f1b02781bfbd748'
- The hostname in the certificate matches 'ldap1.mydomain.co.in'.
- Peer's certificate is trusted
- Version: TLS1.1
- Key Exchange: RSA
- Cipher: AES-128-CBC
- MAC: SHA1
- Compression: NULL
- Handshake was completed
    
- Simple Client Mode:
^C
------------------------------
Input:
cat /etc/ldap.conf

Output:
URI		ldaps://ldap1.mydomain.co.in
TLS_CACERT	/etc/ssl/certs/cacert.pem
TLS_REQCERT	allow
SSL		start_tls
-------------------------------
Input:
ldapsearch -ZZ -d 5 -b "dc=mydomain,dc=co,dc=in" -D "cn=admin,dc=mydomain,dc=co,dc=in" -x -W -H ldaps://ldap1.mydomain.co.in

Output:
ldap_url_parse_ext(ldaps://ldap1.mydomain.co.in)
ldap_create
ldap_url_parse_ext(ldaps://ldap1.mydomain.co.in:636/??base)
ldap_extended_operation_s
ldap_extended_operation
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP ldap1.mydomain.co.in:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 10.1.1.212:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
TLS: peer cert untrusted or revoked (0x42)
TLS: can't connect: (unknown error code).
ldap_err2string
ldap_start_tls: Can't contact LDAP server (-1)
        additional info: (unknown error code)
-----------------------------
Input:
ldapsearch  -d 5 -b "dc=mydomain,dc=co,dc=in" -D "cn=admin,dc=mydomain,dc=co,dc=in" -x -W -H ldap://ldap1.mydomain.co.in uid=bob mail

Output:
ldap_url_parse_ext(ldap://ldap1.mydomain.co.in)
ldap_create
ldap_url_parse_ext(ldap://ldap1.mydomain.co.in:389/??base)
Enter LDAP Password: 
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP ldap1.mydomain.co.in:389
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 10.1.1.212:389
ldap_pvt_connect: fd: 3 tm: -1 async: 0
ldap_open_defconn: successful
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({i) ber:
ber_flush2: 56 bytes to sd 3
ldap_result ld 0xb81242f8 msgid 1
wait4msg ld 0xb81242f8 msgid 1 (infinite timeout)
wait4msg continue ld 0xb81242f8 msgid 1 all 1
** ld 0xb81242f8 Connections:
* host: ldap1.mydomain.co.in  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Wed Aug  4 16:50:37 2010


** ld 0xb81242f8 Outstanding Requests:
 * msgid 1,  origid 1, status InProgress
   outstanding referrals 0, parent count 0
  ld 0xb81242f8 request count 1 (abandoned 0)
** ld 0xb81242f8 Response Queue:
   Empty
  ld 0xb81242f8 response count 0
ldap_chkResponseList ld 0xb81242f8 msgid 1 all 1
ldap_chkResponseList returns ld 0xb81242f8 NULL
ldap_int_select
read1msg: ld 0xb81242f8 msgid 1 all 1
ber_get_next
ber_get_next: tag 0x30 len 12 contents:
read1msg: ld 0xb81242f8 msgid 1 message type bind
ber_scanf fmt ({eAA) ber:
read1msg: ld 0xb81242f8 0 new referrals
read1msg:  mark request completed, ld 0xb81242f8 msgid 1
request done: ld 0xb81242f8 msgid 1
res_errno: 0, res_error: <>, res_matched: <>
ldap_free_request (origid 1, msgid 1)
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt (}) ber:
ldap_msgfree
# extended LDIF
#
# LDAPv3
# base <dc=mydomain,dc=co,dc=in> with scope subtree
# filter: uid=bob
# requesting: mail 
#
ldap_search_ext
put_filter: "uid=bob"
put_filter: default
put_simple_filter: "uid=bob"
ldap_build_search_req ATTRS: mail
ldap_send_initial_request
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_scanf fmt ({) ber:
ber_flush2: 72 bytes to sd 3
ldap_result ld 0xb81242f8 msgid -1
wait4msg ld 0xb81242f8 msgid -1 (infinite timeout)
wait4msg continue ld 0xb81242f8 msgid -1 all 0
** ld 0xb81242f8 Connections:
* host: ldap1.mydomain.co.in  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Wed Aug  4 16:50:37 2010


** ld 0xb81242f8 Outstanding Requests:
 * msgid 2,  origid 2, status InProgress
   outstanding referrals 0, parent count 0
  ld 0xb81242f8 request count 1 (abandoned 0)
** ld 0xb81242f8 Response Queue:
   Empty
  ld 0xb81242f8 response count 0
ldap_chkResponseList ld 0xb81242f8 msgid -1 all 0
ldap_chkResponseList returns ld 0xb81242f8 NULL
ldap_int_select
read1msg: ld 0xb81242f8 msgid -1 all 0
ber_get_next
ber_get_next: tag 0x30 len 96 contents:
read1msg: ld 0xb81242f8 msgid 2 message type search-entry
ldap_get_dn_ber
ber_scanf fmt ({ml{) ber:
ldap_dn2ufn
ldap_dn_normalize
=> ldap_bv2dn(uid=bob,dc=people,dc=mydomain,dc=co,dc=in,0)
<= ldap_bv2dn(uid=bob,dc=people,dc=mydomain,dc=co,dc=in)=0 
=> ldap_dn2bv(64)
<= ldap_dn2bv(bob, people.mydomain.co.in)=0 
# bob, people.mydomain.co.in
dn: uid=bob,dc=people,dc=mydomain,dc=co,dc=in
ber_scanf fmt ({xx) ber:
ldap_get_attribute_ber
ber_scanf fmt ({mM}) ber:
mail: [email]bob.marley@mydomain.co.in[/email]
ldap_get_attribute_ber
ldap_msgfree
ldap_result ld 0xb81242f8 msgid -1
wait4msg ld 0xb81242f8 msgid -1 (infinite timeout)
wait4msg continue ld 0xb81242f8 msgid -1 all 0
** ld 0xb81242f8 Connections:
* host: ldap1.mydomain.co.in  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Wed Aug  4 16:50:37 2010
** ld 0xb81242f8 Outstanding Requests:
 * msgid 2,  origid 2, status InProgress
   outstanding referrals 0, parent count 0
  ld 0xb81242f8 request count 1 (abandoned 0)
** ld 0xb81242f8 Response Queue:
   Empty
  ld 0xb81242f8 response count 0
ldap_chkResponseList ld 0xb81242f8 msgid -1 all 0
ldap_chkResponseList returns ld 0xb81242f8 NULL
ldap_int_select
read1msg: ld 0xb81242f8 msgid -1 all 0
ber_get_next
ber_get_next: tag 0x30 len 12 contents:
read1msg: ld 0xb81242f8 msgid 2 message type search-result
ber_scanf fmt ({eAA) ber:
read1msg: ld 0xb81242f8 0 new referrals
read1msg:  mark request completed, ld 0xb81242f8 msgid 2
request done: ld 0xb81242f8 msgid 2
res_errno: 0, res_error: <>, res_matched: <>
ldap_free_request (origid 2, msgid 2)

# search result
search: 2
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_scanf fmt (}) ber:
ldap_err2string
result: 0 Success
ldap_msgfree

# numResponses: 2
# numEntries: 1
ldap_free_connection 1 1
ldap_send_unbind
ber_flush2: 7 bytes to sd 3
ldap_free_connection: actually freed
-----------------------------
Input:
dpkg-query -W -f='${Package} ${Version} ${Source} ${Status}\n' | egrep 'slapd|ldap|gnutls'

Output:
gnutls-bin 2.8.5-2 gnutls26 install ok installed
ldap-auth-client 0.5.2  install ok installed
ldap-auth-config 0.5.2 ldap-auth-client install ok installed
ldap-utils 2.4.21-0ubuntu5 openldap install ok installed
libapache2-mod-gnutls 0.5.5-1 mod-gnutls install ok installed
libaprutil1-ldap 1.3.9+dfsg-3build1 apr-util install ok installed
libcurl3-gnutls 7.19.7-1ubuntu1 curl install ok installed
libgnutls26 2.8.5-2 gnutls26 install ok installed
libldap-2.4-2 2.4.21-0ubuntu5 openldap install ok installed
libneon27-gnutls 0.29.0-1 neon27 install ok installed
libnss-ldap 264-2ubuntu2  install ok installed
libpam-ldap 184-8.2ubuntu1  install ok installed
php-net-ldap2 2.0.7-1  install ok installed
php5-ldap 5.3.2-1ubuntu4.2 php5 install ok installed
phpldapadmin 1.1.0.7-1.2ubuntu2  deinstall ok config-files
python-ldap 2.3.10-1ubuntu1  install ok installed
slapd 2.4.21-0ubuntu5 openldap install ok installed
------------------------------

Hope it helps to identify anything which I missed so far.
By the way, slapd has no problem in its working. Without
TLS I can use the LDAP server everywhere.

Raghu

---

### Post by drzero on 2010-08-16
There seems to be a bug in ldap-utils which means that TLS_CACERT from ldap.conf is ignored. I worked around this problem by putting the CA certificate into ~/.ldapcert.pem, which ldapsearch and friends do seem to read.

I have reported this as bug #618715.

---

### Post by jetole on 2010-09-29
I thought I would mention that you can read this bug at [https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/618715](https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/618715)

---

### Post by luvshines on 2010-09-29
Well, I have such a setup working for over an year now :)

See if this helps:
[http://ubuntuforums.org/showthread.php?t=1031467](http://ubuntuforums.org/showthread.php?t=1031467)

---

### Post by luvshines on 2010-09-29
I noticed that you are using ldaps:// and -ZZ in ldapsearch.

Is that the correct method ??

My system gives an error "TSL already started"

[http://www.openldap.org/lists/openldap-software/200108/msg00910.html](http://www.openldap.org/lists/openldap-software/200108/msg00910.html)

Also, you are using /etc/ldap.conf for making all the configurations ??
What does your /etc/ldap/ldap.conf file reads ??

AFAIK

/etc/ldap.conf is using by nss_ldap not ldap-utils ie LDAP client commands will not refer that file - Its Man Page is 'man nss_ldap'

/etc/ldap/ldap.conf is referred by LDAP client commands - Its Man Page is 'man ldap.conf'
In case you have ~/.ldaprc file, this will override the /etc/ldap/ldap.conf file parameters

---

