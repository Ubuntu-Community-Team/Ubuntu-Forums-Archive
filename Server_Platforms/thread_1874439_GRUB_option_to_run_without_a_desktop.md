---
title: "GRUB option to run without a desktop"
date: 2011-11-03
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2011-11-03
Having installed a desktop in 11.04/11.10 and set up the server through its use, is there any code that could be used to offer the option of not loading a desktop at startup?

Alternatively, any terminal commands that would deactivate/activate the desktop, and either way save on resources?

---

### Post by volkswagner on 2011-11-03
Check out this thread as this was just discussed.  Possibly there is a bug and should be reported if the grub option no longer works.

[http://ubuntuforums.org/showthread.php?t=1872000](http://ubuntuforums.org/showthread.php?t=1872000)

---

### Post by ChrisRChamberlain on 2011-11-03
volkswagner

Thanks for your reply - not sure I understand exactly what the final resolution was?
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force text"
```does not work in 11.10, so perhaps there is a bug.

---

### Post by volkswagner on 2011-11-03
The way I read it, is use the patch from this thread.

[http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

Then the OP seemed to also needed to apply the "chvt 1" to  /etc/rc.local from the following post.

[http://ubuntuforums.org/showpost.php?p=11413474&postcount=13](http://ubuntuforums.org/showpost.php?p=11413474&postcount=13)

---

### Post by ChrisRChamberlain on 2011-11-04
volkswagner

Thanks for the explanation - will give it a try

---

