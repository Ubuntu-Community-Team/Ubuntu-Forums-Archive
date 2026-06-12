---
title: "SSH/SFTP and Permissions"
date: 2010-03-30
forum: Security
---

### Post by fireman biff on 2010-03-30
Hi,

I have recently secured a server by preventing root from logging in via SSH. Now I log in with a non-root account and use 'su' when necessary.

However, now I can't do something I used to do, which is open 'sftp://user@ipaddress' in nautilus and be able to edit files as root.

Is there anyway to get nautilus to give me root permissions on the server? Or at least end up with root permissions in a GUI text editor on my computer? I don't mind if I have to use bash to start the process, once I can get a GUI for editing files.

Note 1: Yes, I realize I could ssh in and use nano/vi etc, but I'd rather use my graphical text editor.
Note 2: The server does not run X, so I can't just forward it.

---

### Post by cdenley on 2010-03-30
You could allow root authentication with keys. It would be safer than allowing root with password. In my opinion, it would probably even be safer than allowing admin authentication with password. It is probably the safest way to allow unrestricted access to your whole filesystem remotely. Still, it would be safer to only allow your admin user with a key.

---

