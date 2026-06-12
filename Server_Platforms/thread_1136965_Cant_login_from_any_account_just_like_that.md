---
title: "Cant login from any account just like that"
date: 2009-04-25
forum: Server Platforms
---

### Post by srdjo on 2009-04-25
I installed Ubuntu 8.10 and setup LTSP on it and it all worked for over two weeks.

Today I installed a printer on one of my ltsp clients, and printer driver dialog crashed and client freezed. I restarted it and it couldnt boot any more.

Then I got to server and rebooted it, and now I cant login to server neither. It was complaining about nbd-server config file, so I removed nbd-server, and it still wont login from any account.

I just get to LDM enter username and password, and it switches to terminal and back to LDM, and asks for username and password again.

Tried recovery mode, and can login as root, but no one else.

What can I do ?

---

### Post by srdjo on 2009-04-25
I must add that I cant login to shell either (Ctrl+Alt+1/6).

Please help.

---

### Post by srdjo on 2009-04-25
I found a solution.

It was samba problem, so I removed and purged samba from system, and then reinstalled it again, and now it is working.

---

