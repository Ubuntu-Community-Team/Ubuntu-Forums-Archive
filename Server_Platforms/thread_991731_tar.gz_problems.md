---
title: "tar.gz problems"
date: 2008-11-24
forum: Server Platforms
---

### Post by silbro on 2008-11-24
Hello,

I have the problem, that when creating .tar.gz files with special characters such as ä,ö,ü my archive cannot be extracted fully on Windows. It just misspells the special characters in the error log and sais it couldn't extract those files.

I put this under Server Platforms because I run a Ubuntu Server which creates these .tar.gz backup files.

thank you for any hint/help,
sil

---

### Post by silbro on 2008-12-01
For some reason I don't believe that nobody has come across this problem besides me so far ;) There must be some germans or swiss like me, that had this problem before! Im sure of it. Can I replace the special characters with the tar command ? Is the encoding wrong ? What must I look out for?

---

### Post by obg123 on 2008-12-01
I've had this problem (in Sweden). I think the problem is that Linux uses ISO8859-1 while Windows uses Unicode. I don't think there is a way around this. Just use proper file names, or convert them before trying to send them to Windows. ;)

---

### Post by Vegan on 2008-12-01
Unfortunately, you need to use ASCII characters to maximize portability.

---

### Post by silbro on 2008-12-02
Thank you for the replies! 
Your comments make sense to me. Would this also mean, if I transfer the .tar.gz file to Windows, then move that .tar.gz file back to a linux machine, I should be able to extract all files without a problem because the characters are already in a linux format right? ;) Sry about those questions. I will be able to test this scenario in a few days. But if someone already knows the answer I'd appreciate it!

---

### Post by tubezninja on 2008-12-02
> **silbro said:**
> Thank you for the replies! 
Your comments make sense to me. Would this also mean, if I transfer the .tar.gz file to Windows, then move that .tar.gz file back to a linux machine, I should be able to extract all files without a problem because the characters are already in a linux format right? ;) 

Yes, extraction to another linux system should work just fine.

---

### Post by silbro on 2008-12-03
Thank you for your answer :)! This means my backups I'm making are all safe ;)

for me this case is solved. 

sincerely,
Silvio

---

