---
title: "parole media player gives me green screen-will not install demuxer"
date: 2015-12-17
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-12-17
I was just testing PMP on xubuntu (proposed open) and I get a green screen. Do I need Mux for all formats?

Regards..

---

### Post by ventrical on 2015-12-17
Totally busted.

When I install the software I get this ping pong status bar and then it just disappears.

---

### Post by tista on 2015-12-17
Hi,

I just saw your 1st attached screen-shot... Though I have not any clue but it seems there's something wrong with XV output error and/or Xorg user-space driver (especially DRI2 or so), maybe. Or recently happened kernel-space changing in your GPUs?

Regards,
Tista

---

### Post by flocculant on 2015-12-17
try setting to not use clutter - known bug

[https://launchpad.net/ubuntu/+source/parole/+bugs](https://launchpad.net/ubuntu/+source/parole/+bugs)

really quite [https://www.youtube.com/watch?v=b6Bv887-JlM](https://www.youtube.com/watch?v=b6Bv887-JlM)

---

### Post by ventrical on 2015-12-17
> **tista said:**
> Hi,

I just saw your 1st attached screen-shot... Though I have not any clue but it seems there's something wrong with XV output error and/or Xorg user-space driver (especially DRI2 or so), maybe. Or recently happened kernel-space changing in your GPUs?

Regards,
Tista

I did swap the hdd with xubuntu install to another machine with nVidia graphics and then back to original machine.  Usually xubuntu is somewhat immune to this proceedure but it could have inserted somthing into a config file.

To clarify the above - xubuntu (as most of the Buntus) has an amazing property to jockey drivers from machine to machine and back again without any major breakage - so perhaps (if this be the case) it may be a sign of the times in development.

Regards..

---

### Post by ventrical on 2015-12-17
> **flocculant said:**
> try setting to not use clutter - known bug



Awesome. Thanks you guys.

Regards..

---

### Post by MikeMecanic on 2015-12-18
> **ventrical said:**
> Awesome. Thanks you guys.

Regards..

Same here for the green screen.  Then set the Video Output to : X Window System (X11/XShm/XV) and it came back to normal.  Download  video sample there: [http://www.sample-videos.com](http://www.sample-videos.com).

---

### Post by ventrical on 2015-12-18
> **MikeMecanic said:**
> Same here for the green screen.  Then set the Video Output to : X Window System (X11/XShm/XV) and it came back to normal.  Download  video sample there: [http://www.sample-videos.com](http://www.sample-videos.com).

Thanks for the confirm. :)

Regards..

---

