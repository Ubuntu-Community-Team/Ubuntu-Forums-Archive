---
title: "question on montioring routers on nagios on 9.04"
date: 2009-07-22
forum: Server Platforms
---

### Post by kustomjs on 2009-07-22
hey guys
I just re-installed ubuntu 9.04 server and I installed nagios by doing this sudo apt-get install nagios3. but after it was installed I went into the directory of: /etc/nagios3/conf.d  I don't see anything for a switch/router .cfg file what do I need to do to fix this problem?

---

### Post by kustomjs on 2009-07-23
back on top.

---

### Post by dragos2 on 2009-07-23
> **kustomjs said:**
> back on top.

No offence but did you bothered to read the comprehensive Nagios manual ?

---

### Post by kustomjs on 2009-07-23
yes I have but im saying there was no cfg file for switches or routers in the apt-get install nagios3 from ubuntu. so that is my main question how do I get that cfg file for switches/routers if theres no cfg that came with it?

---

### Post by rbishop on 2009-07-23
You can either create the file from scratch using Nano, or you can use a backend configuration utility like nagiosQL.

One problem with doing it by hand is you may miss some of the configuration data.

---

