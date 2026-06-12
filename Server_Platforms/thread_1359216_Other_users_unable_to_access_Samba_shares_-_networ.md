---
title: "Other users unable to access Samba shares - network path not found"
date: 2009-12-19
forum: Server Platforms
---

### Post by CharlesA on 2009-12-19
Hi all,

I upgraded my server to Ubuntu 9.10 from 9.04 (clean install of 9.10), copied smb.conf from the old install to the new, set the Samba passwords. No permissions have changed but I can see the shares listed. However, if any other user besides me tries to access the shares, they get "network path not found."

I do not believe it is a permissions problem, but I don't know what is causing it to behave like this.

I'm running Samba 3.40 on Webmin 1.5 on Ubuntu Server 9.10.

Any help is appreciated. :)

---

### Post by Puck7 on 2009-12-19
Are the workgroups the same on all computers? Didn't the upgrade to the new version of samba change the previous settings, or maybe there are some new settings in the new version? Maybe these question can help you find  the answer (:

---

### Post by CharlesA on 2009-12-19
> **Puck7 said:**
> Are the workgroups the same on all computers? Didn't the upgrade to the new version of samba change the previous settings, or maybe there are some new settings in the new version? Maybe these question can help you find  the answer (:

The workgroups are the same, but I overwrote the default smb.conf file (that came with the new install) with the old smb.conf, so that might have screwed it up, I'm not sure.

I'm rolling back to 9.04 and I'll do more testing in a VM before rolling it out again.

---

### Post by CharlesA on 2009-12-19
Turns out it was a permission problem. That's what I get for changing around uid's. *cough*

Working now! :D

---

