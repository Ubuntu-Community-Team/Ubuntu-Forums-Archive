---
title: "Unable to stop svnserve"
date: 2015-07-23
forum: Server Platforms
---

### Post by Slaymantis on 2015-07-23
I have been unable to stop my svnerve on ubuntu 12 server

If I run ps aux | grep svnserve multiple times I get different process ids

root      21056  0.0  0.0   9612   656 pts/0    S+   12:50   0:00 grep --color=auto svnserve

root      21074  0.0  0.0   9612   652 pts/0    S+   12:52   0:00 grep --color=auto svnserve

root      21236  0.0  0.0   9612   656 pts/0    S+   12:57   0:00 grep --color=auto svnserve 

etc etc

If I try stop it using the kill command I get this error

sudo kill -9 21236

kill: No such process

I have also tried 

sudo killall svnserve

svnserve: no process found

svnserve stop

none working

---

### Post by PaulW2U on 2015-07-23
*Thread moved to **Server Platforms**.*

---

### Post by Habitual on 2015-07-23
outputs of ```
ps aux | grep svnserve | grep -v grep
``` and 
```
sudo dpkg -l subversion | tail -1
```
 please.

---

### Post by steeldriver on 2015-07-23
> **Slaymantis said:**
> I have been unable to stop my svnerve on ubuntu 12 server

If I run ps aux | grep svnserve multiple times I get different process ids

root **     21056  **0.0  0.0   9612   656 pts/0    S+   12:50   0:00 **grep --color=auto svnserve**

root **     21074  **0.0  0.0   9612   652 pts/0    S+   12:52   0:00 [B]grep --color=auto svnserve
[/B]
root **     21236  **0.0  0.0   9612   656 pts/0    S+   12:57   0:00 [B]grep --color=auto svnserve 
[/B]


The results you are seeing here are the PIDs of your grep process - they do **not **indicate that an svnserve process is running

Aside from the 'grep -v' trick mentioned by Habitual, you can prevent the grep from confusing things by turning it into a regex match

```

ps aux | grep [s]vnserve

```

---

### Post by Habitual on 2015-07-24
> **steeldriver said:**
> ```

ps aux | grep [s]vnserve

```
Personally, I prefer less typing. Thanks for the RE nugget

---

