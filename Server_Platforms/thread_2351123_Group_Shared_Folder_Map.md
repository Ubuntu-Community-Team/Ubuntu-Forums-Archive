---
title: "Group Shared Folder Map"
date: 2017-01-31
forum: Server Platforms
---

### Post by yolandre on 2017-01-31
Hi all,


After years of threatening to do so I am busy implementing a Linux file server (Ubuntu 16.04 Server).


I managed get all the preparation done such as adding additional drives, creating custom home directories for users, creating users, getting Samba up and running, etc. up to the point where users can successfully map their Linux based directory to their Mac OS X and Microsoft Windows based workstations.


My challenge comes with group directory sharing. I created logical groups, assigned qualifying users to each group, created data storage directories for each group, configured ownership and permissions for each group directory, shared each group directory in Samba during the process confirming that each shared group directory is writeable, specifying valid groups and read/write groups. The exact same routine was followed with each respective group directory.


The result: some folders map perfectly to workstations whilst other group directories cannot be mapped at all.


The majority of the work was conducted using Webmin, but I also tried using the command line which had the exact same result. All user accounts were twice validated so too each group and “smb.conf”. All appears to be in perfect order with absolutely no indication why the maps should not work.


Any and all advice is appreciated.

---

### Post by howefield on 2017-01-31
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by TheFu on 2017-02-01
You'll need to post the config files to get any help.  I prefer **testparm** output, since that removes all the extra stuff. Please use code tags, so it is easy to read.

I've always used groups as the access level for my share designs. [https://unix.stackexchange.com/questions/197175/how-to-properly-configure-samba-access-using-groups](https://unix.stackexchange.com/questions/197175/how-to-properly-configure-samba-access-using-groups)

---

