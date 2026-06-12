---
title: "BIND9 and chroot - pros and cons??"
date: 2013-01-21
forum: Server Platforms
---

### Post by gregg_hughes on 2013-01-21
Good afternoon, all!

I'm starting a project to move from RHEL to Ubuntu server.  I'll be going with 10.04 LTS because the servers will be hosted on VMware 4.1 and it's a little behind, too.

When building new DNS BIND servers, what are some pros and cons to jailing named?  The current servers are partially jailed, but I haven't seen many Ubuntu BIND servers running jailed.  AppArmor seems to be the current solution of choice.

I'm throwing the question out for comments.  BIND in chroot or not?

Thanks to all!

Gregg

---

### Post by SeijiSensei on 2013-01-21
First, let me suggest that if the rationale for leaving RedHat is avoid paying licensing fees, you'll find it a lot easier to move to CentOS than to Ubuntu.

I've been running CentOS servers for years now with named chrooted as it is done in the Redhat world.  The upside is obviously greater security since an exploit cannot escape the chroot jail and compromise the actual system.  The downside is the need to copy all the required files into the jail.  Examine the contents of /var/named/chroot on the RH system to see what files must be replicated.  Don't worry about proc; the system will handle that for you.  You'll need copies of the files in etc, dev, and var.  Find their equivalents on the Ubuntu machine and copy them to the chroot.

Really, though, all this would be much easier by just installing CentOS 6 where it's all done for you.  Another option is Scientific Linux, another free RedHat clone with good support.

---

### Post by gregg_hughes on 2013-01-23
Thanks, SeijiSensei!  

We considered CentOS, but the dev team is sticking to its guns over Debian derivative.  I've run CentOS and Ubuntu in a couple of different scenarios - it's an either/or choice for me.  The dev guys have already started porting their apps over, so it's pretty much a done deal.

I am, however, still interested in whether running chroot is really necessary in the Ubuntu environment.  It seems that getting updates to run properly in a jailed environment is the primary hurdle here.

Thanks!

---

### Post by hawkmage on 2013-01-23
Why is the dev team dictating what you run DNS on?  Are they going to be doing development on the DNS server?  If you can you should separate your infrastructure services from your applications.  

Also I am curious as to why your development team is rejecting CentOS?  

If you truly have to move to a Debian based using AppArmor is a good solution if properly implemented can provide as much security as chroot.

---

### Post by SeijiSensei on 2013-01-23
> **hawkmage said:**
> Also I am curious as to why your development team is rejecting CentOS?

Sounds like a case of people thinking they know more than they actually do.  Last I looked RedHat and its derivatives continue to dominate in the server room.

---

### Post by hawkmage on 2013-01-25
> **SeijiSensei said:**
> Sounds like a case of people thinking they know more than they actually do.  Last I looked RedHat and its derivatives continue to dominate in the server room.

That is why I asked the question.  I work designing and implementing enterprise platforms for developed and of the shelf applications.  All too often there are "requirement" that are driven by misconceptions or personal preferences.  This is one of my pet peeves.

---

