---
title: "question about gstreamer"
date: 2005-11-24
forum: Ubuntu Backports
---

### Post by duffman25 on 2005-11-24
Hi

planet gnome news says that in december gstreamer 0.10 will be released. I wanted to ask if this would qualify for a valid backport, I suspect no, because I imagine there has been an api change... but maybe someone can bring more info on this.

---

### Post by GazaM on 2005-11-25
I doubt gstreamer is eligible for backporting as it does include API changes and hence apps need to be updated to use the newer version... so backporting gstreamer would also require backporting every single app that uses gstreamer, which is just not an option IMO. Not to mention the fact that some developers wont port their programs until after it is released.

---

