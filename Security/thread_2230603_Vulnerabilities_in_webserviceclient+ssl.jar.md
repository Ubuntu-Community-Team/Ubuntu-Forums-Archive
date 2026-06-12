---
title: "Vulnerabilities in webserviceclient+ssl.jar"
date: 2014-06-20
forum: Security
---

### Post by ruchika.mahajan22 on 2014-06-20
Hi,

I am using Weblogic server 10.3. While checking for the vulnerabilities in project, came across **CVE-2007-0417,CVE-2003-0640,CVE-2001-0098,CVE-2000-0681,CVE-2007-4618,CVE-2007-4617,CVE-2007-0425,CVE-2007-0418,CVE-2007-0408,CVE-2005-4757,CVE-2005-4756** all high vulnerabilities present in **webserviceclient+ssl.jar**. The description of these vulnerabilities says that they should be present in previous versions of Weblogic and should work fine in 10.3.

I am not sure, may be I have missed something while understanding as I am new to this.
Please suggest me the way to resolve these security concerns.

Thanks in Advance!

---

### Post by TheFu on 2014-06-20
I attended training last night about the issue of deploying libraries full of security and other issues and the length of time it takes for fully patched versions to make it back into complete projects. This was java-centric training. I found the average time to fix scary - over a year.  Plus it was pointed out that the ssl libraries used by Java was full of flaws.  Now I understand better why my company doesn't allow Java programs/websites to be used on external sites.
This isn't just a problem for Java - every programming language has it, but I think Java is has the longest time-to-fix over all other F/LOSS languages.

So, the only answer I have is for you to forward this exact post to your weblogic support representative. After all, support is why companies claim proprietary software is better than F/LOSS. Use it.

---

### Post by ruchika.mahajan22 on 2014-06-24
Thanks :P

---

