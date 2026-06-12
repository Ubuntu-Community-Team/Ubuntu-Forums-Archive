---
title: "anyone know how this blog is done?"
date: 2006-08-08
forum: The Cafe
---

### Post by pompeyjohn on 2006-08-08
I really like this [blog ]("http://www.plasticbag.org/")- does anyone know how it is done? I have emailed the author, but he is not replying....

I have had a look at the source code, and cant find anything - there is the following:

// Copyright (c) 1996-1997 Athenia Associates.
// [http://www.webreference.com/js/](http://www.webreference.com/js/)

But nothing there. I am using Wordpress at the moment, but looking for a change.

Cheers
John

---

### Post by bjweeks on 2006-08-08
Xhtml?

---

### Post by picpak on 2006-08-08
It looks real simple: just a fixed-width, left-aligned and padded <div> with a background image.

---

### Post by pompeyjohn on 2006-08-08
thanks - I thought it was a bit more complicated. I have *no idea* about javascript and I saw a load of that in the source.

I really like the hyperlink highlighting - do you reckon that is done in the style sheet? 

(I am kinda new to web development btw)

---

### Post by picpak on 2006-08-08
Yes, it's done in the style sheet.

```
a {background-color: blue}
```

---

