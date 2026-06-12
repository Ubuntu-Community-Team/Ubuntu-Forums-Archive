---
title: "Looking for FTP Solution"
date: 2011-03-06
forum: Server Platforms
---

### Post by Monery on 2011-03-06
Greetings all,

I recently built a SMB file server for my mostly Windows Network. I created a directory /shares where all my important data resides. I am now looking to add another way to access that same directory via FTP. I have played with VSFTP and read the man files but it seems that all it will do is allow me to have FTP access to the home directories of the 3 user accounts on the box. Can anyone recommend a FTP server that I can simply configure so any users I have now, and any additional users I add in the future will have access to this one directory and only this one directory?

---

### Post by aeiah on 2011-03-06
you could just mount --bind your smb directory into the home directories

---

### Post by Monery on 2011-03-06
I could do that, but the boss doesn't want to mess with home directories at all, he just wants that one single directory accessed via FTP. We are doing this with a Windows XP Home machine running FileZilla FTP server.

---

