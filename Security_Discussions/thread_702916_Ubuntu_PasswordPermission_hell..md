---
title: "Ubuntu Password/Permission hell."
date: 2008-02-20
forum: Security Discussions
---

### Post by benzle on 2008-02-20
[INDENT][FONT="Lucida Console"][SIZE="4"][COLOR="DimGray"]
[INDENT]     A quick one for someone who may have been through this, but I'm left entering and reentering my password every 15 minutes, and being denied "permission" for regular tasks such as Emptying the Trash, [COLOR="Black"]
     [INDENT] Thanks in advance [/INDENT]everyone.[/COLOR][/INDENT][/COLOR][/SIZE][/FONT][/INDENT]

-Kyle

---

### Post by mimada on 2008-02-20
Did you copy your files from another account? Try making a new user account and see if the problem persists.

---

### Post by freelinuxhelp on 2008-02-20
If I understand what you're asking, you want to lengthen or disable the timeout for sudo.
Here's how to do that:
Open a terminal.
run this: sudo visudo
on the line that starts with "Defaults" add ",timestamp_timeout=-1"
without quotes of course.
CTRL-X to exit, save your changes.
You might need to log out and back in.

---

