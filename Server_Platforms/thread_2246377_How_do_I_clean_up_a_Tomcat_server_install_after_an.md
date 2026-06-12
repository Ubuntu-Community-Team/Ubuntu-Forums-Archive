---
title: "How do I clean up a Tomcat server install after an Upgrade to 14.04?"
date: 2014-09-30
forum: Server Platforms
---

### Post by MAFoElffen on 2014-09-30
Server was originally 12.04.2, It was running LAMP and Tomcat. Finally got around to upgrading the release on tht server... Now it has an error on boot saying "TomCat 6 is not installed."

Since upgrading yesterday, now I see both Tomcat 6 and 7 installed? When I list out the packages from both, the only difference I see is that package libtomcat7java is there and package libtomcat6java is not. Otherwise, both are the same.

Checking into it, I now see pieces of TomCat6 and Tomcat7. It must have upgraded along the way... but not cleanly removed the previous version(?).

So how do I remove Tomcat6 without effecting Tomcat7? Or should I copy over whatever the config files are and remove all Tomcat instances... to install fresh?

Edit-- 
Looking into it deeper this morning, neither are running right now. So the plan of action might be easier to remove both, then install Tomcat 7... What files should I keep, if any?

---

### Post by Vegan on 2014-09-30
Unfortunately I have seen this problem all too often when users do a distro update

I find it expedient to use a virtual machine and install a new version of Ubuntu fresh with each new version

then once configured I can bring it into production easily

---

### Post by MAFoElffen on 2014-09-30
You do an rsync or dd copy between? 

I have 2 other servers here running kvm. If you have tips on that... I could start doing that from now on. 

This one server, I going to retire... But my friend that is buying it wanted Tomcat and all my management utils to stay... 

Just thought I was doing him a favor by updating it. Not to be causing me more work.

---

### Post by MAFoElffen on 2014-10-03
Solved. Uninstalled... purged. Installed.

---

