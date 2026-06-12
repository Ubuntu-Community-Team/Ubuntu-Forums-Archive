---
title: "openldap-ssl issue"
date: 2009-06-22
forum: Server Platforms
---

### Post by asmii on 2009-06-22
I don't know whether this is the proper forum to post this question or not, but getting no way out, I am posting it here.

For last couple of days, I am busy configuring LDAP, SSL for LDAP so that I can enable LDAP server and so that I can use LDAP for user login on my system on which Ubuntu 9.04 is installed.

For the same, I installed several packages following the steps mentioned in ubuntu help.

I have following configuration entries :

In /etc/default/slapd :

```
SLAPD_SERVICES="ldaps:///"
```In /etc/ldap/ldap.conf

```
BASE dc=ldap,dc=company,dc=com
URI ldaps:///
TLS_CERT /etc/ssl/certs/server.crt
TLS_KEY /etc/ssl/private/server.key
TLS_CACERT /etc/ssl/certs/cacert.pem
```There is no problem in starting slapd as such.

ps shows the following :

```
openldap  7745     1  0 17:15 ?        00:00:00 /usr/sbin/slapd -h ldaps:/// -g openldap -u openldap -F /etc/ldap/slapd.d/
```netstat -plane |grep ":636" shows the following :

```
tcp        0      0 0.0.0.0:636             0.0.0.0:*               LISTEN      0          4392917     7745/slapd      
tcp6       0      0 :::636                  :::*                    LISTEN      0          4392918     7745/slapd   
```But still when I perform "ldapsearch -x", I got following error :

```
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
```When I add "ldap:/// ldapi:///" to /etc/default/ldap along with "ldaps///" and commented BASE and URL entry in ldap.conf, "ldapsearch -x" works fine.

I think there is something wrong in SSL

Also if I enable ldap for paswd, shadow etc in /etc/nsswitch.conf, ssh to server doesn't work (I have imported all groups and users to ldap).

I wonder what may have gone wrong.

Please help me.

-Asmii

---

### Post by asmii on 2009-06-22
I did the following changes in ldap.conf

```
BASE dc=company,dc=com
URI ldaps://ldap.company.com
TLS_REQCERT allow
#TLS_REQCERT demand
TLS_CERT /etc/ssl/certs/server.crt
TLS_KEY /etc/ssl/private/server.key
TLS_CACERT /etc/ssl/certs/cacert.pem
```I also added following entry in /etc/hosts

```
<IP of the server>  ldap.company.com
```/etc/default/slapd contains the following entry :

```
SLAPD_SERVICES="ldap:/// ldapi:/// ldaps:///"
```I am able to get the result for the following query.

```
ldapsearch -x -H ldaps://ldap.company.com -b dc=ldap,dc=company,dc=com uid=testuser
```But the moment I change the value of TLS_REQCERT to demand from allow, the search stops working.

It shows the following error :

```
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
```I feel some configuration is missing. Can anyone please help me out in this regard.

NOTE : I have no slapd.conf in my server. I guess slapd.conf used to be present in older versions.

-Asmii

---

### Post by asmii on 2009-06-23
I ran the commend "ldapsearch -x -d5" and got the following :

```
ldap_create
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP ldap.company.com:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 127.0.0.1:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
TLS: peer cert untrusted or revoked (0x2)
TLS: can't connect: (unknown error code).
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
```Can the error "TLS: peer cert untrusted or revoked (0x2)" be the cause behind all this?

Please suggest.

-Asmii

---

### Post by asmii on 2009-06-23
[COLOR=Blue]I did the configuration again from the scratch and this time I get a new error :

```
#ldapsearch -d5 -x -H ldaps://ubuntu-host -b dc=ldap,dc=company,dc=com uid=amohanty
ldap_url_parse_ext(ldaps://ubuntu-host)
ldap_create
ldap_url_parse_ext(ldaps://ubuntu-host:636/??base)
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP ubuntu-host:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 127.0.1.1:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
TLS: can't connect: A TLS packet with unexpected length was received..
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
```I can see the error message "[/COLOR][COLOR=Blue][COLOR=Red]TLS: can't connect: A TLS packet with unexpected length was received..[/COLOR]" which possibly is the reason behind my issues.

