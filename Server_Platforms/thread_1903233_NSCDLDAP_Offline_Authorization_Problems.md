---
title: "NSCD/LDAP Offline Authorization Problems"
date: 2012-01-02
forum: Server Platforms
---

### Post by linuxpyro on 2012-01-02
I'm setting up Kerberos and LDAP on my network, and would like to be able to have some machines do authentication/authorization offline.  I have not been able to get this to work, and I have the problem narrowed down to something with LDAP.  Here is what I get in /var/log/auth.log on the client when I try to log in via SSH, with my LDAP server stopped:

```

Jan  2 00:39:23 client sshd[3050]: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jan  2 00:39:23 client sshd[3050]: nss_ldap: failed to bind to LDAP server ldap://server/: Can't contact LDAP server
Jan  2 00:39:23 client sshd[3050]: nss_ldap: reconnecting to LDAP server...
Jan  2 00:39:23 client sshd[3050]: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jan  2 00:39:23 client sshd[3050]: nss_ldap: failed to bind to LDAP server ldap://server/: Can't contact LDAP server
Jan  2 00:39:23 client sshd[3050]: nss_ldap: reconnecting to LDAP server (sleeping 1 seconds)...
Jan  2 00:39:24 client sshd[3050]: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jan  2 00:39:24 client sshd[3050]: nss_ldap: failed to bind to LDAP server ldap://server/: Can't contact LDAP server
Jan  2 00:39:24 client sshd[3050]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  2 00:39:24 client sshd[3050]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jan  2 00:39:24 client sshd[3050]: pam_ldap: reconnecting to LDAP server...
Jan  2 00:39:24 client sshd[3050]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jan  2 00:39:24 client sshd[3050]: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jan  2 00:39:24 client sshd[3050]: nss_ldap: failed to bind to LDAP server ldap://server/: Can't contact LDAP server
Jan  2 00:39:24 client sshd[3050]: nss_ldap: reconnecting to LDAP server...
Jan  2 00:39:24 client sshd[3050]: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jan  2 00:39:24 client sshd[3050]: nss_ldap: failed to bind to LDAP server ldap://server/: Can't contact LDAP server
Jan  2 00:39:24 client sshd[3050]: nss_ldap: reconnecting to LDAP server (sleeping 1 seconds)...
Jan  2 00:39:25 client sshd[3050]: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jan  2 00:39:25 client sshd[3050]: nss_ldap: failed to bind to LDAP server ldap://server/: Can't contact LDAP server
Jan  2 00:39:25 client sshd[3050]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  2 00:39:25 client sshd[3050]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jan  2 00:39:25 client sshd[3050]: pam_ldap: reconnecting to LDAP server...
Jan  2 00:39:25 client sshd[3050]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jan  2 00:39:25 client sshd[3050]: Failed password for krbtest from 192.168.1.50 port 44792 ssh2
Jan  2 00:40:10 client nscd: nss_ldap: reconnecting to LDAP server...
Jan  2 00:40:10 client nscd: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jan  2 00:40:10 client nscd: nss_ldap: failed to bind to LDAP server ldap://server/: Can't contact LDAP server
Jan  2 00:40:10 client nscd: nss_ldap: reconnecting to LDAP server (sleeping 1 seconds)...
Jan  2 00:40:12 client nscd: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jan  2 00:40:12 client nscd: nss_ldap: failed to bind to LDAP server ldap://server/: Can't contact LDAP server
Jan  2 00:40:12 client nscd: nss_ldap: could not search LDAP server - Server is unavailable

```

With the LDAP server started I can log in as an LDAP user just fine, and I don't see any of this.  It appears that nscd isn't caching anything, or isn't giving pam the credentials it needs.

Here are configuration files from the client

/etc/pam.d/common-auth:
```

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	required                        pam_group.so use_first_pass
auth	[success=5 default=ignore]	pam_krb5.so minimum_uid=1000 try_first_pass
auth	[success=4 default=ignore]	pam_unix.so nullok_secure try_first_pass
auth	[success=3 default=ignore]	pam_ldap.so use_first_pass
auth	[success=2 default=ignore]	pam_ccreds.so minimum_uid=1000 action=validate use_first_pass
auth	[default=ignore]		pam_ccreds.so minimum_uid=1000 action=update
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional			pam_ccreds.so minimum_uid=1000 action=store
auth	optional	pam_ecryptfs.so unwrap
auth	optional			pam_cap.so 
# end of pam-auth-update config

```

