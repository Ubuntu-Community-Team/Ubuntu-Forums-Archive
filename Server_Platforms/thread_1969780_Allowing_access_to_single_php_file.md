---
title: "Allowing access to single php file"
date: 2012-04-30
forum: Server Platforms
---

### Post by sandyd on 2012-04-30
I currently have my content mapped to a CDN, so I don't want people to have access to the php files within my folders.

I disabled the access to php files via 
```

location ~ /(.+)\.php$ {
deny all;
}

```But how can I enable php access for only one folder?

---

