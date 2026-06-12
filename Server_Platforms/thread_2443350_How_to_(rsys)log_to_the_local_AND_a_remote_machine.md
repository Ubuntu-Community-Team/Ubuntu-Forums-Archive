---
title: "How to (rsys)log to the local AND a remote machine"
date: 2020-05-14
forum: Server Platforms
---

### Post by joshi82 on 2020-05-14
Greetings,

I am in the middle of implementing a Graylog installation at my company. Now I want to route the log files for syslog, apache logs and such from a (local, intranet only) Virtualmin installation to this Graylog box. Putting the GL config aside, how would I tell rsyslog (which is installed by default) to keep the logs locally AND to also send them through TCP to the remote machine? I understand that I can add the other target with @@target-ip, but then the logs are only stored there, right? This is not what I want for multiple purposes.

Thanks in advance for your advice
Joshi

---

### Post by LHammonds on 2020-05-15
[this](https://serverfault.com/questions/181371/log-locally-and-remotely-with-rsyslogd)?

LHammonds

---

