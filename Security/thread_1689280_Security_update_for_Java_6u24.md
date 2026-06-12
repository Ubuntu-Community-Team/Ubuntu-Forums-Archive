---
title: "Security update for Java: 6u24"
date: 2011-02-16
forum: Security
---

### Post by Pjotr123 on 2011-02-16
Oracle has issued a security update for Java JRE: version 6 update 24 (6u24).

In the partner repository of Ubuntu, Java is still at 6 update 22 (6u22). That has become insecure by now.

If you're a user of Java JRE instead of openJDK, you can do two things: wait for the update to hit the partner repo, or install it manually. For a manual installation you can use the how-to on my website:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Good luck! :)

---

### Post by oldos2er on 2011-02-16
Great site; thank you.

---

### Post by Pjotr123 on 2011-02-17
Thanks for the compliment. :)

I'm curious how long it'll take before this update gets into the partner repo. It's a nice test for the responsiveness of the partner repo team.

6u23 never made it into the repo, but that was as expected, because that was no security update. 6u24 on the other hand, contains several critical security fixes and should be applied as soon as possible.

---

### Post by Irihapeti on 2011-02-17
I did this on one machine and it worked just fine.

On another machine, I had the Sun Java JDK; I remove the repo version and installed the version from Oracle and adjusted the instructions to match the different path names. The jre works, but nothing I did could get the browser plugin to work.

Any idea what I might have done wrong?

---

### Post by emarkay on 2011-02-20
Strange, this is, being that the Redmond folks can get "Zero Day" fixes out - AND - that this is a legit security issue.

Anyone have more info what is taking the "Partners" so long to update - is there a technical reason???

---

### Post by cariboo on 2011-02-20
What problem does the update fix?

---

### Post by Cavsfan on 2011-02-20
I am not sure what security issue Java SE 6 Update 24 fixes, but I noticed I didn't have the latest installed via the one link in my signature.
So, I installed it per the other link in my signature.

I did not see this thread and opened my own: 
[[color=blue]_Install latest java version - Java SE 6 Update 24_[/COLOR]](http://ubuntuforums.org/showthread.php?p=10477313#post10477313)

It updates Firefox as well.

---

### Post by emarkay on 2011-02-20
> **cariboo907 said:**
> What problem does the update fix?

[http://www.oracle.com/technetwork/topics/security/javacpufeb2011-304611.html](http://www.oracle.com/technetwork/topics/security/javacpufeb2011-304611.html)
[http://www.oracle.com/technetwork/topics/security/javacpufeb2011-304611.html#AppendixJAVA](http://www.oracle.com/technetwork/topics/security/javacpufeb2011-304611.html#AppendixJAVA)

[http://www.ghacks.net/2011/02/17/oracle-finally-releases-java-6-update-24/](http://www.ghacks.net/2011/02/17/oracle-finally-releases-java-6-update-24/)
[http://krebsonsecurity.com/2011/02/java-6-update-24-plugs-21-securty-holes/](http://krebsonsecurity.com/2011/02/java-6-update-24-plugs-21-securty-holes/)

But then again, the Vulture speaks volumes...
[http://www.theregister.co.uk/2011/02/17/java_security_threat/](http://www.theregister.co.uk/2011/02/17/java_security_threat/)

---

### Post by cariboo on 2011-02-20
There isn't a whole lot of info on the Oracle site. Are these same vulnerabilities present when using openjdk and the iced-tea plugin?

---

### Post by emarkay on 2011-02-21
I don't have the time now to look, but here's some sources.

OpenJDK 'IcedTea' Multiple Signers Privilege Escalation Vulnerability:
[http://www.securityfocus.com/bid/46439](http://www.securityfocus.com/bid/46439)

Recent related Debian bug note:
[http://lwn.net/Articles/428088/](http://lwn.net/Articles/428088/)

Official source for IcedTea info:
[http://openjdk.java.net/projects/icedtea/](http://openjdk.java.net/projects/icedtea/)

Official OpenJDK Security :
[http://openjdk.java.net/groups/security/](http://openjdk.java.net/groups/security/)

Official OpenJDK News and Info:
[http://planetjdk.org/](http://planetjdk.org/)

---

### Post by cariboo on 2011-02-21
There is a ppa available here:

[https://launchpad.net/~ferramroberto/+archive/java](https://launchpad.net/~ferramroberto/+archive/java)

---

### Post by FuturePilot on 2011-02-21
[https://launchpad.net/ubuntu/maverick/+source/sun-java6/6.24-1build0.10.10.1]("https://launchpad.net/ubuntu/maverick/+source/sun-java6/6.24-1build0.10.10.1")

---

### Post by Irihapeti on 2011-02-21
Updates from the Partner repository installing now.

---

