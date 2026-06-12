---
title: "restart process if it dies"
date: 2010-10-30
forum: Server Platforms
---

### Post by ddragas on 2010-10-30
Hi all

I've got perl script that should be running 24/7/365 but after some time, it just dies (no error logged) and I have to rerun it manually.

Can somebody pls let me know how can I make it to be running non stop

this is my script louncher
/usr/local/bin/perl /path/to/my/script/myscript.pl  >/home/user/logs/server/myLog.log &

thank you in advance

kind regards

ddragas

---

### Post by clrg on 2010-10-30
Write a script with the following content:

```
#!/bin/bash
while true; do
/usr/local/bin/perl /path/to/my/script/myscript.pl >>/home/user/logs/server/myLog.log;
echo "Script died, automatically restarting..." >>/home/user/logs/server/myLog.log;
done
```

And that should work just fine.

---

