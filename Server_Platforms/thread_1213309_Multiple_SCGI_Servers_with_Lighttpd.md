---
title: "Multiple SCGI Servers with Lighttpd"
date: 2009-07-14
forum: Server Platforms
---

### Post by devinw on 2009-07-14
I'm trying to configure lighttpd to send SCGI requests to different ports, depending on what file(s) are accessed. Is this possible?
This is what I've tried, and it hasn't worked.

```
$HTTP["url"] == "URL1" {
scgi.server = (
 "/RPC2" =>
  ( "127.0.0.1" =>
   (
    "host" => "127.0.0.1",
    "port" => 5001,
    "check-local" => "disable"
   )
  )
 )
}

$HTTP["url"] == "URL2" {
scgi.server = (
 "/RPC3" =>
  ( "127.0.0.1" =>
   (
    "host" => "127.0.0.1",
    "port" => 5002,
    "check-local" => "disable"
   )
  )
 )
}
```

SCGI requests aren't sent to the correct port, regardless of what file is accessed. Any help would be appreciated.

---

### Post by devinw on 2009-07-18
Looks like I wasn't approaching this in quite the right way. URL tests were not necessary. If anyone is interested, this thread helped me sort things out: [http://ubuntuforums.org/showthread.php?t=1119482](http://ubuntuforums.org/showthread.php?t=1119482)
Particularly this post: [http://ubuntuforums.org/showpost.php?p=7112152&postcount=27](http://ubuntuforums.org/showpost.php?p=7112152&postcount=27)

---

