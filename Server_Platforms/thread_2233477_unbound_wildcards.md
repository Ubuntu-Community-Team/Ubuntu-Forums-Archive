---
title: "unbound wildcards"
date: 2014-07-08
forum: Server Platforms
---

### Post by jj4 on 2014-07-08
I have the following in my conf:
```

local-zone: "amazon.co.uk." redirect
        local-data: "amazon.co.uk. 600 IN A xxx.xxx.xxx.xxx"
        local-zone: "amazon.com." redirect
        local-data: "amazon.com. 600 IN A xxx.xxx.xxx.xxx"
        local-zone: "*.amazon.com." redirect
        local-data: "*.amazon.com. 600 IN A xxx.xxx.xxx.xxx"
        local-zone: "*.amazon.co.uk." redirect
        local-data: "*.amazon.co.uk. 600 IN A xxx.xxx.xxx.xxx"

```

will these wildcards work or is there another way?

---

