---
title: "How to share a game?"
date: 2009-01-19
forum: Wine
---

### Post by famous3warriors on 2009-01-19
I have two different users that would like to play the same game but have different login names and passwords but on the same computer.  I am using wine 1.1.13 installed in ubuntu 8.10.  How could I share this game properly?  Thanks for your help in this situation?

---

### Post by cogadh on 2009-01-20
In theory (I say that because I have never tried it myself) you could use wineprefixcreate to make a .wine directory in a shared directory that both users have access to. Then you just need to configure that .wine directory so that none of its paths point to any particular user's home directory (like the "My Documents" path) and install the game there. Then you would have to manually create shortcuts under each user's login that they could use to launch the game.

However, technically the proper way to do it is to have each user install the game in their own .wine directory under their own login. It means you will actually have two different installs of the game, but each of them is guaranteed to work properly... assuming this is a game that already works in Wine.

---

### Post by famous3warriors on 2009-01-20
Ok cool thanks That is what I will do.  Thanks for you help.  I really do appreciate it.  I installed the game in both directories and it worked great with no problems.  I wasn't sure if I could do that.

---

