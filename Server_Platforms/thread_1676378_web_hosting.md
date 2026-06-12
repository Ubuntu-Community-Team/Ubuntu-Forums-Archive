---
title: "web hosting"
date: 2011-01-27
forum: Server Platforms
---

### Post by MULAMA77 on 2011-01-27
i have a website designed in windows using dream weaver. Is it possible for me to host it in linux. It has oracle as its database?

---

### Post by lisati on 2011-01-27
I'm not sure about the Oracle part (you might have to look for an equivalent or work-alike), but a large part of my own [website]("http://lisati.homelinux.com") was prepared using Windows software and is hosted on a machine running Ubuntu.

---

### Post by SeijiSensei on 2011-01-27
[Oracle]("http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index.html") sells versions of its database software for Linux. In fact, it's one of the most popular platforms for Oracle these days.  I think you can try it out for free, though if you're going to be using it in production, you'll need to buy a license.

That said, I'd agree with lisati that you're probably better off migrating to an open-source SQL server if you're moving to Linux.  I prefer PostgreSQL myself; I believe the SQL syntax it uses is pretty close to that used by Oracle as well.  Of course, since Oracle now owns MySQL, there may be better migration tools for that.

---

