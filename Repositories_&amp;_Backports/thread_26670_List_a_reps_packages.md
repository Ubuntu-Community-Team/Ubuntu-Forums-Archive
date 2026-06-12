---
title: "List a reps packages?"
date: 2005-04-13
forum: Repositories &amp; Backports
---

### Post by titus on 2005-04-13
Is it possible to list which packages a particular rep offers? 

Thanks,

Titus.

---

### Post by jdong on 2005-04-13
Take a look at the Packages.gz file in every repo.

---

### Post by titus on 2005-04-13
thanks. it would be nice to do this from apt-get if possible, is there a way?

:)

---

### Post by jdong on 2005-04-13
Look into the **apt-cache** command, particularly **apt-cache dump**. You might want to use grep or awk to filter the information you want ;)

---

