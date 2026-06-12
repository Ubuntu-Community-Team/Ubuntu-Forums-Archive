---
title: "64-bit operating system privilege escalation vulnerability"
date: 2012-06-19
forum: Security
---

### Post by Inhineritor on 2012-06-19
Hello,  most of you might have already heared about it: A few days ago a security issue on Intel 64-Bit CPU was published.  "Some 64-bit operating systems and virtualization software running on Intel CPU hardware are vulnerable to a local privilege escalation attack. The vulnerability may be exploited for local privilege escalation ..." ([http://www.kb.cert.org/vuls/id/649219](http://www.kb.cert.org/vuls/id/649219))  Now I'd like to ask, if that security issue also affects my Ubuntu 12.04 LTS (64 Bit).  Kind regards

---

### Post by haqking on 2012-06-19
> **Inhineritor said:**
> Hello,  most of you might have already heared about it: A few days ago a security issue on Intel 64-Bit CPU was published.  "Some 64-bit operating systems and virtualization software running on Intel CPU hardware are vulnerable to a local privilege escalation attack. The vulnerability may be exploited for local privilege escalation ..." ([http://www.kb.cert.org/vuls/id/649219](http://www.kb.cert.org/vuls/id/649219))  Now I'd like to ask, if that security issue also affects my Ubuntu 12.04 LTS (64 Bit).  Kind regards

Every OS and software application has some vulnerability, there are millions of them.

[www.cve-mitre.org]("http://www.cve-mitre.org")

A quick search on there for Ubuntu 12.04 brings up 4 [http://web.nvd.nist.gov/view/vuln/search-results?query=ubuntu+12.04&search_type=all&cves=on](http://web.nvd.nist.gov/view/vuln/search-results?query=ubuntu+12.04&search_type=all&cves=on)

That doesnt take into account zero day or the additional applications you may or may not have installed.

Per your specific vulnerability as you can see it is unknown at the moment _[http://www.kb.cert.org/vuls/id/MAPG-8TVPQH](http://www.kb.cert.org/vuls/id/MAPG-8TVPQH)_

The reason i posted was it sounded like you were in fear that your system was vulnerable due to this one vulnerability, and without it you were secure? Which of course is not the case.

Peace

---

### Post by Inhineritor on 2012-06-19
Thank you for your answer.

I know - of course - that there are vulnerabilities.

However I was specifically referring to that single issue described under [http://www.kb.cert.org/vuls/id/649219](http://www.kb.cert.org/vuls/id/649219)

EDIT: OK, now I see that you have also addressed that :)

---