/etc/nsswitch.conf:
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

# pre_auth-client-config # passwd:         compat
passwd: files ldap [NOTFOUND=return] db
# pre_auth-client-config # group:          compat
group: files ldap [NOTFOUND=return] db
# pre_auth-client-config # shadow:         compat
shadow: files ldap

hosts:          files mdns4_minimal dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

# pre_auth-client-config # netgroup:       nis
netgroup: nis

```

/etc/nscd.conf:
```

#
# /etc/nscd.conf
#
# An example Name Service Cache config file.  This file is needed by nscd.
#
# Legal entries are:
#
#	logfile			<file>
#	debug-level		<level>
#	threads			<initial #threads to use>
#	max-threads		<maximum #threads to use>
#	server-user             <user to run server as instead of root>
#		server-user is ignored if nscd is started with -S parameters
#       stat-user               <user who is allowed to request statistics>
#	reload-count		unlimited|<number>
#	paranoia		<yes|no>
#	restart-interval	<time in seconds>
#
#       enable-cache		<service> <yes|no>
#	positive-time-to-live	<service> <time in seconds>
#	negative-time-to-live   <service> <time in seconds>
#       suggested-size		<service> <prime number>
#	check-files		<service> <yes|no>
#	persistent		<service> <yes|no>
#	shared			<service> <yes|no>
#	max-db-size		<service> <number bytes>
#	auto-propagate		<service> <yes|no>
#
# Currently supported cache names (services): passwd, group, hosts, services
#


#	logfile			/var/log/nscd.log
#	threads			4
#	max-threads		32
#	server-user		nobody
#	stat-user		somebody
	debug-level		0
#	reload-count		5
	reload-count		unlimited
	paranoia		no
#	restart-interval	3600

	enable-cache		passwd		yes
	positive-time-to-live	passwd		600
	negative-time-to-live	passwd		20
	suggested-size		passwd		211
	check-files		passwd		yes
	persistent		passwd		yes
	shared			passwd		yes
	max-db-size		passwd		33554432
	auto-propagate		passwd		yes

	enable-cache		group		yes
	positive-time-to-live	group		3600
	negative-time-to-live	group		60
	suggested-size		group		211
	check-files		group		yes
	persistent		group		yes
	shared			group		yes
	max-db-size		group		33554432
	auto-propagate		group		yes

# hosts caching is broken with gethostby* calls, hence is now disabled
# per default.  See /usr/share/doc/nscd/NEWS.Debian.
	enable-cache		hosts		no
	positive-time-to-live	hosts		3600
	negative-time-to-live	hosts		20
	suggested-size		hosts		211
	check-files		hosts		yes
	persistent		hosts		yes
	shared			hosts		yes
	max-db-size		hosts		33554432

	enable-cache		services	yes
	positive-time-to-live	services	28800
	negative-time-to-live	services	20
	suggested-size		services	211
	check-files		services	yes
	persistent		services	yes
	shared			services	yes
	max-db-size		services	33554432

```

I've been combing through howtos, and I did see mention of using libnss-db to do caching in [https://help.ubuntu.com/community/PamCcredsHowto]("https://help.ubuntu.com/community/PamCcredsHowto"), but I would prefer to use nscd.  Otherwise, I've been following that howto and [https://help.ubuntu.com/community/LDAPClientAuthentication]("https://help.ubuntu.com/community/LDAPClientAuthentication").  I've searched around, but haven't been able to find much.  Has anyone else gotten offline authorization working?

---

### Post by linuxpyro on 2012-02-05
So I sort of solved my problem here, or at least worked around it.  I think that the problem here was that the libnss-pam module was trying to talk to the LDAP server regardless of nscd having a cached copy of the information it needed.  When the LDAP server went down, it just returned a failure.  I tried playing with the PAM configuration, but couldn't get this working.

What I ended up doing was switching to sssd, which I recommend.  It wasn't that hard to get going, basically I found this page and followed the guide at the bottom (the "LDAP/Kerberos + sssd + libpam-mklocaluser" section, although I don't use libpam-mklocaluser):
[http://people.skolelinux.org/pere/blog/Caching_password__user_and_group_on_a_roaming_Debian_laptop.html]("http://people.skolelinux.org/pere/blog/Caching_password__user_and_group_on_a_roaming_Debian_laptop.html")

I can now log in to a machine with a Kerberos/LDAP account even if the authentication server is down.  (Although you still have to log in once with the server up so it can cache it, of course.)

---

