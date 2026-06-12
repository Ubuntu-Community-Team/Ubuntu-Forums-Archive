---
title: "FTP Character Translation"
date: 2008-02-26
forum: Server Platforms
---

### Post by michaelGatto on 2008-02-26
I am having a character translation issue with extended characters from my XP environment to Ubunto Gusty. I first detected the issue while backing up to Gusty via SyncBackSE/FTP, the replicated the issue using FileZilla. When I transfer files which contain special characters in their names (ie: "Bélavita.txt") the files transfer but resolve with a strange triangular question mark replacing the é character. On my Ubuntu system I can manually replace the strange triangular question mark with the proper é character no problem, but when I transfer the file back to my XP system I get a file named "BÃ©lavita.txt"?? Any ideas on this one - - I'm stumped.

Thanks in advance

---

### Post by morningboat on 2008-02-26
You should choose the correct server's character encoding on your FTP client's setting. Normally Ubuntu uses UTF-8 as its server encoding. The FTP client that supports multiple server encodings are FileZilla, CrossFTP, etc. The encoding option is often located in the site manager.

---

