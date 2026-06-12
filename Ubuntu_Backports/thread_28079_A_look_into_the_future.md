---
title: "A look into the future"
date: 2005-04-18
forum: Ubuntu Backports
---

### Post by jdong on 2005-04-18
In the near future, I'm planning two major changes:

1. **Migrate to FreeBSD** -- Fedora's Subversion loves to corrupt itself from time to time (it's happened at least 5 times in the past), plus there's serious performance issues with the distro. As a result, we'll follow UbuntuForum's suit and migrate to FreeBSD *within 2 weeks*.

2. **Static Repository** -- to prevent SVN mistakes or instabilities from instantaneously bringing down the database, I plan to checkout/export a static tree to Apache (via Cron), and have the backports repository served from there. This will also reduce the load on the server. I plan on implementing this within 1-2 months. This way also has the distinct advantage that Packages.gz won't have to be uploaded, but rather generated locally via cron. It takes on average 90% of the upload time to get the Packages.gz files uploaded, and out of our 8GB repository, I estimate at least 1GB is just old Packages files.


In the more distant future, I hope to come up with more automated building scripts, that can edit the version number and do intelligent dependency satisfying. That should make multi-architecture development easier (i.e. one build command can do all arches practically simultaneously)

---

