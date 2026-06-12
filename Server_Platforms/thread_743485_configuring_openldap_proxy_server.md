---
title: "configuring openldap proxy server"
date: 2008-04-02
forum: Server Platforms
---

### Post by Beta-Glitch on 2008-04-02
Hi everyone

**Situation:**
I'm struggling to setup a test LDAP proxy at home so I can replicate the setup at work (after having tried several times at work already).

Basically we want to use the LDAP directory on our MAC OS X server outside our firewall for our centres. to do this safely, we want to use an LDAP proxy that is internet facing and also network facing to retreive the information from the main LDAP directory, then cut out the cruft that's not needed, and present the information.

So far, I've managed to successfully setup the ldap proxy, re-write the base-DN, and map and cut out the objectclasses. I'm struggling to fixgure out why I can't do the same to the attributes.

**Configuration:**
Below is my slapd.conf:

```
# Schema and objectClass definitions

include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/misc.schema
include         /etc/ldap/schema/samba.schema
include         /etc/ldap/schema/fmserver.schema
include         /etc/ldap/schema/apple.schema

pidfile         /var/run/slapd/slapd.pid
argsfile        /var/run/slapd/slapd.args
loglevel        any
modulepath	/usr/lib/ldap
moduleload	back_ldap
moduleload	rwm
tool-threads 1




database        ldap

suffix          "dc=aubrey,dc=org,dc=uk"
uri		"ldap://192.168.10.10"
lastmod         off

overlay 	rwm

rwm-suffixmassage "dc=test,dc=aubrey,dc=org,dc=uk" "cn=users,dc=homesvr,dc=aubrey,dc=org,dc=uk"
rwm-map	objectClass	inetOrgPerson 	*
rwm-map	objectClass	extensibleObject 	*
rwm-map	objectClass	top 	*
rwm-map objectClass	*
rwm-map attribute	sn	*
rwm-map attribute	cn	*
rwm-map	attribute	uid	*
rwm-map attribute		*

```

As I said this is a test, so for simplicity I've only mapped the inetOrgPerson from the Mac server, and then only mapped the sn and cn (the requirements for inetOrgPerson), and the uid (as this is the DN for each object). I've included all the schema included on my OS X Server box, and patch up an issue with the apple-specific schema too (well documented on the internet to do with authauthority attribute)

**Expected result:**
As you can see, the rwm-map lines should show only these attributes, then remove all others. 

**actual result:**
I get a blank result set.

**Testing already done:**
If I remove the line "rwm-map attribute		*", I get all the attributes, minus the objectclasses that should have been removed with the similar line above it.

