---
title: "Howto create a working exec Script for collectd"
date: 2010-05-20
forum: Server Platforms
---

### Post by vralfy on 2010-05-20
I'm trying to write a script for collectd, but i've got some problems.

My script returns the following:

```

PUTVAL vx00/exec-Preise/server26-pa interval=7200 N:32.29:30.28:30.96
PUTVAL vx00/exec-Preise/server26-pb interval=7200 N:9.94:9.14:8.88
PUTVAL vx00/exec-Preise/server26-pc interval=7200 N:43.1:41.05:46.80
PUTVAL vx00/exec-Preise/server26-pd interval=7200 N:5:4.16:3.78
PUTVAL vx00/exec-Preise/server26-pe interval=7200 N:5.05:4.92:4.48
PUTVAL vx00/exec-Preise/server26-pf interval=7200 N:19.86:19.49:30.00

```i also added a type in the types.db
```

server26                mean:GAUGE:0:U, min:GAUGE:0:U, store:GAUGE:0:U

```All I get is an empty graph an all values (min,avg,max,last) are "-nan". Did i miss something?

Thnx

---

