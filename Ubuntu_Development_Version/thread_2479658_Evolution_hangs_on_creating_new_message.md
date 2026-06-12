---
title: "Evolution hangs on creating new message"
date: 2022-10-02
forum: Ubuntu Development Version
---

### Post by jcrc-portinter on 2022-10-02
Evolution was working fine
Went from 22.04 to 22.10

It works ok in all the other functions: reading, moving or deleting messages, calendar, or all the other menus and windows.
But it hangs when replying or creating a new message.

after a while a window -- "Evolution" is not responding --
I have to -- Force quit --

No message is displayed if I start it from the terminal.

I think is some configuration file missing or misplaced. 
In another user account (created just now) it works flawless.

Ca someone help me on this?
Regards.

---

### Post by osse7 on 2022-10-02
To investigate:
- glance at related Evolution errors(red lines) /warnings (yellow ones) either into /var/log/ or via 'journalct -b | grep evolution' into a terminal

---

### Post by jcrc-portinter on 2022-10-02
In a new user:
Without setting gnome online accounts it worked ok
after setting gnome online accounts, it worked ok
installing the evolution backup of the other user did not work - Even after erasing ./cache/evolution ./local/share/evolution .config/evolution

After creating multiple users, messing around with account names and permissions and copying only email files ... I logged in to the original user 'et voila': is working.
I have no idea what I did to solve the problem.
This original user account dates back to 19.10 A lot of upgrades and stuff added meanwhile...

Thank you.

---

