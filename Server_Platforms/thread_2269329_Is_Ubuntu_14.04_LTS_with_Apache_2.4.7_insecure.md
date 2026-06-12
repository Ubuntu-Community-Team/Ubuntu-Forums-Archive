---
title: "Is Ubuntu 14.04 LTS with Apache 2.4.7 insecure?"
date: 2015-03-14
forum: Server Platforms
---

### Post by Drone4four on 2015-03-14
The Ubuntu 14.04 server feature list boasts Apache 2.4.7.   This is the version I have installed: ```
$ /usr/sbin/apache2ctl status | grep Version
Server Version: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.6
``` But running this version of Apache in the default installation is high risk according to [a published security bulletin on CVE Details]("http://www.cvedetails.com/cve/CVE-2012-2379/"). According to this bulletin, this security hole was discovered in 2012 which affects older versions of Apache (including 2.4.7 found in 14.04) which could be exploited by an intruder who could totally compromise system integrity - - a task which apparently is easy for a relatively unskilled novice intruder to pull off.  This is monumental.  Is Canonical aware of this security hole?  I should hope so.  Does Canonical have a custom version of Apache in the repos with this security hole patched? I know all the packages I have installed are up to date.  So is my system secure or is this something I should worry about as a beginner sysadmin?  If the version of Apache that comes installed by default is insecure, where can I find the latest Apache package for 14.04?

---

### Post by Thirtysixway on 2015-03-18
Drone4four,

To put it bluntly, you're incorrect in two ways

1 - The CVE you linked to is not for Apache web server, it's for Apache CXF which is a different project entirely.  The exploits used in that CVE can't be used against your web server - you can try all day but it simply won't work :p. You can also verify this on the [Ubuntu Security CVE database]("http://people.canonical.com/~ubuntu-security/cve/2012/CVE-2012-2379.html").

2 - Debian (and thus Ubuntu) pull in security patches for their packages, but the version number will stay the same.  There is nothing "special" that Canonical is doing, this is how most release-based distros function.  This is why despite having 2.4.7, you will still see updates available if you do an apt-get update on your server.  You can also verify this by going to the [package page for apache2 on Trusty]("http://packages.ubuntu.com/trusty/apache2"), and click the **Ubuntu Changelog**. You can see patches being applied.  You can then verify your server has the security patches by checking the installed package version (not the version reported by apache2ctl) by running 'dpkg -l apache2'  as of this post it is 2.4.7-1ubuntu4.4.

---

