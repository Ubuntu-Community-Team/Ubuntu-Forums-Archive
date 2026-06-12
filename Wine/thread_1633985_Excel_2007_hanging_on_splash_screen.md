---
title: "Excel 2007 hanging on splash screen"
date: 2010-11-29
forum: Wine
---

### Post by duncan_bayne on 2010-11-29
Excel 2007 installed fine for me under Wine, but it appeared to hang on the splash screen during startup.

It turns out that the splash screen was hiding a dialog prompting for name and initials; this dialog is displayed infront of the splash screen on Windows.

Starting Excel with the /e command-line option suppresses the splash screen, so the dialog is visible.  Once you've entered your name and initials the first time, the dialog is never displayed again and you can start Excel normally.

---

