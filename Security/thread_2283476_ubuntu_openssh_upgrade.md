---
title: "ubuntu openssh upgrade"
date: 2015-06-22
forum: Security
---

### Post by Jackson_Ku on 2015-06-22
Hi,
My Ubuntu server version is 12.04. Today we use vulnerability scan tool to scan my server, we found OpenSSH hash_buffer overflow vulnerabilitiy ( CVE-2014-1692, [http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-1692](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-1692) ) and mention me we need to upgrade openssh to 6.4 later.

I used the following command to update openssh, after updated the openssh version is 5.9p1 only.
sudo apt-get install openssh-server

Please help to mention me how to upgrade openssh to 6.4 later?

Best Regards,

Jackson Ku

---

### Post by dino99 on 2015-06-22
[https://launchpad.net/ubuntu/+source/openssh](https://launchpad.net/ubuntu/+source/openssh)

Precise use 5.9; all newer ubuntu have 6.6 or 6.7

Looks like nobody asked for a backport; so either dist-upgrade to the next LTS or up, or request a backport

---

### Post by deadflowr on 2015-06-22
Moved to ***Security***

According to the Ubuntu security team it's a non-issue, because the openssh package in Ubuntu does not use the J-PAKE protocol.
See: [http://people.canonical.com/~ubuntu-security/cve/2014/CVE-2014-1692.html](http://people.canonical.com/~ubuntu-security/cve/2014/CVE-2014-1692.html)

---

