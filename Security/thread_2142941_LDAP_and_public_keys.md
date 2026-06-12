---
title: "LDAP and public keys"
date: 2013-05-07
forum: Security
---

### Post by thestrt on 2013-05-07
I am looking at creating a SSH gateway using OpenLDAP.  The idea is to store
our devs public keys in OpenLdap, which would give us the ability to control
who has SSH access to our servers.

Currently everyone shares the same key which means it is impossible to control
access.

Do I just need to...

Install OpenLDAP
Import the public keys into OpenLDAP
Install OpenSSH Server on the OpenLDAP server and configure it to use LDAP.
Configutre the remote servers to use the OpenLDAP servers to authenticate

The the devs can ssh from their computers through the OpenLDAP server to the
remote servers.  How would they need to configure their SSH?



Can anyone help?

---

### Post by Stieneee on 2013-06-17
I'm trying to do the same thing right now. I have gotten as far as ssh password authentication of ldap clients but can seem to figure out how to easily implement keys for ldap clients some guidance would be great.

---

