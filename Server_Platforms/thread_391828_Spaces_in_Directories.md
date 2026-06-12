---
title: "Spaces in Directories"
date: 2007-03-23
forum: Server Platforms
---

### Post by wayne on 2007-03-23
Can anyone tell me why I cannot go in a directory with spaces using the cd command.

I have just setup a Ubuntu 6.10 server with Samba.  If I create a directory from a Windows machine named "test perm" & create a file in it I cannot go into this directory from the server.  I don't think it is related to permissions because I can create a directory such as "testperm" the same way and go into it from the server without a problem. 

The message I get is:  -bash: cd: test: No such file or directory

Any ideas appreciated...

---

### Post by Kaput1982 on 2007-03-23
You have to put the name of the directory or file in quotes.  This should work with most commands.

cd "test perm"
rmdir "test perm"
mkdir "test perm"

You get the idea.

---

### Post by 23meg on 2007-03-23
Put the path in "double quotes", or replace spaces with "\ " (backslash followed by single space).

---

### Post by wayne on 2007-03-23
I get the idea, thanks guys

---

### Post by stalefries on 2007-03-26
Aww, a question I knew the answer to, and it's already been answered. :(

---

