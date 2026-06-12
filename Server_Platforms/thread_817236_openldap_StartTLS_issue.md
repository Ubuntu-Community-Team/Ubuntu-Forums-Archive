---
title: "openldap StartTLS issue"
date: 2008-06-03
forum: Server Platforms
---

### Post by adamos on 2008-06-03
I have a openldap setup running but I am trying to implement TLS in it. I am following the tutorial from: [http://www.openldap.org/faq/data/cache/185.html](http://www.openldap.org/faq/data/cache/185.html)
I create the keys, sign them etc but when I am trying to restart the server i get this error when i debug slapd:
[B]TLS: warning: cacertdir not implemented for gnutls
[/B]
Do you have any idea what is causing that?


Thanks,

Adam

---

### Post by adamos on 2008-06-04
As I am reading through mailing lists it seems that ubuntu 8 and gnutls is a no go. Does anyone has a workaround on this issue?

---

### Post by gpredrag on 2008-06-04
I can't say to know what exactly is your problem, none of my LDAP servers is on Ubuntu 8.04 right now, but is there TLSCACertificatePath in your slapd.conf that is not commented out. That should direct slapd to use individual CA certificates (and that is not supported by gnutls, although it should be just ignored, not generate error I suppose).
What exactly is your problem slapd cannot start? what does slaptest shows.
Client cannot use TLS? What ldapsearch with -d option shows?

---

### Post by adamos on 2008-06-09
I tried whatever was possible. Every other how-to has different explanations and methods. I used a different version of openldap like I was told from the ubuntu-server channel in irc but it didn't work either. Basic unsecure binding works perfect but TLS doesn't work. I am tight on time and I need my ldap configuration to be secure. Some folks in Gentoo seem to have it working but I don't want to give up Ubuntu for a TLS configuration.

---

### Post by Nicster on 2008-07-30
I've spent the day battling to try and get openldap+gnutls working.. no luck unfortunately.

The worst is that the debug info provided by setting

[INDENT]loglevel        -1[/INDENT]

in /etc/ldap/slapd.conf doesn't provide anything useful.

The only conclusion I have is that openldap on ubuntu hardy is broken with TLS. This is surely a serious bug?

---

### Post by Loppan on 2008-08-21
> **adamos said:**
> 
[B]TLS: warning: cacertdir not implemented for gnutls
[/B]


Quoting OpenLDAP Software 2.4 Administrator's Guide:
> 15.2.1.2. TLSCACertificatePath <path>

This directive specifies the path of a directory that contains individual CA certificates in separate files. In addition, this directory must be specially managed using the OpenSSL c_rehash utility. When using this feature, the OpenSSL library will attempt to locate certificate files based on a hash of their name and serial number. The c_rehash utility is used to generate symbolic links with the hashed names that point to the actual certificate files. As such, this option can only be used with a filesystem that actually supports symbolic links. In general, it is simpler to use the TLSCACertificateFile directive instead.

So I must agree with gpredrag, do you still have a TLSCACertificatePath in your conf?

I am about to try the same thing on 8.04.1, will post results.

---

### Post by Apfelmaennchen on 2008-11-04
Hi folks!

I'm facing a similar if not the exact same problem:

I also followed the instructions from openldap.org and end up with the following error:
```
main: TLS init def ctx failed: -64
```

My slapd.conf reads as follows:
```
TLSCACertificateFile /etc/ssl/CA/MyCA/cacert.pem
TLSCertificateFile /etc/apache2/certs/MyHost-cert.pem
TLSCertificateKeyFile /etc/apache2/certs/MyHost-key.pem
```

The host key and certificate are owned by openldap:www-data and have permissions 444 (certificate) and 440 (key), while the CA-certificate is owned by myUser:users, permissions 644.

I even added
```
/etc/ssl/CA/MyCA/cacert r,
/etc/apache2/certs/MyHost-* r,
```
to SLAPD's apparmor profile - but to no avail :mad:

Anyone got any ideas what I am missing?

Thanks A LOT in advance
d

PS:
I have upgraded my system to intrepid this noon after I've spent some hours on this #@?%§$%$ in hardy.

---

### Post by sierraloewe on 2009-01-21
Seems I just ran into the same wall.

Do we have a workaround yet for this problem?

---

### Post by sierraloewe on 2009-01-21
I made the certificates world readable and slapd starts now without any errors... this probably is a bad idea though?

EDIT

TLS still fails.  I get an error that the security flags don't match. Seems to be related to TLSCipherSuite and gnutls.  Is there a way to make this work?  Or do I need to get a different version of openldap?  or compile openssl into slapd?  

What is the best way to fix this?

---

### Post by cotillion2009 on 2009-03-16
having the same problem.

I think it is an permission error. When I run strace with this config:

 strace -Ff -tt slapd -h 'ldap://0.0.0.0:389/' -g openldap -u openldap -f /etc/ldap/slapd.conf 2>&1 | tee /home/abc/slapd.log

I get this error before slapd breaks up:

11:22:35.381437 open("/etc/ldap/ssl/ldapkey.pem", O_RDONLY) = -1 EACCES (Permission denied)

(where ldapkey.pem ist the TLSCertificateKeyFile defined in the /etc/ldap/slapd.conf)

I found the workaround to change the slapd-user in /etc/default/slapd from openldap to root. 

After this, slapd and TLS works. But it doesnt seem to be the perfect way.

In the book OpenLDAP (2nd Edition) by Liebel/Ungar it is told gnuTLS should not be used for encryption with ldap, because it is broken.

Can this be related to this problem?

---

