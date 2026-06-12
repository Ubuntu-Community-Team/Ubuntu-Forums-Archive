---
title: "CVE Security golang package ubuntu 20.04"
date: 2023-10-03
forum: Ubuntu, Linux and OS Chat
---

### Post by slashlinux on 2023-10-03
[COLOR=#232629][FONT=-apple-system]an anyone help me to find and update the package for **golang on ubuntu 20.04** ? After trivy image container scanner found some HIGH cve security but searching on the ubuntu I dont have these packages:[/FONT][/COLOR]
> golang.org/x/text   &#9474; CVE-2021-38561 &#9474; HIGH     &#9474;        &#9474; 0.3.0                             &#9474; 0.3.7                      
golang.org/x/net    &#9474; CVE-2019-9512  &#9474; HIGH     &#9474;        &#9474; 0.0.0-20190404232315-eb5bcb51f2a3 &#9474; 0.0.0-20190813141303-74dc4d7220e7
golang.org/x/crypto &#9474; CVE-2020-29652 &#9474; HIGH     &#9474; fixed  &#9474; 0.0.0-20190308221718-c2843e01d9a2 &#9474; 0.0.0-20201216223049-8b5274cf687f 


> 

root@589417322bdb:/# apt-cache search golang.org/x/text
root@589417322bdb:/# 

root@589417322bdb:/# apt install golang.org/x/text
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package golang.org/x

---

### Post by ian-weisser on 2023-10-03
Keep in mind that....

1) A stock install of Ubuntu pulls security updates 2-4 times daily completely automatically and without notifying you.
2) Most scanners return a LOT of false positives.

...so you need to check each hit to make sure the vulnerability still exists. Many vulnerabilities are mitigated before the scanner runs.


Step 1: Check each CVE at the Ubuntu Security Team CVE Tracker: [URL="https://ubuntu.com/security/cves"]https://ubuntu.com/security/cves
[/URL]            That will also tell you the correct package name.

---

