---
title: "TimeMachine server: OSX client not recognizing change in size"
date: 2013-03-27
forum: Server Platforms
---

### Post by elektronaut on 2013-03-27
Hi,

I just set up a time machine server on Ubuntu 12.04. Initially the 'volsizelimit' in '/etc/netatalk/AppleVolumes.default' was not enough, so I increased it. The problem is that the OSX client doesn't want to recognize the change. Even though when I go to 'System Settings'->'Time Machine' the correct new size is shown, the backup process fails and complains about the limitation as defined by the previous 'volsizelimit' value. Restarting netatalk, and also the Ubuntu server and the OSX client didn't help.

Somebody's got an idea?

---

### Post by smeerbartje on 2013-03-27
Can you please post a link to the tutorial you used for setting up the Time Machine server? I have been looking for this a couple of months.

---

### Post by elektronaut on 2013-03-27
[http://blog.bertelsen.co/2012/07/time-machine-server-on-ubuntu-1204.html]("http://blog.bertelsen.co/2012/07/time-machine-server-on-ubuntu-1204.html")
But don't make the mistake and try to change the size :(

---

### Post by elektronaut on 2013-03-28
Solved. Changing the volsizelimit value signals only the size of the share which can be used. As I already started a (canceled) backup process before, when the set value was too small, some information about the size was registered in the created 'sparse bundle', a special folder in the Time Machine target directory. Simply deleting this folder solved it.

---

