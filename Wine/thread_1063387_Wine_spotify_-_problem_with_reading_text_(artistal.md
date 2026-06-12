---
title: "Wine spotify - problem with reading text (artist/album)"
date: 2009-02-07
forum: Wine
---

### Post by Plexus81 on 2009-02-07
Running:
Ubuntu 8.10
Wine 1.0.1
Spotify

Have problem reading the text inside spotify. The text redraw when I put the cursor over the text, and it will be displayed correct. But if I don't do that the text is all blury.. 

Do anybody have an solution on this problem?

(sorry my english :) )

---

### Post by Plexus81 on 2009-02-12
> **Plexus81 said:**
> Running:
Ubuntu 8.10
Wine 1.0.1
Spotify

Have problem reading the text inside spotify. The text redraw when I put the cursor over the text, and it will be displayed correct. But if I don't do that the text is all blury.. 

Do anybody have an solution on this problem?

(sorry my english :) )

anybody?

---

### Post by mattech420 on 2009-02-18
I had the same problem. Simply copy this:

[Software\\Wine\\X11 Driver] 1210627404
"ClientSideWithRender"="N"

go into your home folder and enable view hidden files. go to .wine then open user.reg in a text editor. go all the way to the bottom and paste. it should look like this:

[Software\\Wine\\MSHTML\\0.1.0] 1214276830
"GeckoPath"="C:\\windows\\gecko\\0.1.0\\wine_gecko"

[Software\\Wine\\WineDbg] 1220822491

[Software\\Wine\\X11 Driver] 1210627404
"ClientsideWithRender"="N"


now open any wine program and yay!!! go ahead and sing and laugh and be joyful.

---

