---
title: "Monthly Shell script"
date: 2011-09-02
forum: Server Platforms
---

### Post by Jay89 on 2011-09-02
Hello, does anyone know of a way to have a shell script run on the first Saturday of every month only? I guess it can only be done using an IF statement as part of the script but I'm having trouble getting it right. What I have right now is:

dow=$(date +%u)
dom=$(date +%d)
if ((dow = 6)) && ((dom < 7)) ; then

[B]RUN THE SCRIPT
[/B]
fi
exit 1

But I just realized that's running every day since the first. Can someone help me make it run on the first saturday of every month? Or at the very least. the first day of every month?

Thanks

---

### Post by Toz on 2011-09-02
See: [http://ubuntuforums.org/showthread.php?p=11138145]("http://ubuntuforums.org/showthread.php?p=11138145")

---

