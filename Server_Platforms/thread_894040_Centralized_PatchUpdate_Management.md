---
title: "Centralized Patch/Update Management"
date: 2008-08-18
forum: Server Platforms
---

### Post by softwsolu1 on 2008-08-18
I operate a medium-sized server farm (160 servers, rapidly on its way to 200), mostly Windows, and I am converting as many as possible to Linux.  I'd like very much to use Ubuntu Server as my platform of choice but I'm running into the following problem --

Our organization operates based on homegrown software and as such we require strict change management and QA on all patches before we can apply into production.  I have built development and QA environments that fully mirror, in both hw and sw configurations, the production environment and have a solid procedure under Windows for approving patches/Windows Updates to development servers, then once these have passed regression testing rolling them to QA and finally production.

The sole obstacle left for me in moving around 30-40% of these boxes to Ubuntu is this type of controlled patch management and I'm fairly certain that, as my searches have not turned up much, I'm thinking about it the wrong way.

The problem I have is that apt-get or aptitude will always grab the latest version of software or any dependencies when it's run.  In other words, if I run aptitude update/upgrade on a server in QA, then go through testing for two weeks and run it in prod, the set of packages I receive in prod will likely be newer than those I grabbed in QA.

I have a local apt mirror and I think what I need to be able to do is grab point in time snapshots of this mirror -- in other words run aptitude update and grab the indexes as they would have been, say on 8/01.  The software would have to stay in the mirrored repository as well.  I would need to keep several mirrors since we have multiple server types which go through dev/QA/production cycles asynchronously.

Is there a different way people are doing this?  Are you just running aptitude update on a dev-type server, then capturing the updated debs and deploying these directly?  This seems clunky and overly-manual.

How are folks handling this type of patch/update management under Ubuntu?  I see Canonical's Landscape, but is this the only way people are doing centralized patch mgmt?

Thanks in advance for any help,

-Eric

---

### Post by HalPomeranz on 2008-08-19
> **softwsolu1 said:**
> 
I have a local apt mirror and I think what I need to be able to do is grab point in time snapshots of this mirror -- in other words run aptitude update and grab the indexes as they would have been, say on 8/01.  The software would have to stay in the mirrored repository as well.  I would need to keep several mirrors since we have multiple server types which go through dev/QA/production cycles asynchronously.


This is certainly one approach that sites are using.  

Another approach is to use configuration management software like Cfengine or Puppet to maintain a consistent software image across your various classes of machines.  The advantage to something like Cfengine or Puppet is that it can not only maintain software revision levels, but also allow you to maintain consistent configuration files, OS settings, etc.  The downside is that there's a pretty steep learning curve for these systems.

---

### Post by softwsolu1 on 2008-08-19
Agreed on cfengine/puppet.

Thanks for your feedback.

---

