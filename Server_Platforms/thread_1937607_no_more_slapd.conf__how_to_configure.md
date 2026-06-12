---
title: "no more slapd.conf ? how to configure ?"
date: 2012-03-08
forum: Server Platforms
---

### Post by NeedALotOfHelpXD on 2012-03-08
I'm a student, i'm trying to learn how to configure ubuntu 12.04 precise server as a domain controller.
With little adjustements i'm following this excellent how to:
[http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)
That is already giving me a lot of learning.
When i get to step 4 it says that i have to add lines to 
/etc/ldap/slapd.conf
that file is no longer used in openldap 2.4 
how do i pass the following parameters to ldap configuration?
include         /etc/ldap/schema/samba.schema
include         /etc/ldap/schema/misc.schema
access to attrs=userPassword,sambaNTPassword,sambaLMPassword

i've understood that now it is all given real time passing somehow some files to ldap, so there is no more need of a restart in slapd after changes?

is there a guide explaining how to pass from old slapd.conf to new way of telling parameters?

Thank you if you can help, and thank you anyway.

i think i found a solution here:
[http://www.openldap.org/doc/admin24/slapdconf2.html](http://www.openldap.org/doc/admin24/slapdconf2.html)  5.4
i'll try slaptest -f /usr/local/etc/openldap/slapd.conf -F /usr/local/etc/openldap/slapd.d
ok i found slapcat and ldapadd

---

