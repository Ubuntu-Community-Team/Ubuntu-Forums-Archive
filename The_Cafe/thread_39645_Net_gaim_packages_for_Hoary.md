---
title: "Net gaim packages for Hoary"
date: 2005-06-05
forum: The Cafe
---

### Post by simprix on 2005-06-05
I have created updated gaim packages for Hoary.

Packages include

gaim-1.3.0
gaim-data-1.3.0
gaim-encryption-2.37


Add this to your /etc/apt/sources.list

deb [http://simprix.net/ubuntu](http://simprix.net/ubuntu) ./


Let me know if there are any bugs

---

### Post by Gtaylor on 2005-06-05
Isn't this in backports or something? I'm running 1.3.0 right now using Ubuntu repositories.

---

### Post by simprix on 2005-06-05
Are you running the staple feed

---

### Post by TravisNewman on 2005-06-06
staple feed?
You mean the stable backports repositories?

jdong has backported gaim 1.3.0 and it's not in extras or staging. So even if you're only running the stable backports repo, you're good. 

If you aren't familiar with backports, it's repositories set up to "backport" packages from breezy and elsewhere into Ubuntu, without breaking things. Since Ubuntu's development on new versions ceases at realease, this project fills the gap.

If you are good at packaging, you might want to think about contributing to the backports.

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)
[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

---

