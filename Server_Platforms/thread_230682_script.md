---
title: "script?"
date: 2006-08-06
forum: Server Platforms
---

### Post by matko on 2006-08-06
hi all

i am running server that is facing many probes from lame hackers. :D 

i would like to know if somebody have or could write script that will analyze
logs from apache2 auth log and mysql.

i would like to see only lines from logs where is "Invalid", "Error", "Failed" etc.

could somebody help me?
thx

---

### Post by lamego on 2006-08-06
```
grep -E "Invalid|Error|Failed" logfile
```
Anyway searching for those strings will not help you against hackers, from your lack of kwonledge I would advise you to not run a server connected o the internet until you get some Linux experience.

---

### Post by matko on 2006-08-06
thanx.

```
Anyway searching for those strings will not help you against hackers, from your lack of kwonledge I would advise you to not run a server connected o the internet until you get some Linux experience.
```

its late :);)

---

