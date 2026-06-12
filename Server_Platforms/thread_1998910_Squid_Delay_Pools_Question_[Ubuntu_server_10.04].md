---
title: "Squid Delay Pools Question [Ubuntu server 10.04]"
date: 2012-06-07
forum: Server Platforms
---

### Post by Nessaja on 2012-06-07
Hi,

I'm trying to set up limits to sites like Youtube, my test config file looks like this:

(No please bare in mind, that I've sourced information from a lot of different tutorials and tried to combine it)

```

acl limitedsites dstdomain -i .youtube.com \.dropbox.com
acl big-file url_regex -i .exe \.flv \.mp3 \.mp4 \.mkv \.3gp \.avi \.mpeg \.mpe \.mpg \.iso \.mov \.zip \.rar

delay_pools 1
delay_class 1 2
delay_parameters 1 -1/-1 8000/8000

delay_access 1 allow limitedsites
delay_access 1 allow big-file
delay_access 1 deny all


```When I start squid I get:
```

2012/06/07 16:02:20| parse_delay_pool_access: Ignoring pool 1 not in 1 .. 0
2012/06/07 16:02:20| parse_delay_pool_access: Ignoring pool 1 not in 1 .. 0
2012/06/07 16:02:20| Squid is already running!  Process ID 23064

```I know I probably didn't do the delay in a remotely correct way, but those tutorials are very hard to understand...

I basically just want to limit certain sites and downloads, that's it, nothing fancy..

---

