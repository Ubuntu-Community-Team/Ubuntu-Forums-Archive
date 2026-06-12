---
title: "IcedTea (Java) Problem"
date: 2012-09-19
forum: Security
---

### Post by rookcifer on 2012-09-19
We all know about the Java security issues published a while back.  I tested my browser at a Java test page and it warned me that my IcedTea plugin is out of date.  When I look in the Chrome plugin section, it also has a warning saying my plugin is out of date and needs security patches.  However, whenever I check the repos to install icedtea-plugin, it says I have the latest version.  Any ideas?

---

### Post by zombifier25 on 2012-09-20
The best bet right now is installing the official Oracle Java. [This is a neat PPA for automatically installing it](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html).

---

### Post by claracc on 2012-09-20
The icedtea plugin version is a bit behind the last oracle java plugin.

For this reason, now it is recommended to install oracle java plugin, you can do it through the webup8 ppa.

---

### Post by QIII on 2012-09-20
(Prologue:  The webupd8 PPA is the way to go for Oracle Java 7. All other methods are overly complex and do not fit the pattern of installation we generally expect in Ubuntu. It is suggested as a method in the Java wiki in my signature, in the Oracle Java 7 section under "Command line methods" and appears as "Using webupd8.org's strikingly simple method".  Because there is a wealth of information in the Community wikis that is constantly updated by members of the community, I prefer to direct people to the wikis when an appropriate one exists rather than giving an advice seeker a URL in a post because we need to let people know the wikis exist and the resources are available.  I'll get off my soap box now.)

The relationship between Oracle Java 7 and OpenJDK 7 is this:  OpenJDK 7 is the open source reference implementation for Oracle Java 7.  What that means is that it is the "standard" by which compliance with Java is judged.  Even Oracle is committed to the promise of using it as the reference, although even they have a good bit of work to do to achieve that (even their proprietary stuff is supposed to comply with the reference.)

Oracle is one of the prime movers and shakers in the development of OpenJDK 7.

At this time, OpenJDK 7 ***may***, for a short time, lag behind newer updates of Oracle Java 7.  Thus, it is ***sometimes*** a good idea to use Oracle Java 7 and the Oracle Java 7 browser plugin if a particular site or application demands it.  However, OpenJDK 7 should be used if at all possible because it is fully open source.  Unfortunately, many application and website developers are not aware of the relationship between OpenJDK 7 and Oracle Java 7 and write products that do not perceive OpenJDK 7 as Java.

The recent spate of security issues have made Oracle make a very unusual move, in that they departed from their normal quarterly security updates and pushed Update 7 out quickly.  They were caught with their pants down and a bit embarrassed to have been caught with a gaping security hole they knew about since April 2012.

Despite what many online tutorials say, it is ***not*** necessary to remove OpenJDK 7 to install Oracle Java 7.  In fact, attempting to uninstall OpenJDK 7 in Ubuntu will result in the installation of OpenJDK 6, which is terribly riddled with security vulnerabilities and will reach end of life along with Oracle Java 6 in November, 2012.  OpenJDK 7 and Oracle Java 7 can coexist on a machine and one can switch between the two.

Using the webupd8 PPA is advantageous because the maintainers of the PPA update their scripts as new Oracle Java 7 Updates are released, meaning that it is not necessary to uninstall and reinstall Oracle Java 7 manually.  Your normal periodic Ubuntu updates will ensure that Oracle Java 7 is kept up to date with no extra effort.

---

### Post by kostkon on 2012-09-20
> **rookcifer said:**
> We all know about the Java security issues published a while back.  I tested my browser at a Java test page and it warned me that my IcedTea plugin is out of date.  When I look in the Chrome plugin section, it also has a warning saying my plugin is out of date and needs security patches.  However, whenever I check the repos to install icedtea-plugin, it says I have the latest version.  Any ideas?
[Software in Ubuntu is always patched for any security holes]("http://www.ubuntu.com/usn"), so even if you have an older version that doesn't mean that your software is unsafe. That's how the policy regarding security updates works in Ubuntu.

So, in general, if your system is up-t-o-date then you are fine, you don't need to do anything about it.

---

### Post by QIII on 2012-09-20
It can't be patched from the repo until a patch is released to be made available in the repo.  In the case of the security issue with both OpenJDK 7 and Oracle Java 7, Oracle was out with a patch faster than it got into OpenJDK.  Oracle Java 7 is proprietary and Oracle does not grant license for maintaining it in repos.  OpenJDK, which is in the repo, was vulnerable until a patch was pushed several days later. This was not a run of the mill security issue.  Red Hat flat out told its enterprise customers to either stop using Java or uninstall it completely.  It was a couple of days before the Update came out for Oracle Java 7 and OpenJDK 7 was even later.

Patches still have to be released, tested and put in the repos.  That takes time.

The fact that someone might have been running Ubuntu was no protection at all from the two pronged vulnerability that was exploited.  You can't just assume you are safe because Ubuntu stops bullets and has x-ray vision.

I don't mean to be argumentative, but the Java debacle a few weeks ago was a very dangerous situation across all OSes, including Microsoft and Apple.

---

### Post by rookcifer on 2012-09-20
> **kostkon said:**
> [Software in Ubuntu is always patched for any security holes]("http://www.ubuntu.com/usn"), so even if you have an older version that doesn't mean that your software is unsafe. That's how the policy regarding security updates works in Ubuntu.

So, in general, if your system is up-t-o-date then you are fine, you don't need to do anything about it.

But that's the problem.  I am getting warnings that Java is out of date even though the repos do not have anything newer.

When this hit a week or two ago, I remember I got an update for OpenJDK in the repos but it was "held back" and I couldn't install it.  So I was wondering if this had something to do with it.  Now I am not noticing anything being held back, but I am still out of date.  

Here is what I have available on my machine:


```
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      manual mode
  2            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1051      manual mode
```

And the IcedTea plugin I am using is **1.6.0_34** (Java 6 Update 34).

So, really my question is:  are the repos out of date with security patches or am I having some sort of dependency issue stopping me from updating?

---

### Post by QIII on 2012-09-20
You should select OpenJDK 7, which is selection 2 in the menu offered.

---

### Post by rookcifer on 2012-09-21
> **QIII said:**
> You should select OpenJDK 7, which is selection 2 in the menu offered.

I did.  I just went ahead and uninstalled Java6.  However, now Chrome is telling me IcedTea is out of date and has security issues even though it is the latest version available.

---

### Post by claracc on 2012-09-21
> **rookcifer said:**
> I did.  I just went ahead and uninstalled Java6.  However, now Chrome is telling me IcedTea is out of date and has security issues even though it is the latest version available.

I think it is true, as icedtea java plugin have not been patched yet for security, in the meantime I would use java plugin from oracle (installed through webup8 ppa, the easy way).

---

### Post by wacky_sung on 2012-09-21
Manually install.

[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by QIII on 2012-09-21
Manually installing via that method is unnecessarily complex and requires reinstallation as Oracle provides updates.

---

### Post by rookcifer on 2012-09-21
> **QIII said:**
> Manually installing via that method is unnecessarily complex and requires reinstallation as Oracle provides updates.

Yeah.  I just reinstalled OpenJDK-7 and got rid of version 6.  Everything is working fine, but I still get the warning in Chrome that icedTea is out of date.  I suppose I won't worry about it until there is an update pushed to the repos.  Besides, I have both the PID and SECCOMP sandboxes enabled for Chrome as well as an AppArmor profile.

Marking as solved.  Thanks for the help.

---

### Post by wacky_sung on 2012-09-21
> **QIII said:**
> Manually installing via that method is unnecessarily complex and requires reinstallation as Oracle provides updates.

Is that complex?Haha...i still prefer manual install inregardless of it because i am in full control.

---

