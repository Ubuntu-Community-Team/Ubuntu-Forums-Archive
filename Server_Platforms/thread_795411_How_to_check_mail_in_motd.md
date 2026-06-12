---
title: "How to check mail in motd?"
date: 2008-05-15
forum: Server Platforms
---

### Post by iissmart on 2008-05-15
Hi, I just did a fresh install of Ubuntu 8.04 Server. One thing I noticed is that when I ssh into the new server, the motd doesn't check your mail anymore - actually 'mail' wasn't even installed. So I installed mail, and now I'm wondering how to have the motd check the user's mail upon login and display something like "No mail for <username>" or "New mail for <username>". I think they do this for the Desktop installations but evidently not for Server installations. Thanks!

---

### Post by iissmart on 2008-05-17
OK, so I realized it's not actually part of the motd, but its something directly after it. I thought it might have something to do with pam but evidently that's only for login via tty, not ssh. Google isn't helping and all of my Linux guru friends are out of ideas, but I know this works because I can log into a debian ssh server and it currently says "No mail.".

---

### Post by iissmart on 2008-05-22
Anyone?

---

