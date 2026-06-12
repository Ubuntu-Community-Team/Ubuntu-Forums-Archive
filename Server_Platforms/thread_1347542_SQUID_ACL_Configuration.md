---
title: "SQUID ACL Configuration"
date: 2009-12-06
forum: Server Platforms
---

### Post by k0sh on 2009-12-06
Hi,

I'm new to SQUID and I'm needing some help to build the ACLs to my squid server.

I want to the limit the access to a very specific group of users:

- Local users that obtained their IP address from the local DHCP server and/or are registered in the local DNS server.

How can the squid server interact with the DHCP and DNS servers so it can obtain the necessary information about the users?

Do I need to write an external ACL?

Thank you.

---

### Post by Lars Noodén on 2009-12-07
One guess is that there might be a way to do it using dhcp-eval to pass the info to squid somehow.  See "execute" in the section on Action Expressions:
  [http://linux.die.net/man/5/dhcp-eval](http://linux.die.net/man/5/dhcp-eval)

If both servers are on the same machine, it is easier.

---

