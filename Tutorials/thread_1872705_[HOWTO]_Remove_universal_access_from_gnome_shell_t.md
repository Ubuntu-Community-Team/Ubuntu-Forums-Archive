---
title: "[HOWTO] Remove universal access from gnome shell top bar"
date: 2011-10-31
forum: Tutorials
---

### Post by phDaemon on 2011-10-31
This is a pretty easy howto (since there is no configuration to actually stop displaying it) that explains how to remove the "Universal Access" icon/menu from the top bar.

Open a terminal and type in the following:
```

sudo gedit /usr/share/gnome-shell/js/ui/panel.js&

```

Now, FIND AND REPLACE:
```

const STANDARD_STATUS_AREA_ORDER = ['a11y', 'keyboard', 'volume', 'bluetooth', 'network', 'battery', 'userMenu'];

```

WITH

```

//const STANDARD_STATUS_AREA_ORDER = ['a11y', 'keyboard', 'volume', 'bluetooth', 'network', 'battery', 'userMenu'];
const STANDARD_STATUS_AREA_ORDER = ['keyboard', 'volume', 'bluetooth', 'network', 'battery', 'userMenu'];

```

FIND AND REPLACE
```

'a11y': imports.ui.status.accessibility.ATIndicator,

```

WITH

```

//'a11y': imports.ui.status.accessibility.ATIndicator,

```

FIND AND REPLACE
```

const GDM_STATUS_AREA_ORDER = ['a11y', 'display', 'keyboard', 'volume', 'battery', 'powerMenu'];

```

WITH

```

//const GDM_STATUS_AREA_ORDER = ['a11y', 'display', 'keyboard', 'volume', 'battery', 'powerMenu'];
const GDM_STATUS_AREA_ORDER = ['display', 'keyboard', 'volume', 'battery', 'powerMenu'];

```

AND LAST FIND AND REPLACE
```

'a11y': imports.ui.status.accessibility.ATIndicator,

```

WITH

```

//'a11y': imports.ui.status.accessibility.ATIndicator,

```

Now do ALT + F2 and type in
```

r

```

Or simply log out and log in...

Done. The entry should be removed.

A lot of the Gnome-Shell and themes/Extensions are simple CSS and javascript so for web developers out there it will be very easy to manipulate a lot of the UI =D


Hope this helps any noobies out there.

---

### Post by iosuna86 on 2011-12-01
It didn't work for me.

It actually removed all my panels and now I can't find the way to restore the previous status since I can't open a terminal. The shortcuts do not work and there is no Applications menu.

---

### Post by iosuna86 on 2011-12-01
> **iosuna86 said:**
> It didn't work for me.

It actually removed all my panels and now I can't find the way to restore the previous status since I can't open a terminal. The shortcuts do not work and there is no Applications menu.

My bad. 

I missed one thing that messed it all up. It actually works perfectly.

Thanks!

---

### Post by altima on 2012-03-03
it does what it is supposed to do! thank you for this howto!

---

