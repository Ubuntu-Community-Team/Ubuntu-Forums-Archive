---
title: "Samba Force Group - Driving me insane"
date: 2014-02-03
forum: Server Platforms
---

### Post by david_hammond on 2014-02-03
Afternoon!

Having installed samba on the test server and it working a treat, we've just taken delivery of the new hardware and installed ubuntu on it, now I can't seem to get a share to work as it does on the test despite using the same smb.conf settings. 

I have a folder (jobs-2014) that will contain all our customer files for the year. I need 770 permissions on this folder, and all inside it, I also need the owner group to be set to staff. 

Below is the smb.conf for said folder, but whenever a new folder is created from Mac OSX or windows 7, the group is the users default group, and the permissions aren't setting to 770 but 750?

```
[Jobs-2014]
path = /home/Samba/Jobs-2014
Browsable = no
unix extentions = no
valid users = @staff
force group = staff
writeable = yes
create mask = 770
force create mode = 770
security mask = 770
force security mode = 770
directory mask = 770
force directory mode = 770
directory security mask = 770
force directory security mode = 770

```
It's got me stumped, I'd welcome any suggestions, I don't know why it works on the test but not the new server?

---

### Post by david_hammond on 2014-02-04
Solved it.

As the jobs folder is accessed by a symbolic link in the respective users home folder, by setting the required permissions for the users home directory seem's to transpose those to the Jobs share. 

I imagine that the host see's the Jobs folder as an actual folder in the home directory not a link.

---

