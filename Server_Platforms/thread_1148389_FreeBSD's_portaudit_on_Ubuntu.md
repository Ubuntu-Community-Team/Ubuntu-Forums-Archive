---
title: "FreeBSD's portaudit on Ubuntu?"
date: 2009-05-04
forum: Server Platforms
---

### Post by djteej on 2009-05-04
FreeBSD's portaudit checks installed packages for known vulnerabilities and generates reports including references to security advisories.

Has anyone managed to port this package for Ubuntu or does anyone know of an equivalent for Ubuntu?  This package is an excellent addition, especially for production servers.

---

### Post by windependence on 2009-05-04
Unfortunately I don't think there's anything like that for Linux. Why not just run FreeBSD? That would be my preference. I only run Linux when necessary.

-Tim

---

### Post by djteej on 2009-05-07
I was reading the Ubuntu Documentation and found the following:

[INDENT]"Another useful package is apticron. apticron will configure a cron job to email an administrator information about any packages on the system that need updated as well as a summary of changes in each package."[/INDENT]

I haven't had the opportunity to evaluate this as of yet, but it sounds promising.

---

### Post by windependence on 2009-05-07
Good deal, and good luck!

-Tim

---

### Post by dreamgear on 2009-09-21
Hi.  I'm posting under this thread because I am also looking for portaudit-like functionality. 

Part of the value proposition for Jeos and the LTS releases is "fewer updates".  But what is the best way to determine when in fact there is a critical (particularly security-related) update?

---

### Post by FakeOutdoorsman on 2009-09-21
> **dreamgear said:**
> Hi.  I'm posting under this thread because I am also looking for portaudit-like functionality. 

Part of the value proposition for Jeos and the LTS releases is "fewer updates".  But what is the best way to determine when in fact there is a critical (particularly security-related) update?

I subscribe to the security mailing list of another distribution and your equivalent would be [ubuntu-security-announce](https://lists.ubuntu.com/archives/ubuntu-security-announce/).  This notifies me of any security update and then I upgrade the system manually.  I upgrade manually because certain package upgrades may disrupt my system.

If you prefer RSS, Ubuntu has that option as well at [Ubuntu Security Notices](http://www.ubuntu.com/usn).

---

### Post by wigwam47 on 2011-03-30
apticron and rss are good, but to save one's time it would be better to see ONLY security issues (not all upgradable packages) and ONLY issuses of installed packages (not all ubuntu packages) - just like portaudit works.

still not found any sw with similar funcionality?

---

