---
title: "do-release-upgrade question"
date: 2012-09-12
forum: Server Platforms
---

### Post by willirl on 2012-09-12
I'm pretty new to Ubuntu and I have a server running 8.0.4.  I found instructions on how to do an upgrade to 10.04 but before I do that I want to know what gets upgraded. 

Is it only the kernel that gets upgraded or do all apps etc. get upgraded as well - I'm particularly interested in PHP.

Thanks

Richard

---

### Post by westie457 on 2012-09-12
The simple answer is everything that is installed gets upgraded to the latest versions relating to the OS you are upgrading to.

Be aware that some things will be upgraded and others will be removed if they are no longer supported by Canonical. Some will be changed to a different default program.

It might be better to do a clean install especially if you have added a lot of programs and apps over the years since the original install.

Make a back up of your current /Home folder first whichever way you go. Just in case it all goes horribly wrong.

---

### Post by snowpine on 2012-09-12
You can see at-a-glance which version of the major packages correspond to each Ubuntu release here: [http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

For more details you can search for a package at: [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by willirl on 2012-09-13
Thank you.  That's some of what I was looking for. I only wanted to upgrade if the PHP was a later version.

---

