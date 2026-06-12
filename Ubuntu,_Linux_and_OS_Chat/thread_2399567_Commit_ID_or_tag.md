---
title: "Commit ID or tag"
date: 2018-08-27
forum: Ubuntu, Linux and OS Chat
---

### Post by its_bigB on 2018-08-27
Keeping records on source codes in Git, which one is the best suitable? Commit ID or tag?

Tag more user friendly, but in general permissions someone can move to a different branch easily.

Commit IDs are unique, but not readable.

---

### Post by spjackson on 2018-08-28
I'm not sure that I fully understand what you are asking. If you need to be able to identify precisely the source code that constitutes a specific release, the commit ID is what you need. A tag such as release_x_y_z can be deleted or moved. However, tags are convenient and I would have strong words with a colleague who moved a release tag without good reason (such as it having been applied to the wrong commit in the first place). Perhaps you can include both in whatever records you are referring to.

---

### Post by its_bigB on 2018-08-28
> **spjackson said:**
> I'm not sure that I fully understand what you are asking.

Yes, you got what I meant correctly.

> **spjackson said:**
> If you need to be able to identify precisely the source code  that constitutes a specific release, the commit ID is what you need. A  tag such as release_x_y_z can be deleted or moved. However, tags are  convenient and I would have strong words with a colleague who moved a  release tag without good reason (such as it having been applied to the  wrong commit in the first place). Perhaps you can include both in  whatever records you are referring to.

I've the same concern. Someone could change or delete a tag. And it's much meaningful to human. Commit ID is unique and generated on each change.

I want to uniquely identify a particular source once someone pushed. That reference shouldn't change.

---

### Post by spjackson on 2018-08-28
> **its_bigB said:**
> I want to uniquely identify a particular source once someone pushed. That reference shouldn't change.
If you need a guarantee that it will never change, you need the commit ID: there's no alternative, AFAIK.

---

