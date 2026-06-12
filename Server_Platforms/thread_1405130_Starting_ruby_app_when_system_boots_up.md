---
title: "Starting ruby app when system boots up"
date: 2010-02-12
forum: Server Platforms
---

### Post by spauldingsmails on 2010-02-12
I've scoured the web but have failed to find an answer to a simple question; how do I start a ruby on rails application when my Ubuntu server starts up/is rebooted?

Currently I start the application by cd-ing into the ruby application's root directory (the application I'm using is Bibapp) and execute the command;

```
sudo rake bibapp:start
```

Any help much appreciated.

---

### Post by drave on 2010-02-12
put that statement without the sudo but maybe with full path into /etc/rc.local (see comments in same)

---

