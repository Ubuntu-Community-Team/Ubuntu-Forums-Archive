---
title: "squid htttps 71 Protocol error"
date: 2014-09-11
forum: Server Platforms
---

### Post by charles38 on 2014-09-11
Hi
Am getting an error while accessing https site, any idea what it is about ?


Failed to establish a secure connection to ip


The system returned: (71) Protocol error


This proxy and the remote host failed to negotiate a mutually acceptable security settings for handling your request. It is possible that the remote host does not support secure connections, or the proxy is not satisfied with the host security credentials.


----
Below is the https line in my squid.conf
https_port 3130 ssl-bump generate-host-certificates=on dynamic_cert_mem_cache_size=4MB key=/etc/squid3/cert/myssl.local.private cert=/etc/squid3/cert/myssl.local.cert

---

