---
title: "Installing Chrome Browser and Adobe Reader in Raring Ringtail"
date: 2013-04-05
forum: Ubuntu Development Version
---

### Post by trotter1985 on 2013-04-05
Just downloaded and installed beta 2.  Three critical (for me)
applications are (1) dropbox; (2) google chrome browser and
(3) adobe reader.  Dropbox went on without a hitch but
google chrome balked and reported a library error.  Also,
acroread is not to be found in the "partners" repository.
Workarounds appreciate.

---

### Post by pfeiffep on 2013-04-05
Google Chromium is supported - Chrome is not

---

### Post by howefield on 2013-04-05
Try this thread for the chrome issue

[http://ubuntuforums.org/showthread.php?t=2132483](http://ubuntuforums.org/showthread.php?t=2132483)

and here for the pdf reader

[https://help.ubuntu.com/community/AcrobatHowTo](https://help.ubuntu.com/community/AcrobatHowTo)

---

### Post by trotter1985 on 2013-04-05
Thanks for the howefield (forums moderator) for the links to
other threads.  The google chrome issue is resolved after I
did the two required downloads as instructed.  But the
Adobe Reader link did not work.  Of course, the wget part is
fine, but when I tried to install the file, I got this error:

  adobereader-enu depends on libgtk2.0-0 (>= 2.4)

There must be a download link somewhere for this
one?! 

Thankx

---

### Post by zika on 2013-04-05
> **trotter1985 said:**
> Thanks for the howefield (forums moderator) for the links to
other threads.  The google chrome issue is resolved after I
did the two required downloads as instructed.  But the
Adobe Reader link did not work.  Of course, the wget part is
fine, but when I tried to install the file, I got this error:

  adobereader-enu depends on libgtk2.0-0 (>= 2.4)

There must be a download link somewhere for this
one?! 

Thankx

[http://packages.ubuntu.com/raring/libgtk2.0-0](http://packages.ubuntu.com/raring/libgtk2.0-0)

At mine place it came from archive.ubuntu.com ...

---

