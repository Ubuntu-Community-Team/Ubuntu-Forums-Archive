---
title: "public signiatures and gpg --keyserver messages"
date: 2018-09-05
forum: Security
---

### Post by mborl on 2018-09-05
I am trying to securely download an ISO by using 

```
 gpg --keyserver [link] --recv-key [key]
``` 

I got the following messages though:

```
2 duplicate signatures removed 
148 signatures not checked due to missing keys 
public key "[key I was importing]" imported
no ultimately trusted keys found
Total number processed: 1
imported: 1
```

Is this ok? I'm still learning about gpg. I just want to make sure this is not compromised. Thanks

---

