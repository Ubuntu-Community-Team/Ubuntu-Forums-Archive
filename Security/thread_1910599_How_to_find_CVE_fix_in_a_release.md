---
title: "How to find CVE fix in a release ?"
date: 2012-01-17
forum: Security
---

### Post by toby53 on 2012-01-17
Hi,
We have CVE-2010-1623 reported in the enabled apache mod_requestimeout.
On the [http://people.canonical.com/~ubuntu-security/cve/2010/CVE-2010-1623.html]("http://people.canonical.com/%7Eubuntu-security/cve/2010/CVE-2010-1623.html") page
it says our apache package: [Ubuntu 10.04 LTS (Lucid Lynx)]("https://launchpad.net/ubuntu/lucid/+source/apache2"):not-affected (2.2.14-5ubuntu8.2) 
It sounds like we are ok ?
 

We are running ubuntu 10.04.3 / apache 2.2.14-5 ubuntu 8.6 using the apt-get package installer. I found another one that was back ported to apache 2.2.14 ( CVE-2010-0425 ).

I'm wondering the best way to do this ?

---

