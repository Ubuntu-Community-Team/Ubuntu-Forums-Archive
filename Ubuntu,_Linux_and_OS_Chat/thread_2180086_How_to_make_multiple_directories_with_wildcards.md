---
title: "How to make multiple directories with wildcards?"
date: 2013-10-11
forum: Ubuntu, Linux and OS Chat
---

### Post by nir2 on 2013-10-11
Hi,
I want to make multiple directories this way:
mkdir dir[0-9]
expecting to create ten directories dir0...dir9
it insteads creates directory dir[0-9]
please help how to use wildcards this way.
Thank in advance 
Nir

---

### Post by steeldriver on 2013-10-11
Try 

```
mkdir dir[COLOR=#0000ff]**{0..9}**[/COLOR]
```

FYI you can create padded sequences as well e.g.

```
mkdir dir[COLOR=#0000ff]**{000..009}**[/COLOR]
```

---

### Post by nir2 on 2013-10-11
/

---

### Post by nir2 on 2013-10-11
Thank you very much steeldriver.
I appreciate your quick reply.

---

### Post by steeldriver on 2013-10-11
No problem - welcome to the forum btw

---

