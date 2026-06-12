---
title: "Issue with linux headers"
date: 2015-03-24
forum: Server Platforms
---

### Post by tony75 on 2015-03-24
[COLOR=#000000][FONT=Verdana]Hi guys,[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]running into an issue with my linux headers. Ubuntu 12.04 server[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]my apt-get -f install output:

[/FONT][/COLOR]```
[COLOR=#000000]dpkg: dependency problems prevent configuration of linux-headers-server:[/COLOR]
 linux-headers-server depends on linux-headers-3.2.0-69-generic; however:
  Package linux-headers-3.2.0-69-generic is not installed.
dpkg: error processing linux-headers-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.69.82); however:
  Version of linux-image-server on system is 3.2.0.77.91.
 linux-server depends on linux-headers-server (= 3.2.0.69.82); however:
  Package linux-headers-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-headers-server
 linux-server [COLOR=#000000]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```[COLOR=#000000][FONT=Verdana]

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Any idea how to fix?[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by ian-weisser on 2015-03-24
I would stop trying to install obsolete headers.  **3.2.0.69** is not in the repositories anymore.
Apt-get's -f flag can't fix that.

```
$ rmadison linux-headers-generic | grep precise
 linux-headers-generic | 3.2.0.23.25  | precise          | amd64, i386
 linux-headers-generic | **3.2.0.79.93**  | precise-security | amd64, i386
 linux-headers-generic | 3.2.0.79.93  | precise-proposed | amd64, i386
 linux-headers-generic | **3.2.0.79.93**  | precise-updates  | amd64, i386
```

Boot from a different kernel and uninstall the 3.2.0.69 kernel, and all associated baggage.

---

