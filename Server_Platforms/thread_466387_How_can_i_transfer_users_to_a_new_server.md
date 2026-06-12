---
title: "How can i transfer users to a new server?"
date: 2007-06-06
forum: Server Platforms
---

### Post by kerinin on 2007-06-06
I am moving from one hosting company to another - both VPS's running LTS.  I would like to move all the users from the old server over to the new server including usernames, names, GUID's, groups, etc.  This way when i move the /home directory to the new server all the file permissions will be intact.  I would also like to keep my existing security setup.

Is this possible?  How?

Many thanks

---

### Post by toorima on 2007-06-06
copying over /etc/passwd /etc/shadow /etc/group should do it I think

---

### Post by obimeister on 2007-06-07
I have done that couple of times. From distro to another. Files mentioned from toorima are right ones but I wouldn't copy them straight over. First made version from passwd and shadow where all system accounts are removed and only user lines left. These you can cat to new files. For a group file I'd check if GID match and if they do then copy over else edit it manually.

---

