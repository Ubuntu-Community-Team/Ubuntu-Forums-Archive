---
title: "Squid3 Transparent Proxy Add Authentication"
date: 2015-03-31
forum: Server Platforms
---

### Post by kks21199 on 2015-03-31
Right now I have set it, http_access allow all and can connect to my server from another location through firefox proxy settings, giving my servers public ip and the port i specified.

I am trying to add authentication so it requests username and password to let anyone connect and not open it to the world. I am using ubuntu 12.04.
```

http_access allow all

 forwarded_for off
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

### Post by SeijiSensei on 2015-03-31
As always, you should start by reading the documentation from the program's developers, in this case [http://wiki.squid-cache.org/Features/Authentication](http://wiki.squid-cache.org/Features/Authentication).

---

### Post by SeijiSensei on 2015-03-31
duplicate deleted

---

