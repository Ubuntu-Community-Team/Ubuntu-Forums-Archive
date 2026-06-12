---
title: "vsftpd - one user, multiple directories"
date: 2012-02-09
forum: Server Platforms
---

### Post by PaulusE on 2012-02-09
Is it possible to add one user to multiple directories so they will be allowed to edit/create files and folder in these directories?

I want to use this situation on a web-development server. What I basicly want is that I have a personal login for the FTP and that I will receive a list of folders I'm assigned to.

**Example:**
In /home/users/ are three sub-directories:
- /home/users/site1/
- /home/users/site2/
- /home/users/site3/

When I sign in with my FTP account I get an empty list back from the server where I can't create new files or folders.
As soon as I assign this user to site1 and site3 I want the server to send me a directory list of:
- /home/users/site1/
- /home/users/site3/

Is it possible to do this using vsftpd or any other FTP server program?

---

