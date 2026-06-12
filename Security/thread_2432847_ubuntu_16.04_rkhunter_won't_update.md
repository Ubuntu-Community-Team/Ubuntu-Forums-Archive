---
title: "ubuntu 16.04 rkhunter won't update"
date: 2019-12-09
forum: Security
---

### Post by dave219 on 2019-12-09
hello team:

i am trying to get rthunter updated but failed to do so:

**user@host**:[COLOR=#3200ca]**~**[/COLOR]$ sudo rkhunter --update


[sudo] password for user: 
[ Rootkit Hunter version 1.4.2 ]


**Checking rkhunter data files...**
  Checking file mirrors.dat                                  [ **Skipped** ]
  Checking file programs_bad.dat                             [ **No update** ]
  Checking file backdoorports.dat                            [ **No update** ]
  Checking file suspscan.dat                                 [ **No update** ]
  Checking file i18n/cn                                      [ **No update** ]
  Checking file i18n/de                                      [ **No update** ]
  Checking file i18n/en                                      [ **No update** ]
  Checking file i18n/tr                                      [ **No update** ]
  Checking file i18n/tr.utf8                                 [ **No update** ]
  Checking file i18n/zh                                      [ **No update** ]
  Checking file i18n/zh.utf8                                 [ **No update** ]
**user@host**:[COLOR=#3200ca]**~**[/COLOR]$  lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.6 LTS
Release:	16.04
Codename:	xenial


tried it on another VM (centOS7) and it works fine. 


what did i do wrong?


thanks


_dave

---

