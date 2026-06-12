---
title: "Jaunty Jackalope: main tls init def ctx failed -1"
date: 2009-06-29
forum: Server Platforms
---

### Post by euphoboy37 on 2009-06-29
I am having issues setting up an HP Proliant G5 server with Ubuntu Jaunty Jackalope Desktop Edition.  I am fairly new to Linux and was told the desktop editions GUI would be better to learn on than the command line interface that the server edition has.

I am sorry for the large post here, but I tried to cover as much as possible in my own troubleshooting.  Any advice would be greatly appreciated.  If more debugging is needed please let me know what code to place in the terminal prompt so I can make sure to get the appropriate feedback.

I am going by the Ubuntu Serverguide for the 9.04 release ([https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)).  The first couple sections go well, but on the Network Authentication I recieve an error when trying to restart slapd after setting up SSL/TLS within OpenLDAP.

At the terminal I run "/etc/init.d/slapd restart" and recieve the following
```
Stopping OpenLDAP: slapd.
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to 
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -h 'ldap://PeaceFP01.peace-sp.org:389/' -g openldap -u openldap -F /etc/ldap/slapd.d/
```I then looked at /var/log/syslog and found

```
Jun 29 08:16:35 PeaceFP01 slapd[17840]: @(#) $OpenLDAP: slapd 2.4.15 (Mar 19 2009 10:08:25) $ ^Ibuildd@palmer:/build/buildd/openldap-2.4.15/debian/build/servers/slapd 
Jun 29 08:16:35 PeaceFP01 slapd[17840]: main: TLS init def ctx failed: -1 
Jun 29 08:16:35 PeaceFP01 slapd[17840]: slapd stopped. 
Jun 29 08:16:35 PeaceFP01 slapd[17840]: connections_destroy: nothing to destroy. 
```After researching more online I found that this error usually meant that OpenLDAP did not have read/write access to the certificate files.  So I gave read/write access to both the user account OpenLDAP and the group account OpenLDAP to the whole /etc/ssl/certs folder and /etc/ssl/private folder and everything in each of them.

I tried restarting slapd again and recieved the exact same error message.  I then tried

```
root@PeaceFP01:~# slapd -h 'ldap://PeaceFP01.peace-sp.org:389/' -g openldap -u openldap -F /etc/ldap/slapd.d/

@(#) $OpenLDAP: slapd 2.4.15 (Mar 19 2009 10:08:25) $
    buildd@palmer:/build/buildd/openldap-2.4.15/debian/build/servers/slapd
ldap_pvt_gethostbyname_a: host=PeaceFP01.peace-sp.org, r=0
daemon_init: <null>
daemon_init: listen on ldap:///
daemon_init: 1 listeners to open...
ldap_url_parse_ext(ldap:///)
daemon: listener initialized ldap:///
daemon_init: 2 listeners opened
ldap_create
slapd init: initiated server.
slap_sasl_init: initialized!
invalid config directory /etc/debugging.txt, error 2
slapd destroy: freeing system resources.
slapd stopped.
connections_destroy: nothing to destroy.

root@PeaceFP01:~# slapd -V
@(#) $OpenLDAP: slapd 2.4.15 (Mar 19 2009 10:08:25) $
    buildd@palmer:/build/buildd/openldap-2.4.15/debian/build/servers/slapd
```and **root@PeaceFP01:~# slapd -d 16383** which I have put the large amount of output here [https://sites.google.com/a/uebelackers.com/ubuntu-issues/Home/slapddebug](https://sites.google.com/a/uebelackers.com/ubuntu-issues/Home/slapddebug)

---

### Post by matey3 on 2009-06-29
sorry this may be unrelated but have you tried to rename the /lib/tls to /lib/tls.old and try it again?

hopefully someone with more knowledge post a reply.

good luck.

---

### Post by euphoboy37 on 2009-06-29
I just tried that, but was unsuccessful and received the same errors.

---

### Post by euphoboy37 on 2009-07-01
Has anybody else have any ideas or run into this issue yet?

---

### Post by flipybcn on 2009-07-10
Hi!
Have you checked the certificates?
Have you created your own CA and then signed the server certificate?

(that was a problem I've had before)

---

### Post by apalacheno on 2009-08-10
Hi,
try disabling AppArmor.

Cheers,
Robert

---

### Post by flxkid on 2009-08-31
I had this same problem.  For me it turned out to be the fact that I had put a passphrase on my server.key file which openldap doesn't currently support.  I removed the passphrase, locked down the file (removed world read rights), and copied it into my /etc/ssl/private folder and voila, server starts perfectly!

HTH,

OLIVER

---

### Post by HDave on 2009-09-18
I have this same problem starting slapd with a self-signed certificate.  I have disabled apparmour and also created a key without a pass-phrase.  Any other ideas?

---

### Post by tc.espinola on 2009-09-29
See it: [http://wiki.debian.org/LDAP/OpenLDAPSetup](http://wiki.debian.org/LDAP/OpenLDAPSetup)

---

### Post by tburkhol on 2009-12-14
Ubuntu/debian openldap is linked against gnutls, not openssl, and this seems to cause some conflict with openssl-generated and signed certificates.  Try using certtool to generate and sign the CSR.  eg:

                certtool --generate-privkey --outfile server.key
                certtool --generate-request --load-privkey server.key --outfile server.csr
                certtool --generate-certificate --load-ca-certificate ca.crt --load-ca-privkey ca.key.insecure --load-request server.csr --outfile signed-server.crt

---

