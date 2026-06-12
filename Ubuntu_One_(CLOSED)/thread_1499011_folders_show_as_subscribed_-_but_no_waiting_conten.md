---
title: "folders show as subscribed - but no waiting content"
date: 2010-06-01
forum: Ubuntu One (CLOSED)
---

### Post by laoshi on 2010-06-01
After several days with no activity on U1 except 'processing queues' - and the ascii-error in 'waiting-metadata - I finally
```
$ sudo rm -rf ~/.local/share/ubuntuone
3. $ rm -rf ~/.cache/ubuntuone
```
and also unsubcsribed all folders through the GUI. Restarted the pc and tried to subscribe one folder, also through GUI. It didn't seem to register.
But on running ```
u1sdtool --list-folders
``` all the previously selected folders are reported as 'subscribed'.
However ```
u1sdtool --waiting-content
``` is empty, and nothing is sync'ing.
So now I seem to be stuck again...

EDIT: When I right click on the folder and chose 'Synchronize on Ubuntu One', half of the time nautilus closes, but sometimes not. And no matter what, the menu still says 'Synchronize...' and does not change to 'Stop Synchronizing'

THIS ISSUE IS NOW SOLVED BY U1 (june 2010)

---

