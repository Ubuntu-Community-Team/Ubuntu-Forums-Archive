---
title: "Linux Kernel Security Threat"
date: 2018-09-27
forum: Security
---

### Post by bionic3epl on 2018-09-27
Is Ubuntu 18.04.1 Protected from this security threat described here?> [https://www.darkreading.com/vulnerabilities---threats/critical-linux-kernel-flaw-gives-root-access-to-attackers/d/d-id/1332906?_mc=rss_x_drr_edt_aud_dr_x_x-rss-simple](https://www.darkreading.com/vulnerabilities---threats/critical-linux-kernel-flaw-gives-root-access-to-attackers/d/d-id/1332906?_mc=rss_x_drr_edt_aud_dr_x_x-rss-simple)

---

### Post by howefield on 2018-09-27
Ubuntu 18.04.1 uses the 4.15 kernel series, not listed as being vulnerable here.. [https://people.canonical.com/~ubuntu-security/cve/2018/CVE-2018-14634.html](https://people.canonical.com/~ubuntu-security/cve/2018/CVE-2018-14634.html)

---

### Post by bionic3epl on 2018-09-27
> **howefield said:**
> Ubuntu 18.04.1 uses the 4.15 kernel series, not listed as being vulnerable here.. [https://people.canonical.com/~ubuntu-security/cve/2018/CVE-2018-14634.html](https://people.canonical.com/~ubuntu-security/cve/2018/CVE-2018-14634.html)

On that Webpage, what's DNE stand for?

---

### Post by deadflowr on 2018-09-27
Does Not Exist

---

### Post by bionic3epl on 2018-09-27
Thanks :biggrin:

---

### Post by howefield on 2018-09-27
As deadflowr said it means that particular package does ot exist within that series.

eg, the package linux-mako does not exist in any version other than 14.04 and 16.04 where it has been marked as abandoned. 
```
Package
Source: linux-mako (LP Ubuntu Debian)
Upstream:	released (4.13~rc1)
Ubuntu 12.04 ESM (Precise Pangolin):	DNE
Ubuntu 14.04 LTS (Trusty Tahr):	ignored (abandoned)
Ubuntu 16.04 LTS (Xenial Xerus):	ignored (abandoned)
Ubuntu 18.04 LTS (Bionic Beaver):	DNE
Ubuntu 18.10 (Cosmic Cuttlefish):	DNE
```

---

### Post by SagaciousKJB on 2018-10-02
> **howefield said:**
> As deadflowr said it means that particular package does ot exist within that series.

eg, the package linux-mako does not exist in any version other than 14.04 and 16.04 where it has been marked as abandoned. 
```
Package
Source: linux-mako (LP Ubuntu Debian)
Upstream:	released (4.13~rc1)
Ubuntu 12.04 ESM (Precise Pangolin):	DNE
Ubuntu 14.04 LTS (Trusty Tahr):	ignored (abandoned)
Ubuntu 16.04 LTS (Xenial Xerus):	ignored (abandoned)
Ubuntu 18.04 LTS (Bionic Beaver):	DNE
Ubuntu 18.10 (Cosmic Cuttlefish):	DNE
```

Any idea how this affects 4.13 in 16.04? I have that version held since 4.15 breaks support for my nvidia driver.

---

