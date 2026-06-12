---
title: "Ubuntu 8.10 LDAP client"
date: 2009-04-15
forum: Server Platforms
---

### Post by smythsys on 2009-04-15
Hi,

     I've set up a 8.10 Ubuntu LDAP server on a local network. It seems to be working fine locally (I can ldap search, phpldap manage and so on).
 
    The problems arise when trying to connect a client. The client can ldapsearch the server (specifying the ip address). However when I try any command and it queries the server (finder, pamtest, getent...) I get auth failed and on the auth log I get the following.


[I]Apr 15 15:44:58 Puesto1 pamtest: PAM unable to dlopen(/lib/security/pam_foreground.so): /lib/security/pam_foreground.so: cannot open shared object file: No such file or directory
Apr 15 15:44:58 Puesto1 pamtest: PAM adding faulty module: /lib/security/pam_foreground.so
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: failed to bind to LDAP server ldapi:///192.168.1.168: Can't contact LDAP server
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: reconnecting to LDAP server...
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: failed to bind to LDAP server ldapi:///192.168.1.168: Can't contact LDAP server
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: reconnecting to LDAP server (sleeping 1 seconds)...
Apr 15 15:45:02 Puesto1 pamtest: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Apr 15 15:45:02 Puesto1 pamtest: nss_ldap: failed to bind to LDAP server ldapi:///192.168.1.168: Can't contact LDAP server
Apr 15 15:45:02 Puesto1 pamtest: nss_ldap: could not search LDAP server - Server is unavailable
Apr 15 15:45:02 Puesto1 pamtest: pam_unix(passwd:auth): check pass; user unknown
Apr 15 15:45:02 Puesto1 pamtest: pam_unix(passwd:auth): authentication failure; logname=persona uid=1000 euid=1000 tty= ruser= rhost=[/I]


Would anybody know why the client can´t connect to the server?
I'd appreciate any help.

Thanks

---

### Post by JochenJung on 2009-04-16
On our servers (SLES 9) I got the issue, that ldapsearch was using /etc/openldap/ldap.conf, but PAM was looking into /etc/ldap.conf

Maybe these two use differnt config files in Ubuntu, too.

---

### Post by shunan on 2009-04-18
> **smythsys said:**
> Hi,

     I've set up a 8.10 Ubuntu LDAP server on a local network. It seems to be working fine locally (I can ldap search, phpldap manage and so on).
 
    The problems arise when trying to connect a client. The client can ldapsearch the server (specifying the ip address). However when I try any command and it queries the server (finder, pamtest, getent...) I get auth failed and on the auth log I get the following.


[I]Apr 15 15:44:58 Puesto1 pamtest: PAM unable to dlopen(/lib/security/pam_foreground.so): /lib/security/pam_foreground.so: cannot open shared object file: No such file or directory
Apr 15 15:44:58 Puesto1 pamtest: PAM adding faulty module: /lib/security/pam_foreground.so
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: failed to bind to LDAP server ldapi:///192.168.1.168: Can't contact LDAP server
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: reconnecting to LDAP server...
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: failed to bind to LDAP server ldapi:///192.168.1.168: Can't contact LDAP server
Apr 15 15:45:01 Puesto1 pamtest: nss_ldap: reconnecting to LDAP server (sleeping 1 seconds)...
Apr 15 15:45:02 Puesto1 pamtest: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Apr 15 15:45:02 Puesto1 pamtest: nss_ldap: failed to bind to LDAP server ldapi:///192.168.1.168: Can't contact LDAP server
Apr 15 15:45:02 Puesto1 pamtest: nss_ldap: could not search LDAP server - Server is unavailable
Apr 15 15:45:02 Puesto1 pamtest: pam_unix(passwd:auth): check pass; user unknown
Apr 15 15:45:02 Puesto1 pamtest: pam_unix(passwd:auth): authentication failure; logname=persona uid=1000 euid=1000 tty= ruser= rhost=[/I]


Would anybody know why the client can´t connect to the server?
I'd appreciate any help.

Thanks
We had a similar issue where the reserver DNS was not set!

Try using the FQDN for in the ldap config file rather than the IP!

So instead of dapi:///192.168.1.168/ try using the servername.domainname.com

---

### Post by smythsys on 2009-04-19
For any who encounters the problem.

   The problem is with using ldapi.  If you use ldap:// (2 backslash not 3) on both server and client it works.

        Seems ldapi is the future but still not working correctly.

---

### Post by nroussi on 2009-04-28
thank you smythsys.  it worked perfectly

---

