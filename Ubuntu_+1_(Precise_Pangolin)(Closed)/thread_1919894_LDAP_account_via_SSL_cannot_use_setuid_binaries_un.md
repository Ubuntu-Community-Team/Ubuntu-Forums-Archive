---
title: "LDAP account via SSL cannot use setuid binaries until gnutls26 is rebuilt with nettle"
date: 2012-02-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nutznboltz on 2012-02-03
If your account is an LDAP one and your LDAP client connects to its LDAP server via SSL then running setuid programs from your account fail since libgcrypt11 is horribly broken and upstream GnuTLS no longer recommends using it as the backend crypto library:
[http://lists.debian.org/debian-legal/2011/02/msg00006.html](http://lists.debian.org/debian-legal/2011/02/msg00006.html)

In the past it was possible to work around this by using nscd but that work around no longer has any effect.

When I rebuild gnutls26 with nettle I am able to use setuid binaries from my LDAP account which connects via SSL to its LDAP server.

Reproducing:

1. Install an OpenLDAP server that speaks LDAP over SSL, see
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
for details.

2. Install Ubuntu 12.04 and configure it to be an LDAP client that connects via to its LDAP server via SSL.

3. Log into the Ubuntu 12.04 created in step using an LDAP account not an account in /etc/passwd.

4. Attempt to use sudo. You will see unexpected results:

nutz@dubnium:~$ sudo id
[sudo] password for nutz:
sudo: setresuid(ROOT_UID, ROOT_UID, ROOT_UID): Operation not permitted
sudo: unable to open /var/lib/sudo/nutz/1: Operation not permitted
sudo: unable to set gid to runas gid 0: Operation not permitted
sudo: unable to execute /usr/bin/id: Operation not permitted
nutz@dubnium:~$

5. Apply patched version of gnutls26, see attached branch.

(see this PPA: [https://launchpad.net/~nutznboltz/+archive/gnutls26-with-nettle](https://launchpad.net/~nutznboltz/+archive/gnutls26-with-nettle) )

6. Attempt to use sudo. You will see expected results:

nutz@dubnium:~$ sudo id
[sudo] password for nutz:
uid=0(root) gid=0(root) groups=0(root)

---

### Post by nutznboltz on 2012-02-10
Who is the maintainer of gnutls?

---

### Post by cariboo on 2012-02-10
Have you looked at /usr/share/doc/gnutls-doc/AUTHORS.gz?

---

### Post by Ibidem on 2012-02-11
And the question is... 

Where is the bug report?

If you don't report the bug, how will it ever get fixed?
Standard practice is ask on the forums if you aren't sure that it's a bug; if there is a bug, post a link to your launchpad bug report.

---

### Post by dino99 on 2012-02-11
all you needs to know:  [https://launchpad.net/ubuntu/+source/gnutls26](https://launchpad.net/ubuntu/+source/gnutls26)

and the requested contacts :) what else ?

---

