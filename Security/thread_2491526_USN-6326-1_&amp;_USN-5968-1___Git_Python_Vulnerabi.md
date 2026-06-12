---
title: "USN-6326-1 &amp; USN-5968-1   Git Python Vulnerability"
date: 2023-10-12
forum: Security
---

### Post by jeremyhillman on 2023-10-12
[USN-5968-1: GitPython vulnerability | Ubuntu security notices | Ubuntu]("https://ubuntu.com/security/notices/USN-5968-1")
[USN-6326-1: GitPython vulnerability | Ubuntu security notices | Ubuntu]("https://ubuntu.com/security/notices/USN-6326-1")

Hello all, I have these vulnerabilities coming up in Qualys scans and on the USN pages the patch is listed as only available for Pro for Ubuntu 20.04
It states "In general, a standard system update will make all the necessary changes." I have patched the affected systems to no avail.
Does anyone have any insight as to how I can patch these systems without purchasing additional support? 
Thanks!

---

### Post by deadflowr on 2023-10-12
Pro is free for users with up to 3 machines (50 machines for Ubuntu Members).
Did you sign-up for Pro?

---

### Post by jeremyhillman on 2023-10-12
I work for a large company and have 47 servers. I thought that being in "[COLOR=#000000][FONT=Ubuntu]LTS standard security maintenance for Ubuntu Main" by being 20.04 would have all the necessary security patches. [/FONT][/COLOR][Ubuntu release cycle | Ubuntu]("https://ubuntu.com/about/release-cycle")
 Is there a place to get the patches sperately from apt?

Thank you for your time!

---

### Post by ian-weisser on 2023-10-12
> **jeremyhillman said:**
> I have patched the affected systems to no avail.

What does that mean? Patched is patched.
Are you saying that your scanner is still claiming the patched software as vulnerable? Such false positives are common.

> **jeremyhillman said:**
> I thought that being in "[COLOR=#000000][FONT=Ubuntu]LTS standard security maintenance for Ubuntu Main" by being 20.04 would have all the necessary security patches.[/FONT][/COLOR]

It's about the repository.
Standard Security Maintenance does not include the Universe repository. Never has.
The "python-git" package is in Universe.
The lack of community action patching Universe packages is why the market for Pro subscriptions exists.

Folks who don't want to pay for Pro can simply apply Universe security patches  themselves. Better yet, they can submit patched packages to MOTU for  upload. That avenue is still open. Then everybody gets the patched package for free.

> **jeremyhillman said:**
> Does anyone have any insight as to how I can patch these systems without purchasing additional support? 

That is confusing. You can patch yourself, or you can pay somebody to patch for you. What are you asking?
One assumes you have reviewed the relevant CVEs. Perhaps you can  mitigate another way. Or perhaps you are already not vulnerable.

---

