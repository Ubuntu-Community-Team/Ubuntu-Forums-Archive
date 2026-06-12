---
title: "sun-java6"
date: 2011-12-15
forum: The Cafe
---

### Post by Johnny3 on 2011-12-15
I am a old new bee and use Ubuntu 11.10 got this in my email today.
The Canonical partner archive currently contains Oracle's Sun Java JDK
packages (sun-java6) for Ubuntu 10.04 LTS, Ubuntu 10.10 and Ubuntu 11.04.

As of August 24th 2011, we no longer have permission to redistribute new
Java packages as Oracle has retired the &#8220;Operating System Distributor
License for Java&#8221; [1][2].

Oracle has published an advisory about security issues in the version of
Java we currently have in the partner archive [3]. Some of these issues are
currently being exploited in the wild.

Due to the severity of the security risk, Canonical is immediately
releasing a security update for the Sun JDK browser plugin which will
disable the plugin on all machines. This will mitigate users' risk from
malicious websites exploiting the vulnerable version of the Sun JDK.

In the near future (exact date TBD), Canonical will remove all Sun JDK
packages from the Partner archive. This will be accomplished by pushing
empty packages to the archive, so that the Sun JDK will be removed from all
users machines when they do a software update. Users of these packages who
have not migrated to an alternative solution will experience failures after
the package updates have removed Oracle Java from the system.

If you are currently using the Oracle Java packages from the partner
archive, you have two options:

1- Install the OpenJDK packages that are provided in the main Ubuntu
   archive. (icedtea6-plugin for the browser plugin, openjdk-6-jdk or
   openjdk-6-jre for the virtual machine)
2- Manually install Oracle's Java software from their web site [4].

For more information, please consult the wiki page on the subject [5].

We apologize for any inconvenience this may cause, and thank you for your
understanding.

[1] - [http://jdk-distros.java.net/](http://jdk-distros.java.net/)
[2] - [http://robilad.livejournal.com/90792.html](http://robilad.livejournal.com/90792.html)
[3] - [http://www.oracle.com/technetwork/topics/security/javacpuoct2011-443431.html](http://www.oracle.com/technetwork/topics/security/javacpuoct2011-443431.html)
[4] - [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
[5] - [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/Java6Transition](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/Java6Transition)

I went into Ubuntu Software Center and remove anything with Java6 that was installed. I still left Ubuntu restricted extras installed unchecked Java applets. Is this OK or do I need to do more?
Thanks and God Bless Johnny3 65++

---

### Post by BC59 on 2011-12-15
The openjdk6 we have installed in our Ubuntu 11.10 is installed during the installation of the restricted extras and it's open source. Has nothing to do with the proprietary Oracle/Sun Java. It was not necessary to uninstall it.

---

### Post by Copper Bezel on 2011-12-15
This makes me happy given the concerns about iOS, Android, and Windows 8 remotely deleting software off users' machines due to security issues. It also couldn't have happened to a nicer plugin.

Naturally, I have Java disabled in my default browser to begin with, but it's good that this doesn't affect the "open" JRE, since some folks need services that really do depend on it.

---

### Post by Johnny3 on 2011-12-15
> **BC59 said:**
> The openjdk6 we have installed in our Ubuntu 11.10 is installed during the installation of the restricted extras and it's open source. Has nothing to do with the proprietary Oracle/Sun Java. It was not necessary to uninstall it.

Thanks if I have any problems I will recheck it. But everything works great and I guess because I have a windows PC too anything with Java I rather not have.
Thanks and God Bless Johnny3 65+++

---

### Post by Primefalcon on 2011-12-15
> **Johnny3 said:**
> Thanks if I have any problems I will recheck it. But everything works great and I guess because I have a windows PC too anything with Java I rather not have.
Thanks and God Bless Johnny3 65+++
Definitely glad I updated to the latest manually now, tbh if I wasn't an avid RuneScape player I'd be using openjdk

---

