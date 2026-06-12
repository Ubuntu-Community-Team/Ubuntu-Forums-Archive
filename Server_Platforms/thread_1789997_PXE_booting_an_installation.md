---
title: "PXE booting an installation"
date: 2011-06-24
forum: Server Platforms
---

### Post by DanHorniblow on 2011-06-24
Hi, at my work all of the PC's are running windows, I would really like to dual boot with ubuntu as well. How ever the local HD's are only 80GB, which is fine for windows but there is not enough room for both OS's.

So instead of having to upgrade all of the PC's hard drives, is it possible for the clients to PXE boot into a ubuntu installation from a server which contains all the necessary applications for the users?

We are running gigabit links to all clients and 10 gigabit to all servers, so I don't thick bandwidth would be an issue.

---

### Post by Bachstelze on 2011-06-24
What you want is called "thin clients". I think in Buntu you do that with LTSP

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

Never done it myself, though.

---

### Post by Azdour on 2011-06-24
Hi,

You may also want to look at DRBL: [https://sourceforge.net/projects/drbl/](https://sourceforge.net/projects/drbl/)

This is something I have used many times.

---

