---
title: "NSS mappings required for LDAP to work?"
date: 2012-12-20
forum: Server Platforms
---

### Post by Philip Colmer on 2012-12-20
I've been following the ubuntu documentation on setting up an LDAP server ([https://help.ubuntu.com/12.04/serverguide/openldap-server.html](https://help.ubuntu.com/12.04/serverguide/openldap-server.html)) and an LDAP client ([https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)).

As I understand it, ubuntu now has a variety of schemas built in (which previously needed manually adding) including inetorgperson. It is this class that I'm using when I define users.

However, although I've got the client communicating with the server, commands like "getent passwd" aren't returning any results from LDAP.

Running slapd in debug mode shows that getent is querying a whole bunch of attributes and classes that appear to belong to the Posix schema. As a result, I've tried updating /etc/ldap.conf on the client to adjust these over to the inetorgperson schema:

nss_map_objectclass posixAccount inetOrgPerson
nss_map_objectclass shadowAccount inetOrgPerson
nss_map_objectclass posixGroup groupOfUniqueNames

This shows users being explicitly queried on the LDAP server but getent still isn't displaying anything. At the moment, I don't know what other  attributes or classes I need to map but I suspect that is what I need to do in order to get this working.

Has anyone else used inetOrgPerson with OpenLDAP and had to make some nss entries to get it to work?

Philip

---

### Post by sandyd on 2012-12-20
Interesting.

I used libpam-ldapd, and everything worked, after entering the bindpw into nslcd.

Can you post your /etc/nsswitch.conf ?

---

### Post by Philip Colmer on 2012-12-21
Hi

Here is /etc/nsswitch.conf:

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

# pre_auth-client-config # passwd:         compat
passwd: files ldap
# pre_auth-client-config # group:          compat
group: files ldap
# pre_auth-client-config # shadow:         compat
shadow: files ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

# pre_auth-client-config # netgroup:       nis
netgroup: nis

I did try libnss.ldapd, libpam.ldapd and nslcd but the logs were showing the same challenge of trying to map requests for Posix-schema items over to the schema I'm using.

Unfortunately, I cannot move over to using the Posix schema because that will cause me problems elsewhere with a different application I'm using - Atlassian Crowd. Unless I've misread the documentation for Crowd, it looks like using the Posix schema gives me two limitations - Crowd will only support it in a read-only mode and will not handle nested groups.

So I do need to get it working with the inetorgperson schema and I'm really puzzled as to why Ubuntu isn't supporting this in a cleaner manner or at least with some commented out mapping statements.

Thanks for any help you can provide.

Philip

---

### Post by Philip Colmer on 2012-12-21
I've purged both the client and the server and started again, and it seems to be working OK now - at least with the sample data that [https://help.ubuntu.com/12.04/serverguide/openldap-server.html](https://help.ubuntu.com/12.04/serverguide/openldap-server.html) gets you to add.

In that sample data, though, the user has multiple classes (inetOrgPerson, posixAccount and shadowAccount) so I'll need to do some further testing with Crowd to make sure it is "happy" with that. At least, though, getent passwd is returning John Doe from the LDAP server.

Curious ...

---

