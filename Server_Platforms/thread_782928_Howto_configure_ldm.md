---
title: "Howto configure ldm?"
date: 2008-05-05
forum: Server Platforms
---

### Post by azzamite on 2008-05-05
Hi there,
I installed Ubuntu 8.4 in my box and from that
installation I turned it into a LTSP server with
the apropiate packages.

Everything works fine so far, but I don't find
a way to configure ldm, I want the clients to
use a resolution of 800x600 since I have very
old monitors, but ldm always uses 1024x768.

Does anyone knows how to change the resolution?

This is my configuration
/var/lib/tftpboot/ltsp/i386/lts.conf

```

[default] 
    SCREEN_01    = shell
    SCREEN_02    = ldm
    SOUND        = False
    LOCALDEV     = False
    CONFIGURE_X  = True
    X_COLOR_DEPTH= 16
    X_MODE_0     = 800x600
    LDM_DIRECTX  = True

```

---

