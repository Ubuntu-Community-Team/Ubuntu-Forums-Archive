---
title: "MariaDB failing to update via apt - Repository problem"
date: 2021-11-11
forum: Server Platforms
---

### Post by LHammonds on 2021-11-11
I had a MariaDB 10.04 installation that was throwing apt errors.  It was mad about the repository.  I found out that the repository I had been using was going away so it was a simple matter of removing the broken mirror from /etc/apt/sources.list and adding a new one (which I picked from [this page]("https://mariadb.org/download/?t=repo-config&d=20.04+%22focal%22&v=10.4&r_m=gigenet")).

Also, since there were two newer versions of MariaDB than 10.4, I made the mistake of removing 10.4 and installing 10.6 at the same time of correcting the mirror.  It was a mistake because 10.6 no longer allows "compressed rows" by default and restoring databases with those settings failed.  I decided to remove 10.6 and just install 10.5 and stay on that version until the app that uses compressed rows is updated to not require that option before going to 10.6 or higher.

LHammonds

---

