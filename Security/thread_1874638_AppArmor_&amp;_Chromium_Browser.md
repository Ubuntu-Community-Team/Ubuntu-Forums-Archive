---
title: "AppArmor &amp; Chromium Browser"
date: 2011-11-03
forum: Security
---

### Post by Blutkoete on 2011-11-03
Hello!

I've put all apparmor profiles in the enforce mode, including the default Chromium Browser profile. I had to make some adjustments so that Chromium was able to start up, including this one:

```
@{PROC}/[0-9]*/oom_score_adj rw,
```

I'm not happy about that. If I understand correctly, that'll allow Chromium to write to *oom_score_adj *of every process, doesn't it? Is there a placeholder to only allow access to the proc-folder of the process itself?

Thank you very much,

Blutkoete

---

### Post by Dangertux on 2011-11-03
You shouldn't need that for Chromium to be functional (that I'm aware of) it's not in my chromium profile.

That being said,  I do see it in a couple of Chromium profiles, so maybe I am just not noticing some innate functionality isn't working that I never utilize.

---

### Post by Blutkoete on 2011-11-03
Thank you!

You're right, it's not needed, the reason Chromium didn't start up was that the regular expression

  ```
/sys/devices/pci[0-9]*/[0-9]*/resource r,
```

didn't match my computer because the folder e.g. is named

  ```
/sys/devices/pci0000:00/...
```

on my machine. It's probably a good thing if I only allow things that provide functionality needed for my daily work.

Maybe it's a good idea if I google for what I'm actually allowing Chromium access to :).

---

### Post by Dangertux on 2011-11-03
Glad it worked out for you.

---

### Post by Blutkoete on 2011-11-03
Just for the records: The problem was that my /sys/devices/pci** folder has a subfolder more than specified in the profile.

So I had to add a new rule which included an additional */[0-9]*/*.

---

