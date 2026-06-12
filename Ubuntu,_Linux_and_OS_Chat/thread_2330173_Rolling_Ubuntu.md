---
title: "Rolling Ubuntu"
date: 2016-07-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Omar_Jair on 2016-07-08
I've always wondered why does Ubuntu keep focusing on non LTS relases or so, and why Canonical has not decided to make it a rolling relase, is there that stops ubuntu from being rolling like Arch or similar?

---

### Post by grahammechanical on 2016-07-09
The main reason that Ubuntu does not follow the rolling release model is because the Ubuntu developers decided not to. A simple rolling release model would not have the stability that many users, especially business uses, need.

So, the situation is this. If you want stability install an LTS. If you want bleeding edge then install the development release. The development release gets updates daily. But I should warn you. Stability is built into the development release as well. The idea is for developers to use the development release and update their applications without having to wait for the next version of Ubuntu to be released.

There was a big discussion about this subject several years ago at a Ubuntu developer summit. Interestingly, things are done differently on Ubuntu phone. A retail Ubuntu phone is set by default to a stable update channel and updates/upgrades are pushed out every 6 - 8 weeks. But there are other channels that can be used and those channels receive daily updates.

If we every get Ubuntu desktop built on a snappy Ubuntu core, then that OS will almost have a rolling release model. Snappy Ubuntu core is designed in such a way that if an upgrade to the OS snap fails in some way the system will roll back to using the previous OS snap. The method is called Transactional Updates. Instead of the system being upgraded package by package, library by library it is only the code differences that are downloaded. 

Regards.

---

### Post by buzzingrobot on 2016-07-09
Corporations and other organizations that roll out Ubuntu on, potentially, thousands of systems want as little change as possible in those systems after they are  deployed.  For them, "stability" means, essentially, "give us security updates but don't change anything, don't give us feature updates". They're looking to install something that meets their needs for several years to come. Change costs money: Upgrades are typically tested internally, downtime may be needed to make the changes, employee retraining may be a factor, etc. 

For these customers, it is very much a "if it works, don't change anything" approach.  Rolling releases mean constant change with no real gain for them, while increasing the chances for breakage, introduction of new bugs and security risks, incompatibilities with internal software, etc.

---

### Post by mastablasta on 2016-07-09
> **buzzingrobot said:**
> Corporations and other organizations that roll out Ubuntu on, potentially, thousands of systems want as little change as possible in those systems after they are  deployed.  For them, "stability" means, essentially, "give us security updates but don't change anything, don't give us feature updates". They're looking to install something that meets their needs for several years to come. Change costs money: Upgrades are typically tested internally, downtime may be needed to make the changes, employee retraining may be a factor, etc. 

For these customers, it is very much a "if it works, don't change anything" approach.  Rolling releases mean constant change with no real gain for them, while increasing the chances for breakage, introduction of new bugs and security risks, incompatibilities with internal software, etc.

true. which makes me wonder why they are going with windows 10 as an option. as i udnerstand widnows 10 will be kind of rolling. so in a few years or so i wonder what will happen whn drivers will no longer support it or similar. or you know how Xp neede 256 MB to run then 512 MB min, then suddenly you needed 2 Gb to run the system normally. now imagine you would suddenly get an update to Vista level where 4 GB practically is required while you just change all machines to mach the 2 GB needed.

---

### Post by buzzingrobot on 2016-07-09
> **mastablasta said:**
> true. which makes me wonder why they are going with windows 10 as an option. as i udnerstand widnows 10 will be kind of rolling...

Isn't it Microsoft that's "going" with Linux?  They have a demonstrated need to keep developers on Windows.  Many of those developers sometimes need to develop on, test on, etc., a Linux, but remain primarily Windows developers in Windows shops. Micrsooft is giving them some tools in hopes that they won't wander away. It's nice Canonical did a deal to work on the translation layer, but I"m sure MS could have done it, too. The Canonical tie-in is probably Microsoft's way of buying some cred.

My own opinion about Win10's updating scheme is that it's intended to be a way for Microsoft to transition users from the current stale NT-based platform, loaded with zillions of lines of code to support ancient software, on to what will eventually turn out to be a new platform.  For obvious reasons, Microsoft can't just release a  new platform that breaks a billion Windows installs. The *control* Microsoft has over the software on Win10 systems will allow them to do that over the next several years.  And I would not be surprised to see Microsoft begin to apply different end-of-life dates to various major Win10 components. E.g.,"here's a new font rendering engine.  It's good for three years.  Then it's EOL, along with all the other rendering engines that date back to XP. You have 3 years to get ready, Mr. Developer and Ms Enterprise."

---

### Post by mastablasta on 2016-07-11
well yes they will start with shorter EOL times, but that would increase the cost for businesses until they realise they can again stay on the same thing for 8 years (or 10) if they get Red Hat.

meh... the way out is "apps" that are services and work on web anyway. which is why probably MS is so pushy about office 365.

---

