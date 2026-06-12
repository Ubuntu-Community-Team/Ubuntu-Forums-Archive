---
title: "vsftpd configuration"
date: 2011-08-06
forum: Server Platforms
---

### Post by Monery on 2011-08-06
Hello, 
 
I am trying to setup VSFTPD to share a single directory for everyone that has a user account on the Ubuntu 11.04 server. Somehow I fowled it all up and now the server opens at /. I am trying to get everyone that logs in to default the home to /shares. Its been awhile since I have done this and I know from a previous project that this was possible.

---

### Post by volkswagner on 2011-08-07
I'm sorry, but could you clarify.

Do you wish to have one directory /some/path/share to be the default directory for all users (one directory public to all users)?

Or do you wish to have all users jailed to a directory in /home/username directory?  ie: each user has a unique directory not shared with other users.

---

