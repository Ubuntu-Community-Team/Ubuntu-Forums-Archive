---
title: "Can't get cron job to kick off at 12 and midnight?"
date: 2012-01-03
forum: Server Platforms
---

### Post by Gizim on 2012-01-03
I can save it fine like this
* 12 * * * /root/backup12hr.sh

But if i do 


* 12,24 * * * /root/backup12hr.sh

it says bad hour

Edit: Well son of a b....
nevermind

---

### Post by HugoSerrano on 2012-01-04
23:58
23:59
00:00
00:01

There's no 24:00
;-)

---

