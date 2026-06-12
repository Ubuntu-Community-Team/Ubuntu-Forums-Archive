---
title: "Why only old Java?"
date: 2014-01-16
forum: Security
---

### Post by kkkkdddd on 2014-01-16
I am using Ubuntu 12.04

I have Java 7 installed:
openjdk-7-jre version 7u25-2.3.10-1ubuntu0.12.04.2

This is the newest version in precise-security repository.

Why there are no newer versions?
Oracle has already released update 51.

By using outdated version of Java, users are at risk.

---

### Post by QIII on 2014-01-16
Since Oracle Java 7 is third party and proprietary, it has to be tested and packaged before inclusion.  Oracle Java is tricky because Oracle does not allow inclusion of the actual files in repositories.  An installer has to fetch the files from Oracle.  So there can be a significant delay.

OpenJDK would get security updates, but it's otherwise frozen at Ubuntu release time.

I've included a link to webupd8.org's installation method for Oracle Java 7 in the Java wiki in my signature.  Webupd8 gets their installer updated pretty quickly, so if you add their PPA you'll get updates as you do your normal updates.

That is one of only a very select few PPAs I use.

---

### Post by mickey12gauge-n on 2014-01-17
[http://ubuntuhandbook.org/index.php/2013/07/install-oracle-java-6-7-8-on-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/07/install-oracle-java-6-7-8-on-ubuntu-13-10/)

---

### Post by kkkkdddd on 2014-01-18
Java 7 update 40 was released on 2013-09-10
More than four months ago.
Was it to short time to test it?

In updates 40, 45 and 51 there were together more than 100 security fixes (see 
[http://en.wikipedia.org/wiki/Java_version_history#Java_7_updates](http://en.wikipedia.org/wiki/Java_version_history#Java_7_updates) ).
By using 7u25, users are in great danger. Especially when they use browser plugin.

In my opinion you should do one of:
-keep Java installer up to date in the repository
-delete Java installer from your repository and tell users to download and update Java by themselves

The same policy should apply to other popular attack vectors - Adobe Flash Player and Acrobat Reader.

In current situation users may think that their system is up to date and secure. But the truth is, that it is not.

---

### Post by cariboo on 2014-01-18
Java isn't even available via the Ubuntu repositories, you have to use a ppa to install it. Which aren't official Ubuntu packages.

---

### Post by 1clue on 2014-01-18
For years I've been downloading my own Java and putting it in /opt/java rather than have any linux distro take care of it.

About half a year ago, I decided to let the repo (or in this case the PPA) do it.

Then I went through a PCI compliance process (so you can process credit cards) for one of the servers I'd made this switch on.  It's a PITA.

So here's the deal.  Any distro has a period of testing before they include a new release into the repository.  That's what everybody expects, and that's the reason they attribute to any delay.

12.04 is a long-term support release.  So what they did here is pick a point in time, freeze the versions of the upstream product and then call that stable.  After that they kept the same upstream version and then applied security and maybe stability fixes, no new features.  You can look here: [http://people.canonical.com/~ubuntu-security/cve/](http://people.canonical.com/~ubuntu-security/cve/) and enter the CVE (standard vulnerability identifier) to see whether the vulnerability has been fixed for your version of Ubuntu.

I would strongly recommend that anything you do with Java or Tomcat be done by downloading your own and installing it someplace like /usr/local/java or /opt.  Get on the updates mailing list from Oracle.  Checking every couple weeks to see if everything is up-to-date is much less pain than trying to check if the tomcat or Java that Ubuntu (or any other distro) has had a patch backported, filing an exception request (which takes a week or so to process) and then re-running an external third-party vulnerability scan.

For what it's worth, I stayed with the Ubuntu version of apache2 for the front-end.

---

### Post by angryfirelord on 2014-01-20
openjdk-7 is in the universe repository, which isn't directly covered by Canonical. Therefore, security updates come from the community.
[https://wiki.ubuntu.com/SecurityTeam/FAQ]("https://wiki.ubuntu.com/SecurityTeam/FAQ")
> What software is officially supported by the Ubuntu Security team?
Ubuntu is currently divided into four components: main, restricted, universe and multiverse. Packages in main and restricted are supported by the Ubuntu Security team for the life of an Ubuntu release, while packages in universe and multiverse are supported by the Ubuntu community. 

---

### Post by kkkkdddd on 2014-01-24
openjdk-7 was today updated from 7u25-2.3.10-1ubuntu0.12.04.2 to 7u51-2.4.4-0ubuntu0.12.04.2

---

