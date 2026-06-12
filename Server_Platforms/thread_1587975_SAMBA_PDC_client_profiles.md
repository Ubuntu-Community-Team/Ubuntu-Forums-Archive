---
title: "SAMBA PDC client profiles"
date: 2010-10-04
forum: Server Platforms
---

### Post by alex_l on 2010-10-04
First of all, sorry for my English.

I am searching solution for one problem. I need to set up server Samba PDC where users have local domain accounts on client computers, but also restrict some functionality for this user as this solution will be in school. So I made NTconfig.pol and placed to netlogon directory. So the problem is - if I use logon path to server profiles, where actualy is no real profile client machine make new temporary profile and use my NTCONFIG.POL. Unfortunately it is not OK for me because after  log-off all data in profile is lost. If I use local profile (logon path = ) then my NTCONFIG.POL is not used. Can I get to work both, local profile and NTCONFIG.POL?

---

