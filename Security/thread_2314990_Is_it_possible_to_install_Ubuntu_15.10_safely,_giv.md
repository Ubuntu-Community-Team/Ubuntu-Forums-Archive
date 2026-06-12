---
title: "Is it possible to install Ubuntu 15.10 safely, given the recent glibc DNS bug?"
date: 2016-02-25
forum: Security
---

### Post by lamefun-x0r on 2016-02-25
Bug info: [http://linux.slashdot.org/story/16/02/16/1724222/red-hat-google-disclose-severe-glibc-dns-vulnerability-patched-but-widespread](http://linux.slashdot.org/story/16/02/16/1724222/red-hat-google-disclose-severe-glibc-dns-vulnerability-patched-but-widespread)

From what I've read, remote code execution attacks are possible against glibc applications using specially crafted DNS responses. I couldn't find any concrete mitigation instructions.

The Ubuntu 15.10 install images dates 20 Oct (see [http://releases.ubuntu.com/15.10](http://releases.ubuntu.com/15.10)), and this security notice: [http://www.ubuntu.com/usn/usn-2900-1](http://www.ubuntu.com/usn/usn-2900-1) - says that the 15.10 release is vulnerable.

This is my concern: apt-get obviously needs to perform DNS lookups to find out the IPs of the mirrors, and it runs as root. Am I not exposing myself to being hacked by MITM/hacked DNS server by just updating a fresh Ubuntu 15.10 install?

I.e. install, update immedately - get a trojan/rootkit/spam bot from the update.

Why haven't the images been updated sinc the discovery of the bug? Am I missing something? Are there some protection mechanisms that prevent the vulnerability from being exploited?

---

### Post by haplorrhine on 2016-02-25
Can't you bypass DNS lookup by using IP address instead of domain name?  I would change my update server and specify it by IP.

Thanks for this btw!

---

### Post by lamefun-x0r on 2016-02-25
I don't think that'll help, there are probably many background services that perform DNS lookups.

---

### Post by mörgæs on 2016-02-25
If you run ```
apt-cache policy libc6
``` and compare with the USN page to which you linked you will most likely see that the package is already updated to a fixed version. Important security bugs in Linux are always fixed fast after their discovery.

---

### Post by lamefun-x0r on 2016-02-25
> **mörgæs said:**
> Bugs in Linux are always fixed fast after their discovery.

Yes, the package in the repositories has of course been updated, but the 15.10 installation image hasn't been updated, it seems.

I don't think I can't safely update a fresh Ubuntu 15.10 installation, because the initially installed package manager is vulnerable, and there's no patched ISO for me to download.

---

### Post by haplorrhine on 2016-02-25
> **lamefun-x0r said:**
> I don't think that'll help, there are probably many background services that perform DNS lookups.

Isn't this translation done by the DNS server, after the packets leave?

---

### Post by mörgæs on 2016-02-25
> **lamefun-x0r said:**
> Yes, the package in the repositories has of  course been updated, but the 15.10 installation image hasn't been  updated, it seems.

I don't think I can't safely update a fresh Ubuntu 15.10 installation,  because the initially installed package manager is vulnerable, and  there's no patched ISO for me to download.

I have not heard of a vulnerable package manager but if it is then it will 'heal itself' by downloading a new package together with all the other packages.

Just install the ISO and update right after that, then you will be safe from the bug.

---

### Post by lamefun-x0r on 2016-02-25
> **mörgæs said:**
> I have not heard of a vulnerable package manager

According to what I've read, almost everything that uses DNS is vulnerable, since the vulnerability is in glibc.

A hacker in control of the DNS server or a computer in the middle of the connection potentially can take over applications that perform DNS lookups by sending specially crafted DNS responses.

I'm assuming that the package manager is vulnerable as well.

> **mörgæs said:**
> but if it is then it will 'heal itself' by downloading a new package together with all the other packages. Just install the ISO and update right after that, then you will be safe from the bug.

Unless I'm unlucky and happen to be attacked while I'm first updating my fresh installation. I know that the probability is probably low, but still, that's not good...

---

### Post by ian-weisser on 2016-02-25
> **lamefun-x0r said:**
> According to what I've read, almost everything that uses DNS is vulnerable, since the vulnerability is in glibc.

A hacker in control of the DNS server or a computer in the middle of the connection potentially can take over applications that perform DNS lookups by sending specially crafted DNS responses.

I'm assuming that the package manager is vulnerable as well.

The vulnerability, while real, is not a world-shaker. It would be difficult to use the exploit effectively. Not impossible, but difficult.
I can think of several easier ways to nefariously install poisoned packages onto the systems of unwary users.

The simplest workaround is to install using the 16.04 iso, which *is* patched against this vuln.
Another simple workaround is to install 15.10 offline, then edit your sources to use IP numbers instead of domain names. Then go online to upgrade to the patched versions.

---

### Post by lamefun-x0r on 2016-02-25
> **ian-weisser said:**
> The vulnerability, while real, is not a world-shaker.

Thanks for the reassurance. The news were all like: "critical", "extremely severe", "patch now", etc.

---

### Post by mörgæs on 2016-02-25
If this answers your question then please mark the thread 'solved' using Thread Tools.

---

