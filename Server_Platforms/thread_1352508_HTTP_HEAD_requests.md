---
title: "HTTP HEAD requests"
date: 2009-12-11
forum: Server Platforms
---

### Post by Cyked on 2009-12-11
Why would I have a bunch of HEAD requests in my Apache access logs?
The directory in question (and the ONLY directory from what I can see from logs that is being hit) is hidden and directory browsing is disabled?

```
"HEAD /dir1/.dir2/image.jpg HTTP/1.1" 200 - "-" "Mozilla/4.0 (compatible; MSIE 7.0; AOL 9.1; AOLBuild 4334.5006; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR 3.5.30729; .NET CLR 3.0.30729; customie8)"
```

Thoughts?

The IPs are all for AOL - 64.12.116.* or 64.12.117.*  These are relatively new.  I'll have to dig through my zipped logs.

Not really worried about them, just seems odd to have a HEAD request on a specific file.

---

