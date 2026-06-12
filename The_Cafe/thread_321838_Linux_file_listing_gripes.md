---
title: "Linux file listing gripes"
date: 2006-12-19
forum: The Cafe
---

### Post by mahy on 2006-12-19
Hi there people,

i'm sorry if this was already been discussed, but it's something that drives me nuts. I know diversity should be an advantage of Linux, but file listing is way too horrible. This how it works in Linux:

Case-sensitivity:

1) all capitalized filenames first 
2) all capitalized filenames last
3,4) case-insensitive; in such case they're two possibilities (foo followed by Foo or vice versa)

Handling of hidden files:

a) all hidden files first
b) all hidden files last
c,d) mix 'em up; again, either .foo followed by foo or vice versa


Priorities also figure: 2-b will produce different results than b-2. Now, it's 32 possible ways of displaying files in a directory (correct me if i'm wrong). Midnight Commander, Opera, Xmms, all these programs display directory contents differently. Any chance of standardizing it?

---

### Post by DoctorMO on 2006-12-19
it should be hidden files first '.' then capitals, then lower case just as it is in ls.

only changing options should allow a different system.

---

