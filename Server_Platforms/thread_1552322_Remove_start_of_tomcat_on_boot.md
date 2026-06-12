---
title: "Remove start of tomcat on boot"
date: 2010-08-13
forum: Server Platforms
---

### Post by Nimridil on 2010-08-13
Hey fellow Ubuntu users.
Does anybody know how to stop tomcat 6 from loading on startup? It is not listed in System > Preferences > Startup Application but still starts with the system.
I found this old [thread]("http://ubuntuforums.org/showthread.php?t=391714"), but I don't have the exact same files and folders as in the last post. In /etc/ I have rc0.d through rc6.d and rcS.d
In terms of files, those only contain:
> K08tomcat6
K08tomcat6
S92tomcat6
S92tomcat6
S92tomcat6
S92tomcat6
K08tomcat6
but no S20tomcat6 or K20tomcat6
:confused:

---

