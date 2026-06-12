---
title: "ldap login issue..."
date: 2005-11-12
forum: Server Platforms
---

### Post by unixnorks on 2005-11-12
Is anybody here knows how to set up user accounts in slapd?? Im 4 weeks troubled how i can make my ldap server usable to ldap clients... :confused: 


ANY HELP IS HIGHLY APPRECIATED,...

---

### Post by gruepig on 2005-11-12
You'll need to configure ldap/slapd and add the user account info to ldap (using ldapadd or whatever).  Once you can query that data out of ldap (from a client mahcine), you'll need to configure pam on the client machine to use ldap (/etc/pam.d/*).  If you have the ldap server running, pam is probably what you are looking for.  The other two things worth noting are (1) you may need to edit /etc/ldap/ldap.conf on the client machine to set the base dn and (2) that running nscd will significantly decrease the load on your ldap server and make commands like 'ls -l' run much faster on the client.

I haven't set up ldap recently, so that's all pretty vague.  If you have more specific problems or need details, ask.

---

### Post by unixnorks on 2005-11-13
> You'll need to configure ldap/slapd and add the user account info to ldap (using ldapadd or whatever).

Thanks ***gruepig*** i appreciate..Fortunately id able to run my ldap server by issuing this command.../usr/sbin/slapd ....ldapsearch is working so fine too.. However when i issue the ff..

#ldapadd -x -D "cn=admin,dc=example,dc=org" -W -f group.ldif
Enter LDAP Password: <i used the default password given in slapd.conf (secret) >
ldap_bind: Invalid credentials

Is there something i lacked to configure? 

Anyways i used the GQ ldap client as my administrative tools. Anybody can locate me to some site that will give me more overview on how to use it?

Thanks..

---

### Post by gruepig on 2005-12-02
Sorry for the delay in reply ... if you are still having problems, try stopping slapd and using slapadd rather than ldapadd.  Something like 'slapadd -v -c -l some.ldif -f /etc/openldap/slapd.conf' (not sure if that's exactly it, but it's close).  You'll want to have the admin user with password in the ldif file.  Then run slapindex to index and start slapd.

---

