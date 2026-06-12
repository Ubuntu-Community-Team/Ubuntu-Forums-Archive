---
title: "join ubuntu server to domain"
date: 2018-11-29
forum: Server Platforms
---

### Post by thaddeus2 on 2018-11-29
Hi all, 

I have a ubuntu workstation. I need to join it to domain (windows 2016).

How do i join it to domain.

Is there any GUI that will help to do this?

---

### Post by SeijiSensei on 2018-11-29
[https://freedesktop.org/software/realmd/docs/guide-active-directory.html](https://freedesktop.org/software/realmd/docs/guide-active-directory.html)

---

### Post by thaddeus2 on 2018-12-12
that didnt help im still getting error. 

/home/thaddeus realm discover --verbose domain.com
 * Resolving: _ldap._tcp.domain.com
 * Performing LDAP DSE lookup on: IP ADDRESS
 * Performing LDAP DSE lookup on: 
 * Performing LDAP DSE lookup on: 10.1.10.35
 * Successfully discovered: domain.com 


  type: kerberos
  realm-name: domain.com
  domain-name: domain.com
  configured: no
  server-software: active-directory
  client-software: sssd
  required-package: sssd-tools
  required-package: sssd
  required-package: libnss-sss
  required-package: libpam-sss
  required-package: adcli
  required-package: samba-common-bin

---

### Post by HermanAB on 2018-12-13
The good news, is that yes it is possible.  The bad news is that easy, it ain't.

You need to install Kerberos.  You need the machine hooked to a time server, since Kerberos depends on accurate time.  Some of the configuration is extremely Case Sensitive.  For example Kerberos settings must be in UPPER CASE ONLY.  You need to point the server to the MS Active Directory DNS server.  You need to touch PAM and she is a very sensitive lady - if you make a mistake then the machine may be unbootable as a result.

You should expect to spend about 2 weeks on this problem.  However, if you keep very good notes, then the next server could be done in about 2 minutes...

---

### Post by slickymaster on 2018-12-13
*Thread moved to **Server Platforms**.*

---

