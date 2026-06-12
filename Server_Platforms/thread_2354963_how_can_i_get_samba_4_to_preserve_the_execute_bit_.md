---
title: "how can i get samba 4 to preserve the execute bit for the owner"
date: 2017-03-08
forum: Server Platforms
---

### Post by fomember on 2017-03-08
I have various scripts on Linux which of course have the execute bit set for the owner (chmod u+x).
Whenever I edit these scripts on windows or rename them the owner loses the execute flag.
In the past this was no problem but with samba 4 something seems to have changed.
I have tried to change permission masks or map archive bit = yes but nothing worked properly.

How can I get samba to keep the execute bit and just leave it as it is set?

---

### Post by fomember on 2017-03-08
5h17
The problem was with an include file where the create mode parameter had been set to 644.
Sorry for any confusion.
I just had better looked closer enough at the given samba parameters.

---

