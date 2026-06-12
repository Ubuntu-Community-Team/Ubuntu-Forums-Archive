---
title: "Dansguardian ClamAV dependency"
date: 2009-03-24
forum: Security
---

### Post by sbcontt on 2009-03-24
I normally use Avast free on-demand scanner. Today I installed WebStrict(Dansguardian frontend) in my Intrepid amd64 & ClamAV was installed as a prerequisite. It seems Dansguardian is supposed to scan web traffic with clamav. 
My first question: does Dansguardian really scan web traffic with clamav without dazuko kernel?

The installed ClamAV is an outdated version. When I updated it using  $ sudo freshclam  it said
```
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.94.2 Recommended version: 0.95
DON'T PANIC! Read http://www.clamav.net/support/faq
main.cld is up to date (version: 50, sigs: 500667, f-level: 38, builder: sven)
daily.cvd is up to date (version: 9156, sigs: 33303, f-level: 41, builder: guitar)
```
Second question: Will updating ClamAV to latest version make it incompatible with Dansguardian or break the integrity?
:confused::confused::confused:

---

