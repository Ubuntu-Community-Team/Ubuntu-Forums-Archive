---
title: "bind9 kernel problem"
date: 2009-03-17
forum: Server Platforms
---

### Post by dp4 on 2009-03-17
Hello there,

I have a strange problem with my ubuntu server and the bind9 service. Sometimes bind9 cannot connect to the forwarder servers and gets a timeout. After a while, about 15..60 minutes, it acts normally as before.

Configuration seems to be ok, the only wired thing that I can find is this log entry in messages:

> Mar 17 13:04:37 ubuntu kernel: [430208.408979] audit(1237291477.481:67): type=1502 operation="capable" name="sys_resource" pid=26967 profile="/usr/sbin/named" namespace="default"

I could not find any useful hints about this in Internet :(

---

### Post by lu5t on 2010-06-18
I have this same log message on bind9 startup:

kernel: [  679.885381] audit(1276876038.859:4): type=1503 operation="capable" name="sys_resource" pid=5242 profile="/usr/sbin/named" namespace="default"

did you ever figure out if this is a problem or just diagnostic?

---

