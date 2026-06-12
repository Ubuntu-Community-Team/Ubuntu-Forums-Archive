---
title: "Understanding Apparmor and Auditd"
date: 2019-03-22
forum: Security
---

### Post by espressobeanie on 2019-03-22
I'm noticing that both Apparmor and Auditd use the /var/log/audit/audit.log file to write violations to and I'm trying to see if this is intentional and whether these two programs have some relation to one another given their default log file location.

---

### Post by joegry on 2019-04-20
This is intentional as explained in the apparmor man page. Checkout the section under the heading ERRORS  [http://manpages.ubuntu.com/manpages/xenial/en/man7/apparmor.7.html](http://manpages.ubuntu.com/manpages/xenial/en/man7/apparmor.7.html)

---

