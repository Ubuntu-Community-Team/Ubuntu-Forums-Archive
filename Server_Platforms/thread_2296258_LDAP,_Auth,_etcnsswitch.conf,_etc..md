---
title: "LDAP, Auth, /etc/nsswitch.conf, etc.?"
date: 2015-09-24
forum: Server Platforms
---

### Post by JSeymour on 2015-09-24
Hi There,

Have been following this documentation: [OpenLDAP Server]("https://help.ubuntu.com/lts/serverguide/openldap-server.html")

After *Access Control*, skipped the *TLS* and *Replication and TLS* sections, went right to *LDAP Authentication*

Got as far as
> 
         You will be prompted for details of your LDAP server. If you make a mistake you can try again using:    
     
 sudo dpkg-reconfigure ldap-auth-config

      The results of the dialog can be seen in /etc/ldap.conf. If your server requires options not covered in the menu      edit this file accordingly.     

      Now configure the LDAP profile for NSS:     

 sudo auth-client-config -t nss -p lac_ldap

*auth-client-config* complains
```

# auth-client-config -t nss -p lac_ldap
Usage: auth-client-config -p PROFILE -a -t TYPE [-dn -f FILE]
       auth-client-config -p PROFILE -a -t TYPE -r [-n -f FILE]
       auth-client-config -p PROFILE -a -t TYPE -s [-f FILE]

auth-client-config: error: option -p: invalid choice: 'lac_ldap' (choose from 'ldap_example', 'kerberos_example', 'cracklib')

```
and 
*dpkg-reconfigure ldap-auth-config* does not exist
```

# dpkg-reconfigure ldap-auth-config
dpkg-query: package 'ldap-auth-config' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: ldap-auth-config is not installed

```
and apt-cache search comes up bupkis?

How to proceed, please?

Thanks,
Jim

---

### Post by JSeymour on 2015-09-25
Solved.  Problem was probably from not following the referenced "how to" _exactly_.  I'd gotten to the part about editing /etc/ldapscripts/ldapscripts.conf, saw the comments therein about "DEBIAN: values from /etc/nslcd.conf (base maps) are used." and thought installing nslcd was a Good Idea.  I backed-up a couple steps back from where things went awry, did _exactly_ as told, and all was well

Sorry for the false alarm.

Jim

---

### Post by marwen-somrani on 2015-10-25
hello, have strating over from the begining ? i have followed the instructions step by step until i come in this step of authentication

---

