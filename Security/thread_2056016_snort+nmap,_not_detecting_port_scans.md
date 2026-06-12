---
title: "snort+nmap, not detecting port scans"
date: 2012-09-10
forum: Security
---

### Post by Leo Matheus on 2012-09-10
im using snort2.9.3 and baryard2.1.8, and im testing it. the problem is: Snort not alerting portscans. if i create a log file, he will log the scans, but not alerting! i tried to use the file of output unifield2 to log, but it didn't work. any idea what would be?

---

### Post by d3v1150m471c on 2012-09-10
do any of the ports you're trying to protect actually have listening services?

---

### Post by Leo Matheus on 2012-09-10
i have an http server on the ids machine (using base as grafic interface).
When i do a portscan, he detect the port 80 open.

---

### Post by d3v1150m471c on 2012-09-10
if you're worried about someone reaching your httpserver other than yourself you shouldn't make it accessible. no port scan detection is going to prevent an attacker
from reaching it. i recommend binding the server to localhost or your private address and make sure you aren't port forwarding from your router.

---

### Post by Leo Matheus on 2012-09-11
im doing an ids to protect a network not a specifc host. So, i have to detect any portscans from outside and inside the network. my problem is that snort is not sending any alert, but he can log in a file.

---

### Post by Leo Matheus on 2012-09-28
well, i've try some think diferent, i have put another network plaque on my desktop, but snort still don't detecting. Am i doing some think wrong?

---

