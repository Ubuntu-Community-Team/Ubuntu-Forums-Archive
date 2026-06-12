---
title: "openldap + gnutls"
date: 2009-05-28
forum: Server Platforms
---

### Post by gotzon on 2009-05-28
First of all, sorry about my english and sorry if there are any posts with the same problem. I did a search but i couldn't found any help about this.

Hi all. I am new on this GNU/Linux world, and i am having some problems implementing selfsigned certificates with gnutls and openldap. I build an Ubuntu server with the ubuntu 7.10 version, with openldap and openssl selfsigned certificates that works fine!! My problem starts when I tried to build a server with the 8.10 version. I read that this new versions of openldap does't supports openssl certificates and I must use gnutls certificates.
I don't know very well how, but I got my 7.10 server running openldap with certificates made with gnutls and desktops with unbuntu 8.04 or 8.10 versions with those certificates. But when I try to connect a desktop machine with the 9.04 version of ubuntu, the certificates don't work... and when I try to replicate from the 8.10 server to the 7.10 openldap server, I got certificate errors too... 

I had read that the GnuTls had errors with the openldap version that uses the ubuntu 8.XX versions and that I must to recompile the openldap with openssl lib files... Is this true?? Is this a bug?? It is solved in the 9.04 server version??

I know that this thread could be a little stupid, but I am trying to migrate my works PCs from windows to GNU/Linux, and this problem with the certificates is delaying too much my work, and my bosses starting to think that is a bad idea the migration.

Thank you for your help, and again, sorry about my english and sorry again if there was a thread with the same problem.

Gotzon

---

### Post by grunthus on 2009-05-28
Hi,

I have been having a similar problem with the 9.04 OpenLDAP Server guide for Ubuntu:
[https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html)

The first 2 sections seemed to go exactly as documented (configuring and populating)
I am not implementing replication, so missed out the section on replication.
Things seem to go wrong for me in the TLS and SSL section. I have created self-signed certificates as described in the Certificates and Security guide.

However, after modifying /etc/default/slapd as specified and trying to restart slapd, slapd fails to restart:

```
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

```Checking the syslog as suggested shows the likely problem is with the TLS certificates:
```
tail /var/log/syslog
May 28 21:49:05 chanpints slapd[27006]: main: TLS init def ctx failed: -1 
May 28 21:49:05 chanpints slapd[27006]: slapd stopped. 
May 28 21:49:05 chanpints slapd[27006]: connections_destroy: nothing to destroy.


```I'm a novice with Ubuntu and also with LDAP. Previously I've done a lot of Gentoo-ing, using NIS for authentication. I have tried wiping the configuration and starting with the guide twice over, but still no go. Not finding much about this anywhere else?

Any advice welcome!

Cheers

---

### Post by apalacheno on 2009-08-10
Hey there,
stumbling across your posts, you might want to try to deactivate AppArmor and see if it works.

Cheers,
Robert

---

### Post by HDave on 2009-09-18
> **grunthus said:**
> Any advice welcome!

I know its been a while since you posted this question, but I think I found the problem and the solution in this thread:

[http://archive.netbsd.se/?ml=OpenLDAP-software&a=2009-01&t=9665882](http://archive.netbsd.se/?ml=OpenLDAP-software&a=2009-01&t=9665882)

Apparently, Debian & Ubuntu compile OpenLDAP against GnuTLS instead of the more appropriate and secure OpenSSL.  Because you probably used openssl to create your certificates, there is an incompatibility.  Incredibly, the format of the pem file differs between GnuTLS and OpenSSL.

You either need to create new certs with GnuTLS or manually fix the ones you created for OpenLDAP (sigh).

---

### Post by HDave on 2009-09-18
Wups -- The link I reported was for error -207.  I see you are having error -1.  Perhaps this will help:

[https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/420277](https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/420277)

---

