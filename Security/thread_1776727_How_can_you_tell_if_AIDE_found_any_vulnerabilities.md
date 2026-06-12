---
title: "How can you tell if AIDE found any vulnerabilities"
date: 2011-06-06
forum: Security
---

### Post by toolmania1 on 2011-06-06
[FONT=Calibri] How can you tell ifAIDE found anything?  I read the tutorial in this forum, but it does not show me examples that I can compare to see if AIDEhas found anything.[/FONT]

---

### Post by crispy_420 on 2011-06-07
It basically looks at files changed. You have to establish a baseline and look for files changed. It will not actively protect you from threats but rather show you after the fact. Symantic has a good read on it here:

[http://www.symantec.com/connect/articles/securing-linux-aide](http://www.symantec.com/connect/articles/securing-linux-aide)

Near the end it explains how to use near the end to find if you have already been compromised.

Another guide here as well: [http://www.howtoforge.com/linux-security-notes-aide-file-integrity](http://www.howtoforge.com/linux-security-notes-aide-file-integrity)

---

