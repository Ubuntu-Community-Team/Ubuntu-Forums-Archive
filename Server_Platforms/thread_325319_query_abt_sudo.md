---
title: "query abt sudo"
date: 2006-12-25
forum: Server Platforms
---

### Post by usien on 2006-12-25
i am new to ubuntu nd still getting 2 know it.i wanted to know if there is some way to get pass sudo (or the security restrictions it posts e.g i can't delete my files from the gui file browser although i have admin rites).cant it b done without typing sudo in the terminal everytime.btw wat is the terminal command for deleting a file

---

### Post by KenSentMe on 2006-12-28
The command for deleting a file is 'rm filename'.

You can do sudo -i. This way you are logged in as root and only have to fill in the password once. But watch out what you do, because root can do a lot of things, but can break a lot too.

---

