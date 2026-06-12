---
title: "share a folder with the Windows AD security group 'domain admins'??"
date: 2008-10-17
forum: Server Platforms
---

### Post by kpm on 2008-10-17
The cmd "wbinfo -g" displays a long list of all the groups on the Window's network.  One of these groups is 'tld/domain admins'.  I would like the users who belong to 'domain admins' to have access to \var\www\ on the Ubuntu LAMP server.  I know I have to chgrp on the directory, but I am not sure how to enter the cmd when the group name has a domain prefix?  There are no such examples in the chgrp --help file... 
Thanks

---

