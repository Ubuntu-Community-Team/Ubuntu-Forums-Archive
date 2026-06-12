---
title: "Is there a wget resume equivalent program?"
date: 2009-08-07
forum: The Cafe
---

### Post by kevdog on 2009-08-07
I have this crappy unreliable wireless connection.  Oftentimes when I'm doing a continuous large download -- like a source project, the wireless connection hangs.  If I'm using wget -- that means restarting the entire download.  Is there a way to have wget or some such program be able to resume a download without having to start from scratch?

---

### Post by dragos240 on 2009-08-07
I would LOVE that also.

---

### Post by kg84 on 2009-08-07
I wanted to download some podcasts from isc.sans.org last night. I kept getting a message saying that the connection was terminated (or something like that) before the downloads had completed.

I thought this was a wget issue, but after I tried doing the same via the browser, I kept getting the same result. 

(I eventually got the podcasts I wanted via wget after a few hours).

A resume function would be well handy :)

---

### Post by zekopeko on 2009-08-07
wget -c path-to-file ?

you also might try Gwget or Kget.

---

### Post by kg84 on 2009-08-07
> **zekopeko said:**
> wget -c path-to-file ?

you also might try Gwget or Kget.


When in doubt, read the manual, eh? :)

Thanks for pointing this out.

Am trying the -c switch now, but the downloads seem to be working perfectly :D

---