Please suggest.

-Asmii[/COLOR]

---

### Post by asmii on 2009-06-23
I think I missed the following step during configuration mentioned [here]("https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html")

```
ldapmodify -x -D cn=admin,cn=config -W
                Enter LDAP Password:
dn: cn=config
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem
-
add: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ssl/certs/server.crt
-
add: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ssl/private/server.key

modifying entry "cn=config"
```After executing this, slapd refuses to start. I have uploaded the output of slapd -d 16383 with this post.

Please help.

-Asmii

---

### Post by euphoboy37 on 2009-06-30
Do you receive the "main: tls init def ctx failed -1" as that is what I received when trying to follow the server guide.  I am new to Linux and do not know what it means.

---

### Post by Quentusrex on 2009-07-11
I am having the same issue. The error basically says that there is a problem with the CA Cert.

---

### Post by asmii on 2009-07-15
[COLOR=Blue]Hi,

[/COLOR][COLOR=Blue]Try using certtools to create key and certificate files instead of the existing procedures defined.

This solved my problem and I hope this works for others too.

However this solves the certificate and key issue due to which slapd shows error when restarted. This doesn't solve the issue defined in my first post. I am able to get rid of the error and slapd now starts successfully, "[/COLOR]  [COLOR=Blue]TLS_REQCERT demand" still creates issues for me. It only works with "[/COLOR][COLOR=Blue]TLS_REQCERT allow".

-Asmii[/COLOR]

---

### Post by asmii on 2009-07-16
[COLOR=Blue]Hi All,

Has anyone faced the same issue and found a solution ([/COLOR][COLOR=Blue]TLS_REQCERT demand/allow)?

Please let me know the same.

-Asmii
[/COLOR]

---

### Post by apalacheno on 2009-08-10
Unfortunately no solution, but otherwise I'm in the same boat as you are. "TLS_REQCERT allow" works, "TLS_REQCERT demand" does not. Still looking for a solution...

---

### Post by HDave on 2009-09-20
@asmii -- are you using a self-signed certificate?  If so, I don't believe "demand" will work.

@euphoboy37 - Also I have found that the most common reason behind the "main: tls init def ctx failed -1" error is that slapd cannot read the private key file from the /etc/ssl/private directory.  The instructions in the server guide are incomplete.  Please triple check that the ssl-cert group has read access on this directory and that openldap user is a member of this group.

For myself, I have yet to establish my first connection to slapd over SSL.  It works fine in plain text on port 389.   Everytime I try I get:
```
ldapsearch -x -H ldaps://192.168.1.26:636
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

```

I am using a self-signed certificate.

---

### Post by HDave on 2009-09-20
OK -- I was finally able to connect.  My problem was because the "Common Name" in the certificate didn't match the hostname in ldap.conf.

I found out that ldapsearch has a debug option.  Start with -d 1 and go up to -d 3.  It was immensely helpful as was running slapd from the command line with it's debug option on.

I am able to connection in "demand" mode with a self signed certificate with no problem however.  In order to do this I put the TLS_CACERT option in.  

@asmii -- I see that in your ldap.conf file you have used the TLS_CERT and TLS_KEY directives.  I didn't need these...and frankly their use confuses me.  Why would a client public/private pair be needed?

---

### Post by apalacheno on 2009-09-21
Thank you very much, Dave, now it works for me too using a self-signed certificate. This is the content of my */etc/ldap/ldap.conf*:

```
BASE		dc=home,dc=ro
URI		ldap://ldap.home.ro
TLS_REQCERT	demand
TLS_CACERT      /usr/share/ca-certificates/cacert_home.crt
```

Of course, I had to copy the CA certificate to the above location.

Thanks, man!

---

### Post by HDave on 2009-09-22
Nice!

---

