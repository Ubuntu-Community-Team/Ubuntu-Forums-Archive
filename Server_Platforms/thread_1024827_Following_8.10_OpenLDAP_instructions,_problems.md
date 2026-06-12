---
title: "Following 8.10 OpenLDAP instructions, problems"
date: 2008-12-29
forum: Server Platforms
---

### Post by poke4christ on 2008-12-29
**Main Problem:**

When I try to run:

```
sudo auth-client-config -a -p lac_ldap
```

I get the following error:

```
Error in updating the file: 'pam_account' not found
--
Errors found.  Aborting (no changes made)
```

**Situation:**

I've recently installed and begun playing with Ubuntu Server with the goal of eventually having my own home server running all sorts of things like Network Authentication, mail serving, file serving, print serving, and whatever else I may want.  Now, I'm having trouble with the OpenLDAP configuration instructions.   Specifically, the "LDAP Authentication" section.

[https://help.ubuntu.com/8.10/serverguide/C/network-authentication.html](https://help.ubuntu.com/8.10/serverguide/C/network-authentication.html)

**Other issues:**

Basically, I want network authentication, but I've had a bit of a learning curve on the LDAP stuff.  I'm not sure what in the instructions is required configuration and what is just instructions on ways to modify and search LDAP.  It seems like the only sections you need to follow for installation are "Installation" and "LDAP Authentication".  Then use the rest of the instructional for adding and removing users.  Is this correct?  Overall, the guide just seems to be problematic for someone unfamiliar with LDAP.

---

### Post by scorp123 on 2008-12-29
The instructions given here were originally written for Ubuntu 7.10 ... but they should still work for 8.04 and 8.10:
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

---

### Post by poke4christ on 2008-12-29
I've already run through much of the other tutorial.  Would you recommend I uninstall what I have installed  through apt-get and then start fresh on the tutorial?  This seems like a pretty good tutorial so far.  Thanks.

---

### Post by scorp123 on 2008-12-29
> **poke4christ said:**
> Would you recommend I uninstall what I have installed  through apt-get and then start fresh on the tutorial? Best thing to use here would be a virtualisation solution, e.g. VirtualBox. It would have the advantage that you can try all the things out and before and after each step take a "snapshot" of the virtual system. If you mess up, you simply revert your virtual machine to a previous snapshot. Like this you can gain a lot and have an excellent learning experience but you don't have to go through the frustrations of having to install everything again in case you seriously mess up. With a virtual machine and a snapshot getting a fully working system again is just one mouse click away .... I'd really recommend that.

How to get xVM VirtualBox 2.10 from Sun's repos:
[http://ubuntuforums.org/showpost.php?p=6332363&postcount=16](http://ubuntuforums.org/showpost.php?p=6332363&postcount=16)

---

### Post by poke4christ on 2008-12-30
I've went through a lot of the thread and found the explaination to this, but I can't really find a solution.

My /etc/ldap/slapd.conf was missing and through some research I found it wasn't used in the new version for configuration.  However, you could change it to point to it.  When I did this, it simply had no config file and trying to restart it just gave an error.  Even pointing it back to the default didn't work.  Do I need to rerun the configuration to cause it to build the slapd.conf?  I didn't want to try to make my own because I could screw it up and it would take a long time to figure out the ins and outs.

Also, should I even switch back to this version or should the new config method be followed?

---

### Post by poke4christ on 2008-12-31
I hate to bump this, but I'm really not sure about this part?  I'm gonna try just copying the configuration file from the guide and going through it to make sure everything is right for my computer.

---

### Post by poke4christ on 2008-12-31
well, creating my own slapd.conf didn't work :(

---

### Post by Madkinder on 2009-01-09
Take a look [here]("https://bugs.launchpad.net/ubuntu/+source/auth-client-config/+bug/295008/comments/4"). The doc's seem to be a bit outdated.
[QUOTE=John Florian]
It appears that this is now a two step process. The first step is to update NSS as Jamie showed above. The second step is to update PAM, which it looks like you can do via:
```

$ sudo auth-client-config -t nss -p lac_ldap
$ sudo pam-auth-update ldap

```
[/QUOTE]

The other issue is that the doc doesn't say anything about initialization of LDAP tree (e.g. creating of ou=Groups; ou=People, etc.). This is mentioned [here]("https://bugs.launchpad.net/ubuntu-doc/+bug/291779/") and could be done as follows: ```
$ sudo ldapinit
``` This command is to be done after setting of the /etc/ldapscripts/ldapscripts.{conf,passwd} files.

---

