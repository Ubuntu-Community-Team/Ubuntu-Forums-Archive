---
title: "Bash History 2"
date: 2011-08-17
forum: Security
---

### Post by themanfromdelmonte on 2011-08-17
I found the following in my bash history. I didn't enter it. Any idea what it did to my pc?

                                 [SIZE=1]/usr/bin/printf '*.=info;*.=notice;*.=warn;\\\n\tauth,authpriv.none;\\\n\tcron,daemon.none;\\\n\tmail,news.none -/var/log/messages\n' > /etc/rsyslog.d/99-fixlog.conf sudo /usr/bin/printf '*.=info;*.=notice;*.=warn;\\\n\tauth,authpriv.none;\\\n\tcron,daemon.none;\\\n\tmail,news.none -/var/log/messages\n' > /etc/rsyslog.d/99-fixlog.conf #2REVElL /usr/bin/printf '*.=info;*.=notice;*.=warn;\\\n\tauth,authpriv.none;\\\n\tcron,daemon.none;\\\n\tmail,news.none -/var/log/messages\n' > /etc/rsyslog.d/99-fixlog.conf exit[/SIZE]

---

### Post by tubbygweilo on 2011-08-17
I wonder if this is something along the lines of [bug#776361]("https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/776361")?

---

