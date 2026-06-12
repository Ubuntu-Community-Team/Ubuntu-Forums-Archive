---
title: "create mask calculation"
date: 2010-01-23
forum: Security
---

### Post by mlohmiller on 2010-01-23
I have a setup samba and want to get the correct security permissions when my wife creates / copies files from her camera onto the shared/mapped drive on her new laptop (windows 7)
I want the permissions set to 770 or maybe 760. 
See my config below. 

Now I can get it to create 760 but even if I change the mask it still generates the same permissions.  After every change I restart the samba service.  
the umask is still 0022, do not know if that makes a difference?
The directory permission's are correct with this mask.  
Do I need to look at groups?

Any help is appreciated. Thanks in advance. 

[Media]
        path = /bigdrive/Media
        create mode = 0770
#       security mask = 0770
        directory mask = 0770
        writeable = yes
[backup]
        path = /bigdrive/backup
        create mode = 0770
        directory mask = 0770
        writeable = yes
[Amy]
        path = /bigdrive/Amy
        create mode = 0770
        directory mask = 0770
        writeable = yes

---

### Post by bodhi.zazen on 2010-01-24
Try this;

When you mount the samba share, use the noperm option.

---

