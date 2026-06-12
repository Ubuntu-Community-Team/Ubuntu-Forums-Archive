---
title: "Audacity freezes when loading project"
date: 2009-08-10
forum: Ubuntu Studio
---

### Post by mjrmua on 2009-08-10
When I load certain projects in audacity, audacity will appear to load the project correctly but won't respond to any button presses.

This seems to  only happen with some projects (created with the same version of audactiy)

Has anyone else seens this?
Is there any way to enable debugging output from audactiy so I can try isolate the cause or the problems

---

### Post by sgx on 2009-08-13
> **mjrmua said:**
> When I load certain projects in audacity, audacity will appear to load the project correctly but won't respond to any button presses.

This seems to  only happen with some projects (created with the same version of audactiy)

Has anyone else seens this?
Is there any way to enable debugging output from audacity so I can try isolate the cause or the problems

Hi, for me, audacity works fine until there is too little diskspace for its temp files, or when there is too little memory available. And it is good luck to work off a fresh boot, not after an internet session.
If you start it from a terminal, there may be output available when things go belly up. There is also a 'tail' command people use to track and compare system events, and then check the logs in  /var, you can google up the syntax for using tail. Is there a chance some projects were from a different version of audacity? It's easy to revert back for awhile if it's a special project Cheers

---

