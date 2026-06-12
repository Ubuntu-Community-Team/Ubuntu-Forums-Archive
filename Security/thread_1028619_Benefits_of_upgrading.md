---
title: "Benefits of upgrading?"
date: 2009-01-02
forum: Security
---

### Post by adam35413 on 2009-01-02
I am currently running a production server on an Ubuntu 7.10 server.  I make sure that the server automatically updates all security related areas, and I periodically do manual aptitude safe-upgrades.  However, I ran an automated N-Stalker pen-test, and got back several "critical" issues relating to old versions of apache2, php5, etc.  Is this just an artifact of using the standard Ubuntu distributions of php5 and apache2, or are there real security threats if I am not on an LTS version such as 8.04?

---

### Post by HermanAB on 2009-01-02
If you applied the security patches then you should be fine.

Most security issues on Linux are due to having bad quality passwords, enabling hackers to log in via SSH or FTP, or sometimes they break in via a bad quality forum program written in PHP.

So, keep strong passwords of 9 characters or more and use iptables rate limiting filter to guard against brute force and DOS attacks  - then you should be fine.

Cheers,

Herman

---

### Post by cdenley on 2009-01-02
I'm not familiar with that particular test, but it probably only checks the version you are running, and checks for vulnerabilities that were found after the official release of that software. Most likely the "problems" listed by that test have been patched by ubuntu's package maintainers, even though the patches weren't available when that version was released.

I think the security is the same regardless of whether you use an LTS release or not, as long as the release is still supported, of course.

---

