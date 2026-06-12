---
title: "juju bootstrap running machine configuration script (stall)"
date: 2019-01-05
forum: Ubuntu Cloud and Juju
---

### Post by rafise on 2019-01-05
Hello All,

 Setting up a MAAS cloud with 12 bare-metal machines, the issue I'm having after executing $juju bootstrap --debug, maas deploy a node and juju stall at some point not sure why is juju saying (running machine configuration script)? if someone can tell me how to fix this would appreciate a lot thanks.

12:28:08 DEBUG juju.provider.maas maas2instance.go:79 "real-toucan" has addresses ["local-cloud:10.0.0.2@default-space(id:2)"]
12:28:13 INFO  cmd bootstrap.go:344 Connected to 10.0.0.2
12:28:13 INFO  juju.cloudconfig userdatacfg_unix.go:465 Fetching agent: curl -sSfw 'agent binaries from %{url_effective} downloaded: HTTP %{http_code}; time %{time_total}s; size %{size_download} bytes; speed %{speed_download} bytes/s ' --retry 10 -o $bin/tools.tar.gz <[https://streams.canonical.com/juju/tools/agent/2.4.3/juju-2.4.3-ubuntu-amd64.tgz]>
12:28:13 INFO  cmd bootstrap.go:414 Running machine configuration script...

---

### Post by rafise on 2019-01-11
I've found the nodes was not getting internet access, that was the issue.

---

