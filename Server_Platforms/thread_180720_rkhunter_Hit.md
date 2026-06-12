---
title: "rkhunter Hit"
date: 2006-05-22
forum: Server Platforms
---

### Post by cssutto on 2006-05-22
When I run rkhunter, I get the following message, but I can not find this file so I have no idea what to do about it.

* Application version scan
gpg: WARNING: unsafe ownership on configuration file `/home/claude69694/.gnupg/g pg.conf'
   - GnuPG 1.4.1                                              [ Old or patched v ersion ]
   - Procmail MTA 3.22                                        [ OK ]


What do I do about it?



CSSJR

---

### Post by RavenOfOdin on 2006-05-23
That'll happen if you've installed or used GnuPG for the first time recently.

You'll want to chown your GnuPG directory to root:root (or at least gpg.conf)

Files with "." in front of them are hidden, so go into your file manager (Nautilus/Konqueror) and click "Show Hidden Files" in the View tab.

---

