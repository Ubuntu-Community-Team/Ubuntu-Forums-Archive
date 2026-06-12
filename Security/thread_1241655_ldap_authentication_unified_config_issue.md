---
title: "ldap authentication unified config issue"
date: 2009-08-16
forum: Security
---

### Post by Keeper of the Keys on 2009-08-16
I recently decided to switch Debian clients on our network to Ubuntu (the server remains Debian) but I am into a slightky annoying issue:

We use LDAP authentication and while on Debian there are two (almost identical) files to configure PAM and NSS to work with ldap it seems that Ubuntu has decided to add these two files together.

As the files are almost identical this may have seemed like a logical step but it means that you can't restrict access to only one branch of the tree or even one user while still retaining the possibility of showing proper owner/group information on files.

Ie. in my old setup the libnss_ldap.cpnf basedn would be "dc=mydomain,dc=tld" while the pam_ldap.conf basedn would be "ou=someou,dc=mydomain,dc=tld" etc. this would bar people in a different ou access to that specific machine while still being able to show proper group (and owner information in shared directories) information as the groups sat in "ou=groups,dc=mydomain,dc=tld"

Is there a solution for this usage scenario on Ubuntu?

---

### Post by Keeper of the Keys on 2009-08-17
So I have been trying stuff with the NIS compat notation in /etc/passwd eg.:
-@dept::::::
or
+@dept::::::/bin/false

But to no avail, any suggestions would be very welcome.....

---

### Post by Keeper of the Keys on 2009-08-17
I found my answer in /usr/share/doc/libpam-ldap/README.Debian
> 
Ubuntu uses /etc/ldap.conf as libpam-ldap's configuration file and
/etc/ldap.secret as the file to store the password of the rootbinddn.
This file is shared with libnss-ldap, which should work for most
configurations. If separate configuration files for libnss-ldap and 
libpam-ldap are required, you can specify an alternate configuration file
in /etc/pam.d/common-* by adding a config=</path> argument to the
pam_ldap.so entry, such as:

    auth sufficient pam_ldap.so config=/etc/pam_ldap.conf

This would let you have two separate configurations: /etc/ldap.conf for
NSS, and /etc/pam_ldap.conf for PAM. Thanks to Etienne Goyer for pointing 
this out.


Other than that I might just start playing around with pam_check_host_attr...

---

