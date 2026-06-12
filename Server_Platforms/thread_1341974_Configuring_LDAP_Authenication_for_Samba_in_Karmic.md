---
title: "Configuring LDAP Authenication for Samba in Karmic"
date: 2009-11-30
forum: Server Platforms
---

### Post by neurostu on 2009-11-30
I'm trying to setup a NAS using 9.10. I'm planning on using SAMBA as the file server and want users to authenticate using LDAP. 

I could use the built in SAMBA authentication but we have a VPN and it would be nice to use the same authentication credentials to connect the VPN and the NAS.

I've been hitting google hard for the last 12-24 hours looking for a decent guide on how to setup a Samba server using LDAP for authentication and I can't find anything. The problem is that the LDAP packages were changed in Karmic such that they don't automatically setup a backend db. Bug reports have been filed on launchpad with regards to this.

Also it seems that a lot of configuration files have been moved in the newest version of ldap. 

The problem I'm running into is that all of the guides I can find are out of date. They assume that the backend db is setup. and they point to missing configuration files. I've found a post in this forum that explains how to get ldap up and running:
[http://ubuntuforums.org/showthread.php?t=1313472](http://ubuntuforums.org/showthread.php?t=1313472)

However I have yet to find a guide for how to configure LDAP and SAMBA for 9.10.  I'm really hitting my head against a wall here ](*,) .

Has anybody figured this out yet? Would it be worth my time to install that packages from Jaunty?  Should I just go back to using Hardy which is an LTS?

---

### Post by neurostu on 2009-11-30
All of the samba docs I've read refer to /etc/ldap/slapd.conf which doesn't exist in a standard karmic install so I tried editing /etc/defaults/slapd.conf
By setting the SLAPD_CONF parameter to: SLAPD_CONF=/etc/ldap/slapd.conf

but now when I try to restart slapd I get:
```

The pidfile for slapd is neither specified in "/etc/ldap/slapd.conf" nor
in /etc/default/slapd. Consequently, slapd will not be started.

```

---

### Post by tenmoi on 2009-11-30
> **neurostu said:**
> All of the samba docs I've read refer to /etc/ldap/slapd.conf which doesn't exist in a standard karmic install so I tried editing /etc/defaults/slapd.conf
By setting the SLAPD_CONF parameter to: SLAPD_CONF=/etc/ldap/slapd.conf

but now when I try to restart slapd I get:
```

The pidfile for slapd is neither specified in "/etc/ldap/slapd.conf" nor
in /etc/default/slapd. Consequently, slapd will not be started.

```

/etc/defaults/slapd.conf is for you to set some extra parameters and not used for config of openldap. It's /etc/ldap/slapd.conf that you are supposed to edit. However, karmic uses openldap version 3.4 (I dont remember) which replaces slapd.conf with slapd.d and to be able to config it you must read the openldap administration guide 2.4. IF you would stick to karmic then you must do some homework and readthe guide or search for a guide (i dont remember the website) that shows you how to convert the slapd.conf to the new config format.

Or you can "mv slapd.d slapd.d.orig" and create a slapd.conf file and config it the old way. Now is the good time to "edit /etc/defaults/slapd.conf by setting the SLAPD_CONF parameter to: SLAPD_CONF=/etc/ldap/slapd.conf"

I personally recommend using 389 DS, which unluckily is unusable right now on karmic so you must install it on fedora. If you go this way then there's this wonderful howto [http://forums.fedoraforum.org/showthread.php?t=183837&highlight=ldap+domain+controller](http://forums.fedoraforum.org/showthread.php?t=183837&highlight=ldap+domain+controller) (you must adapt it and it will rack your brain a little because it's a little outdated. I asked a question there but had to solve it myself.) 

Hope this'll help.

---

