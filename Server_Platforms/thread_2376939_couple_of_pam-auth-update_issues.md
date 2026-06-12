---
title: "couple of pam-auth-update issues"
date: 2017-11-07
forum: Server Platforms
---

### Post by taliosfalcon on 2017-11-07
I've been trying to configure ubuntu 14.04 and 16.04 to authenticate against a freeipa server, and it's been working fine, except for two small quirks, 
in pam-auth-update. If i select Unix authentication AND SSS authentication simultaneously (which I want) SSS password changes no longer work, due to token manipulation errors, turn off unix auth and it works fine, 


secondly and more important issue; I have "Create home directory on login" selected, and it creates the directory in /home with all the proper permissions and ownership as far as I can see, but the account doesnt' seem to actually be associated with it, no history, can't autofill commands with tab etc. So far I haven't been able to find any issues in any logs. Anyone know what could be causing this or have any pointers on where I should start investigating?

---

