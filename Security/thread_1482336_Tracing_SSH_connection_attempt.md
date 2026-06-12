---
title: "Tracing SSH connection attempt"
date: 2010-05-13
forum: Security
---

### Post by zexelon on 2010-05-13
I have a question about connections using SSH. When I try to connect to my remote server from certain sites the connections simply time out. I know that somewhere along the line there is a filter that is killing all encrypted connections that are not HTTPS. 

Is there a way to find out where along the line this filtering is taking place? (i.e. ISP, local router, etc.)

Basically is there the equivalent of a tracert style program for tracking a ssh connection attempt across networks? 

- zexelon

---

### Post by cdenley on 2010-05-13
```

sudo apt-get install tcptraceroute
tcptraceroute myserver 22

```

---

