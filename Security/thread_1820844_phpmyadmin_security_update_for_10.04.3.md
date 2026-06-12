---
title: "phpmyadmin security update for 10.04.3?"
date: 2011-08-08
forum: Security
---

### Post by Chris_81 on 2011-08-08
Just got a message about critical security holes for phpmyadmin (see e.g. [http://www.h-online.com/open/news/item/phpMyAdmin-updates-close-critical-security-holes-1285281.html](http://www.h-online.com/open/news/item/phpMyAdmin-updates-close-critical-security-holes-1285281.html)) and wondering, when I'd get an update for my ubuntu server Lucid Lynx 10.04.3?

Currently installed version is 4:3.3.2-1, published on 2010-04-16.

---

### Post by bodhi.zazen on 2011-08-08
You should file a bug report on LP, against phpmyadmin, and mark as security related.

---

### Post by wacky_sung on 2011-08-08
> **bodhi.zazen said:**
> You should file a bug report on LP, against phpmyadmin, and mark as security related.
I think you got the thing wrong.What he/she requesting Ubuntu update since phpmyadmin has fixed the problems with an update. Likewise shall he/her file against Ubuntu for not keeping the file up to date?

---

### Post by bodhi.zazen on 2011-08-08
> **wacky_sung said:**
> I think you got the thing wrong.What he/she requesting Ubuntu update since phpmyadmin has fixed the problems with an update. Likewise shall he/her file against Ubuntu for not keeping the file up to date?

I think you do not understand how bug reporting (launchpad works).

This is a security bug in phpmyadmin resolved by updating the package in Ubuntu.

This is tracked via bug reports, Ubuntu uses Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/phpmyadmin](https://bugs.launchpad.net/ubuntu/+source/phpmyadmin)

If you go through the process, you will see you first provide a summary, then review current bugs to see if this is a duplicate.

You then add in a more detailed description, and there is an option to mark it as a security bug.

This will notify the phpmyadmin and the security team that the package needs to be reviewed and updated.

How else do you think one should communicate the problem ? Certainly not a thread on the forums.

Here is a link that gives you some insight into a package maintainers thought process:

[http://www.redhat.com/magazine/020jun06/features/bugzilla/](http://www.redhat.com/magazine/020jun06/features/bugzilla/)

Sure , it is for RHEL / bugzilla, but the point is the package maintainers use Launchpad.

Go ahead and try to file a bug against all of Ubuntu, it will be marked as invalid.

I suggest you take the time to learn how to file bug reports.

---

### Post by Thewhistlingwind on 2011-08-08
> **bodhi.zazen said:**
> 
Go ahead and try to file a bug against all of Ubuntu, it will be marked as invalid.


I can see it now:

"Bug scope: Ubuntu

"Bug: Ubuntu sukz!!!!!1111"

Details: I r not abl to prnt in my buntu instll, distro R teh brokenz!!!!"

@the op, yeah, file a bug report. It should be fixed soon after.

---

### Post by wacky_sung on 2011-08-08
> **bodhi.zazen said:**
> I think you do not understand how bug reporting (launchpad works).

This is a security bug in phpmyadmin resolved by updating the package in Ubuntu.

This is tracked via bug reports, Ubuntu uses Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/phpmyadmin](https://bugs.launchpad.net/ubuntu/+source/phpmyadmin)

If you go through the process, you will see you first provide a summary, then review current bugs to see if this is a duplicate.

You then add in a more detailed description, and there is an option to mark it as a security bug.

This will notify the phpmyadmin and the security team that the package needs to be reviewed and updated.

How else do you think one should communicate the problem ? Certainly not a thread on the forums.

Here is a link that gives you some insight into a package maintainers thought process:

[http://www.redhat.com/magazine/020jun06/features/bugzilla/](http://www.redhat.com/magazine/020jun06/features/bugzilla/)

Sure , it is for RHEL / bugzilla, but the point is the package maintainers use Launchpad.

Go ahead and try to file a bug against all of Ubuntu, it will be marked as invalid.

I suggest you take the time to learn how to file bug reports.
Thank for enlightening me.I do not file those bugs but keep findings bugs. The process is slow and painful but effective.

---

### Post by Chris_81 on 2011-08-10
Thank you [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") for letting me know how to file a bug / an outdated package. I am gonna do it as you suggest.

---

### Post by bodhi.zazen on 2011-08-10
> **Chris_81 said:**
> Thank you [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") for letting me know how to file a bug / an outdated package. I am gonna do it as you suggest.

You are most welcome.

Another useful link is here:

[http://www.chiark.greenend.org.uk/~sgtatham/bugs.html](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html)

Again, I understand it is frustrating to run into bugs or broken packages, but, you also need to at least understand the perspective of the developer so as to communicate effectively.

To use a car analogy, what would you do if you were a mechanic and got a bug report saying "my whole car is broken" ?

Perhaps the car is out of gas, perhaps it is an electrical problem, perhaps the owner lost the keys.

You get the idea, and that link is a must read if you would like to assists open source projects squash bugs, either as someone who reports bus or working on the so called bug squads.

The bug squads are regular users who understand how to file a bug report. They assist the developer by asking for more information and triaging bugs so developers can spend time coding.

[https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad)

[https://wiki.ubuntu.com/BugSquad/GettingInvolved](https://wiki.ubuntu.com/BugSquad/GettingInvolved)

---

