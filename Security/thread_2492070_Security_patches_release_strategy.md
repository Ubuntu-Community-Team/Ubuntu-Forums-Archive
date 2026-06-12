---
title: "Security patches release strategy?"
date: 2023-10-29
forum: Security
---

### Post by koval.roma on 2023-10-29
Hello, 

On my **Ubuntu 20.04.6 LTS**, multiple vulnerabilities with **Critical** status were detected by the Wazuh scanner. 

For example:
[https://ubuntu.com/security/CVE-2022-28734](https://ubuntu.com/security/CVE-2022-28734)
[https://ubuntu.com/security/CVE-2022-28734](https://ubuntu.com/security/CVE-2022-28734)
[https://ubuntu.com/security/CVE-2016-1585](https://ubuntu.com/security/CVE-2016-1585)
[https://nvd.nist.gov/vuln/detail/CVE-2022-48174](https://nvd.nist.gov/vuln/detail/CVE-2022-48174)
[https://ubuntu.com/security/CVE-2016-1585](https://ubuntu.com/security/CVE-2016-1585)

And some others. 

Some of them exist for more than three months. 

I have also installed **RHEL 8.8**, where Wazuh shows 0 Critical CVE.

Is it a normal situation for Ubuntu? I have always thought that when a critical CVE is identified, it should be patched as thoroughly and quickly as possible.

---

### Post by ian-weisser on 2023-10-29
Let's not jump to conclusions.

None of those CVEs, upon inspection by the Ubuntu Security Team, are Critical to Ubuntu.
All are Medium according to the links you provided...or Fix Released ([https://ubuntu.com/security/cves?q=CVE-2022-48174](https://ubuntu.com/security/cves?q=CVE-2022-48174))

If you believe that a CVE has been misjudged, or that you have seen an exploit for one of them in the wild, please discuss with the Ubuntu Security Team directly (not here).

Discussion of the general theory of how patching and updates are pushed is appropriate for here.
As are general complaints about the perfidity of many commercial scanners.

---

