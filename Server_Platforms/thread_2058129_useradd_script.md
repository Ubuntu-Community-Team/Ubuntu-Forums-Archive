---
title: "useradd script"
date: 2012-09-15
forum: Server Platforms
---

### Post by arlenn on 2012-09-15
I have done some searching for this topic and find some things that are similar; however i really don't know enough about scriping to pull together what i need.

What i need is a small script to take a username and password from the command line, create a new user, with alternate shell, add an additional group then copy some files around.

for example:

# newuser username password

create the user, change the password, add a group and assign a home directory using the arguments passed.

the rest i can probably figure out.



Thanks in advance for any help.

---

### Post by dniMretsaM on 2012-09-15
I believe all the things you want to do can be done with the [FONT=Courier New]useradd[/FONT] command itself. Read the man page ([FONT=Courier New]man useradd[/FONT]) and look at the [FONT=Courier New]--gid[/FONT], [FONT=Courier New]--groups[/FONT], [FONT=Courier New]--skel[/FONT], [FONT=Courier New]--create-home[/FONT], [FONT=Courier New]--password[/FONT], and [FONT=Courier New]--shell[/FONT] options.

---

