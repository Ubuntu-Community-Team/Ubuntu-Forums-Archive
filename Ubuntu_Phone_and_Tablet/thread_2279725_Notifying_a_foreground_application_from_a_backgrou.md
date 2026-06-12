---
title: "Notifying a foreground application from a background service?"
date: 2015-05-25
forum: Ubuntu Phone and Tablet
---

### Post by CaesarS on 2015-05-25
[Assuming a background service application is possible]

Is it possible & how would the background service notify the foreground application?

Many Thanks, Caesar.

---

### Post by SeijiSensei on 2015-05-25
Perhaps an easier approach is to make the background service a daemon and have the foreground application poll it periodically.

---

