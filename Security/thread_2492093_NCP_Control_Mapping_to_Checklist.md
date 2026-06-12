---
title: "NCP Control Mapping to Checklist"
date: 2023-10-30
forum: Security
---

### Post by joe-murray on 2023-10-30
TL;DR Is there an Ubuntu set of Checklists for best practices for the various security controls required to meet common standards like NIST 800-53, SOC 2 and ISO 27001 ?

Many orgs want to do security right but don't have the capacity to develop expertise in all areas of security related to their servers. Checklists, as starting points, can be immensely helpful. For example, [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812) and the other sticky posts in [https://ubuntuforums.org/forumdisplay.php?f=338](https://ubuntuforums.org/forumdisplay.php?f=338). 

 I recently came across [https://ncp.nist.gov/cmc?focalDocId=3&checklistId=980&isIntersect=true&isDoesNotIntersect=true](https://ncp.nist.gov/cmc?focalDocId=3&checklistId=980&isIntersect=true&isDoesNotIntersect=true) which is great as a starting point for organizations that would like to be compliant and demonstrate to auditable levels their compliance with various standards including security controls like NIST 800-53 ([https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final)), SOC 2 and ISO 27001. There are checklists for RHEL 7 and RHEL 8 but none for Ubuntu that list control areas and provide checklists for them.

We have one RHEL 8 server, a half dozen Debian servers, and a few dozen Ubuntu LTS servers. Are there any similar documents, especially officially recognized ones, that provide checklists for security controls in official standards for Ubuntu?

---

### Post by TheFu on 2023-11-06
[https://ubuntu.com/blog/disa-has-released-the-ubuntu-20-04-lts-stig-benchmark](https://ubuntu.com/blog/disa-has-released-the-ubuntu-20-04-lts-stig-benchmark)

They often run 2+ yrs behind each release and sometimes they don't support any sub-release besides the initial or the .1 release.
"STIG" is the search term.

But no checklist blindly followed can replace system and security knowledge. Most of us don't have 1000 identical systems.  Be have 5 to hundreds of snowflake systems, each slightly different.  We are expected to apply security using our requirements and likely attack vectors, not blindly.

---

