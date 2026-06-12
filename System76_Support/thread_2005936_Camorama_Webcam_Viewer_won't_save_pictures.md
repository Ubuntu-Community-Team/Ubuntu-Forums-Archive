---
title: "Camorama Webcam Viewer won't save pictures"
date: 2012-06-18
forum: System76 Support
---

### Post by colinmccubbin on 2012-06-18
I just received a new pan9. Camorama Web Viewer worked but wouldn't save a picture reporting "Could't create folder ~/Webcam_Pictures"

Since ~ should be my home directory I went there and created the folder, still the same problem.

Googled, and found a debian bug report saying that it was treating ~ as literal text, and not resolving it to the user's home folder.

The fix is while in Camorama to go to Edit>Preferences and change the local folder to save to to your full path, eg /home/currentUserName/Webcam_Pictures

Now it works and saves pics there. :P

Probably the same problem occours on all new systems shipped..?

---

### Post by colinmccubbin on 2012-06-18
BTW Here is the link to the Bug Report:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=219328]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=219328")

---

### Post by isantop on 2012-06-18
I believe systems are currently shipping with Cheese rather than Camorama, so I don't think is currently affecting most of our users.

---

