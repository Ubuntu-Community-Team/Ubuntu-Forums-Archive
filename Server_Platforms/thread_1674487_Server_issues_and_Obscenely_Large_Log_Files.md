---
title: "Server issues and Obscenely Large Log Files"
date: 2011-01-24
forum: Server Platforms
---

### Post by oomar on 2011-01-24
I'm running Ubuntu 10.04 server edition and basically I have my server to reset every six hours because after a period of time it becomes unresponsive. It is a headless server, so it is only unresponsive to network requests... which is all I use it for. I have no idea why it becomes unresponsive. I'm running SSH (key based, no password), squid, used to run TOR but took it down because my temporary fix (restarting it every 12 hours then every 6 no longer worked), http, and webmin.

SIDE note: I seem to have port 9128 open but i suspect that I simply changed the port for squid... gunna have to check that.

SIDE SIDE NOTE: After further investigation... I did not change the port for squid and for the life of me have no idea why i would have it up... i HAD 9001 and 9030 up for tor but they were shut... so I dont know. i think it has been compromised. so i have disconnected the ethernet cable. i'm probably going to just wipe it and reinstall. not gunna take any chances. 

Now, one of the problems i was experiencing was log files individually in excess of 300+Mb. AFTER I cycled them. So what I want to know is what would be an effective way of controlling their size. If it exceeds a certain limit, say 100MB, how would I automatically trim the files or somethgin. I can't realistically go through 2GB of log files.

---

### Post by HermanAB on 2011-01-24
You forgot to configure logrotate properly.

---

