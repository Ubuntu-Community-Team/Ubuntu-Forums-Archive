---
title: "Hoary and postgresql"
date: 2007-06-15
forum: Ubuntu Backports
---

### Post by theQmaster on 2007-06-15
I want to install postgresql 8.2.3 on my current 5.04 Ubuntu server. Does postgresql is part of the hoary's backports ? I know, people suggested me to move to latest version but this is a production box and I can't shut it down... 

Thanks for reading and look forward for a word or two.
Q

:popcorn:

---

### Post by theQmaster on 2007-06-19
I migrated to 6.10 and postgresql is part of the distro. Upgrade took me 2 days. one at the time, the reason took me that much as that I didn't have a monitor and tried to do it all via putty and VNC client - the last part burned me some hours! 

Now all's good! Contemplating to move to 7.04 but I'll wait till 7.10 comes up and do two in the same day.

Thanks for reading!
Q

---

### Post by angryfirelord on 2007-07-10
There's no backport for the whole postgresql package. The version that Hoary ships is 7.4.7, so if you want to upgrade, you'll have to alien the rpms on their site, compile your own, or try to use Feisty's debs, all of which could easily fail. 

I recommend upgrading to Dapper, as that has support until '09 for desktop and '11 for servers or if you need never packages, upgrade to feisty. I recommend doing a clean install because Ubuntu for some reason is bad at dist-upgrades. Even if that means you have to get up at 3AM on a Sunday morning to do it. ;)

---

