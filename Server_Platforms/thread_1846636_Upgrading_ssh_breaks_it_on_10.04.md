---
title: "Upgrading ssh breaks it on 10.04"
date: 2011-09-19
forum: Server Platforms
---

### Post by HarryWild on 2011-09-19
Hi there,

I use Ubuntu 10.04 on a virtual server. It is a fresh minimum installation (recently made available by my hoster after offering only 08.04 so far).

First thing I did was an "apt-get update" followed by an "apt-get upgrade".

This led my ssh to disconnect from the server and i wasn't able to reconnect to it again. :(

I had to apply a new image a start all over.

Has anyone else ever had this problem? I can't find the reason why upgrading ssh fails.

On my 08.04 install I had "update & upgrade" in my crontab running once a week, which worked fine. But now it seems to be a bad practice since it can render my system unusable.

thanks in advance
Harry

---

### Post by CharlesA on 2011-09-19
Haven't had any problems with my install of 10.04. Perhaps contact the host and see if they made any customizations that could cause it.

---

