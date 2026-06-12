---
title: "Rkhunter error 12255 after OpenSSL after dist-upgrade to Hardy"
date: 2008-11-22
forum: Server Platforms
---

### Post by yaddoshi on 2008-11-22
Hi,

I recently performed a dist-upgrade on my server to Hardy Heron 8.04, and rkhunter has started reporting the following with each run:
```
    
Checking version of GnuPG                                [ OK ]
    Checking version of OpenSSL                              [ OK ]
[: 12255: -1: unexpected operator
[: 12255: 1: unexpected operator
    Checking version of PHP                                  [ OK ]
    Checking version of 0                                    [ Skipped ]
    Checking version of Procmail MTA                         [ OK ]
    Checking version of ProFTPd                              [ OK ]
    Checking version of OpenSSH                              [ OK ]
```
This is the first time in a long time that I have been unable to find anyone else with the same issue in the forums or elsewhere.  I am running rkhunter 1.3.0 - the only other person I found with an identical issue was running OpenBSD, so I suspect this is specifically an rkhunter issue.  Any thoughts?

---

