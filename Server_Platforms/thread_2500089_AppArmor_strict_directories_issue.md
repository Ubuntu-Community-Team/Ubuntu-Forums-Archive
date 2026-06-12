---
title: "AppArmor strict directories issue"
date: 2024-08-22
forum: Server Platforms
---

### Post by tracerds on 2024-08-22
I'm having some troubles with AppArmor on my Ubuntu Server 24.04.
I have a directory [FONT=courier new]**/server**[/FONT] for storing my server files.
In that directory I have also a second directory [FONT=courier new]**/server/certs**[/FONT] for storing ssl certificates (symlinked certs into [FONT=courier new]**/server/certs/***[/FONT]).
Now, if I add **[FONT=courier new]/server/certs/[/FONT]** into the apparmor config then it will only give permissions **to the actual files/directories in that folder** but not for symlinked files.
Is there a way to fix that?

---

### Post by currentshaft on 2024-08-22
rules

---

### Post by tracerds on 2024-08-23
And what would I do with these aliases?
How would I use them here?

---

