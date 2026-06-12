---
title: "CUPS, printbot[ANDROID APP] and &quot;ServerAlias *&quot;"
date: 2013-11-30
forum: Security
---

### Post by hankoor on 2013-11-30
Hi folks,
i tried to access my shared printer [cups on ubuntu] with my android device and all Windows-PCs at home.
Sharing the printer with the other Win-PCs went well.
But i had problems accessing the printer via an Android-Phone with the Tool printbot.
Having a look into the cups-log showed this:
```
E [30/Nov/2013:12:55:41 +0100] [Client 18] Request from "192.168.0.103" using invalid Host: field ""
```
The device seemed to access my CUPS with a wrong Hostname or something similar.
So I tried a bit around and put this into my cupsConfig:

```
ServerAlias *
```

That works fine and i'm able to print via Android now.
But this has a bad taste for me. I don't know how it could be dangerous, but it seems to be no good Idea to "allow all Aliases".

What i need to know is. Does this make my System more vulnurable?
Is there any better solution to fix this?

Thx
HanKooR

---

