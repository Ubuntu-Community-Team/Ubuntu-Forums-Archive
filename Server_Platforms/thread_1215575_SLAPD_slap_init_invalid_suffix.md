---
title: "SLAPD slap_init invalid suffix"
date: 2009-07-17
forum: Server Platforms
---

### Post by matt_lethargic on 2009-07-17
Hi noob here,

Am trying to get LDAP setup on my home server, I've tried following a few tutorials and think I've got myself in a muddle now!

Whenever I try and run

```
sudo dpkg-reconfigure slapd
```

I get the error

```
Stopping OpenLDAP: slapd.
  Creating initial slapd configuration... done.
  Creating initial LDAP directory... failed.

Loading the initial directory structure from the ldif file (/tmp/slapd_init_dir.ldif.XUPrF16094) failed with the following
error while running slapadd:
    slapadd: slap_init invalid suffix ("dc=mattsplace,dc=lan")

```

Could anyone help me please?
Let me know if you need any files posting etc

8.10 server

---

### Post by matt_lethargic on 2009-08-14
*** BUMP ***

Anyone?

---

