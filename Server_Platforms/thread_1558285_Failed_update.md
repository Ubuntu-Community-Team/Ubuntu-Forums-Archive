---
title: "Failed update"
date: 2010-08-22
forum: Server Platforms
---

### Post by robbrandt on 2010-08-22
I am attempting to update from 8.04 to 10 LTS.  After updating to the latest 8.04 I did

sudo do-release-upgrade --devel-release

It ran well until it asked about differences between etc/services.  It gave me an option to view the differences, which I did, but it then did not prompt for a choice after that.  Not knowing what else to do I did ctrl-c; the upgrade continued and I thought it was successful.  However by all indications I am still on 8.04.

I tried to run the upgrade again, but the script remembers my previous input choice (D) for the etc/services issue and fails, aborting the upgrade.

How do I force it to ask for a new choice here?  Any other advice?

---

