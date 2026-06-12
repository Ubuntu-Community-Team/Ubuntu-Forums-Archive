---
title: "Upgrade from 9.04 to 9.10"
date: 2009-11-03
forum: Server Platforms
---

### Post by expatCM on 2009-11-03
I wish to upgrade my server to 9.10.  Apparently sudo apt-get dist-upgrade is not going to work.

There seem to be rather mixed suggestions as to what will work. 

What is the preferred approach?

The following instructions seem to enjoy some support but I do not understand the third step......

> 1. Run: apt-get install update-manager-core

2. Then: nano /etc/update-manager/release-upgrades

2.1. Change Prompt=lts to Prompt=normal

3. Finally run: do-release-upgrade

---

### Post by mrsteveman1 on 2009-11-03
Yep, sounds about right.

Open a terminal window and type "sudo do-release-upgrade" and follow what it says.

---

### Post by expatCM on 2009-11-03
ok ... thank you ....  I will press a few buttons and see what happens then ...

---

