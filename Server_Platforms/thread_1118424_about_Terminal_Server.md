---
title: "about Terminal Server"
date: 2009-04-07
forum: Server Platforms
---

### Post by mykelm03 on 2009-04-07
im a newbie and hopefully that someone could help or share some idea about this. im planning to setup a terminal server in ubuntu so that user outside (internet) can connect to my win2003 server. is this possible? the ubuntu box is like a bridge from the user to win2003? thanks in advance...

---

### Post by cdenley on 2009-04-07
What do you mean by "terminal server" on linux? The easiest way to connect to an internal server through a linux server is to use SSH with port forwarding.
```

ssh user@ubuntuhost -L 3389:windowshost:3389

```

---

### Post by HermanAB on 2009-04-07
No, no, all you need to do is forward port 3389/TCP through your firewall to the Win2003 server and enable RDP.  You can then access the server using either Windows remote desktop client or the Linux rdesktop program.

RDP works very well and it is secure.

---

