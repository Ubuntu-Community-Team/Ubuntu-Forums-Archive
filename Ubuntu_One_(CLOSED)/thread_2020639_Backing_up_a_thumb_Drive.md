---
title: "Backing up a thumb Drive"
date: 2012-07-08
forum: Ubuntu One (CLOSED)
---

### Post by Jonas thomas on 2012-07-08
Hello,
I have my personal thumb drive that I bounce between work(windows) and home(ubuntu) on.
Currently, I backup my gtd list locally on my laptop hard drives, but I wound't mind backing up my entire thumb drive with ubuntu one.
I suppose at some point, I just do everything from the cloud, but at this point, I just want to back up my thumb drive.

Is there a painless how to that someone can point me to?
(Still on 10.04)
Thanks,

---

### Post by thnewguy on 2012-07-10
I suppose you could put a script on your desktop which would sync all the data from your thumb drive to your Ubuntu One folder. Then you could just click the script's icon whenever you plugged in the thumb drive. The script would probably look a bit like this:

#!/bin/bash
rsync -av /media/thumb-drive ~/Ubuntu One/Thumb

Which the path name to your thumb-drive changed to whatever it is on your system.

---

### Post by Jonas thomas on 2012-07-14
> **thnewguy said:**
> I suppose you could put a script on your desktop which would sync all the data from your thumb drive to your Ubuntu One folder. Then you could just click the script's icon whenever you plugged in the thumb drive. The script would probably look a bit like this:

#!/bin/bash
rsync -av /media/thumb-drive ~/Ubuntu One/Thumb

Which the path name to your thumb-drive changed to whatever it is on your system.
Thanks... I will give that a go and see how it goes.

---

