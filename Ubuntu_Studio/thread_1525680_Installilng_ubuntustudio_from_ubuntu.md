---
title: "Installilng ubuntustudio from ubuntu?"
date: 2010-07-07
forum: Ubuntu Studio
---

### Post by dillandriskell on 2010-07-07
Hi! I don't have a DVD write drive, and there doesn't seem to be any options for CD's for studio. So I googled alternatives and I found this thread: [http://ubuntuforums.org/archive/index.php/t-592295.html](http://ubuntuforums.org/archive/index.php/t-592295.html)

Basically, several users suggested installing the current version of ubuntu and then installing ubuntu studio with just "sudo apt-get install"

This is great and very convenient for me, but this thread is clearly for an older version. Can anybody please enlighten me as to how this would be done with 10.4?

---

### Post by ronnielsen1 on 2010-07-07
The packages are the same, so it shouldn't be an issue installing it in the same way

---

### Post by hansdown on 2010-07-07
Hi dillandriskell.

If you search for 

```
ubuntustudio
```

in synaptic,

You can install any of the packages.

---

### Post by bluesscream on 2010-07-09
but maybe, if you install ubustu over a genuine ubuntu, you run into issues with rights management, groups and priorities: Make sure your user is member of groups audio, disk and video and there are entries like "@audio   -  rtprio     99" in files /etc/security/limits.d/audio.conf and in /etc/security/limits.conf

---

