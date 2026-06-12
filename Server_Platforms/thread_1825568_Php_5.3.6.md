---
title: "Php 5.3.6"
date: 2011-08-15
forum: Server Platforms
---

### Post by Techn0crat on 2011-08-15
Hello,

In order to pass PCI compliance I need to upgrade our webserver from php 5.3.5 to php 5.3.6.  I found this: [http://ubuntuforums.org/showpost.php?p=11125421&postcount=8](http://ubuntuforums.org/showpost.php?p=11125421&postcount=8) however it doesn't seem to work. My best guess is due to the fact I have 64bit server.  Is there something else I can do without going through a compile?

Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty

Linux 2.6.38-10-server #46-Ubuntu SMP Tue Jun 28 16:31:00 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Thanks

---

### Post by Bachstelze on 2011-08-15
If your business is critical enough that you need PCI compliance, you should hire someone who is familiar with this stuff. This forum is not for professional-grade support.

---

### Post by Techn0crat on 2011-08-15
Though I appreciate your concern this does not help me with my problem.

---

### Post by AlexDudko on 2011-08-15
Only if someone else will compile it for you.
Why do you need this version? Are you sure that known security fixes are not backported in the current version?

---

### Post by AlexDudko on 2011-08-15
Though it's about Redhat, I think this link could be interesting for you.
[https://access.redhat.com/security/updates/backporting/?sc_cid=3093]("https://access.redhat.com/security/updates/backporting/?sc_cid=3093")

---

### Post by Techn0crat on 2011-08-15
When you run through compliance it gives you a report.  In the report it tells you all the security issues you might have.  All the issues are security flaws in 5.3.5 and the recommended way to resolve these is to upgrade.  I assume since the scan is from the outside it tries the exploits.  Using that assumption then these fixes are not in the current natty version of php 5.3.5.

I can compile it but it is such a pain.  I would rather use a package.

I have found that PPA has a 64 release.  So it seems my issue is for some reason its not looking to that PPA for an upgrade.  Is there something I can do to force it to look there?

---

### Post by AlexDudko on 2011-08-15
If the scan is from the outside it doesn't try the exploits since it's almost impossible. It just tries the versions.
Here is the list of all bugs, fixed in PHP-5.3.6.
[http://www.php.net/ChangeLog-5.php#5.3.6]("http://www.php.net/ChangeLog-5.php#5.3.6")
You can find bug reports and try to reproduce them in your system thus finding out whether it is still vulnerable.
As an example I chose this bug:
[https://bugs.php.net/bug.php?id=54055]("https://bugs.php.net/bug.php?id=54055")
I couldn't reproduce it even though my version is:
[PHP]php --version
PHP 5.2.14 with Suhosin-Patch 0.9.7 (cli) (built: Jun  1 2011 13:35:03) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2010 Zend Technologies
    with Suhosin v0.9.32.1, Copyright (c) 2007-2010, by SektionEins GmbH[/PHP]
because the patch has already been backported to it.

---

### Post by AlexDudko on 2011-08-15
See this link: [http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.5-1ubuntu7.2/changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.5-1ubuntu7.2/changelog")
Security Enhancements and Fixes in PHP 5.3.6 **were** backported to the Natty's version of PHP (5.3.5-1ubuntu7.2).

---

