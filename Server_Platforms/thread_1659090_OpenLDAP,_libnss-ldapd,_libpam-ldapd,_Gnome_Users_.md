---
title: "OpenLDAP, libnss-ldapd, libpam-ldapd, Gnome Users / Posix accounts..."
date: 2011-01-03
forum: Server Platforms
---

### Post by woodman231 on 2011-01-03
Hello,

I have tried to search the forums to see if anyone has had this problem before and I haven't see it.

I am trying to set up a terminal server (Free NX Server).  I haven't installed the Free NX on to this server yet because I want to make sure I have my LDAP and everything set up correct first.

I currently have Ubuntu Server 11.04 with GNome 2.32.0.  

I have installed OpenLDAP (slapd).

I am able to add users to LDAP both by using the ldapadduser command line script as well as using a GUI called JXplorer.


In fact the first LDAP user that I added was via the JXplorer and I used the following Ldap classes when I added it: inetOrgPerson, OrganizationPerson, posixAccount, shadowAccount, person, and top.  This user actually shows up on the gnome screen.  However the second user that I added using the exact same steps does not show up on the Gnome screen.

When I run "getent passwd" i see the users that I made.  When I run "su -l newaccount1" I am able to log in to the terminal just fine.  Same if I do "su -l newaccount2".  So the accounts work fine.  I also added one using the ldapadduser script and same results I can log in with them but they do not show up on the Gnome screen.

Good news as well is that if I select "Other" on the gnome screen I am able to log in to the accounts using the User Name and password from LDAP so *technically* I can log in to the LDAP accounts just fine.  And them not showing up on the Gnome login screen isn't that big of a deal.  It's just strange that only the first one shows up and the rest of them don't.

The problem that I do have is that when I go to System -> Administration -> Users and Groups I also don't see them there (for some reason not even the one that actually does appear on the Gnome login screen).  The big reason that I at least want the LDAP users to show up in the Users and Groups is so that I can access the "User Privileges" tab and administer the necessary things there.

I am using the libnss-ldapd and libpam-ldapd packages.

nscd.conf:
```

#
# /etc/nscd.conf
#
# An example Name Service Cache config file.  This file is needed by nscd.
#
# Legal entries are:
#
#    logfile            <file>
#    debug-level        <level>
#    threads            <initial #threads to use>
#    max-threads        <maximum #threads to use>
#    server-user             <user to run server as instead of root>
#        server-user is ignored if nscd is started with -S parameters
#       stat-user               <user who is allowed to request statistics>
#    reload-count        unlimited|<number>
#    paranoia        <yes|no>
#    restart-interval    <time in seconds>
#
#       enable-cache        <service> <yes|no>
#    positive-time-to-live    <service> <time in seconds>
#    negative-time-to-live   <service> <time in seconds>
#       suggested-size        <service> <prime number>
#    check-files        <service> <yes|no>
#    persistent        <service> <yes|no>
#    shared            <service> <yes|no>
#    max-db-size        <service> <number bytes>
#    auto-propagate        <service> <yes|no>
#
# Currently supported cache names (services): passwd, group, hosts, services
#


#    logfile            /var/log/nscd.log
#    threads            4
#    max-threads        32
#    server-user        nobody
#    stat-user        somebody
    debug-level        0
#    reload-count        5
    paranoia        no
#    restart-interval    3600

    enable-cache        passwd        yes
    positive-time-to-live    passwd        600
    negative-time-to-live    passwd        20
    suggested-size        passwd        211
    check-files        passwd        yes
    persistent        passwd        yes
    shared            passwd        yes
    max-db-size        passwd        33554432
    auto-propagate        passwd        yes

    enable-cache        group        yes
    positive-time-to-live    group        3600
    negative-time-to-live    group        60
    suggested-size        group        211
    check-files        group        yes
    persistent        group        yes
    shared            group        yes
    max-db-size        group        33554432
    auto-propagate        group        yes

# hosts caching is broken with gethostby* calls, hence is now disabled
# per default.  See /usr/share/doc/nscd/NEWS.Debian.
    enable-cache        hosts        no
    positive-time-to-live    hosts        3600
    negative-time-to-live    hosts        20
    suggested-size        hosts        211
    check-files        hosts        yes
    persistent        hosts        yes
    shared            hosts        yes
    max-db-size        hosts        33554432

    enable-cache        services    yes
    positive-time-to-live    services    28800
    negative-time-to-live    services    20
    suggested-size        services    211
    check-files        services    yes
    persistent        services    yes
    shared            services    yes
    max-db-size        services    33554432

```nslcd.conf
```

# /etc/nslcd.conf
# nslcd configuration file. See nslcd.conf(5)
# for details.

# The user and group nslcd should run as.
uid nslcd
gid nslcd

# The location at which the LDAP server(s) should be reachable.
uri ldap://localhost/

# The search base that will be used for all queries.
base dc=example,dc=com

# The LDAP protocol version to use.
#ldap_version 3

# The DN to bind with for normal lookups.
binddn cn=admin,dc=example,dc=com
bindpw xxxxx

# The DN used for password modifications by root.
#rootpwmoddn cn=admin,dc=example,dc=com

# SSL options
#ssl off
#tls_reqcert never

# The search scope.
#scope sub

```nssswitch.conf
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat ldap
group:          compat ldap
shadow:         compat ldap

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 ldap
networks:       files ldap

protocols:      db files ldap
services:       db files ldap
ethers:         db files
rpc:            db files ldap

netgroup:       nis ldap
aliases:        ldap

```pam.d/common-account
```

account    [success=1 new_authtok_reqd=done default=ignore]    pam_unix.so 
account    requisite            pam_deny.so
account    required            pam_permit.so
account    [success=ok user_unknown=ignore default=bad]    pam_ldap.so minimum_uid=1000

```pam.d/common-auth
```

auth    [success=2 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_ldap.so minimum_uid=1000 use_first_pass
auth    requisite            pam_deny.so
auth    required            pam_permit.so

```pam.d/common-password
```

password    requisite            pam_cracklib.so retry=3 minlen=8 difok=3
password    [success=2 default=ignore]    pam_unix.so obscure use_authtok try_first_pass sha512
password    [success=1 default=ignore]    pam_ldap.so minimum_uid=1000 try_first_pass use_authtok
password    requisite            pam_deny.so
password    required            pam_permit.so
password    optional    pam_gnome_keyring.so

```I have also been sure to make sure that the uidnumbers are all unique as well so this is very strange.

The preferred way for me to have it anyways is them not to show up in the Gnome screen but to show up within the Users and Groups management window, but if the users show up in both sections that is just fine.

Any help is greatly appreciated.

Thanks,
Sean W.

---

