---
title: "Windows may restore completely transparent"
date: 2012-08-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-24
After today's updates to QQ I'm seeing some windows completely transparent when they are minimized and then restored. It is erratic. Minimizing/restoring again makes them visible. I have seen this happen with Chrome, Gedit and Rhythmbox. Below is a screenshot of Rhythmbox when this happens (you can only see its Titlebar and borders).

[ATTACH]223118[/ATTACH]

Regards,
Effenberg

EDIT: 
Here's a screenshot of invisible CCSM over normal Thunderbird:
[ATTACH]223119[/ATTACH]

And here's Gedit over Tunar and Chrome:
[ATTACH]223121[/ATTACH]

---

### Post by ventrical on 2012-08-24
Not here Al.

What graphics  card are you using?

Here:

```

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

```

*edit*

Compiz is crashing after this recent update, but all compiz gizzmos are working, so apport is again erronously report bad compiz.

Apologies for being OT.

---

### Post by effenberg0x0 on 2012-08-24
> **ventrical said:**
> Not here Al.

What graphics  card are you using?

The one that is known for working perfectly with current QQ. Nvidia :)
> **ventrical said:**
> 
Here:

```

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

```

*edit*

Compiz is crashing after this recent update, but all compiz gizzmos are working, so apport is again erronously report bad compiz.

Apologies for being OT.

I think this is nvidia related at this point. I had to do all the downgrading thing in order to have a working QQ machine. This is probably a side effect.

Regards,
Effenberg

---

