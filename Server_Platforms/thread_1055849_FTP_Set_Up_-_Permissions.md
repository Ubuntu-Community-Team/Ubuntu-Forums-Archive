---
title: "FTP Set Up - Permissions"
date: 2009-01-31
forum: Server Platforms
---

### Post by adamcoppard on 2009-01-31
I have just setup ProFTPD on my server, and under my user, jailed them to the home directory. /var/www was then mounted to ~/www so that I could access it. The user can create a folder, file, and read said folder / files, but not save. I was wandering a) how to get this to work, and b) if there is a safer / more secure way of achieveing what I am trying too?

---

### Post by adamcoppard on 2009-01-31
After looking at the problem again:
Any files created after the change can be added, edited, deleted, you name it. Anything before carrying out the steps above cannot be added / changed by the user 'adam', down to permissions.

---

