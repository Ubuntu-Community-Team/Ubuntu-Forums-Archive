---
title: "Ardour 2 problem importing files"
date: 2008-11-16
forum: Ubuntu Studio
---

### Post by kroitus on 2008-11-16
I am using Ubuntu 8.10. I want to add existing audio file to track in ardour session. And only thing I can do that, is to drag that file from file browser. I can't select any file from file selection dialog, because it gives me screen with buttons "cancel", "apply" and "ok", few combo boxes, and nothing more. Where could be a problem?

---

### Post by Stochastic on 2008-11-16
I ran into this same issue and needed to get files in so I went and compiled 2.6 from source (which allowed me to include VST support as well) and the issue disappeared.  I did find an official Launchpad bug report here: [https://bugs.launchpad.net/ubuntu/+source/ardour/+bug/279723](https://bugs.launchpad.net/ubuntu/+source/ardour/+bug/279723) that claims there are debs available from getdeb for 2.6 that fix this.

---

### Post by binbash on 2008-11-16
Try with latest release .Deb : 

[http://www.getdeb.net/app/Ardour](http://www.getdeb.net/app/Ardour)

---

### Post by kroitus on 2008-11-17
Thanks. I will try it as soon, as I will access to getdeb

---

### Post by TKoorn on 2008-11-26
So basically Ubuntu studio 8.10, which is commonly used for recording audio and things like that, comes with non-functioning audio recording software? I find that a really strange way of putting out a new release.

---

### Post by Stochastic on 2008-11-26
> **TKoorn said:**
> So basically Ubuntu studio 8.10, which is commonly used for recording audio and things like that, comes with non-functioning audio recording software? I find that a really strange way of putting out a new release.

It functions just fine, minus the import dialogue.  This is a major bug, but it's certainly not something that can't be worked around.  To import without that dialogue, a simple drag/drop import works just fine.  In general though, 8.10 is widely known to have many bugs for audio users as the dev team were working hard to get the rt kernel working before they worried about trouble shooting other bugs.

---

