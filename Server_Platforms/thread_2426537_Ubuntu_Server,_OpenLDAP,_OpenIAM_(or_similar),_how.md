---
title: "Ubuntu Server, OpenLDAP, OpenIAM (or similar), how do users authenticate?"
date: 2019-09-10
forum: Server Platforms
---

### Post by seanhaynes1 on 2019-09-10
Afternoon, I'm trying to get my brain around a problem and looking for an Open Source solution;

The problem:

In our business we have a Windows AD 2019 network which works fine for domain users.

We do however have a need to be able to authenticate users who are not members of the domain, their job is transient and temporary by nature but we still need to be able to authenticate them and the hand held devices they use in their role.

So I have been looking at an OpenLDAP solution, fronted by an identity manager solution. The LDAP db will be populated from a backend iseries - my question is the how do users authenticate against the OpenLDAP server? The devices are standalone and the users essentially stand alone.... how does this work in plain and simple english?

Many thanks

---

### Post by TheFu on 2019-09-10
**FreeIPA** replaces AD or you any keep AD and try to get the Samba/AD solution working.  [https://help.ubuntu.com/lts/serverguide/sssd-ad.html](https://help.ubuntu.com/lts/serverguide/sssd-ad.html)

LDAP authentication uses PAM. Took me a few days to figure it out about a decade ago, but it wasn't THAT hard.  I used a Zimbra LDAP directory as the main store for userids with POSIX schema extensions. During a Zimbra upgrade, I had to remove all those extra schemas and didn't bother putting them back.

If I were starting fresh today, I'd install a CentOS 7 or 8 VM and load FreeIPA into it to serve as the identify management for the network.  It took about a decade for FreeIPA server to be ported to debian/Ubuntu, so I'm not very confident in that solution.  Whereas the CentOS version is known to be working longer than a decade by some of my friends.

There is no "plain and simple english (sic)" of which I'm aware for any of this.

---

