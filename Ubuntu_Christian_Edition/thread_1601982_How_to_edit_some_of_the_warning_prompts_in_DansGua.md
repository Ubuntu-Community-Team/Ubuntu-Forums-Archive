---
title: "How to edit some of the warning prompts in DansGuardian"
date: 2010-10-20
forum: Ubuntu Christian Edition
---

### Post by iehichez on 2010-10-20
Hi. I am new to this forum and I was searching for a thread in reference to Dans Guardian with information about how to edit some of the warning prompts that the parental control software displays (if possible). Please, forgive me if this has been addressed elsewhere and I did not see it. My issue is that I have a 6-year-old boy using our family computer in the living room. Sometimes while searching in YouTube many pages will be blocked as expected due to one or more weighted phrases, and the reason most of the times is listed as some foreign language and the category "Pornography" and it shows a box with some examples of the (while not explicit still awkward) 'terms' found on the page. Well, I found myself having to explain to my son a water-down definition of the word "pornography" as well as some of the items listed in the box. I would like it to read "Inappropriate content" instead of "Pornography" and nothing displayed in the box. So that we don't have to explain these terms again every time other small kids (girls included) come to play at our house. If anyone knows how to accomplish this, please let me know. Thx.

---

### Post by david_kt on 2010-10-21
You could edit as follow:

```
gksudo gedit /etc/dansguardian/languages/ukenglish/template.html
```

If you use other language, replace ukenglish with your language.

DK

---

