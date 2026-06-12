---
title: "Update manager not updating"
date: 2009-08-21
forum: System76 Support
---

### Post by pseudotheist on 2009-08-21
Subject about says it all.  For the last couple days my update manager has come up to tell me that I have updates to install, but when I try to click "install updates" it does nothing.  Any ideas what's wrong?

---

### Post by staf0048 on 2009-08-21
I'm not sure if you get the same error message I get, but every once in a while I'll get "Unable lock  /var/something/something."  

The only way I know of to fix it is to restart the computer.  You've probably already tried that, but just in case . . .

---

### Post by gamerchick02 on 2009-08-21
> **pseudotheist said:**
> Subject about says it all.  For the last couple days my update manager has come up to tell me that I have updates to install, but when I try to click "install updates" it does nothing.  Any ideas what's wrong?

Have you tried

```
sudo apt-get update
sudo apt-get upgrade
```

This should do your updates.

Amy

---

### Post by pseudotheist on 2009-08-22
And of course this morning the updates go through just fine...

gamerchick02: Is that just the shell commands to accomplish the exact same task?  Just want to make sure I understand what I'm doing if it happens again.

---

### Post by rubbsdecvik on 2009-08-22
> gamerchick02: Is that just the shell commands to accomplish the exact same task? Just want to make sure I understand what I'm doing if it happens again.

Yes.

```
sudo apt-get update
sudo apt-get upgrade
```

will accomplish the same result as using the update manager.

---

