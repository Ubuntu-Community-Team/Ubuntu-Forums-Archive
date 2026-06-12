---
title: "Ubuntu 10.04.4 LTS upgrade PHP"
date: 2012-11-09
forum: Server Platforms
---

### Post by Spankmaster79 on 2012-11-09
Hi,

sorry if this question is obvious, but I just couldn't find the specific documentation.

I'm a developer and have to depend on sysadmins to upgrade our server systems. I wanted an upgrade of PHP to the next stable supported version 5.3.x to run ZF2 which requires 5.3.3 at least.

Our Sysadmins told me that Ubuntu 10.04 LTS comes bundles with 5.3.2 and they're not willing to upgrade PHP because of security reasons with other running PHP applications. And that it's not recommended to touch the PHP version.

Is this really true?

The System runs Ubuntu 10.04.4 with PHP Version 5.3.2-1ubuntu4.18.

And I thought you would have the possibility of upgrade software...

Regards

---

### Post by CharlesA on 2012-11-09
You'd have to either install php from source or use backport (I think?), but it is generally a good idea to not mess with the default configuration unless you are willing to deal with breakage and doing updates yourself as Ubuntu won't update a version of php that has been compiled and installed manually.

---

### Post by snowpine on 2012-11-09
Ubuntu does not push major PHP updates on their users, as that would break people's websites and apps.

Here is a great article on the topic, written for Red Hat but the same theory applies to Ubuntu:

[https://access.redhat.com/security/updates/backporting/?sc_cid=3093](https://access.redhat.com/security/updates/backporting/?sc_cid=3093)

10.04 implies it was released April 2010 and therefore uses older software. The standard solution to your situation would be to use Ubuntu 12.04 (the current Long Term Support release with support through April 2017 and PHP 5.3.10) or any number of other current distro releases if you are avoiding Ubuntu 12.04 for some reason.

---

### Post by CharlesA on 2012-11-09
> **snowpine said:**
> 
10.04 implies it was released April 2010 and therefore uses older software. The standard solution to your situation would be to use Ubuntu 12.04 (the current Long Term Support release with support through April 2017 and PHP 5.3.10) or any number of other current distro releases if you are avoiding Ubuntu 12.04 for some reason.

+1. Altho, you also need to weigh the possibility of the upgrade breaking things too. ;)

Good link as well.

---

### Post by stmiller on 2012-11-10
Upgrade to 12.04... 

Cheers,

---

### Post by Spankmaster79 on 2012-11-13
> Ubuntu does not push major PHP updates on their users, as that would break people's websites and apps.

For me an update from 5.3.2 to 5.3.14 wouldn't be a major update. Just a minor. 

So there sadly is no other way then compiling... or upgrading to 12.04.

Ok, thought this would be a minor problem. But seems we have to invest in 12.04 then.... :(

---

### Post by snowpine on 2012-11-13
> **Spankmaster79 said:**
> So there sadly is no other way then compiling... or upgrading to 12.04.


If you owned a 2010 Ford truck but really wanted the updated engine from a 2012 Ford truck, your choices would be to after-market install the part yourself (possibly voiding your warrantee) or to trade in your vehicle for the newer model. Ubuntu is a consumer product and no different. Fortunately because Ubuntu is "open source" software, you have **absoulte freedom and control** to install whatever version of PHP you desire, because its source code is readily available. I don't know why you say this happy state of affairs is "sad." ;)

---

### Post by Spankmaster79 on 2012-11-13
> If you owned a 2010 Ford truck but really wanted the updated engine from a 2012 Ford truck, your choices would be to after-market install the part yourself (possibly voiding your warrantee) or to trade in your vehicle for the newer model.  :P:P great comparison :)

> you have absoulte freedom and control to install whatever version of PHP you desire, because its source code is readily available. I don't know why you say this happy state of affairs is "sad."

Sad because "I" could and would compile and upgrade. But our administration would only do it if they leave the servers in my responsibility then. And this kind of destroys our structure that administration keeps control over servers. 

I think I'll have to talk to them as soon as I really need 5.3.x. The next big ZF2 project will bring updates to 12.04 then I guess.:P

---

### Post by snowpine on 2012-11-13
Ah yes, got to keep the bosses happy. Good luck! :)

---

