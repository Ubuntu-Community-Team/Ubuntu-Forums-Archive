---
title: "Ubuntu One icon missing ?"
date: 2010-05-03
forum: Ubuntu One (CLOSED)
---

### Post by Peterfc on 2010-05-03
I had an icon in my panel at the top of my screen, when Ubuntu One was updating i could see it updating and i could click on connect if needed. Now after the upgrade to Lucid i have no icon on my Panel. I need this so i can make sure that files are uploaded for when i get home from work.

Thanks for reading

---

### Post by duanedesign on 2010-05-03
The Ubuntu One applet has been replaced by the Ubuntu One Preferences Panel. This is accessed by going to the me Menu and selecting Ubuntu One. Additionally you can access it from System > Preferences > Ubuntu One. The Emblems on the files should accurately portray the status of the file. Also at the top of the Ubuntu One Preferences Panel there is some text showing the status. Finally the u1sdtool has a -s option for getting the syncdaemon status.

u1sdtool -s

some other neat u1sdtool options

u1sdtool --waiting-metadata
u1sdtool --waiting-content
u1sdtool --current-transfers

---

