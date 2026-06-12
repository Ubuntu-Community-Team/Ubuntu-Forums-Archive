---
title: "What is the connection between slapd.conf and the slapd.d"
date: 2011-10-13
forum: Server Platforms
---

### Post by trongbang on 2011-10-13
Hi guys,
For old documents for setting up and configuring LDAP, you would want to see something like this:
> Edit slapd.conf  and you would need to add the following line  
 
TLSCACertificateFile /etc/ldap/sasl2/ldap.pem 
TLSCertificateFile /etc/ldap/sasl2/ldap.pem 
TLSCertificateKeyFile /etc/ldap/sasl2/ldap.pem 
TLSCipherSuite HIGH:+MEDIUM:!LOW 
 
SSLVerifyClient none

But for new LDAP, it uses the directory slapd.d which looks like this:
>  ls /etc/ldap/slapd.d
cn=config  cn=config.ldif

So for example, how can I apply the steps for old slapd.conf to slapd.d here.

Many thanks in advance!

---

### Post by SwitchLink on 2011-10-14
This should get you started:

[http://www.openldap.org/doc/admin24/slapdconf2.html]("http://www.openldap.org/doc/admin24/slapdconf2.html")

You have to build an LDIF file and use the LDAPADD command.

[https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html]("https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html")

Unfortunately I am still learning myself, so I can't be more specific than that.  :)

---

### Post by trongbang on 2011-10-14
> **SwitchLink said:**
> This should get you started:

[http://www.openldap.org/doc/admin24/slapdconf2.html]("http://www.openldap.org/doc/admin24/slapdconf2.html")

You have to build an LDIF file and use the LDAPADD command.

[https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html]("https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html")

Unfortunately I am still learning myself, so I can't be more specific than that.  :)

Sure sure! I'm also learning. I'm having some problems in understanding the documentation. As I said, most of the documents tell us to add those configuration lines into slapd.conf but now it has changed so I don't know how to add probably. 

anyway thanks bro!
Still waiting for someone with good answers!

---

### Post by luvshines on 2011-10-15
As I understood it, slapd.conf was the old way where configs were static. Any changes made to the file needed to restart the ldap service
With slapd.d, it accepts run-time changes by creating and loading the ldif file

I simply threw away the new method and still love the old slapd.conf way ;)

Don't know for sure but may look like a starting point
[http://www.zytrax.com/books/ldap/ch6/slapd-config.html](http://www.zytrax.com/books/ldap/ch6/slapd-config.html)

---

### Post by trongbang on 2011-10-17
> **luvshines said:**
> As I understood it, slapd.conf was the old way where configs were static. Any changes made to the file needed to restart the ldap service
With slapd.d, it accepts run-time changes by creating and loading the ldif file

I simply threw away the new method and still love the old slapd.conf way ;)

Don't know for sure but may look like a starting point
[http://www.zytrax.com/books/ldap/ch6/slapd-config.html](http://www.zytrax.com/books/ldap/ch6/slapd-config.html)


Yes, I love the old way of doing it. So how did you change to the old way? I got stuck and I don't know how to use slapd.conf now.

---

### Post by luvshines on 2011-10-18
> **trongbang said:**
> Yes, I love the old way of doing it. So how did you change to the old way? I got stuck and I don't know how to use slapd.conf now.

Well it has been a long time since I did it. For you , I have reconfigured it on a test machine to document these steps
It's plain LDAP with no SSL/TLS, using berkeley database:

1. Switched to root user and renamed the directory slapd.d to slapd.d.new dir in /etc/ldap directory
2. Copied my slapd.conf from old system to /etc/ldap directory. Added moduleload line since required with this ldap server. The file now looks like```

include		/etc/ldap/schema/core.schema
include		/etc/ldap/schema/cosine.schema
include		/etc/ldap/schema/inetorgperson.schema
include		/etc/ldap/schema/nis.schema

allow bind_v2

argsfile	/var/run/slapd/slapd.args

moduleload      back_bdb.la
database	bdb

suffix		"dc=luvshines,dc=com"

rootdn		"cn=Manager,dc=luvshines,dc=com"
rootpw		secret

directory	/var/lib/ldap

index objectClass                       eq,pres
index ou,cn,mail,surname,givenname      eq,pres,sub
index uidNumber,gidNumber,loginShell    eq,pres
index uid,memberUid                     eq,pres,sub
index nisMapName,nisMapEntry            eq,pres,sub

```
3. chown openldap : openldap /etc/ldap/slapd.conf
4. Also changed /etc/default/slapd to look like ```
SLAPD_CONF="/etc/ldap/slapd.conf" # Updated file location
SLAPD_USER="openldap"
SLAPD_GROUP="openldap"
SLAPD_PIDFILE="/var/run/slapd/slapd.pid" # Added pid file location
SLAPD_SERVICES="ldap:///" # Removed ldapi:///
SLAPD_SENTINEL_FILE=/etc/ldap/noslapd
SLAPD_OPTIONS=""
```
5. Also copied DB_CONFIG file from an old system to /var/lib/ldap directory and chown openldap : openldap it. Haven't checked why it is required but atleast slapcat doesn't crib for same when called
6. Hacked /etc/init.d/slapd to create/remove pid file on start/stop```

# Added this pid line before the closing } of start_slapd funtion
        # Backward compatibility with OpenLDAP 2.1 client libraries.
        if [ ! -h /var/run/ldapi ] && [ ! -e /var/run/ldapi ] ; then
                ln -s slapd/ldapi /var/run/ldapi
        fi
        pidof /usr/sbin/slapd > "$SLAPD_PIDFILE"
}

# Similarly remove pid line before closing } of stop_slapd function
        rm -f "$SLAPD_PIDFILE"
}
``` Needed this so that slapd start/stop/status is smooth else it reported 'stopped' even when it was running and won't stop it on 'service slapd stop'
7. Now started the slapd service, added users and it was done

Hope this helps !!

Note:
1. Haven't tried SSL with this. Don't know if that runs smoothly or not
2. Haven't added any special schema, just basic ones
3. Maybe if this works for you, you can try adding some security to it and keep documenting it all the way

Best of Luck !!

---

