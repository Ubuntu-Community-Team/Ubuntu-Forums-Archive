---
title: "PAE in 32bit generic by default?"
date: 2008-10-12
forum: The Cafe
---

### Post by hyper_ch on 2008-10-12
I've seen quite a few threads from people that have more than 4gb ram and run a 32bit OS and ask why they can't see more than those 4gb ram.

I know the server kernel has PAE enabled by default which allows to have up to 64gb ram on a 32 (or rather 34bit) system and I wonder, why the generic kernel doesn't have it enabled also by default.

Any ideas?

---

### Post by Canis familiaris on 2008-10-12
> **hyper_ch said:**
> ... 64gb ram on a 32 (or rather **34bit**) system and 

Any ideas?

36 bit I think...

---

### Post by chungy on 2008-10-12
I believe (correct me if I'm wrong) that PAE uses up more memory for simply addressing memory, so it would be disadvantageous to enable for less-than-4GB systems (which is the vast majority of desktops/laptops).

If you need more than 4GB, I would probably just install or configure a PAE-enabled kernel...

---

### Post by mihai.ile on 2008-10-12
So then at least should exist a very easy howto page on the wiki so that the average user can do it?

---

