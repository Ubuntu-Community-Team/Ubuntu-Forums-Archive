---
title: "Integrating LDAP and Active Directory"
date: 2008-04-29
forum: Server Platforms
---

### Post by xyko on 2008-04-29
Hi All,
as the new version 8.04 has native integration with Microsoft AD and has LDAP and Kerberos support I would like to know if it's possible to use Ubuntu server to authenticate unix and linux users from a lot of servers, using users and groups defined in AD. My goal is to have a single point of administration of users.
All help is welcome.
Thanks in advance.

---

### Post by lazyart on 2008-04-29
Short answer, yes.
Long answer, [http://www.ubuntu.com/products/whatisubuntu/serveredition/features/integration](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/integration)

---

### Post by xyko on 2008-04-30
Thanks for your reply Lazyart.
Regards.

---

### Post by MaindotC on 2008-10-15
It's good to know Server edition can do this.  Does anyone have a link for getting this working?  I read the community docs for ActiveDirectoryHowTo and Authentication & Integration but it proves it works by showing successful ldap queries from the command line.  I'd like some sort of help in seeing the Ubuntu machines showing up in the gpedit snap-in or explaining how the Ubuntu machine logs into the AD Domain.  THanks!

---

### Post by lazyart on 2008-10-15
Check out likewise.  It's in the repos as of Hardy.  [www.likewisesoftware.com](www.likewisesoftware.com) can give you some more info.

---

### Post by MaindotC on 2008-10-15
I'm having a very interesting conversation w/ a guy in #openldap who claims integration is impossible - there can only be one authentication server and it has to be either AD or LDAP.

---

