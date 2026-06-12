---
title: "Lucid - Wine. Pre RC1 1.2 and On.  No Steam (X_CreateWindow)"
date: 2010-05-29
forum: Wine
---

### Post by oXYnary on 2010-05-29
Ever since the release before RC1 1.2 Steam has stopped working with the below.  I only use steam for the dedicated windows servers for games with no linux client.


Console
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  1313
  Current serial number in output stream:  1317

```System:
4 Gig Opteron Dual Core HP server.
Matrox Integrated server card.  I think it has 32 megs.  I know it has no acceleration.
No sound.
Note:  I am running customized Ubuntu Server with a xfce desktop.

Reinstalled wine including deleting .wine directory.

Google searches haven't helped. Or, I don't know what to search for.

Downgrading?  I guess if absolutely necessary.  Will have to see how to get the last release that worked manually.  Rather not per added functionality, >optimization<, and revision each wine release brings.

Should note, was working with the new steam client, so its not that change at least.

---

### Post by asdfoo on 2010-05-29
you could file a bug report, but you'll need to include the results of a regression test to identify which change broke it for you

[http://wiki.winehq.org/RegressionTesting](http://wiki.winehq.org/RegressionTesting) - if you need more info prob. best to ask at [http://forum.winehq.org](http://forum.winehq.org)

---

