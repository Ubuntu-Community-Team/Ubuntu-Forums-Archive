---
title: "Oracle (Sun) Java JRE 6 update 22"
date: 2010-10-13
forum: Security
---

### Post by Pjotr123 on 2010-10-13
Oracle has made available Java JRE 6 update 22. Among other things, this contains security fixes:
[http://www.oracle.com/technetwork/java/javase/6u22releasenotes-176121.html](http://www.oracle.com/technetwork/java/javase/6u22releasenotes-176121.html)

If you want it now: it's not in the repo's (yet), but you can install it manually as well. For example by applying this updated how-to:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Good luck! :)

---

### Post by bep7987 on 2010-10-13
Thank you!

:KS

---

### Post by Pjotr123 on 2010-10-15
> **bep7987 said:**
> Thank you!

:KS

You're welcome. :)

Of course this update (6u22) should get into the repositories as well. Both Lucid and Maverick are affected: Lucid has 6u20 and Maverick has 6u21.

An interesting test for the responsiveness of the Ubuntu security team. :)

---

### Post by Pjotr123 on 2010-10-17
Update: there's an active bug report on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/659937](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/659937)

It appears they're working on it. :-)

---

### Post by daniel.cotter on 2011-07-10
I've got the Sun JRE installed, dpkg reports it (ii) installed and healthy, but when I type ```
java -version
```  it tells me I am using OpenJDK (IcedTea).  I need to run the sun proprietary version, because of a site I visit which requires it (for the time being).

```
sudo update-java-alternatives -s java-6-sun
``` gets me ```
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-sun
```Any suggestions how to define the sun version as the global default?

Thanks in advance,
Daniel

---

### Post by mikewhatever on 2011-07-12
If you have followed Pjotr123's howto, the command to update your java version should look like this:
> sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_26/bin/java" 1

---

