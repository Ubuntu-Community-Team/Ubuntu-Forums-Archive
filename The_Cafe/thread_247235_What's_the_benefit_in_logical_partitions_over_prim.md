---
title: "What's the benefit in logical partitions over primary?"
date: 2006-08-30
forum: The Cafe
---

### Post by K.Mandla on 2006-08-30
Excuse my ignorance toward the logical partition, but I'm trying to pin down an answer as to why I would use one over a primary partition. I've been to wikipedia and a couple of obscure techie sites, but all I really want to know is ... what's the use? ;)

---

### Post by Jucato on 2006-08-30
Because of some historical/technical reasons, you are limited only to having 4 primary partitions per drive. Extended partitions (a primary partition that contains logical partitions) were developed so that you could have more than 4 partitions. They're practically the same, AFAIK.

---

### Post by K.Mandla on 2006-08-30
Okay, that's what I was wondering. I couldn't see why I would pick one over the other, but I suppose if I was making separate partitions for a bunch of different things, it would make sense. Thanks for the help! Cheers!

---

### Post by mips on 2006-08-30
If you ever intend using BSD you need a primary partition. It does not play nicely with logical partitions at all ;)

---

