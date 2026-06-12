---
title: "Spotify install problems"
date: 2010-07-15
forum: Wine
---

### Post by malcmail on 2010-07-15
When trying to install wine I get the following problem:-

```
malc@new-server:~$ wine spotify.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:shell:SHAutoComplete stub

```

Although the install window comes up it won't actually install but this is problem number 1. I'm using wine1.2 on 10.04.  I can't find anything to help me out - I've tried some winetricks inc comctl32 but no joy.

Thanks for any help in advance.

---

### Post by hikaricore on 2010-07-15
Sadly, there are no actual errors in the output you've posted, so it's not real helpful.
I assume you fixed your problems from your other thread on this same topic or is this a continuation of that issue posted in a new thread for no good reason?

---

### Post by malcmail on 2010-07-15
Is the Cannot find Windows etc not a problem?

Actually got it running now - with varyin degrees of success. Now no sound - claiming a problem with sound card. Which must be a WINE issue as I've no started using Grooveshark in Ubuntu instead and it works perfectly instead :)

---

### Post by hikaricore on 2010-07-15
Fixme messages are debug output and can generally be ignored.

---

