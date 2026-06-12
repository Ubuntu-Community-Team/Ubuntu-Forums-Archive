---
title: "Error trying to install slapd"
date: 2011-02-04
forum: Server Platforms
---

### Post by Bill2011 on 2011-02-04
Hi, new guy here! So please, bear with me if I make some mistakes.

I'm new to LDAP, but I'm harvesting all the internet lore in search of information about it. So far, so good when getting into the idea. But when I get to install and configure it... well...that's usually where I get stuck.

So... here's my problem:

I already installed (through make|make install) Berkeley DB from Oracle site. Downloaded and installed (same) succesfully OpenLDAP from the official site as well. Then I tried to find any ways of starting a database, but found out that I had to have slapd running as well (I figured out it would be already installed by the OpenLDAP, but it didn't actually. No clue if was my mistake either).

I should already say it, but I'm running on an Ubuntu Jaunty Server on a VM in a remote Server Cluster and I have some other applications HIGHLY CRITICAL running there, so if I screwed the system... I think you got the idea...

Searching through the packages by aptitude I found out I could easily have done it...oh, well... then I tried to install slapd and...... got here asking if any of you could give me a hand on this error I get: 

> Setting up slapd (2.4.15-1ubuntu3.1) ...
  Creating initial slapd configuration... Loading the initial configuration from the ldif file (/tmp/slapd_init.ldif.jqdQDmtYci) failed with the following
error while running slapadd:
    str2entry: invalid value for attributeType objectClass #0 (syntax 1.3.6.1.4.1.1466.115.121.1.38)
    slapadd: could not parse entry (line=16)
dpkg: error processing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up slapd (2.4.15-1ubuntu3.1) ...
  Creating initial slapd configuration... Loading the initial configuration from the ldif file (/tmp/slapd_init.ldif.wFDRkBhTdm) failed with the following
error while running slapadd:
    str2entry: invalid value for attributeType objectClass #0 (syntax 1.3.6.1.4.1.1466.115.121.1.38)
    slapadd: could not parse entry (line=16)
dpkg: error processing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd

I combed almost every site through google, but not a soul had the same problem I'm having. Can anyone help me in this?

Thanks for any cooperation.

---

