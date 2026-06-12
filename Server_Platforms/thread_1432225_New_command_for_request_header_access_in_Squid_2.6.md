---
title: "New command for request_header_access in Squid 2.6.Stable6?"
date: 2010-03-17
forum: Server Platforms
---

### Post by Zer0d on 2010-03-17
Hi.

**[COLOR="Red"]2.7.STABLE6 is the version, I wrote wrong in post title.[/COLOR]**

My squid.conf give me erro's:
```

2010/03/17 20:19:05| parseConfigFile: squid.conf:4970 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4971 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4972 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4973 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4974 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4975 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4976 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4977 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4978 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4979 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4980 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4981 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4982 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4983 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4984 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4985 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4986 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4987 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4988 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4989 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4990 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4991 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4992 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4993 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4994 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4995 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4996 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4997 unrecognized: 'request_header_access'
2010/03/17 20:19:05| parseConfigFile: squid.conf:4998 unrecognized: 'request_header_access'


```

I suspect the new version of Squid has a new command for doing this configuration? 


These are the lines in the configuration which causes the error's:
```

request_header_access Allow allow all 
request_header_access Authorization allow all 
request_header_access WWW-Authenticate allow all 
request_header_access Proxy-Authorization allow all 
request_header_access Proxy-Authenticate allow all 
request_header_access Cache-Control allow all 
request_header_access Content-Encoding allow all 
request_header_access Content-Length allow all 
request_header_access Content-Type allow all 
request_header_access Date allow all 
request_header_access Expires allow all 
request_header_access Host allow all 
request_header_access If-Modified-Since allow all 
request_header_access Last-Modified allow all 
request_header_access Location allow all 
request_header_access Pragma allow all 
request_header_access Accept allow all 
request_header_access Accept-Charset allow all 
request_header_access Accept-Encoding allow all 
request_header_access Accept-Language allow all 
request_header_access Content-Language allow all 
request_header_access Mime-Version allow all 
request_header_access Retry-After allow all 
request_header_access Title allow all 
request_header_access Connection allow all 
request_header_access Proxy-Connection allow all 
request_header_access User-Agent allow all 
request_header_access Cookie allow all 
request_header_access All deny all 

```

---

### Post by Zer0d on 2010-03-20
Just had to change request_header_access into header_access. Setting thread to solved.

---

