---
title: "Is there a server guide out for 8.10?"
date: 2008-12-10
forum: Server Platforms
---

### Post by AngryNapkin on 2008-12-10
I just installed, and so far it looks exactly like it's non-server version. I want to be absolutely sure I installed the right version before I get to work. Is there a sure way to tell? Also, are there guides out for the latest version yet?

---

### Post by cariboo on 2008-12-10
Unless you specifically installed the gui, the server version has no gui. To check what kernel version you are running, in a terminal type:

```
uname -a
```

The result should look like this:

```
 uname -a
Linux willy 2.6.27-9-server #1 SMP Thu Nov 20 22:56:07 UTC 2008 x86_64 GNU/Linux

```

All the server configuration files are text files, so there is really no need for a gui.

Jim

---

### Post by davidvan on 2008-12-10
> **cariboo907 said:**
> Unless you specifically installed the gui, the server version has no gui. To check what kernel version you are running, in a terminal type:

```
uname -a
```

The result should look like this:

```
 uname -a
Linux willy 2.6.27-9-server #1 SMP Thu Nov 20 22:56:07 UTC 2008 x86_64 GNU/Linux

```

All the server configuration files are text files, so there is really no need for a gui.

Jim

Impressive... where do you learn this? I've been windozed for too long..

---

### Post by AngryNapkin on 2008-12-10
Interesting. I didn't realize the GUI came with it by default from the, "get ubuntu page" (with the desktop/server tab). Anyway, thanks for the answer.

---

### Post by hyper_ch on 2008-12-11
> **davidvan said:**
> Impressive... where do you learn this? I've been windozed for too long..
Learning by doing... the more yuo work with the cli the better you get to know it... :)

---

