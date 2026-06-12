---
title: "Easy root access during startup"
date: 2006-09-16
forum: Server Platforms
---

### Post by sni on 2006-09-16
Hello
I just noticed that doing a Ctrl-C at startup left me in a shell logged on as root.

I know it that it's not possible to protect against everything when a "bad guy" has physical contact with the computer but I found it a bit shocking that it was this easy.

Best regards
Søren
(using Dapper)

---

### Post by MrHorus on 2006-09-16
> **sni said:**
> Hello
I just noticed that doing a Ctrl-C at startup left me in a shell logged on as root.


At what point do you press this and what happens exactly?

---

### Post by sni on 2006-09-16
> **MrHorus said:**
> At what point do you press this and what happens exactly?

When the filesystemcheck started. Pressed Ctrl-C (hoping to skip it) and got a root shell to make the check manually.

---

### Post by MrHorus on 2006-09-16
> **sni said:**
> When the filesystemcheck started. Pressed Ctrl-C (hoping to skip it) and got a root shell to make the check manually.

Probably because it's still in single user mode at that point then.

---

### Post by sni on 2006-09-16
> **MrHorus said:**
> Probably because it's still in single user mode at that point then.

I understand that there are propably some good explanation. I just thought it would be a little more "tricky" to get full access to the system.

---

### Post by Peter76 on 2006-09-16
Post abug about this; IMO this should't be possible in a production environment

---

### Post by Klaidas on 2006-09-16
Just give that root a password - you will then be asked for it before logging in to single user mode.

---

### Post by aysiu on 2006-09-16
Anyone who has a little know-how and physical access to your computer can essentially become root anyway.

Anyone who *doesn't* have a little know-how would have no idea what to do at the root prompt--probably wouldn't even know to type *reboot* and would just do a hard reboot by pressing the power button.

Do you really think a non-savvy user is going to get to a root prompt and accidentally type *rm -rf /*?

---

### Post by sktx on 2006-09-17
> **aysiu said:**
> Do you really think a non-savvy user is going to get to a root prompt and accidentally type *rm -rf /*?

Note to newbie users: ***don't*** *test that command!!* :p

Anyway, aysiu is right.  Anyone with a little bit of know-how and physical access to your box can do anything they want to it.  Your only solution is to power down your box when you're not using it and lock it in a steel box.  You can't prevent physical-access attacks without locks and keys, short of carrying your computer with you wherever you go.

  sktx

---

