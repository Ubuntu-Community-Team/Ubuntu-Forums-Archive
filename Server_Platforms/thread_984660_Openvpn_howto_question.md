---
title: "Openvpn howto question"
date: 2008-11-16
forum: Server Platforms
---

### Post by Shwick2 on 2008-11-16
I'm going through the openvpn howto, section "Configuring client-specific rules and access policies", [http://openvpn.net/index.php/documentation/howto.html#policy](http://openvpn.net/index.php/documentation/howto.html#policy).

I understand how the network is segregated, different subnets for employees, sys admins and contractors.

I don't understand how openvpn identifies a user as either an employee, sys admin or contractor.

Is that what the next section, "Using alternative authentication methods" deals with?  Does it involve using the openvpn-auth-pam plugin?

I don't see where else openvpn could recognize a user, other than if the client built it into their certificate.

For example, is this how it works:

 You login with user sysadmin1 / some password via the openvpn-auth-pam plugin, openvpn recognizes the sysadmin1 user and invokes "ifconfig-push 10.8.1.1 10.8.1.2".

---

