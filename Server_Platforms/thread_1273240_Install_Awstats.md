---
title: "Install Awstats"
date: 2009-09-23
forum: Server Platforms
---

### Post by dragos2 on 2009-09-23
I am trying to install awstats in Lighttpd using
```

apt-get install awstats

```

and I defined the alian in lighty
$HTTP["url"] =~ "^/awstats" {
  alias.url += (
    "/awstats/"      => "/usr/share/awstats/wwwroot/cgi-bin/",
    "/awstatsicons/" => "/usr/share/awstats/wwwroot/icon/",
  )But /usr/share/awstats/wwwroot does not exist?

How are these paths changed ?

---

