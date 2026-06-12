---
title: "Can't access QA Tracker"
date: 2014-10-30
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-10-30
Just trying to report a test result and I get 403 Forbidden trying to access:

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

The page just says:

> Forbidden

You don't have permission to access / on this server.
Apache/2.2.14 (Ubuntu) Server at iso.qa.ubuntu.com Port 80

Do others get that as well?

---

### Post by Elfy on 2014-10-30
yes - it's down.

IS are aware - it will be up again.

---

### Post by kansasnoob on 2014-10-30
> **Elfy said:**
> yes - it's down.

IS are aware - it will be up again.

Thanks. I'd been mucking about quite a bit with my LAN so thought I may have borked something on my end.

---

### Post by Elfy on 2014-10-30
[https://lists.ubuntu.com/archives/ubuntu-quality/2014-October/005635.html](https://lists.ubuntu.com/archives/ubuntu-quality/2014-October/005635.html)


> 
The iso, package and hardware trackers along with the site are all down and
with no current ETA. The sites are offline in response to "drupalgeddon"
which has affected many drupal sites. The Drupal project recommends
rebuilding all sites and restoring all drupal instances with a backup from
before the vulnerability disclosure.

As such, the sites will be rebuilt and a backup restored. We will need to
do the work to include the results missing from the backup. It's unclear
how much data will need to be restored in this way at this time.

I apologize for the lateness of the email, and I'd like to personally thank
Pasi for filing an RT on the issue this morning. I've been disconnected
from the internet for a few days and hopped back online as events were
unfolding.

I will keep you informed as I find out more information.

Nicholas

---

### Post by kansasnoob on 2014-10-30
> **Elfy said:**
> [https://lists.ubuntu.com/archives/ubuntu-quality/2014-October/005635.html](https://lists.ubuntu.com/archives/ubuntu-quality/2014-October/005635.html)

Yikes!

---

### Post by kansasnoob on 2014-11-04
I see it's back up and running :D

@ *elfy*, did you happen to see this bug report:

[https://bugs.launchpad.net/ubuntu-qa-website/+bug/1387312](https://bugs.launchpad.net/ubuntu-qa-website/+bug/1387312)

---

### Post by Elfy on 2014-11-04
@kansasnoob - I did see that bug report - that would be something that someone on the Ubuntu Gnome release team or balloons would do.

---

### Post by kansasnoob on 2014-11-04
> **Elfy said:**
> @kansasnoob - I did see that bug report - that would be something that someone on the Ubuntu Gnome release team or balloons would do.

Thanks, I sent him a PM ;)

---

