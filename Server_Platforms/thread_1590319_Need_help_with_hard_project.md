---
title: "Need help with hard project"
date: 2010-10-07
forum: Server Platforms
---

### Post by joek71 on 2010-10-07
Hello guys

Ok this is what i need to do, i am runnng LAMP, now i have 3 users (user1, user2 and user3)
they are all working on a same project but i dont want them to interfere in one another way.  When user1 changes something in his code and ftp's to his directory he wants to see his changes in his browser, and when user2 does something he wants to see changes in his browser but they dont want to see global changes, so when user1 makes change user2 should not see it on his browser.  This is all on a LAN Server.
Also i need to give them direct ftp access to only there files with read, write and execute permission.

Can anyone help please.

thank you in advance.

---

### Post by wmcbrine on 2010-10-07
You need a version control system. Something like git, perhaps.

---

### Post by joek71 on 2010-10-07
How do i get that?
Cause i just made changes at /var/www/user1
and it made them globally i just wanted the changes to take affect on user1

---

