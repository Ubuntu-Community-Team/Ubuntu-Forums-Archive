---
title: "Adduser Error No More than 2 names"
date: 2006-11-08
forum: Server Platforms
---

### Post by jscrilla on 2006-11-08
I'm confused...keep getting this error when I try to add a user.

I type this in: 

sudo adduser autoins -d /mypath -s /bin/false

And get this returned:

adduser: No more than two names.

Anyone know what's going on there?

---

### Post by mssever on 2006-11-08
I just read the adduser man page, and it doesn't appear that adduser accepts short options. You might try something like this (if I'm guessing correctly the intended meaning of your short options): ```
adduser --system --home=/mypath autoins
``` If this is a system account, you might also want to specify --disabled-login and/or --no-create-home.

EDIT: It looks like you're using the syntax for useradd, not adduser.

---

