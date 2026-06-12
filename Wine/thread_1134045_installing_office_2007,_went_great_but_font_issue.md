---
title: "installing office 2007, went great but font issue"
date: 2009-04-23
forum: Wine
---

### Post by gatorbrit on 2009-04-23
I installed office 2007 using this howto
[http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840)

Everything went great.  The programs run and seem to work fine, except that the old issue of wine not rendering fonts right occurs.

This issue is documented here
[http://ubuntuforums.org/showthread.php?t=1009930](http://ubuntuforums.org/showthread.php?t=1009930)

The solution is to add 
"ClientSideWithRender"="N"

to the registry.  That works fine and makes the winecfg fonts display nicely, but the fonts within the windows apps - such as word are still messed up.  

I am not sure why this is.

Here is what they look like

I am running a nvidia graphics card fwiw.

Thanks

---

### Post by NightMKoder on 2009-04-23
Hmm that doesn't look very nice. Did you install office into a separate wine prefix? If you did then you will need to prepend the prefix to run winecfg/regedit like this:
```

WINEPREFIX=~/.wine_office2007 regedit
WINEPREFIX=~/.wine_office2007 winecfg

```

Then set the same key there and see if it helps.

---

### Post by gatorbrit on 2009-04-24
> **NightMKoder said:**
> Hmm that doesn't look very nice. Did you install office into a separate wine prefix? If you did then you will need to prepend the prefix to run winecfg/regedit like this:
```

WINEPREFIX=~/.wine_office2007 regedit
WINEPREFIX=~/.wine_office2007 winecfg

```

Then set the same key there and see if it helps.

Thanks VERY much.   I had not fully understood what the wineprefix command did. So I was changing stuff in the wine directory not the wine_office2007.  I understand why the changes I was making were not having the desired effect.

Anyhow, I started over and did it all again and it works great now.

One thing, although it is a small issue is that now, the windows Office button in the top left hand corner doesn't show.  This is not a big deal as I know it is there, but before it showed up just fine (althought the fonts were blurred).

Anyhow, thanks for the help.

---

