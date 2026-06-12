---
title: "Simple auth system, like AD?"
date: 2009-04-30
forum: Security
---

### Post by Kazade on 2009-04-30
Hi all,

Is there a simple way (I mean no fiddling with config files, LDAP commands etc. etc. just preferably an "apt-get install") to set up an authentication server where I can add users and tell PCs on the network to authenticate with that server?

I've looked at OpenLDAP, I've tried twice to get it working and never succeeded. The closest solution I've found is to run a Windows server and use likewise-open to authenticate with it. But now, I have to configure a small Linux only network for authentication and I can find no easy way to do it. So my requirements are:

1. A central authentication system
2. That must be easy (and quick) to set up
3. That has GUI tools for adding/removing users

I don't need integration with samba, roaming home directories or anything like that. I just need simple authentication. Does something like this exist?

---

### Post by jcostom on 2009-04-30
> **Kazade said:**
> Hi all,

Is there a simple way (I mean no fiddling with config files, LDAP commands etc. etc. just preferably an "apt-get install") to set up an authentication server where I can add users and tell PCs on the network to authenticate with that server?


Simple, like AD, eh?  That's really a bit like talking about a simple medical procedure, like brain surgery. :)

Seriously though, Jaunty includes likewise-open, which has a GUI available for it, in the repositories.  It's what you're looking for.

[http://ubuntuserver.wordpress.com/2009/03/23/likewise-open-5-in-jaunty/](http://ubuntuserver.wordpress.com/2009/03/23/likewise-open-5-in-jaunty/)

[http://packages.ubuntu.com/jaunty/likewise-open5](http://packages.ubuntu.com/jaunty/likewise-open5)

---

### Post by HermanAB on 2009-04-30
Howdy,

Yes, there is a way, but simple it ain't, though Active Directory isn't simple either. Go to the Samba web site and read the Official Howto.

---

