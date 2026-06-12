---
title: "eDirectory LDAP authentication: nss_ldap stuck on gettimeofday"
date: 2009-02-27
forum: Server Platforms
---

### Post by lamsgael on 2009-02-27
Hi all

I'm trying to configure a server to perform ldap authentication. The ldap backend is a Novell eDierctory.

I first followed the ubuntu documentation but a "getent passwd username" was giving anything back. I was seeing a " nss_ldap: could not search LDAP server - Server is unavailable" on the log even if on the eDirectory log the connection was accepted.

I then decide to do the configuration by hand (I already have +/- 60 SLES servers performing LDAP authentication on the eDirectory), but stil have the same problem (actually my working SLES configuration of /etc/ldap.conf was really similar to the ubuntu generated one).

also tcpdump confirm that the connection with the LDAP backend is established.

I then used "strace getent ..." and saw that after establishing the connection the ldap backend (getpeername(3, {sa_family=AF_INET, sin_port=htons(389), sin_addr=inet_addr("172.20.11.11")}, [16]) = 0
) strace get stuck with I don't know how many:
gettimeofday({1235747668, 479783}, NULL) = 0
getrusage(RUSAGE_SELF, {ru_utime={0, 10000}, ru_stime={0, 20000}, ...}) = 0
time(NULL)                              = 1235747668
times({tms_utime=1, tms_stime=2, tms_cutime=0, tms_cstime=0}) = 1837394
 
On the SLES machines, after the connection with the backend is established. I see a getuid and the result is writtend.

The connection should be established in TLS.

I found this thread :
[http://www.nabble.com/ldapsearch-works---nss_ldap-does-not---but-only-when-tls-ssl-isenabled-p10643733.html](http://www.nabble.com/ldapsearch-works---nss_ldap-does-not---but-only-when-tls-ssl-isenabled-p10643733.html)

I'm wondering whether it's a bug?

Any help would be appreciated

here below a copy of /etc/ldap.conf and nsswitch.conf

Regards,

Gael

ldap.conf
# Your LDAP server.
host myhost.mydomain.org 

# The distinguished name of the search base.
base o=ITC_ILO

# The LDAP version to use (defaults to 3
# if supported by client library)
ldap_version 3

# Reconnect policy: hard (default) will retry connecting to
# the software with exponential backoff, soft will fail
# immediately.
bind_policy soft

# Group to enforce membership of
pam_groupdn cn=GP-SOLICOMM,ou=SSH,ou=GROUPS,o=ITC_ILO

pam_password md5

# Remove old password first, then update in
# cleartext. Necessary for use with Novell
# Directory Services (NDS)
pam_password clear_remove_old
pam_password nds

# configure --enable-nds is no longer supported.
# NDS mappings
#nss_map_attribute uniqueMember member

# OpenLDAP SSL mechanism
# start_tls mechanism uses the normal LDAP port, LDAPS typically 636
ssl start_tls
#ssl on

# For NDS:

nss_map_attribute uniqueMember member
nss_reconnect_tries 2
pam_filter objectclass=posixAccount

nss_base_passwd o=ITC_ILO

nss_base_shadow o=ITC_ILO

nss_base_group o=ITC_ILO 

/etc/nsswitch.conf

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

netgroup:       nis

---

