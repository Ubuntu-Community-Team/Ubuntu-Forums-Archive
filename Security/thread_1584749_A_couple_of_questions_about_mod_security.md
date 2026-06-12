---
title: "A couple of questions about mod_security"
date: 2010-09-29
forum: Security
---

### Post by TheAlien on 2010-09-29
Hi!

I have just installed the latest version of mod_security from source on Ubuntu Server 10.04. And it seems like it went okay while I followed the official installation manual for UNIX.

Question 1: How do I know that mod_security is really on? Can I view any status anywhere?

Question 2: What's the difference between the base_rules and the optional_rules? When I load the optional_rules, I always get an error message and Apache2 won't run. The base_rules works fine.

Thanks in advance!

---

### Post by gordintoronto on 2010-09-29
Administration/System Monitor can show you what processes are running. I assume you would recognize the process for mod_security.

During the installation, did you do something which would make the program run at system startup? If not, have a look at Preferences/Startup Applications.

I assume there is a web site for the program where you can find the answer to your second question. Try Google, since this program is not part of Ubuntu.

By the way, to install an application in Ubuntu, first try Administration/Synaptic. Since mod_security is there, it would have been much, much easier to install it that way -- and you would be sure that there are no lib version incompatibilities which can come back and bite you, and you would also get updates automatically. Any time you download something from the Internet and manually install it, you are inviting disaster.

---

### Post by FuturePilot on 2010-09-29
1. Check /var/log/apache2/mod_security/modsec_audit.log and modsec_debug.log

2. See [this]("http://ubuntuforums.org/showthread.php?t=1564663")

---

### Post by TheAlien on 2010-09-30
> **gordintoronto said:**
> By the way, to install an application in Ubuntu, first try Administration/Synaptic. Since mod_security is there, it would have been much, much easier to install it that way -- and you would be sure that there are no lib version incompatibilities which can come back and bite you, and you would also get updates automatically. Any time you download something from the Internet and manually install it, you are inviting disaster.

The problem with the mod_security from the repos is that it's outdated, unmaintained and has a security flaw that is very much serious. I would like to use the repos myself, but not all the packages in there are maintained and secure(unless they're from the MAIN section). That can lead to even a bigger disaster IMO.

---

### Post by FuturePilot on 2010-09-30
> **TheAlien said:**
> The problem with the mod_security from the repos is that it's outdated, unmaintained and has a security flaw that is very much serious. I would like to use the repos myself, but not all the packages in there are maintained and secure(unless they're from the MAIN section). That can lead to even a bigger disaster IMO.

Just curious, what is the vulnerability the version in the repos has?

---

### Post by TheAlien on 2010-09-30
> **FuturePilot said:**
> Just curious, what is the vulnerability the version in the repos has?

> 
ModSecurity v2.5.12 ([change log]("https://sourceforge.net/projects/mod-security/files/modsecurity-apache/2.5.12/CHANGES_2.5.12.txt/download")) has been released. This release fixes several important issues to help prevent a **detection bypass and denial of service attacks** against ModSecurity.  Many thanks to the Sogeti/ESEC R&D team for sending us the results of their code review.  In addition, this release fixes quite a few small but notable bugs and includes the latest Core Ruleset (v2.0.5). 

[http://www.modsecurity.org/](http://www.modsecurity.org/)
It's sad that the repo version (2.5.11-1) has not been updated since the release of 10.4 LTS. :( I mean; this mod is a very important and much used apache2 mod for webserver security!

---

### Post by FuturePilot on 2010-09-30
> **TheAlien said:**
> It's sad that the repo version (2.5.11-1) has not been updated since the release of 10.4 LTS. :( I mean; this mod is a very important and much used apache2 mod for webserver security!

Ah thanks. FYI I've just backported 2.5.12 from Maverick in my PPA.
[https://launchpad.net/~futurepilot/+archive/ppa/]("https://launchpad.net/~futurepilot/+archive/ppa/")

---

