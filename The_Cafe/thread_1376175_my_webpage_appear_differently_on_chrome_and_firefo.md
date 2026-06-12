---
title: "my webpage appear differently on chrome and firefox, images have borders on firefox:S"
date: 2010-01-08
forum: The Cafe
---

### Post by chriskin on 2010-01-08
i'm making a page in order to learn some html and i am experiencing this problem: the page's images (the ones in a table i have made at least) have borders in firefox even though border is set to 0

screenshots from chrome and firefox :

---

### Post by Frak on 2010-01-08
You need to reset using CSS, or do a 

```
img { outline: none; border: none; }
```

In your stylesheet.

---

### Post by NoaHall on 2010-01-08
> **chriskin said:**
> i'm making a page in order to learn some html and i am experiencing this problem: the page's images (the ones in a table i have made at least) have borders in firefox even though border is set to 0

screenshots from chrome and firefox :

Oh. I forgot to look at the second screenshot. And a word of advice - don't use heavy images for a background, don't use tables.

---

### Post by chriskin on 2010-01-08
@frak : i'll try it now

@NoaHall : what do you mean that you don't see any?

---

### Post by NoaHall on 2010-01-08
> **chriskin said:**
> @frak : i'll try it now

@NoaHall : what do you mean that you don't see any?

I only looked at the first screenshot.

---

### Post by Frak on 2010-01-08
What NoaHall said, don't use tables for layout. Use them for tabular data, use div's, floats, and positioning for everything else.

---

### Post by chriskin on 2010-01-08
i'll stay away from tables in the future then - it worked with what frak said 

thanks :)

---

### Post by Frak on 2010-01-08
> **chriskin said:**
> i'll stay away from tables in the future then - it worked with what frak said 

thanks :)
Cheers

---

