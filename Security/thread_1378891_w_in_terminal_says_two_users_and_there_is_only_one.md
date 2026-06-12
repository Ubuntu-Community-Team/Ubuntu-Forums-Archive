---
title: "w in terminal says two users and there is only one. Problem?"
date: 2010-01-12
forum: Security
---

### Post by houseworkshy on 2010-01-12
I've just typed w in my terminal which tells me that there are two users on my machine and there aren't.  I then used finger and it game the name of the other as hplip. I don't have an hp printer but do I have a problem?

---

### Post by houseworkshy on 2010-01-12
Whilst I've been using apps on Ubuntu for some time I know very little about it and was just trying out commands in the terminal.  I've discovered that I appear as a user for each terminal I open as myname in lower case.  The other was USER.  So the above post may simply reflect my ignorence.  But I still don't understand the referance to a printer I don't own.

---

### Post by ad_267 on 2010-01-12
Yeah, every time you open a new terminal you effectively log in again as yourself.

That seems weird that hplip would show up when running finger though. I think hplip is installed by default by Ubuntu to support HP printers and the hplip user is created, but I don't know why it would show up when running finger.

---

