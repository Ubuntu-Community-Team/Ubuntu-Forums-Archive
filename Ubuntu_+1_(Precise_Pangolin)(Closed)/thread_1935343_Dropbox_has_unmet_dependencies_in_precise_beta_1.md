---
title: "Dropbox has unmet dependencies in precise beta 1"
date: 2012-03-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kanishkdudeja on 2012-03-04
When i install Dropbox in Ubuntu 12.04 Beta 1, it says:

```
kanishk@kanishk-Inspiron-1525:~$ sudo dpkg -i nautilus-dropbox_0.7.1_i386.deb
[sudo] password for kanishk: 
(Reading database ... 132821 files and directories currently installed.)
Preparing to replace nautilus-dropbox 0.7.1 (using nautilus-dropbox_0.7.1_i386.deb) ...
Unpacking replacement nautilus-dropbox ...
dpkg: dependency problems prevent configuration of nautilus-dropbox:
 nautilus-dropbox depends on libnautilus-extension1 (>= 1:2.22.2); however:
  Package libnautilus-extension1 is not installed.
dpkg: error processing nautilus-dropbox (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Errors were encountered while processing:
 nautilus-dropbox

```

Then when i try to install libnautilus-extension1, it says:

```
kanishk@kanishk-Inspiron-1525:~$ sudo apt-get install libnautilus-extension1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libnautilus-extension1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnautilus-extension1a

E: Package 'libnautilus-extension1' has no installation candidate

```

And libnautilus-extension1a is already installed.

So what should i do now?

---

### Post by lucazade on 2012-03-04
why don't you directly install dropbox from repositories?

```
sudo apt-get install nautilus-dropbox
```

otherwise try to fix your previous dropbox installation with:

```
sudo apt-get install -f
```

---

### Post by kanishkdudeja on 2012-03-04
```
sudo apt-get install nautilus-dropbox
``` 

WORKED. :)

Thank you so much :)

---

### Post by sffvba[e0rt on 2012-03-04
Hmmm... just installed 12.04 on my system and got the same dependency issues when trying to install the deb file form the Dropbox website.

Will install from the Software Center directly and see if that also works for me (should have done that to start with :p)


404

---

