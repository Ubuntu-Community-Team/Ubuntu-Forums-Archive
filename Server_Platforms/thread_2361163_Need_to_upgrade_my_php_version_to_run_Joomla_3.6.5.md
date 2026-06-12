---
title: "Need to upgrade my php version to run Joomla 3.6.5, questions"
date: 2017-05-13
forum: Server Platforms
---

### Post by kostianev on 2017-05-13
Hello,

we have colocated server with **Ubuntu 11.10 version GNU/Linux 3.0.0-12-server x86_64**.

So, on this server there are hosted Joomla 1.5 which is running well, but for the new version and our new website, which is created with Joomla 3.6.5 the requirments are to have minimum php version 5.3.10, but we have 5.3.6-13ubuntu3.6.

**My question is**: Is there way to upgrade to the minimum php version, which is required with minimum application (maybe only the php) and how :confused:
_**Important**_: On this server are hosted also Wooza media server, which is streaming and VLC application with some filters, which we must have to know, before upgrade, because maybe can be some issues, which can cause?

---

### Post by SeijiSensei on 2017-05-13
> **kostianev said:**
> the requirments are to have minimum php version 3.6.10, but we have 5.3.6-13ubuntu3.6.
That contains PHP 5.3.6 which is far beyond the minimum 3.6.10.  The numbers around "ubuntu" have to do with which build of 5.3.6 is contained in the package.

I will begin the chorus of comments telling you that 11.10 is far beyond its end-of-support date, and that no server should be running anything other than an LTS version of Ubuntu like 16.04 or 14.04.  Those have five years of support; all other releases are only supported for nine months.

---

### Post by kostianev on 2017-05-13
Sorry, I mean Joomla 3 requires php version 5.3.10, not 5.6.10 it's mistake.
I know, that our Ubuntu is old, but we have Wooza media server and VLC with few custum written scripts and we`re afraid of upgrades.

So we have 5.3.6-13 and only need to upgrade the php to 5.3.10.

---

