---
title: "problem with wow graphics"
date: 2010-02-26
forum: Wine
---

### Post by Arminius on 2010-02-26
half of my wow graphics are missing?
I'm not sure what the difference in mechanics is so I'll just list what's missing and maybe someone can tell me what I need to do to fix it.

the button next to remember account name
the mail border is missing
in video settings the slider bar is missing.

---

### Post by 68pontiac on 2010-03-03
Hope this helps, I took it straight from [www.wowwiki.com]("http://www.wowwiki.com/Wine_troubleshooting")

```
UI corruption

If you experience corrupt icons or interface textures, you then you may need to set the UIFaster parameter in wtf/Config.wtf

Use it like this:

Set UIFaster "x"

Where x equals:

0 – This turns off all UI acceleration
2 – Enables partial UI acceleration only.
3 – Enables all UI acceleration.

Example:

Set UIFaster "2"

The value 2 usually corrects this problem. 
```

---

