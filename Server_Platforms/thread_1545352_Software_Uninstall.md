---
title: "Software Uninstall"
date: 2010-08-03
forum: Server Platforms
---

### Post by cvandal on 2010-08-03
Hello,

I've just ran the following commands to remove munin and cacti from my server.

sudo apt-get --purge remove munin
sudo apt-get --purge remove cacti

Is this enough to ensure that all traces of these programs have been removed or is there additional clean up required?

---

### Post by chopinhauer on 2010-08-03
> **cvandal said:**
> 
Is this enough to ensure that all traces of these programs have been removed or is there additional clean up required?


No further clean up is necessary. There are surely some data that these applications generated (logs, MySQL databases), but you probably want to keep that.

---

### Post by cvandal on 2010-08-03
> **chopinhauer said:**
> No further clean up is necessary. There are surely some data that these applications generated (logs, MySQL databases), but you probably want to keep that.

Great Thanks :)

---

### Post by cludgie on 2013-01-20
I was having a little trouble with Munin. I found the following helpful:

grep 'munin' / var / lib / dpkg / statoverride
difference difference 755 / var / lib / difference
difference difference 755 / var / www / difference
difference difference 775 / var / lib / difference / plugin-state
root munin 750 /etc/munin/plugin-conf.d
munin munin 755 / var / cache / munin / www
munin adm 750 / var / log / munin

To solve the problem simply remove them with a little sed:

sed -i '/munin/d' /var/lib/dpkg/statoverride

Regards
Cludgie

---

