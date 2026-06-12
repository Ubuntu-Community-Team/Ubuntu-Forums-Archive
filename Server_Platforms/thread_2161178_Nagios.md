---
title: "Nagios"
date: 2013-07-09
forum: Server Platforms
---

### Post by lebomotsai on 2013-07-09
Good People I Need urgent advise I am new to Ubuntu was given a task at work to install nagios to monitor few servers at our company ,I am unable to complete the installation when running this command "sudo make install-webconf "error cannot create regular file /etc/httpd/conf.d/nagios.conf

---

### Post by cariboo on 2013-07-09
Moved to Server Platforms, as this question is server related.

---

### Post by CharlesA on 2013-07-10
Why not install nagios from the repos?

With that being said, it looks like that version of Nagios is set to use httpd, not apache2, so you'll probably have to do some edits.

---

### Post by Habitual on 2013-07-10
[http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194)

---

### Post by CharlesA on 2013-07-10
> **Habitual said:**
> [http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194)

+1. I parts of that tutorial when I configured Nagios at work.

---

### Post by lukecolb on 2013-07-11
> **CharlesA said:**
> Why not install nagios from the repos?

With that being said, it looks like that version of Nagios is set to use httpd, not apache2, so you'll probably have to do some edits.

When installing from repos certain things change its best to install using the quick install guides on the site as all the plugins etc you might use in the future will assume this

---

### Post by lukecolb on 2013-07-11
+1 aswell this has everything you need in

---

