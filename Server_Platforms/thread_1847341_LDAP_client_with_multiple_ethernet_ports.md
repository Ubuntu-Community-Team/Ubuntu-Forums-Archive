---
title: "LDAP client with multiple ethernet ports"
date: 2011-09-20
forum: Server Platforms
---

### Post by digitalramble on 2011-09-20
I have (several actually) ubuntu server machines that are querying a "master" LDAP server for login and autofs mounting.  This setup works very well on the servers with single IP addresses.  However I have recently tracked down an annoying "bug" that turned out to be related to the servers with multiple ethernet ports that are using different IP addresses on the extra ports.  

What seems to happen is that a port is chosen at random to make the LDAP request for authentication meaning that we had failures when using IP addresses that the LDAP server machine did not have in its iptables (and of course did not export from /etc/exports since the relevant IP addresses weren't listed).

Now, the immediate workaround is, of course, to add the extra IP addresses to the iptables and to the /etc/exports of the LDAP server.  But it got me wondering if there was a way to configure an LDAP client to use only a particular IP address when making an LDAP query.  I didn't find any documentation on this through relatively casual perusal of the man pages or on googling around.  Does anyone know if it's possible to restrict LDAP clients in this way?  Since we might do something similar with yet another set of IP addresses, it would be really nice to nip that in the bud and not be forever increasing iptables and exports entries to get around that...

Thanks,
--Cindy

---

