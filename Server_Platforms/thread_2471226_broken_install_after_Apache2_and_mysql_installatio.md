---
title: "broken install after Apache2 and mysql installation on Ubuntu 20.04"
date: 2022-01-24
forum: Server Platforms
---

### Post by arimann on 2022-01-24
i have a broken install after Apache2 and mysql installation on Ubuntu 20.04.

i am trying to get updates and upgrades with :

**sudo apt update and   **[B]sudo apt upgrade

and the result is :  [/B]dbconfig-mysql : Depend: default-mysql-client : but not installed or default-mysql-client .

**It seems to be **[COLOR=#232629][FONT=-apple-system]because of the [/FONT][/COLOR]**ppa ondrej**[COLOR=#232629][FONT=-apple-system] file in the installation of apache2 and mysql.

[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]Is there something to do,please?[/FONT][/COLOR]

---

### Post by schragge on 2022-01-24
So, what Apache2 are you using? The one from official Ubuntu repos or that from Ond&#345;ej's PPA? If the latter, have you seen this notice in the PPA description:
> IMPORTANT: The <foo>-backports is now required on older Ubuntu releases.
That means **focal-backports** must be enabled in order to be able to use Apache2 from the PPA.

---

### Post by howefield on 2022-01-24
Thread moved to the "*Server Platforms*" forum.

---

