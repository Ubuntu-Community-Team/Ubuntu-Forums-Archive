---
title: "Security Failure [exim] and negligence"
date: 2021-05-04
forum: Security
---

### Post by keathmon on 2021-05-04
If I'm understanding the reality here, exim put out notification over the last 6 months to many issues.
Ubuntu decided not to address those for 16.04 LTS and only announced 2 days after going in to ESM that they will not put out an update.
A lot of admins made choices on migration and the need to move off 16.04 based on the time ESM would give us to safely migrate.

Absolutely disappointed in all involved and feel I can no longer trust this distro on the security front.

~K

---

### Post by alexmurray on 2021-05-04
This is incorrect (assuming you are talking about the Exim vulnerabilities announced [here]("https://www.openwall.com/lists/oss-security/2021/05/04/6") and fixed in regular Ubuntu releases via [USN-4934-1]("https://ubuntu.com/security/notices/USN-4934-1")).

The Ubuntu Security team got 7 days notice ahead of time before these vulnerabilities were announced publicly and 16.04 LTS transitioned to ESM in that timeframe - over these 7 days we started preparing the updates which were covered in USN-4934-1 and we are in the process of preparing an equivalent update for exim4 in 16.04 ESM which should be available in the next day or so I suspect. This takes a bit longer than the other releases as this code base is now over 5 years old so backporting the patches takes more effort, but this is actively being worked on and should be available to 16.04 ESM users soon. As 16.04 ESM includes security support for all high and critical CVEs that affect packages in main in 16.04 you can rest assured this will be supported so I think your claims are quite unfounded.

---

