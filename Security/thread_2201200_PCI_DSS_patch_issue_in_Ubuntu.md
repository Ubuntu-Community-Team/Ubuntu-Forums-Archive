---
title: "PCI DSS patch issue in Ubuntu"
date: 2014-01-23
forum: Security
---

### Post by ashraf2 on 2014-01-23
Hi All,

I am new bee to Linux/ubuntu forum,

Recently we have performed PCI scan on one of our website, and we have found some vulnerabilities. The App we are using for this site is

OS :  ubuntu 12.04.3
language : php 5.3.10
web server : nginx 

In the PCI report there are certain CVE's that i am unable to found in ubuntu repository change log ([http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.10-1ubuntu3.9/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.10-1ubuntu3.9/changelog)). So my question is where i can reach for this information , i have already search the internet but dint find any thing interesting.

Where are at php.net they follow issues with Bug number , now typical thing is who to relate CVE's with Bug numbers. 


Pls suggest , some path way  to proceed.

some of the CVE's which i could not found information are (CVE-2005-1871
CVE-2012-0831
CVE-2007-2768
CVE-2007-4528
CVE-2006-5178
CVE-2005-2106
CVE-2007-2243
CVE-2006-4023
CVE-2011-4963
CVE-2010-5107
CVE-2013-1362
CVE-2013-2110
CVE-2005-1871
CVE-2012-0831
CVE-2012-3365  )  This includes CVE's for php , openssh, nginx , Drupal.

---

### Post by sandyd on 2014-01-23
> **ashraf2 said:**
> Hi All,

I am new bee to Linux/ubuntu forum,

Recently we have performed PCI scan on one of our website, and we have found some vulnerabilities. The App we are using for this site is

OS :  ubuntu 12.04.3
language : php 5.3.10
web server : nginx 

In the PCI report there are certain CVE's that i am unable to found in ubuntu repository change log ([http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.10-1ubuntu3.9/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.10-1ubuntu3.9/changelog)). So my question is where i can reach for this information , i have already search the internet but dint find any thing interesting.

Where are at php.net they follow issues with Bug number , now typical thing is who to relate CVE's with Bug numbers. 


Pls suggest , some path way  to proceed.

some of the CVE's which i could not found information are (CVE-2005-1871
CVE-2012-0831
CVE-2007-2768
CVE-2007-4528
CVE-2006-5178
CVE-2005-2106
CVE-2007-2243
CVE-2006-4023
CVE-2011-4963
CVE-2010-5107
CVE-2013-1362
CVE-2013-2110
CVE-2005-1871
CVE-2012-0831
CVE-2012-3365  )  This includes CVE's for php , openssh, nginx , Drupal.

Nginx:
[https://security-tracker.debian.org/tracker/CVE-2011-4963](https://security-tracker.debian.org/tracker/CVE-2011-4963) (Only affects nginx on windows)

Drupal:
[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2005-1871](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2005-1871) 
[https://security-tracker.debian.org/tracker/CVE-2005-2106](https://security-tracker.debian.org/tracker/CVE-2005-2106)
[https://security-tracker.debian.org/tracker/CVE-2005-1871](https://security-tracker.debian.org/tracker/CVE-2005-1871)


PHP:
[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2012-0831](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2012-0831)
[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-4528](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-4528) (Doesn't apply unless your using an ancient php5)
[https://security-tracker.debian.org/tracker/CVE-2006-5178](https://security-tracker.debian.org/tracker/CVE-2006-5178) (Same as above)
[https://security-tracker.debian.org/tracker/CVE-2006-4023](https://security-tracker.debian.org/tracker/CVE-2006-4023) (unimportant)
[https://security-tracker.debian.org/tracker/CVE-2013-2110](https://security-tracker.debian.org/tracker/CVE-2013-2110)
[https://security-tracker.debian.org/tracker/CVE-2012-0831](https://security-tracker.debian.org/tracker/CVE-2012-0831)
[https://security-tracker.debian.org/tracker/CVE-2012-3365](https://security-tracker.debian.org/tracker/CVE-2012-3365) (unimportant)

Misc:
[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-2768](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-2768)

OpenSSH:
[https://security-tracker.debian.org/tracker/CVE-2007-2768](https://security-tracker.debian.org/tracker/CVE-2007-2768) (unimportant)
[https://security-tracker.debian.org/tracker/CVE-2007-2243](https://security-tracker.debian.org/tracker/CVE-2007-2243) (unimportant)
[https://security-tracker.debian.org/tracker/CVE-2010-5107](https://security-tracker.debian.org/tracker/CVE-2010-5107)

Nagios:
[https://security-tracker.debian.org/tracker/CVE-2013-1362](https://security-tracker.debian.org/tracker/CVE-2013-1362)

---

### Post by Lloyd_mcse on 2014-01-23
Firstly, welcome to the forums.
I find the best way to find Ubuntu CVE's is to just google "[ubuntu CVE-2012-0831]("https://www.google.co.uk/search?q=ubuntu+CVE-2012-0831&oq=ubuntu+CVE-2012-0831&aqs=chrome..69i57.4295j0j8&sourceid=chrome&espv=210&es_sm=122&ie=UTF-8")" for example and you see it right at the top.
That shows you which Ubuntu versions the CVE has been patched on. As you can see it has been patched right back to 8.04 LTS and 12.04 LTS is not affected.
So you can report that as false positive.

---

