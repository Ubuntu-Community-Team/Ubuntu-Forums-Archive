---
title: "Latest update asks to install unattended upgrades"
date: 2019-05-09
forum: Security
---

### Post by adrienkennebec on 2019-05-09
The last time the update program popped up, i let it install updates and then a dialogue opened up asking me to set up unattended upgrades. By what I understand that would only happen if I installed the unattended-upgrades package. I was a little bit concerned because it was kind of weird. 

Has this happened to anyone else? I hope it's a normal update.

---

### Post by Xian on 2019-05-09
The Update Manager can be configured on its own to install unattended security upgrades. 

It does not require the need of the unattended-upgrades package. 

Some other methods are outlined here: [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates).

---

### Post by mikewhatever on 2019-05-10
The unattended-upgrade package is preinstalled. There is nothing weird about it or its updates.

---

### Post by again? on 2019-05-10
...and to continue on it relies on your update strategy.
> This script is the backend for the APT::Periodic::Unattended-Upgrade
 option.

---

