---
title: "Wine error"
date: 2008-12-27
forum: Wine
---

### Post by Static_Flow on 2008-12-27
Ok so wine was working fine until today when an upgrade came out for wine I installed it as it told me but now when i try and run wine filename I get this error:

           ```
wine client error:82: version mismatch 339/346.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

```

any suggestions.

---

### Post by aviscich on 2008-12-29
I am having the exact same problem.  I know there's gotta be an easy solution to this...

---

### Post by faith1215 on 2009-01-06
I think I found a solution:

```

$wineserver -k 15
$wineserver

```

When I ran it, it fixed my issue. Though, I still don't quite understand what happened.

---

