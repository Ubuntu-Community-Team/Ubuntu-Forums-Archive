---
title: "Upgrading from Jaunty"
date: 2011-10-05
forum: Server Platforms
---

### Post by Sajjen on 2011-10-05
I've just recently been given responsibility for a server running Ubuntu 9.04. Is there any way to upgrade this to a newer version without doing a full reinstallation? `do-release-upgrade` gives me "An upgrade from 'jaunty' to 'lucid' is not supported with this tool." and the karmic repositories are no longer available.

---

### Post by lcman on 2011-10-05
> **Sajjen said:**
> I've just recently been given responsibility for a server running Ubuntu 9.04. Is there any way to upgrade this to a newer version without doing a full reinstallation? `do-release-upgrade` gives me "An upgrade from 'jaunty' to 'lucid' is not supported with this tool." and the karmic repositories are no longer available.

You can't upgrade from jaunty to natty directly, not with the do-release-upgrade tool at least. You should upgrade to lucid first and then to natty if you want but I'd recommend lucid over natty for a server because of LTS.

OR, you could try editing /etc/apt/sources.list and change every "jaunty" to "natty" and:
```
apt-get update && apt-get upgrade
```

Also, take a look at documentation:
```
https://help.ubuntu.com/community/UpgradeNotes
```

---

### Post by Bucky Ball on 2011-10-05
Long-term support releases are recommended for servers (5 years support as opposed to 18 months). 10.04 LTS is current, stable, and supported until April 2015. 

Icman, Natty is not mentioned, the error is "An upgrade from 'jaunty' to 'lucid' is not supported with this tool." Lucid is 10.04.

Sajjen; I would backup the valuables and bite the bullet. Install the LTS release. The other reason is that LTS releases will upgrade with a couple of clicks to the next LTS release, unlike your current situation, so you'll only have to do this once (in theory!).

---

### Post by Sajjen on 2011-10-05
I upgraded to karmic via this: [https://help.ubuntu.com/community/Upgrades#Upgrades_via_alternate_CD](https://help.ubuntu.com/community/Upgrades#Upgrades_via_alternate_CD)

The plan is to upgrade to lucid (LTS) and then wait for 12.04 before upgrading again.

EDIT: Upgrade to lucid went fine, I can now safely await 12.04.

---

### Post by Bucky Ball on 2011-10-07
Good news and well done! ;)

12.04 LTS will be supported until April 2015.

---

