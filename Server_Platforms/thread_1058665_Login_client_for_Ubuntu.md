---
title: "Login client for Ubuntu"
date: 2009-02-03
forum: Server Platforms
---

### Post by alltaf on 2009-02-03
Hi
I have read a lot on the internet, but can't find anything to get me in the right direction.

How do I log into a Ubuntu server with a Ubuntu client, in the same manner I would log in a Windows client into a Windows server. I have a few Ubuntu clients, and would like to be able to log in from any of them, wihout creating accounts on them just on the server.

A gdm login to the server, and get everything fixed, mounts, printer connection.

I have looked for a few weeks, and I would believe that it should be easy, but I have had no luck. I have had a look at opendirectory, but it seems a little bit overkill for this.

Please just point me in the right direction and I should be able to manage the rest.


regards
alltaf

---

### Post by bluefrog on 2009-02-03
ldap directory. nfs mount for /home

the easiest way for you, edubuntu I presume.

---

### Post by alltaf on 2009-02-14
Thank You bluefrog!

I searched for openldap and samba, found
[http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)
It worked fine after a few tries. I can use the resources from an XP client, have'nt tried from Linux yet. I can attach to the server after logging in to the XP client.

What I would like to do is log in to a client, using the LDAP for authentication. I have searched for a guide on the matter.

 I have seen that more people are looking for an Intrepid Ibex guide+openLDAP+Samba.

Please just point me in a direction, I´ll find my way.

regards alltaf

---

