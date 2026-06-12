---
title: "Critical Vulnerabilities from PHP 5.3.5 in Ubuntu 11.04"
date: 2011-09-14
forum: Security
---

### Post by bkudrle on 2011-09-14
I have a 11.04 installation of Ubuntu 11.04 and have run a Vulnerability scan on it using Rapid7's NEXPOSE, community edition. It comes up with 4 Critical Vulnerabilities, all related to the default PHP version with Ubuntu 11.04, namely PHP 5.3.5. The 4 descriptions are as follows. 

1. Description  
Integer overflow in ext/shmop/shmop.c in PHP before 5.3.6 allows context-dependent attackers to cause a denial of service (crash) and possibly read sensitive memory via a large third argument to the shmop_read function.

2. Description  
Multiple format string vulnerabilities in phar_object.c in the phar extension in PHP 5.3.5 and earlier allow context-dependent attackers to obtain sensitive information from process memory, cause a denial of service (memory corruption), or possibly execute arbitrary code via format string specifiers in an argument to a class method, leading to an incorrect zend_throw_exception_ex call.

3. Description  
Use-after-free vulnerability in the substr_replace function in PHP 5.3.6 and earlier allows context-dependent attackers to cause a denial of service (memory corruption) or possibly have unspecified other impact by using the same variable for multiple arguments.

4. Description  
Stack-based buffer overflow in the socket_connect function in ext/sockets/sockets.c in PHP 5.3.3 through 5.3.6 might allow context-dependent attackers to execute arbitrary code via a long pathname for a UNIX socket.

The first 2 can be fixed apparently by upgrading to 5.3.6 and the last 2 by upgrading further to 5.3.7. 

But since these versions of PHP aren't available through the default apt-get repositories (and I am not sure where else they might be apart from compiling the php, which I am reluctant to do since version 5.3.8 seems to have its own issues and what about compatibility issues with other packages), then I am wondering if anyone has had any problems with these vulnerabilities on their 11.04 platforms. I can assume that because of the lack of posts on this issue, then there are probably not any major issues, but I wanted to make sure.

---

### Post by uRock on 2011-09-14
Have you filed a bug report via Launchpad?

---

### Post by Ibidem on 2011-09-16
Check the changelogs in /usr/share/doc/<packagename> for what security fixes are included.
Then check Launchpad.  If there's no fix and no bug, file a bug.  But Ubuntu may have backported the fixes.

---

### Post by Dangertux on 2011-09-16
You have to watch vulnerability scanners with Ubuntu. Ubuntu tends to do a lot of backporting as others mentioned and most vulnerability scanners will check known versions against CVE's nexpose included.

As far as I am aware the only one that ISN'T patched in 11.04 is CVE-2011-1938. Which coincidentally is #4 (the one that yields code execution).

I would suggest either using LTS or upgrading to a newer version via compiling from source. On a side note from looking at POC code for CVE-2011-1938, I wouldn't sweat it, after all is said and done it likely will not yield anything more than a Denial of Service.

Patch if you want : [http://svn.php.net/viewvc?view=revision&revision=311369](http://svn.php.net/viewvc?view=revision&revision=311369)

---

