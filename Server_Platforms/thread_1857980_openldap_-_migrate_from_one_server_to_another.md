---
title: "openldap - migrate from one server to another"
date: 2011-10-11
forum: Server Platforms
---

### Post by SwitchLink on 2011-10-11
When installing openldap for the first time on a fresh install of ubuntu, the namingContexts were set to the following:

```
ldapsearch -x -b '' -s base '(objectclass=*)' namingContexts


# extended LDIF
#
# LDAPv3
# base <> with scope baseObject
# filter: (objectclass=*)
# requesting: namingContexts
#

#
dn:
namingContexts: dc=domain,dc=com

# search result
search: 2
result: 0 Success

# numResponses: 2
# numEntries: 1
```

I'm guessing that is being pulled from the hosts file or some other network information, as the installer never prompted me to set the namingContexts.

These are the steps I followed to migrate the data from the old server to the new server:

```

service slapd stop

cd /var/lib/ldap/
rm *__db.* *.bdb alock log.*

slapadd -l dbFromOldServer.ldif -q

```

At this point it was adding in the ldif file.  It took about 5 minutes.  And returned with the following error:

```

Closing DB...Error, entries missing!
entry 1: dc=domain,dc=com
entry 2: dc=ldap,dc=domain,dc=com
```

I could not find any information on what to do about this or even if I should be concerned about it, so I pushed ahead with the next step: indexing the newly imported database using the slapd.conf file.

Here is a copy of the slapd.conf file (minues the comments) that I used to index the database when it was done importing:

```
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema

pidfile         /var/run/slapd/slapd.pid

argsfile        /var/run/slapd/slapd.args

loglevel        none

modulepath      /usr/lib/ldap
moduleload      back_bdb

sizelimit 500

tool-threads 1

backend         bdb

database        bdb

suffix          "dc=prod,dc=ldap,dc=domain,dc=com"

directory       "/var/lib/ldap"

dbconfig set_cachesize 8 0 16


dbconfig set_lk_max_objects 1500
dbconfig set_lk_max_locks 1500
dbconfig set_lk_max_lockers 1500

index           default pres,eq
index           objectClass eq
index           uid,sn,cn
index           entryCSN,entryUUID

lastmod         on

checkpoint      512 30

access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=prod,dc=ldap,dc=domain,dc=com" write
        by anonymous auth
        by self write
        by * none

access to dn.base="" by * read

access to *
       by dn="cn=admin,dc=prod,dc=ldap,dc=domain,dc=com" write
       by * none

threads 8
idletimeout 3600
cachesize 50000
cachefree 100

```


```
slapindex -f /usr/share/slapd/slapd.conf
```

I let the index run overnight, came back in the morning and changed the permissions of the files in /var/lib/ldap to openldap because as I had run the import and index using sudo, file permissions were set to root.

I started slapd:  service slapd start

I verified that slapd was running.  I tested connecting to the ldap server using either JExplorer or Apache Directory Studio and can see what appear to be correct data.

However, the namingContexts is still set to: 
    dc=domain,dc=com

Instead of what I want it to be which is:  
    dc=prod,dc=ldap,dc=domain,dc=com


This probably has something to do with the error I recieved when I imported the data.  My question is, can I change the namingContexts post mortem or do I need to go back and add a step at some point during the whole process to change the namingContexts to what it needs to be?

Why is the namingContexts not being pulled from the slapd.conf file?  Where else could it possibly be pulling from?

All help is greatly appreciated, thanks!

---

### Post by SwitchLink on 2011-10-17
The new version of OpenLDAP doesn't use slapd.conf anymore - I was not originally aware of that.  I did some reading and testing using some web resources including the [Admin Guide]("http://www.openldap.org/doc/admin24/index.html").

The naming contexts defaults to the local domain.  I was reading about ldapmodify and some other tools but could not figure out how to change the namingContexts because they were in the rootDSE.  So I reinstalled clean to do some testing, stopped slapd, modified the config ldif files directly and was able to change not only the rootDSE, but other values as well.  This gave me the correct namingContext.

More information about the solution I found to this can be found here:

[http://ubuntuforums.org/showthread.php?t=1860022]("http://ubuntuforums.org/showthread.php?t=1860022")

It was a lot of trial and error, and I'm not even sure if I was right in what I did, but I'm sharing anyway in case it helps someone else.  :)

---

