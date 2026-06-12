---
title: "Samba 4 can replace 2008 AD?"
date: 2011-05-20
forum: Server Platforms
---

### Post by vtk on 2011-05-20
I've done a bit of googling but have not been able to find a definitive answer.  Can Samba4 replace the Active Directory on a Windows Server 2008 platform?  I want to bring down my DC and replace it with a Samba4 server, but the AD is at 2008 level.

---

### Post by arrrghhh on 2011-05-20
> **vtk said:**
> I've done a bit of googling but have not been able to find a definitive answer.  Can Samba4 replace the Active Directory on a Windows Server 2008 platform?  I want to bring down my DC and replace it with a Samba4 server, but the AD is at 2008 level.

Samba4 is still alpha AFAIK... I would say **no**, it cannot replace a full-blown DC yet.

Perhaps if this isn't a production environment and you're just playing around... but it sounds like it is a production environment.

I hope one day Samba4 gives AD a run for its money - but at this stage, I don't think it can completely replace AD.

Samba3 can run as a PDC or as a member, but I'm not sure how deep the services run... I'm no AD expert, sorry!

---

### Post by hawkmage on 2011-05-20
That would not be a good idea, Samba 4 is only in its Alpha release phase.  

From what the stated goals are for the Samba 4 release it sounds like it will be able to do what you want but not yet.  They do not even have an expected release date yet.

---

### Post by elico on 2011-05-21
i dont remember the goal of SAMBA to be a replacement for AD but an implementation of AD structure..
a server that compatible with AD and most of it's features but i dont think that in the current advantage of development it can compete with Microsoft team so fast.

---

