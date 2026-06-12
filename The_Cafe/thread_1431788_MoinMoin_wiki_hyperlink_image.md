---
title: "MoinMoin wiki hyperlink image?"
date: 2010-03-17
forum: The Cafe
---

### Post by humphreybc on 2010-03-17
Hi everyone,

I'm trying to create a "Download Now!" button on our wiki page. I've got an image of a button attached to the page and inserted, but I want it to download a PDF when someone clicks on it.

Is this even possible in MoinMoin?

(The wiki page in question is [https://wiki.ubuntu.com/ubuntu-manual](https://wiki.ubuntu.com/ubuntu-manual))

Thanks!

---

### Post by the yawner on 2010-03-17
Hmm... From [Moinmoin]("http://moinmo.in/MacroMarket/ImageLink") I found:

> 
Old way:

<<ImageLink(image,target[,width=width[,height=height]][,alt=alttag])>>

New way:

[[target|{{image|alt|width=123,height=456}}]]

Which one were you using?

---

### Post by humphreybc on 2010-03-17
Yay! Thankyou!

---

### Post by the yawner on 2010-03-17
I see you've implemented it just fine.
Glad to be of help. :)

---

