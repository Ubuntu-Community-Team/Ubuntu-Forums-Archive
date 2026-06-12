---
title: "Would this command work..."
date: 2011-10-03
forum: The Cafe
---

### Post by ninjaaron on 2011-10-03
... if your harddrive was large enough.

```
wget -r http://en.wikipedia.org/
```

When I thought of this command, my brain broke, so I'm afraid to think what it might do to my computer.

---

### Post by LowSky on 2011-10-03
```
[john@mediacenter disk4]$ wget -r 'http://en.wikipedia.org/wiki/Ubuntu_(operating_system)'
--2011-10-03 00:48:23--  http://en.wikipedia.org/wiki/Ubuntu_(operating_system)
Resolving en.wikipedia.org... 208.80.152.201
Connecting to en.wikipedia.org|208.80.152.201|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 285771 (279K) [text/html]
Saving to: `en.wikipedia.org/wiki/Ubuntu_(operating_system)'

100%[======================================>] 285,771      376K/s   in 0.7s    

2011-10-03 00:48:24 (376 KB/s) - `en.wikipedia.org/wiki/Ubuntu_(operating_system)' saved [285771/285771]

Loading robots.txt; please ignore errors.
--2011-10-03 00:48:24--  http://en.wikipedia.org/robots.txt
Reusing existing connection to en.wikipedia.org:80.
HTTP request sent, awaiting response... 200 OK
Length: 27355 (27K) [text/plain]
Saving to: `en.wikipedia.org/robots.txt'

100%[======================================>] 27,355      --.-K/s   in 0.06s   

2011-10-03 00:48:24 (413 KB/s) - `en.wikipedia.org/robots.txt' saved [27355/27355]

FINISHED --2011-10-03 00:48:24--
Total wall clock time: 1.1s
Downloaded: 2 files, 306K in 0.8s (379 KB/s)

```

---

