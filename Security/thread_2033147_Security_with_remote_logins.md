---
title: "Security with remote logins"
date: 2012-07-25
forum: Security
---

### Post by sushy on 2012-07-25
I have a system that is divided into 2 groups of servers - Group A and Group B. My problem is I need to allow a certain set of users to login to Group A. But these same users should not be allowed to login to Group B via Group A. (Infact they should be totally unaware of existence of Group B ;)) I was just hoping to get some pointers on this. I was trying to see if LDAP could help me do this but again I am clueless on this front.

---

### Post by sushy on 2012-07-25
Anyone?????:confused:

---

### Post by needhelppeeps on 2012-07-25
Use the VPN feature of your firewall (may require licenses). Give Group A only access to the IPs of the machines for Group A, in Group B give access only to the IPs for those machines, in group C provide access to all servers in both A &  B and give that to only the people who need access to everything. Some firewalls allow per user or per group shortcuts to servers which will launch a Java application to provide connectivity. The same security should be in place on each server, in other words, only the people who need access should have the ability to login. I'm generally against the idea of allowing people have remote access to entire LAN segments for no particular reason. I would also favor two factor authentication and many "fat client" VPN solutions do seem to make it easy to require a token or preshared key.

---

