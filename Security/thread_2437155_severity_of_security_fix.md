---
title: "severity of security fix"
date: 2020-02-19
forum: Security
---

### Post by goeldi on 2020-02-19
Is there something like the severity tag in yum upgrades for apt?
In yum, any security fix has a severity of "low", "important" or "critical".
In apt I cannot find anything like this.

On a RedHat system the command "yum updateinfo list --security" gives output like this:

[FONT=courier new]RHSA-2020:0374              **Important**/Sec. python-perf-3.10.0-1062.12.1.el7.x86_64[/FONT]
[FONT=courier new]FEDORA-EPEL-20 **Low**/Sec.       python2-pip-8.1.2-12.el7.noarch
RHSA-2020:0374              **Critical**/Sec.  kernel-3.10.0-1062.12.1.el7.x86_64[/FONT]
[FONT=courier new]RHSA-2020:0227              **Important**/Sec. sqlite-3.7.17-8.el7_7.1.x86_64[/FONT]

---

### Post by EuclideanCoffee on 2020-02-19
Typically Debian, where Ubuntu pulls security and patches (especially in universe branch), builds security patches for CVEs publicly announced: see [https://www.debian.org/security/faq#handling](https://www.debian.org/security/faq#handling).

Ubuntu naturally then follows a similar flow of patches, providing patches to CVEs when made known, and they will prioritize CVEs.

[https://usn.ubuntu.com/](https://usn.ubuntu.com/)

I've noted in the past the RHEL and Ubuntu patches differently. Where RHEL allows you to decide on which patch to install, Ubuntu generally expects system administrations to decide for themselves.

If you are looking to provide an enterprise solution for Ubuntu patching, I know a lot of architecture that I can describe in detail if needed. For example, I use mirrors to prioritize certain patches and to make others unavailable.

---

