---
title: "LDAP, Samba, and SSL"
date: 2005-07-06
forum: Server Platforms
---

### Post by heisters on 2005-07-06
Hello.

I'm having trouble connecting to a samba server that uses LDAP for authentication. I got it working fine without SSL, but as soon as I change these lines in smb.conf, logging in times out.

```

   passdb backend = ldapsam:ldaps://ldap.marlboro.edu
   ldap ssl = yes

```

Trying this with ldapsam:ldap://ldap.marlboro.edu and start_tls did not change the situation. The samba log reveals the timeout:

```

[2005/07/06 10:48:24, 1] lib/smbldap.c:another_ldap_try(990)
  Connection to LDAP server failed for the 10 try!
[2005/07/06 10:48:25, 1] lib/smbldap.c:another_ldap_try(990)
  Connection to LDAP server failed for the 11 try!
[2005/07/06 10:48:26, 1] lib/smbldap.c:another_ldap_try(990)
  Connection to LDAP server failed for the 12 try!
[2005/07/06 10:48:27, 1] lib/smbldap.c:another_ldap_try(990)
  Connection to LDAP server failed for the 13 try!
[2005/07/06 10:48:29, 0] lib/smbldap.c:smbldap_search_suffix(1155)
  smbldap_search_suffix: Problem during the LDAP search: (unknown) (Timed out)

```

So I was wondering if SSL is even compiled in to libldap in Ubuntu:

```

# ldd /usr/lib/libldap.so | grep ssl
# ldd /usr/sbin/smbd | grep ssl

```

Perhaps not, because on another server, where this works, I get this:

```

# ldd /usr/lib/libldap.so | grep ssl
        libssl.so.0.9.6 => /usr/lib/libssl.so.0.9.6 (0x40069000)
# ldd /usr/local/samba/sbin/smbd | grep ssl
        libssl.so.0.9.6 => /usr/lib/libssl.so.0.9.6 (0x40066000)

```

Okay, so it seems SSL is not compiled in to Ubuntu Hoary libldap by default. This seems strange to me. So I tried installing openssl and libssl, but that didn't change anything. Obviously I could compile from source, but I feel like that would complicate long term maitenance of the server, and I would like to avoid doing that. Since it seems strange to me that Ubuntu would not have SSL support for Samba/LDAP, am I missing something? Is there a package I can install to enable SSL? Is there a configuration option somewhere? Or if you want SSL support do you really need to compile from scratch?

Thanks for your advice.

---

### Post by LordHunter317 on 2005-07-06
I believe the issue here really stems from Debian's rather assine handling of OpenSSL using applications, including OpenLDAP.  libldap3 in Debian is several revisions behind the offical one due to this, and so unless Ubuntu has updated the package (which it is apparent they have not), it's out of date and missing SSL support.

Anyway, your only recourses are to rebuild libldap with OpenSSL support, or convince the Ubuntu developers to include/backport a newer version with SSL support.  And unless you're hellbent on using the provided versions, I'd upgrade too.  There are apparently some bugs in the Debian version that make it integrating with Active Directory less than functional.

---

### Post by heisters on 2005-07-07
I would think using SSL with LDAP would be, well, just a wee little bit important. Do you or anyone else have any idea why the Debian packages are so far behind? What do most people do when they need LDAP and SSL, or does everyone just compile? It's just that it seems like this specific issue wouldn't be so rare as to be overlooked by the package maintainers.

Thanks for the reply. I'll compile from the newest version in that case.

---

### Post by LordHunter317 on 2005-07-07
[QUOTE=heisters]I Do you or anyone else have any idea why the Debian packages are so far behind?[/quote]Because they can't use GNU TLS, just OpenSSL.  And everything using OpenSSL is currently in a state of great flux, because there's a push to remove it from Debian. :roll:  

There may be some other OpenLDAP specific issues I'm unaware of it.  But the core issue is related to OpenSSL, not OpenLDAP AFAIK.

---

### Post by heisters on 2005-07-11
Hmm. A little more research has shown that while Ubuntu Hoary only has [libldap](http://packages.ubuntu.com/hoary/libs/libldap2)  2.1.30 without SSL, Debian testing has [libldap](http://packages.debian.org/testing/libs/libldap-2.2-7) 2.2-7, which is the current stable revision, and includes SSL support.

I started compiling the current version of OpenLDAP but started running into dependency issues, which were exacerbated by the fact that the Ubuntu packages of the dependencies (libdb3) are not compatible with the current OpenLDAP revision. While this could of course be worked around, the increase in maintenance difficulty makes me want to look some more for a better way to do this.

I suppose trying to install the debian libldap would cause all kind of dependency conflagrations, and be more of a headache. Any thoughts?

----

P.S. resolved dependency issues easily enough. Still, odd that Debian has SSL support, but Ubuntu doesn't...

---

### Post by jts on 2005-08-01
Welcome to my world of pain ([http://ubuntuforums.org/showthread.php?t=51685)](http://ubuntuforums.org/showthread.php?t=51685)).

I now have chills, when I hear the words OpenLDAP, SASL2 and compiling in Ubuntu.

---

