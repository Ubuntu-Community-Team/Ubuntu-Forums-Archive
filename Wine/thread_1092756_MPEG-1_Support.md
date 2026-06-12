---
title: "MPEG-1 Support?"
date: 2009-03-10
forum: Wine
---

### Post by Dark Aspect on 2009-03-10
Is there any codec I can install to fix 

```
MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
```

If there was it would fix cutscenes for a variety of Direct-X/Windows games.I tried to install Xvid but I don't believe that installed a MPEG-1 codec.

---

### Post by cogadh on 2009-03-10
I don't believe it is actually a lack of a codec problem, but rather a lack of functionality that would normally be used by a codec. In other words, even if you had the right codec, it still wouldn't work. Correcting this problem is on the Wine "to do" list (in the DirectShow section, I believe).

---

### Post by Dark Aspect on 2009-03-28
> **cogadh said:**
> I don't believe it is actually a lack of a codec problem, but rather a lack of functionality that would normally be used by a codec. In other words, even if you had the right codec, it still wouldn't work. Correcting this problem is on the Wine "to do" list (in the DirectShow section, I believe).

Actually I thought that too at first but I found a fix, just replace and add quartz.dll as native and it works.

---