I've enabled full logging and tried a search. It doesn't mean much to me, but for help to others:
```
Apr  2 19:25:00 ldapproxy slapd[7659]: daemon: activity on 1 descriptor 
Apr  2 19:25:00 ldapproxy slapd[7659]: daemon: activity on:
Apr  2 19:25:00 ldapproxy slapd[7659]:  
Apr  2 19:25:00 ldapproxy slapd[7659]: >>> slap_listener(ldap:///) 
Apr  2 19:25:00 ldapproxy slapd[7659]: daemon: listen=8, new connection on 9 
Apr  2 19:25:00 ldapproxy slapd[7659]: daemon: added 9r (active) listener=(nil) 
Apr  2 19:25:00 ldapproxy slapd[7659]: conn=0 fd=9 ACCEPT from IP=127.0.0.1:59650 (IP=0.0.0.0:389) 
Apr  2 19:25:00 ldapproxy slapd[7659]: daemon: epoll: listen=7 active_threads=0 tvp=NULL 
Apr  2 19:25:00 ldapproxy slapd[7659]: daemon: epoll: listen=8 active_threads=0 tvp=NULL 
Apr  2 19:25:00 ldapproxy slapd[7659]: daemon: activity on 1 descriptor 
Apr  2 19:25:00 ldapproxy slapd[7659]: daemon: activity on:
Apr  2 19:25:00 ldapproxy slapd[7659]:  9r
Apr  2 19:25:00 ldapproxy slapd[7659]:  
Apr  2 19:25:00 ldapproxy slapd[7659]: daemon: read active on 9 
Apr  2 19:25:00 ldapproxy slapd[7659]: connection_get(9) 
Apr  2 19:25:00 ldapproxy slapd[7659]: connection_get(9): got connid=0 
Apr  2 19:25:00 ldapproxy slapd[7659]: connection_read(9): checking for input on id=0 
Apr  2 19:25:00 ldapproxy slapd[7659]: daemon: epoll: listen=7 active_threads=0 tvp=NULL 
Apr  2 19:25:00 ldapproxy slapd[7659]: daemon: epoll: listen=8 active_threads=0 tvp=NULL 
Apr  2 19:25:00 ldapproxy slapd[7659]: do_bind 
Apr  2 19:25:00 ldapproxy slapd[7659]: >>> dnPrettyNormal: <> 
Apr  2 19:25:00 ldapproxy slapd[7659]: <<< dnPrettyNormal: <>, <> 
Apr  2 19:25:00 ldapproxy slapd[7659]: do_bind: version=3 dn="" method=128 
Apr  2 19:25:00 ldapproxy slapd[7659]: conn=0 op=0 BIND dn="" method=128 
Apr  2 19:25:00 ldapproxy slapd[7659]: send_ldap_result: conn=0 op=0 p=3 
Apr  2 19:25:00 ldapproxy slapd[7659]: send_ldap_result: err=0 matched="" text="" 
Apr  2 19:25:00 ldapproxy slapd[7659]: send_ldap_response: msgid=1 tag=97 err=0 
Apr  2 19:25:01 ldapproxy slapd[7659]: daemon: activity on 1 descriptor 
Apr  2 19:25:01 ldapproxy slapd[7659]: daemon: activity on:
Apr  2 19:25:01 ldapproxy slapd[7659]:  9r
Apr  2 19:25:01 ldapproxy slapd[7659]:  
Apr  2 19:25:01 ldapproxy slapd[7659]: daemon: read active on 9 
Apr  2 19:25:01 ldapproxy slapd[7659]: connection_get(9) 
Apr  2 19:25:01 ldapproxy slapd[7659]: connection_get(9): got connid=0 
Apr  2 19:25:01 ldapproxy slapd[7659]: connection_read(9): checking for input on id=0 
Apr  2 19:25:01 ldapproxy slapd[7659]: daemon: epoll: listen=7 active_threads=0 tvp=NULL 
Apr  2 19:25:01 ldapproxy slapd[7659]: daemon: epoll: listen=8 active_threads=0 tvp=NULL 
Apr  2 19:25:01 ldapproxy slapd[7659]: do_search 
Apr  2 19:25:01 ldapproxy slapd[7659]: >>> dnPrettyNormal: <dc=test,dc=aubrey,dc=org,dc=uk> 
Apr  2 19:25:01 ldapproxy slapd[7659]: <<< dnPrettyNormal: <dc=test,dc=aubrey,dc=org,dc=uk>, <dc=test,dc=aubrey,dc=org,dc=uk> 
Apr  2 19:25:01 ldapproxy slapd[7659]: SRCH "dc=test,dc=aubrey,dc=org,dc=uk" 1 3
Apr  2 19:25:01 ldapproxy slapd[7659]:     0 0 0 
Apr  2 19:25:01 ldapproxy slapd[7659]: begin get_filter 
Apr  2 19:25:01 ldapproxy slapd[7659]: PRESENT 
Apr  2 19:25:01 ldapproxy slapd[7659]: end get_filter 0 
Apr  2 19:25:01 ldapproxy slapd[7659]:     filter: (objectClass=*) 
Apr  2 19:25:01 ldapproxy slapd[7659]:     attrs:
Apr  2 19:25:01 ldapproxy slapd[7659]:  objectclass
Apr  2 19:25:01 ldapproxy slapd[7659]:  
Apr  2 19:25:01 ldapproxy slapd[7659]: conn=0 op=1 SRCH base="dc=test,dc=aubrey,dc=org,dc=uk" scope=1 deref=3 filter="(objectClass=*)" 
Apr  2 19:25:01 ldapproxy slapd[7659]: conn=0 op=1 SRCH attr=objectclass 
Apr  2 19:25:01 ldapproxy slapd[7659]: ==> limits_get: conn=0 op=1 dn="[anonymous]" 
Apr  2 19:25:01 ldapproxy slapd[7659]: [rw] searchDN: "dc=test,dc=aubrey,dc=org,dc=uk" -> "cn=users,dc=homesvr,dc=aubrey,dc=org,dc=uk" 
Apr  2 19:25:01 ldapproxy slapd[7659]: >>> dnPrettyNormal: <cn=users,dc=homesvr,dc=aubrey,dc=org,dc=uk> 
Apr  2 19:25:01 ldapproxy slapd[7659]: <<< dnPrettyNormal: <cn=users,dc=homesvr,dc=aubrey,dc=org,dc=uk>, <cn=users,dc=homesvr,dc=aubrey,dc=org,dc=uk> 
Apr  2 19:25:01 ldapproxy slapd[7659]: str2filter "(!(objectClass=*))" 
Apr  2 19:25:01 ldapproxy slapd[7659]: begin get_filter 
Apr  2 19:25:01 ldapproxy slapd[7659]: NOT 
Apr  2 19:25:01 ldapproxy slapd[7659]: begin get_filter 
Apr  2 19:25:01 ldapproxy slapd[7659]: PRESENT 
Apr  2 19:25:01 ldapproxy slapd[7659]: end get_filter 0 
Apr  2 19:25:01 ldapproxy slapd[7659]: end get_filter 0 
Apr  2 19:25:01 ldapproxy slapd[7659]: conn=0 op=0 RESULT tag=97 err=0 text= 
Apr  2 19:25:01 ldapproxy slapd[7659]: do_bind: v3 anonymous bind 
Apr  2 19:25:01 ldapproxy slapd[7659]: send_ldap_result: conn=0 op=1 p=3 
Apr  2 19:25:01 ldapproxy slapd[7659]: send_ldap_result: err=0 matched="" text="" 
Apr  2 19:25:01 ldapproxy slapd[7659]: send_ldap_result: conn=0 op=1 p=3 
Apr  2 19:25:01 ldapproxy slapd[7659]: send_ldap_result: err=0 matched="" text="" 
Apr  2 19:25:01 ldapproxy slapd[7659]: send_ldap_response: msgid=2 tag=101 err=0 
Apr  2 19:25:01 ldapproxy slapd[7659]: conn=0 op=1 SEARCH RESULT tag=101 err=0 nentries=0 text=
```

I've read the man pages inside out trying to find what I'm doing wrong, and It all seems fine. I've googled it dosens of times too, with no luck.

Can anyone with more experience configuring openldap show me whats wrong, or at least point me in the direction of a resource I can use.

thanks

- Scott

---

