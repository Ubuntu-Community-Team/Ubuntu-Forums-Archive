---
title: "RHN now GPL.  Will Landscape follow?"
date: 2008-06-20
forum: The Cafe
---

### Post by meeas on 2008-06-20
So now that RedHat has realased RHN to the community under GPLv2, how long do you think it will take Canonical to do the same with Landscape?  And what can we do to help encourage them?

---

### Post by motin on 2009-02-23
Probably not in a while.

> WorksWithU: Is Landscape an open source product?

Drachnik: The Client for Landscape is open source and available on Launchpad under a GPL license. However,  Landscape is a paid for service from Canonical and the code is proprietary.  You might be asking this because Red Hat has recently open sourced their RH Network software as SpaceWalk. Since Red Hat follows  “procurement” model, you cannot get RH packages or updates without buying a subscription. So RH can provide their management code for free, because they charge customers for updates. Conversely, customers get very little value from Spacewalk unless they already have a subscription to RH.

Ubuntu follows an “acquisition” open source model in that Ubuntu AND updates are free. So we charge for a service to manage packages (essentially automating many of the tasks that sys admins do manually)  and provide monitoring for systems.  Anyone can get Ubuntu updates for free - this is central to our values - but we do ask them to pay for value added services like package management and monitoring, just like we charge for support and training.

From: [http://www.workswithu.com/2009/02/19/canonicals-saas-landscape-upgrade-managing-ubuntu-from-afar/](http://www.workswithu.com/2009/02/19/canonicals-saas-landscape-upgrade-managing-ubuntu-from-afar/)

---

### Post by meeas on 2009-02-23
I agree, this should be great for Ubuntu, and hopefully open some previously closed doors.  However their short-sightedness is disheartening.  

"Conversely, customers get very little value from Spacewalk unless they already have a subscription to RH."

Guess the didn't think about:
 - increased security from not having to open up firewall holes to the Internet
 - decreased bandwidth since all of your servers aren't pulling updates across the ISP link
 - all the people using Fedora, CentOS, and most other RPM based distros that RedHat doesn't support

I think Ubuntu's Landscape service is great, but I would like to have the option to run that service in-house, preferable in an open-source manner like the rest of the distro.  They can still provide this as a SaaS add-on for customers, especially the new cloud computing modules.  I'm a firm believer that the availability of Landscape is going to draw the same number of paying customers whether its open source or proprietary, so why not provide a benefit to the MUCH MUCH larger community as a whole by open sourcing Landscape?

---

### Post by sej7278 on 2009-02-23
the RHN client is pretty much useless without a subscription, so who cares if they opensourced it?

standard old YUM as used on CentOS makes a better alternative to RHN anyway.

---

### Post by meeas on 2009-02-23
> **sej7278 said:**
> the RHN client is pretty much useless without a subscription, so who cares if they opensourced it?

standard old YUM as used on CentOS makes a better alternative to RHN anyway.

sej7278, RedHat opened up the server-side code for RHN last year.  That is what matters.  While YUM is great for individuals and companies is small deployments, it isn't practicle for large deployments.  The open source RHN is now called Spacewalk, and can be installed in your own network to manage hundreds of servers.  It provides a single location to go and see the patch level of every machine and their hardware profile.  It also allows you to push patches to any number of servers at the same time.  I've ran local repositories, and that is nothing compared to the functionality that RHN/Spacewalk/Landscape provide.

sej7278, your argument appears to be the same argument Ubuntu is using.  Ubuntu provides users with APT updates and that is all they need.  But there are many of us that are running larger deployement who would like to use Landscape but cannot or don't want to pay for support.  I think its same to assume that the majority of the people who would use an open source version of Landscape are the same people who would never purchase support.  Just like the majority of Ubuntu users never purchase support.  Many of us use open source so we CAN support it ourselves and don't have to deal with contracts.

---

