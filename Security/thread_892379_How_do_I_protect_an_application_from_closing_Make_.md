---
title: "How do I protect an application from closing? Make it require sudo?"
date: 2008-08-17
forum: Security
---

### Post by Spyros_Gre on 2008-08-17
Hello! I am running Ubuntu 8.04 and I am hosting virtual servers using VM-Ware workstation 6. 
I have a simple question about vm-ware and virtually every application. 

How can I protect an app from accidental closing from e.g. the taskbar or from terminal with kill? 
I was thinking of forcing this application to run with elevated rights ie requiring sudo. But then again is this recommended? Is it too much maybe? Thank you!

---

### Post by hyper_ch on 2008-08-17
you do not want to run applications as sudo - if not necessary...

---

### Post by Biochem on 2008-08-17
> **hyper_ch said:**
> you do not want to run applications as sudo - if not necessary...

I have to agree with this.

However maybe there is a way if you create another user and use 

```
su -c 'command' user2
```

However, I don't know how to make it use X using this.

If you find a way please share. I have a friend who is constantly kill it's XCFE-panels by accident.

---

