---
title: "FireFox Update Question"
date: 2008-07-29
forum: Security
---

### Post by WilliamB on 2008-07-29
I updated my 8.04.1 install on Saturday (26th) and one of the packages installed was:

firefox 3.0.1+build1+nobinonly-0ubuntu0.8.04.2

Today, there was a newer version of said package:

firefox 3.0.1+build1+nobinonly-0ubuntu0.8.04.3

The change listed for the newer package was very short:

'no change rebuild for -security'

Is -security an option of some sort when the package is built or is that a reference to something else?

Can someone more fully explain why the two successive package releases as the 8.04.3 doesn't seem to change much. Was there an error in the first one?

Thanks!

---

### Post by cdenley on 2008-07-29
[http://www.ubuntu.com/usn/usn-626-1](http://www.ubuntu.com/usn/usn-626-1)

---

### Post by WilliamB on 2008-07-29
> **cdenley said:**
> [http://www.ubuntu.com/usn/usn-626-1](http://www.ubuntu.com/usn/usn-626-1)

Thanks for the response.

As best I can see, that doesn't address the two successive package releases and the difference between them. Am I missing something?

---

### Post by cdenley on 2008-07-29
> **WilliamB said:**
> 
As best I can see, that doesn't address the two successive package releases and the difference between them. Am I missing something?

Apparently.
> 
=========================================================== 
Ubuntu Security Notice USN-626-1              **July 29, 2008**
firefox-3.0, xulrunner-1.9 vulnerabilities
CVE-2008-2785, CVE-2008-2933, CVE-2008-2934
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 8.04 LTS

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.

[B]The problem can be corrected by upgrading your system to the
following package versions:
[/B]
Ubuntu 8.04 LTS:
  firefox-3.0                     **3.0.1+build1+nobinonly-0ubuntu0.8.04.3**
  xulrunner-1.9                   1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3

After a standard system upgrade you need to restart Firefox and any
applications that use xulrunner, such as Epiphany, to effect the
necessary changes.

Details follow:

A flaw was discovered in the browser engine. A variable could be made to
overflow causing the browser to crash. If a user were tricked into opening
a malicious web page, an attacker could cause a denial of service or
possibly execute arbitrary code with the privileges of the user invoking
the program. (CVE-2008-2785)

Billy Rios discovered that Firefox and xulrunner, as used by browsers
such as Epiphany, did not properly perform URI splitting with pipe
symbols when passed a command-line URI. If Firefox or xulrunner were
passed a malicious URL, an attacker may be able to execute local
content with chrome privileges. (CVE-2008-2933)


---

### Post by strushb on 2008-07-29
USN-626-1 explains a new package within that short time, it is a bug that has been fixed in the ubuntu-security repository. Like in ubuntu**-security**

PS: Hello Ubuntu forums : )

Edit: Now that I think of it, why does the package log simply say "no change" when other debs say wich CVE has been fixed?

---

### Post by WilliamB on 2008-07-30
> **strushb said:**
> USN-626-1 explains a new package within that short time, it is a bug that has been fixed in the ubuntu-security repository. Like in ubuntu**-security**

PS: Hello Ubuntu forums : )

Edit: Now that I think of it, why does the package log simply say "no change" when other debs say wich CVE has been fixed?

Thanks for the reply.

That's exactly what I was attempting to figure out, why the 'no change' but another build.

I believe the prior 8.04.2 version had the CVE's listed as being fixed so those fixes were in the .2 version so was trying to figure out what was different about the 8.04.3 version above and beyond the CVE security updates as those appeared to be fixed with the .2 version.

---

