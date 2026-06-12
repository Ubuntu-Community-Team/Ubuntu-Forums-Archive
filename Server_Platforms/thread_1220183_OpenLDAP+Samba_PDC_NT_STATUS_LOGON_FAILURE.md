---
title: "OpenLDAP+Samba PDC NT_STATUS_LOGON_FAILURE"
date: 2009-07-22
forum: Server Platforms
---

### Post by black_wolf on 2009-07-22
I'm trying to use OpenLDAP for user management/authentication using this tutorial: [[HOW TO] Ubuntu Server 9.04 PDC]("http://ubuntuforums.org/showthread.php?t=1184288"), except that I'm not using slapd.conf (file) to hold the configuration, I'm using the database itself. Eventually this LDAP server should be used with a host of other services, but for now I'm just trying to get it to work with Samba (as a PDC).

The LDAP directory is set up, and has a few users in the database. The LDAP database also has entries for the server's local accounts as well as a test account I've added.

When trying to log into the server using samba with an LDAP account (only) after typing the password I get an error:

> session setup failed: NT_STATUS_LOGON_FAILURE

However logging in with a local account works correctly as expected.

I'm able to do an ldapsearch and display the users. But doing getent passwd doens't display any of the test accounts (which should be there if this was working correctly).

I'm thinking that its a problem with PAM/NSS, but I can't figure out where to go from here. Any ideas?:confused:

---

