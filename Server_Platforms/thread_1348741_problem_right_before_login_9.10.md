---
title: "problem right before login 9.10"
date: 2009-12-07
forum: Server Platforms
---

### Post by rmb938 on 2009-12-07
So I just installed the 32-bit 9.10 server edition on one of my computers. But when I boot up the computer and right before I login I get this error: 

```
           [       8.326932] render error detected, EIR: 0x00000010
[       8.326930][drm: i915)handle_error]*ERROR* EIR stuck: 0x00000010, masking
[       8.326932] render error detected, EIR: 0x00000010
```

It stops my ssh server and ftp server I am running on it. 9.04 was working fine so I upgraded to 9.10 and that gave me the same issue. So I did a clean install of 9.10 and this is what happened.

I would install 9.04 again but I lost the cd I burned. Any idea why this is happening?

---

### Post by windependence on 2009-12-07
Looks like a video problem. Try a different desktop environment, or set up not to log in to the GUI at all and see if it works. If so, you may have a video driver issue.

-Tim

---

### Post by rmb938 on 2009-12-07
Its the server edition so there is no GUI. I will try another video card but I doubt that will work. I also tried it on my other pc and it worked fine.

---

