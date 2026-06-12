---
title: "Versions and how they are named"
date: 2008-03-25
forum: Security Discussions
---

### Post by eisublime on 2008-03-25
I have a question regarding reading the "fixed in" versions for security and bug reports.  Here's an example so that you can understand what I'm talking about.

[http://nvd.nist.gov/nvd.cfm?cvename=CVE-2007-3382](http://nvd.nist.gov/nvd.cfm?cvename=CVE-2007-3382) describes a vulnerability in tomcat.  I'm running tomcat5.5 so I went down to 

External Source:   DEBIAN  (disclaimer)
Name: DSA-1447
Hyperlink: [http://www.debian.org/security/2008/dsa-1447](http://www.debian.org/security/2008/dsa-1447)

to get information on how to patch my system.  on that page it says:

For the stable distribution (etch), these problems have been fixed in version 5.5.20-2etch1.

I'm running version 5.5.20-4ubuntu1.  the -4 makes me think that this vulnerability is fixed since it was fixed in -2, but does etch vs ubuntu matter?  and is my assumption about the numbers correct?  I'm running dapper if that matters.

Thanks!

---

### Post by Oldsoldier2003 on 2008-03-25
> **eisublime said:**
> I have a question regarding reading the "fixed in" versions for security and bug reports.  Here's an example so that you can understand what I'm talking about.

[http://nvd.nist.gov/nvd.cfm?cvename=CVE-2007-3382](http://nvd.nist.gov/nvd.cfm?cvename=CVE-2007-3382) describes a vulnerability in tomcat.  I'm running tomcat5.5 so I went down to 

External Source:   DEBIAN  (disclaimer)
Name: DSA-1447
Hyperlink: [http://www.debian.org/security/2008/dsa-1447](http://www.debian.org/security/2008/dsa-1447)

to get information on how to patch my system.  on that page it says:

For the stable distribution (etch), these problems have been fixed in version 5.5.20-2etch1.

I'm running version 5.5.20-4ubuntu1.  the -4 makes me think that this vulnerability is fixed since it was fixed in -2, but does etch vs ubuntu matter?  and is my assumption about the numbers correct?  I'm running dapper if that matters.

Thanks!

Ubuntu does its own security patches. though they are "kissing cousins" they are not the same distro

---

### Post by eisublime on 2008-03-25
Hmm, I see.  Ok, so how can I find out if that particular vulnerability has been addressed?

---

### Post by Oldsoldier2003 on 2008-03-25
> **eisublime said:**
> Hmm, I see.  Ok, so how can I find out if that particular vulnerability has been addressed?
you could sign up for the security mailing list:
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

---

### Post by cdenley on 2008-03-25
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)
[http://changelogs.ubuntu.com/changelogs/pool/universe/t/tomcat5/tomcat5_5.0.30-9/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/t/tomcat5/tomcat5_5.0.30-9/changelog)
[http://changelogs.ubuntu.com/changelogs/pool/universe/t/tomcat5.5/tomcat5.5_5.5.25-1ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/t/tomcat5.5/tomcat5.5_5.5.25-1ubuntu1/changelog)
You're running dapper with tomcat 5.5?

---

### Post by eisublime on 2008-03-25
Wow, that USN list is great, thank you very much.  
Yes, I'm running tomcat5.5
$ dpkg -l | grep tomcat5.5
ii  libtomcat5.5-java                    5.5.20-4ubuntu1              Java Servlet engine -- core libraries
ri  tomcat5.5                            5.5.20-4ubuntu1              Servlet and JSP engine

on dapper
$ uname -r
2.6.20-15-server
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

It looks like CVE-2007-3382 and CVE-2007-3385 are not listed, does that mean that they have not been addressed?

---

### Post by cdenley on 2008-03-25
Apparently not. I haven't looked up those vulnerabilities, but often there are vulnerabilities that can only be exploited if somebody writes sloppy web scripts, so they don't get patched. It doesn't look like tomcat5.5 is in the dapper repository, so you might want to install the "officially supported for dapper" package.

It looks like hardy will have tomcat 5.5.25, so maybe you should wait for that, or use the [beta]("http://www.ubuntu.com/testing") release.

---

### Post by eisublime on 2008-03-25
Hmm, ok.  Pardon the noob question, but how do I find out the officially supported for dapper release?  Thanks very much for your help by the way.

---

### Post by cdenley on 2008-03-25
```

sudo dpkg -P tomcat5.5 libtomcat5.5
sudo apt-get install tomcat5

```
Unless I'm completely misreading something, you couldn't have installed tomcat5.5 on dapper with apt unless you configured another repository in sources.list. If you install everything with apt from the default repositories, then it should all be compatible and supported, and you will be able to install periodic security updates.

---

### Post by eisublime on 2008-03-25
Interesting, you know now that I'm thinking about it, I don't know if I was actually the one who installed tomcat5.5 on there.  I'm going to have to do some digging, thanks very much for your help.

---

