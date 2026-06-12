---
title: "Will KMS get rid of the annoying Verbose flickering at shutdown?"
date: 2009-06-03
forum: The Cafe
---

### Post by BOXXHED on 2009-06-03
I hope so :(

---

### Post by Mazza558 on 2009-06-03
I thought it needed Plymouth as well to achieve that?

If so, it's not happening. We're not getting Plymouth for Karmic because there's a new boot speed aim: 10 seconds. And that's not possible if we wanted to have Plymouth as well.

---

### Post by ssam on 2009-06-03
KMS means the graphics mode can be controlled by the kernel, and so gives quick clean switchs in and out of X. plymouth is a splash screen program that uses KMS to give nice graphics during boot. so you could use something other than plymouth to get smooth boots and shutdown, it would be using KMS.

---

