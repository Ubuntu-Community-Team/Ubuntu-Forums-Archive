---
title: "logging in to user with no password field"
date: 2007-06-02
forum: Server Platforms
---

### Post by Gavyn_R on 2007-06-02
I can't log into a new user that I create unless the password field in the /etc/passwd file is specified.
eg:
"# cat /etc/passwd"
frazer::5000:5000:test:/home/frazer:/bin/bash

"su frazer"
Password: 
su: Authentication failure
Sorry.

Anyone have an idea as to why this is and how I can fix it?

---

