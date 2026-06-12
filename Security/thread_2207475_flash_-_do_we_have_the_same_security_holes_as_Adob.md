---
title: "flash - do we have the same security holes as Adobe has posted 2 emergency patches"
date: 2014-02-23
forum: Security
---

### Post by squakie on 2014-02-23
Adobe has posted 2 emergency patches in the last week for flash that they say are for security holes were someone can actually take control of your computer, and the article on Yahoo claimed this affected not just Windows, but Linux and other OS's.

I know Adobe stopped support for Linux, so my question is do we have the same holes in our last version of flash, and indeed what can someone actually do to a Linux computer via those holes?  It sounds like it somehow gives root priviledges to the offender.

The article also said something about updating the version of Java and one other thing (I have forgotten - the late 60's and 70's were fun, just clouded my memory a bit! ;) ).

Any serious input on this would be greatly appreciated!

---

### Post by monkeybrain20122 on 2014-02-23
I have gotten updates for flash in routine updates in the last couple of days, maybe that was it? Adobe does provide security updates for Linux.
Not sure about java, I use openjdk and icetea rather than Oracles'

---

### Post by bashiergui on 2014-02-24
The best way to determine if you are vulnerable to any given 0-day is to look for the CVE number. [http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-0502](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-0502)

> Double free vulnerability in Adobe Flash Player before 11.7.700.269 and 11.8.x through 12.0.x before 12.0.0.70 on Windows and Mac OS X and **before 11.2.202.341 on Linux**, Adobe AIR before 4.0.0.1628 on Android, Adobe AIR SDK before 4.0.0.1628, and Adobe AIR SDK & Compiler before 4.0.0.1628 **allows remote attackers to execute arbitrary code via unspecified vectors**, as exploited in the wild in February 2014.This means that Linux is vulnerable so apply the patch. It's a remote code execution vulnerability, which is about as bad as it gets. 

Flash is still supported on Linux. They're not developing anything new, but they will continue to release security updates for another 5 years or so.

---

### Post by bashiergui on 2014-02-24
Here are the CVEs for the other recent Flash vulns.
[http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-0499](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-0499)
[http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-0498](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-0498)


If you want to know if your version of java is vulnerable then figure out exactly which version you're running 
```
dpkg -l *jdk*
dpkg -l *icetea*
``` and then search for the package name on [http://web.nvd.nist.gov/view/vuln/search](http://web.nvd.nist.gov/view/vuln/search)

---

### Post by bashiergui on 2014-02-24
Just to be clear there is a difference between having Java on your computer and having a Java plugin enabled in your browser. 

There are so many 0-days and vulns for the browser plugins that I have lost track. If you have to have a plugin then keep it disabled all the time except when you actually need it.

Java software itself is like any other software: keep it parched and don't run random code from the internet and you'll probably be okay.

---

### Post by sam_baker2 on 2014-02-27
was it something to do with this?

[http://ubuntuforums.org/showthread.php?t=2203768](http://ubuntuforums.org/showthread.php?t=2203768)

---

