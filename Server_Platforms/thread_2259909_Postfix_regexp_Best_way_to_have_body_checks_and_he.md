---
title: "Postfix regexp: Best way to have body_checks and header_checks share a few lines"
date: 2015-01-07
forum: Server Platforms
---

### Post by robsoles on 2015-01-07
I have some lines in my body_checks that I wish repeated in my header_checks file and for now I am just re-copying them from which-ever of the two files involved I modify them in to the other file manually.

When it occurred to me that it would be great if I could use a simily of '#include: "otherfile.ext"' in both of those and put the common lines in a third file I started searching for methods that might have been implemented that might allow me anything similar - I had such a lack of luck with that I've decided to risk ridicule and ask;

Is there anything even remotely similar to '#include' I can use in those files?

---

