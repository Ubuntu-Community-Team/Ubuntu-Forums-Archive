---
title: "system variables"
date: 2008-05-21
forum: Windows
---

### Post by anystupidname on 2008-05-21
I have 2 questions:

1) Is there a *COMPLETE* list of system variables? I keep discovering obscure ones that are not usually listed in the normal charts.
[Example table]("http://www.atlguide2000.com/windowvista/index.php?aid=235")

2) Why do some variables not work on some machines?
For example: %appdata% always seems to work but %localappdata% doesn't.

---

### Post by LaRoza on 2008-05-21
> **anystupidname said:**
> I have 2 questions:

1) Is there a *COMPLETE* list of system variables? I keep discovering obscure ones that are not usually listed in the normal charts.
[Example table]("http://www.atlguide2000.com/windowvista/index.php?aid=235")

2) Why do some variables not work on some machines?
For example: %appdata% always seems to work but %localappdata% doesn't.

0. Yes, type "set" I think and it will give a list. Anyone can set a variable, so they are not all "standard". Also take into account the version of Windows being used.

1. It depends on the version and configuration. "localappdata" is for non roaming profiles and is probably specific to a version of Windows.

---

