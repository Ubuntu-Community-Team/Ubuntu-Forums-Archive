---
title: "Kerberized LDAP access causing daemon problems"
date: 2009-10-09
forum: Server Platforms
---

### Post by Despot on 2009-10-09
I was hoping somebody could help me with a bit of an issue I'm having with authentication to my LDAP directory using Kerberos.

I've got Kerberos working properly, and I'm using it for authentication for all hosts on my network. I recently configured my OpenLDAP directory (running on Ubunt 8.04 Server) to start using Kerberos for authentication.

I've been partially successful: I can search the directory, and I've been able to configure my hosts to authenticate correctly, so they can get user and group information from the directory. The usual "getent passwd" and "ldapwhoami" tests pass, both as a standard user, and as root.

However, I still have a bit of an issue with daemons on my Jaunty desktops. In particular, I'm not sure how to configure the DBus daemon to properly authenticate using Kerberos. I keep getting message in /var/log/auth.log that nss_ldap couldn't find a credentials cache when requested to get user/group info by dbus-daemon.

I tried to create a credentials cache that was owned by the messagebus user (I believe that this is the user that the dbus daemon runs under, based on what ps tells me), and put KRB5CCNAME="/path/to/cache" environment variable in /etc/default/dbus, but that did not solve the problem.

Any ideas? Here's a snip from auth.log:

> 
Oct  9 20:24:49 <host> dbus-daemon: nss_ldap: reconnecting to LDAP server...
Oct  9 20:24:49 <host> dbus-daemon: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (No credentials cache found)
Oct  9 20:24:49 <host> dbus-daemon: nss_ldap: failed to bind to LDAP server ldap://<server.fqdn>/: Local error
Oct  9 20:24:49 <host> dbus-daemon: nss_ldap: reconnecting to LDAP server (sleeping 1 seconds)...
Oct  9 20:24:50 <host> dbus-daemon: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (No credentials cache found)
Oct  9 20:24:50 <host> dbus-daemon: nss_ldap: failed to bind to LDAP server ldap://<server.fqdn>/: Local error
Oct  9 20:24:50 <host> dbus-daemon: nss_ldap: could not search LDAP server - Server is unavailable


---

### Post by Despot on 2009-10-11
This is definitely a permissions issue: given rw privileges to all users allows the dbus daemon to do its thing. Seems the "No credentials cache found" really means "Permission denied when trying access credentials cache"

Now to figure out exactly what user the daemon is running under...

---

### Post by Despot on 2009-10-16
It seems that using the environment variables with dbus has no effect, since the messagebus user's shell is set to /bin/false. If I understand things correctly, the lack of shell means there is no way for a daemon like dbus to be configured with its own credentials cache, since the KRB5_CCNAME environment variable is the only way that I know of to configure a credentials cache for a specific daemon.

I discovered a fork of nss-ldap called nss-ldapd ([http://arthurdejong.org/nss-pam-ldapd/](http://arthurdejong.org/nss-pam-ldapd/)). nss-ldapd implements a daemon to interface with the LDAP directory instead of requiring each user to connect as needed. This handily solves the permissions problems for daemons like dbus, since any daemon or user on the system can talk to the nss-ldapd daemon. I'm not sure about the security ramifications yet, but for now it's working.

The latest version of nss-ldapd is available in the Debian Sid repo, and can be installed directly to Ubuntu Jaunty. Details on getting the correct keys (to avoid apt warnings about unverified packages, and generally wise when you're installing packages related to authentication services!) can be found here: [http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt) (the key for Sid is the same as the key for Lenny).

---

