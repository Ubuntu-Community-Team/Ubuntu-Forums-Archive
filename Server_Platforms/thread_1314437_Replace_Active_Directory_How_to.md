---
title: "Replace Active Directory How to"
date: 2009-11-04
forum: Server Platforms
---

### Post by bjbehrendt on 2009-11-04
I am soon going to need to either replace my Windows 2003 active directory with 2008 server or find another solution. I would prefer to use a linux server for authentication but I will need the same configuration features.

I have been looking for a good guide to setting up Ubuntu server or CentOS as an alternative to Active Directory, but have not found one yet.

The features I want to see.
1. works with Windows clients.
2. Network Home folders (does not neessisarly need to hold profile information)
3. Logon scripts for clients.
4. shared printers
5. shared folders.
6. can log linux boxes in with the same credentials and logon scripts.

-bj

---

### Post by Iowan on 2009-11-04
[Here]("https://help.ubuntu.com/community/OpenLDAPServer") is a help page for an LDAP server (with possible update link). 
[Here]("https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix") is another.
There's also a [Perfect Server]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2") article for Jaunty on howtoforge.com.

---

### Post by whoop on 2009-11-04
This (very complete) tutorial was written for ubuntu server 7.10 (which is end of life), but it also works for ubuntu server 8.04 (the current LTS):
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)
This is everything you need concerning open source active directory technology.

There are very little changes between 7.10 and 8.04 concerning this tutorial.

I found a little document on my hd, in which I documented all the changes I made for 8.04. It's not very user friendly and not all is required, but maybe it is useful to you (just ignore it, and check it if you get stuck in the tutorial):

```

/etc/mdadm.conf ==> /etc/mdadm/mdadm.conf
vim /etc/mdadm.conf  ==> vim /etc/mdadm/mdadm.conf 

<<++++++++++++++extra edits to slapd.conf++++++++++++++++>>
suffix          "dc=example,dc=local"

access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=nodomain" write
        by anonymous auth
        by self write
        by * none

access to *
        by dn="cn=admin,dc=example,dc=local" write
        by * read
<<++++++++++++++++++++++++++++++++++++++++++++++++++++++++>>


apparmor problem (add before /etc/init.d/slapd.start)
<<++++++++++++++++++++++START old /etc/apparmor.d/usr.sbin.slapd+++++++++++++++++++++++++++++++++++>>
# vim:syntax=apparmor
# Last Modified: Fri Jan  4 15:18:13 2008
# Author: Jamie Strandboge <jamie@ubuntu.com>

#include <tunables/global>

/usr/sbin/slapd {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  #include <abstractions/ssl_certs>
  /etc/ssl/private/ r,
  /etc/ssl/private/* r,

  /etc/sasldb2 r,

  capability dac_override,
  capability net_bind_service,
  capability setgid,
  capability setuid,

  /etc/gai.conf r,
  /etc/hosts.allow r,
  /etc/hosts.deny r,
  /etc/ldap/ldap.conf r,
  /etc/ldap/schema/* r,
  /etc/ldap/slapd.conf r,

  # the databases and logs
  /var/lib/ldap/ r,
  /var/lib/ldap/* rw,

  # lock file
  /var/lib/ldap/alock kw,

  # pid files and sockets
  /var/run/slapd/* w,

  /usr/lib/ldap/ r,
  /usr/lib/ldap/* mr,

  /usr/sbin/slapd mr,
}
<<++++++++++++++++++++++++++END old /etc/apparmor.d/usr.sbin.slapd+++++++++++++++++++++++++++++++++++>>

<<++++++++++++++++++++++START new /etc/apparmor.d/usr.sbin.slapd+++++++++++++++++++++++++++++++++++>>
# vim:syntax=apparmor
# Last Modified: Fri Jan  4 15:18:13 2008
# Author: Jamie Strandboge <jamie@ubuntu.com>

#include <tunables/global>

/usr/sbin/slapd {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  #include <abstractions/ssl_certs>
  /etc/ssl/private/ r,
  /etc/ssl/private/* r,

  /etc/sasldb2 r,

  capability dac_override,
  capability net_bind_service,
  capability setgid,
  capability setuid,

  /etc/gai.conf r,
  /etc/hosts.allow r,
  /etc/hosts.deny r,
  /etc/ldap/ldap.conf r,
  /etc/ldap/schema/* r,
  /etc/ldap/slapd.conf r,

  # the databases and logs
  /var/lib/ldap/ r,
  /var/lib/ldap/* rw,
  /ldap_data/ r,
  /ldap_data/* rw,
  /ldaphome/ r,
  /ldaphome/* rw,

  # lock file
  /var/lib/ldap/alock kw,
  /ldap_data/alock kw,
  /ldaphome/alock kw,

  # pid files and sockets
  /var/run/slapd/* w,

  /usr/lib/ldap/ r,
  /usr/lib/ldap/* mr,

  /usr/sbin/slapd mr,
}
<<++++++++++++++++++++++++++END new /etc/apparmor.d/usr.sbin.slapd+++++++++++++++++++++++++++++++++++>>


type in terminal
slappasswd (enterpassword 12345) output: {SSHA}vIcj3rnKjEV4DL7Nlwdrix6Knrc3pgwF
edit slapd.conf
rootdn cn=admin,dc=example,dc=local
rootpw {SSHA}vIcj3rnKjEV4DL7Nlwdrix6Knrc3pgwF

<<+++++++++++++++++++++++++++++++++++START secret sid++++++++++++++++++++++++++++>>
SID for domain DC01-UBUNTU is: S-1-5-21-2412740001-785497693-1967185243
<<+++++++++++++++++++++++++++++++++++END secred sid++++++++++++++++++++++++++++>>

Your php memory limit is low - currently 16M
/etc/php5/apache2/php.ini
memory_limit = 50M


ubuntu clients (.local DN does not resolve because of avahi)
either purge avahi-daemon, avahi-autoipd, and libnss-mdns
or edit edit /etc/nsswitch.conf
from this:
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
to this:
hosts: files dns mdns4
or this:
hosts: files dns mdns4_minimal [NOTFOUND=return] mdns4

[ignore]
ubuntu client /etc/ldap.conf
uri ldap://dc01-ubuntu.example.local/ should be
uri ldapi://dc01-ubuntu.example.local/
[/ignore]

solution one:
add the following line below "nss_shadow=shadow: compat ldap" in /etc/auth-client-config/profile.d/open_ldap
Quote:
nss_netgroup=netgroup: compat ldap 

[ignore]
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
[/ignore]

on hardy dns ip reset at reboot:
Remove the comment (#) and change it to:
Code:

prepend domain-name-servers 4.2.2.1;

4. Next, look for the domain-name-servers, and remove it:

Code:

prepend domain-name-servers 4.2.2.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;

```

As for the new LTS (lucid) which will be released end april 2010, some things could brake, as some changes are made for the new LTS concerning LDAP.
This feature is very important to get proper support (this means proper documentation). 
So please **vote** for this ubuntu idea:
[http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)
as we really need up-to-date documentation on roaming profile stuff and the likes for the latest LTS release.

---

