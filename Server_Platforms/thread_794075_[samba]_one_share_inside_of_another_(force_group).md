---
title: "[samba] one share inside of another (force group)"
date: 2008-05-14
forum: Server Platforms
---

### Post by kacper86 on 2008-05-14
Hi!
I have some nasty problem and i cannot figure it out. There are 3 places (all of them have its own section in smb.conf):
/home/shares/company
/home/shares/development   (force group = dev)
/home/shares/management    (force group = man)
Then, there some links:
/home/shares/company/link1->development
/home/shares/company/link2->management

When i connect to the share (/home/shares/development) directly, "force group" works perfectly. However, when I connect to the share (/home/shares/company) and go to the "development" using the link, "force group" doesn't work. I tried "iherit permissions=no" and "inherit group=no", but it doesn't work either. What should i do?

---

