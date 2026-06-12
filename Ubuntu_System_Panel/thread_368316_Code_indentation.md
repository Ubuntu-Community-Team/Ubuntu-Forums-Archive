---
title: "Code indentation"
date: 2007-02-23
forum: Ubuntu System Panel
---

### Post by Prism on 2007-02-23
Hi there,

I'm wondering what's the tabs policy used in USP. When I open usp in gedit or in geany, I can see that in line 68 the indentation level doesn't follow the above line. I simply don't know why usp is running, because in python there's a lot of difference between <tab> and 4x<space>.

Lines 67-68 look like this, in both of my text editors:

```

67: <tab><tab>self.CompactButtons()
68: <tab><space><space><space><space><space><space><space><space>self.client.notify_add( '/apps/usp/plugins_list', self.RegenPlugins )

```

So, what's the indentation convention used here?

---

### Post by chanders on 2007-02-23
Hmmm... That shouldnt be... Initially using Eclipse it was space tabs but we have come up with the convention of tabs and not spaces with the tab width being 8chars.

I will fix the above as soon as I get to work ;-)

---

### Post by Prism on 2007-02-23
I believe that Eclipse can auto-indent the code. I'd do it myself, but I'm not familiar with the code yet so I'm afraid I'll break something.

---

