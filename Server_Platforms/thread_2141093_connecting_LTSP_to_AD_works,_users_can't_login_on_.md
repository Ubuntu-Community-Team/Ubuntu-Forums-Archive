---
title: "connecting LTSP to AD works, users can't login on a thin client."
date: 2013-05-01
forum: Server Platforms
---

### Post by the1joker on 2013-05-01
Hey Everyone,

I have a 12.04 LTSP server, thin clients can connect fine if there account was created before i attached it to my Windows 2012 Active Directory.

Now i connected it to my AD with likewise, and this seems fine at first, since i can use my AD credentials to login to the ltsp server through SSH.

So the next step was trying  a thin Client, and somehow i get kicked back after "Verifying Password", and my desktop is not loaded, but agian, i can use that same user to login through ssh and i have even added sudo rights to my group.

Upon logging in with a brand new AD user, it correctly makes me change the password, and after that creates my home directory...

Can anyone tell me whats going on???

Thanks for any help!

---

