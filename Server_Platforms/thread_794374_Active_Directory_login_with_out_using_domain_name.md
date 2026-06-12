---
title: "Active Directory login with out using domain name"
date: 2008-05-14
forum: Server Platforms
---

### Post by wizardofyendor on 2008-05-14
Hello all.  A little background on what I'm doing.  I'm setting up a safesquid web proxy, with Active Directory authentication. 

I followed this guide to setup PAM and kerberos: [http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/")

Now my question is, when I login to the ubuntu box, or thru safe squid, I need to give the username as: 'DOMAIN\USER'.

Is there a way to not require the domain name on the safesquid login prompt?

---

### Post by jefframsey on 2008-05-29
Just add this line to the end of /etc/samba/lwiauthd.conf:

winbind use default domain = yes


That is all that you need to do. Save this file, restart likewise, and you'll be home free.

---

