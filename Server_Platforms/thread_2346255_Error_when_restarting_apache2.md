---
title: "Error when restarting apache2"
date: 2016-12-12
forum: Server Platforms
---

### Post by iwan_rhosadi on 2016-12-12
after I install apache2, when I wanted to restart apache2 notification appears fail


what causes it and how to fix

thank's

[ATTACH=CONFIG]272687[/ATTACH]

---

### Post by bastibasti2 on 2016-12-13
Some other service is already running on port 80, or the apache is not stopped.
can you stop the apache and then 'ps ax' and send the process list?

---

