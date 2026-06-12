---
title: "Samba, LDAP and gnutls"
date: 2009-12-03
forum: Server Platforms
---

### Post by stefanadelbert on 2009-12-03
I'm trying to setup samba to authenticate against LDAP using TLS and self-signed certificates.

I've followed a number of howto's, some of which are listed below:
[LIST]
[*][https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html]("https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html")
[*][https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html]("https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html")
[*][https://help.ubuntu.com/8.10/serverguide/C/certificates-and-security.html]("https://help.ubuntu.com/8.10/serverguide/C/certificates-and-security.html")
[*][http://ubuntuforums.org/showthread.php?t=1241136]("http://ubuntuforums.org/showthread.php?t=1241136")
[/LIST]

The biggest stumbling block was generating the correct keys and certificates. I found out after a lot of pain that Ubuntu ldap packages are built against gnutls rather than openssl. This means that you need to generate your keys and certificates using gnutls (see the last link in the list above).

I'm having problems generating the certificates correctly though. I think I need to generate a Certificate Authority key and certificate so that I can selfsign my LDAP server certificate. But there are a number of parameters when setting up the certificates and I think that's what is causing the problems here.

The error message I'm getting when attempting to create the server certificate using CA key, CA self-signed certificate and server key is:

```
set_dn: The request is invalid.
```

I was trying to generate it using this command (with a template file specifically setup for the server)

```
certtool --generate-certificate --load-privkey server.key --outfile server.pem --load-ca-certificate cacert.pem --load-ca-privkey ca.key --template server.template
```

Does anyone know what "set_dn" in the error message above refers to?

---

### Post by kwickcut on 2009-12-03
dont know if this helps but i found this 

[http://apidock.com/ruby/URI/LDAP/set_dn](http://apidock.com/ruby/URI/LDAP/set_dn)


kwick

---

### Post by stefanadelbert on 2009-12-03
Good find, but regrettably not all that useful. I would be useful to know what the "val" parameter to set_dn is supposed to be. Thing is that what I'm doing doesn't even have anything to do with ldap yet! I'm just trying to create the certificates. Baffling!

---

### Post by stefanadelbert on 2009-12-07
Here is a [link]("http://libvirt.org/remote.html") to a good, simple walkthru on creating self-signed certificates for those who are interested.

---

### Post by mverwijs on 2012-07-06
If anyone happens to come across this still: the answer is that in the template the value 'state' is empty, or just two quotes (""). 

Comment it out or give it a value and it should work ok.

---

### Post by kennethconn on 2012-07-06
Error messages when creating certificates can be pretty baffling when you come across them (especially using openssl). Any that I have come across were almost always to do with values expected and not provided (at least providing them took care of errors).
 
Once you do get the certs created for use, problems using them are usually down to file permissions.
 
Keep us posted.

---

