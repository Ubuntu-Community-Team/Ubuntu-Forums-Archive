---
title: "Is kernel vulnerabilities applicable for nonexistent hardware device ?"
date: 2020-07-08
forum: Security
---

### Post by compete2cooperate on 2020-07-08
**General Question**: Is kernel vulnerabilities related  to a specific hardware device driver still applicable if that device  specific to the vulnerability is not installed / not present ?.
 **A specific version of the same question:** I found that [CVE-2019-15925]("https://people.canonical.com/%7Eubuntu-security/cve/2019/CVE-2019-15925")  is applicable for the version of Kernel that we are using but could not  find any hardware which use Hisilicon HNS3 ethernet device driver. Is  the vulnerability still applicable ?

---

### Post by EuclideanCoffee on 2020-07-08
Any vulnerability could be exploited. The safest response is to patch your kernel using Ubuntu's LTS release.

---

### Post by CharlesA on 2020-07-08
If that device is not present, normally the kernel modules are not loaded, so it is unlikely you would be affected.

However, as EuclideanCoffee said, ensure your system is patched. You don't necessarily need to use a LTS version of Ubuntu, but that is supported for longer than the normal 6 month releases.

---

