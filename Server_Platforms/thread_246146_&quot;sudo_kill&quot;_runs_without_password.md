---
title: "&quot;sudo kill&quot; runs without password?"
date: 2006-08-28
forum: Server Platforms
---

### Post by mouser13 on 2006-08-28
Why does "sudo kill" run without prompting for password? That way every shell script on my computer can kill my system? How can I change that?

---

### Post by Anonii on 2006-08-28
It asks for a password for me.
"[I]$ sudo kill
Password:
[/I]"
Probably, you are within the same sudo session and it doesnt ask you for a password again. (I unfortunately, dont know how the sudo sessions work, but yes, it prompts for a password, at least for me.)

---

### Post by mouser13 on 2006-08-28
Yes, now I tried it more carefully and it does ask me for password the first time I run it and then works without a password. 
Sorry for the stupid question I am not used to the "no root" working yet.

---

