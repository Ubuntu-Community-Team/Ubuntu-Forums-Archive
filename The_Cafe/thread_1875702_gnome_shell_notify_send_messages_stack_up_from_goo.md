---
title: "gnome shell notify send messages stack up from google voice"
date: 2011-11-05
forum: The Cafe
---

### Post by sdowney717 on 2011-11-05
[https://bugzilla.redhat.com/show_bug.cgi?id=693207](https://bugzilla.redhat.com/show_bug.cgi?id=693207)

I get calls coming in and the info stays down there unless I manually remove every one.

So is this a google voice video chat issue, has anyone else noticed this?
running this commands demonstrates it can be transient, and I wonder if this could be customizable behavior. Some people might like to keep them around, some might not.

notify-send --hint=int:transient:1 Test

---

