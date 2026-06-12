---
title: "OpenLDAP Sudo Behaviour"
date: 2013-03-07
forum: Server Platforms
---

### Post by OmegaHarvest on 2013-03-07
Hey

This is more a question about the workings of Sudo with LDAP rather than how to get it working. So here goes!

I've setup a basic LDAP server in my test environment (minus TLS) and have created a user and a group (called ldapusers). I've added my user to the group, and then added the group to the sudoers file on my local server.

I can log in as the LDAP user fine, and when I run a sudo command I'm prompted for the credentials of the local administration account I setup when I installed Ubuntu, rather than the password of my LDAP account. Is this normal behavior for this scenario or have I missed a step?

I know you can do stuff to add sudo user accounts directly in LDAP but I read somewhere that you can't do this with TLS enabled. Is this true?

Thanks in advance!

---

