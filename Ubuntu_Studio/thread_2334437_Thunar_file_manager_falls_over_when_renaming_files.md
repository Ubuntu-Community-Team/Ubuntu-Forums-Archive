---
title: "Thunar file manager falls over when renaming files"
date: 2016-08-19
forum: Ubuntu Studio
---

### Post by Nosphky on 2016-08-19
Since making a clean install of 16.04.1 just over a week ago, I've had Thunar 1.6.10 (which came with the UbuntuStudio distro) fall over very frequently when I rename a file.

Sometimes it happens on the first file I rename, sometimes on the 3rd or even higher. Once it has fallen over, it happens more frequently during the session.  By fall-over, I mean Thunar just vanishes from the screen and has to be restarted. The rename operation was completed each time and no data is lost (so far) so it is just annoying rather than worrying.

I never had this happen in UStudio 14.04 during the two years or so that I was using it.  Has anyone else had this happen ?

---

### Post by Nosphky on 2016-09-03
In addition to regular fallings over of Thunar when renaming files, I also get occasional fallovers when sliding a file from one directory to another.
The error message comes up "Sorry Ubuntu 16.04 has experienced an internal error" which when I look further is always something like :
"thunar crashed with SIGSEGV in g_type_check_instance_is_fundamentally_(a)" plus associated texts.
This error report is  automatically uploaded (to Ubuntu I suppose?).
It's strange that no one else has chimed in with similar problems with Thunar. It's a pity, because I quite like handling files in a graphical interface.
Are there any other recommendations for graphical file managers ?

---

### Post by PaulW2U on 2016-09-03
> **Nosphky said:**
> I never had this happen in UStudio 14.04 during the two years or so that I was using it.  Has anyone else had this happen ?

Its a known bug - [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1512120](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1512120) - which was first reported in November of last year.

There have been a various attempts at fixing the problem but its still an outstanding issue for, I would think, virtually everyone who uses Xubuntu and Ubuntu Studio 16.04.

---

### Post by Nosphky on 2016-09-08
Thank you PaulW2U for the info about the bug 1512120.

I have been to that Launchpad site tonight and find that a fix 'may' have been made.  A PPA has been set up to try modified DEB packages. I have installed those packages and renamed some 30 files without any fallover of Thunar.

Also, associated with this problem was that Thunar did not always update to reflect files dragged out or into a directory. I have dragged 30 or so files into and out of directories, both singly and in multiples and so far have not seen this aspect of the problem either.

So, if we are lucky, these modified DEB patches may well have fixed the problem.

---

