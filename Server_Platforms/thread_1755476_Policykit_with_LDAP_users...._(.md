---
title: "Policykit with LDAP users.... :("
date: 2011-05-11
forum: Server Platforms
---

### Post by danbishop on 2011-05-11
I've got an LDAP/Kerberos setup working perfectly... except for one thing, policy kit.

Admin users are in the LDAP group named "admin" and clients have their /etc/nsswitch.conf file configured like so:

passwd ldap files
group ldap files
shadow ldap files

Giving priority to LDAP for group information. This enables users in the admin group to use sudo with no further configuration, but when using things like the software centre, users are asked for the password for root!

Does anyone know why policykit isn't seeing that users are part of the admin group and accepting their password?

---

### Post by Brianetta on 2011-05-11
This also affects me, using LDAP alone for authentication.  The PolicyKit PAM configuration file just uses the same common files as every other configured PAM service, but PolicyKit doesn't authenticate.  I don't have a root password, so I've been working around this by using command line tools with sudo.

My nsswitch configuration is the same as danbishop's.

---

### Post by danbishop on 2011-05-11
I've had it working before, in fact it works on my setup at home... but I'm sure all I had to do there was change nsswitch.conf

I'll study my home setup in more detail later and post back if I work it out!

---

### Post by danbishop on 2011-05-12
I've looked at my home setup and it turns out I've added the LDAP user "dan" to the local admin group (gid 120).

```
sudo adduser dan admin
```

Removing dan from that group actually broke both sudo and policykit, which is odd because nsswitch.conf is still configured to use ldap first for users groups and shadow... :(

Perhaps there's a bug lurking here?

---

### Post by davefromnz on 2011-11-19
Hi, is this what you are seeing?

[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/892680](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/892680)

Cheers,
Dave

---

### Post by davefromnz on 2011-12-18
Judging by one of the responses I've had at:

[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/892680](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/892680)

this is indeed an issue. I have also observed a problem with LDAPS, which I have logged here:

[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/892480](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/892480)

My main question is how are other people working around this?

Cheers, 
Dave

---

### Post by Brianetta on 2012-01-07
> **davefromnz said:**
> My main question is how are other people working around this?
My work around is to swear vehemently, then switch to doing whatever it was on the command line, the long way.

Adding users to the local admin group works, apparently, but the whole point of LDAP in my case was not to have to distribute custom changes to passwd and group files.

---

### Post by tonymaro on 2012-04-06
The file you're looking for is:

```
/etc/polkit-1/localauthority.conf.d/51-ubuntu-admin.conf
```

Add the group name that has your administrators in it, separated by a semi-colon:

```
[Configuration]
AdminIdentities=unix-group:admin;unix-group:Domain Admins
```

I did a full post about this in my blog recently - it ticked me off because it's been a problem for me ever since Ubuntu started migrating to policykit several releases ago and doesn't seem very well documented yet:

[http://www.ossramblings.com/ubuntu-with-ldap-user-root-password-issue]("http://www.ossramblings.com/ubuntu-with-ldap-user-root-password-issue")

This is a separate issue from sudo - things like Synaptic and other GUI items in Ubuntu no longer use sudo, instead they use policykit-1.

---

### Post by Brianetta on 2012-04-12
There is a confirmed bug at play here, too:

[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/781737](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/781737)

In my case, there's nothing wrong with the stock localauthority config file, because my LDAP admin group is named "admin". Alas, there's no quick fix for me - I have to either work around the problem by using tools that don't use policykit, or patch and compile my own policykit.

---

