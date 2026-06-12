---
title: "grep email address in .txt file"
date: 2011-07-06
forum: Server Platforms
---

### Post by zerobravo83 on 2011-07-06
I have file.txt on server which contains the following lines:


51:mail-address@domain.com:c1a1r94d81s3ba5ckc5e6725e74fd94c:1187000806:name surname:091
.
.
.
.


How can I draw only email addresses in the new file (filtered.txt)?

[email]mail-address@domain.com[/email]
.
.
.
.

I try with command:

grep @ file.txt > filtered.txt but unsuccessfully (no space between email address and left and right side in the line).

---

### Post by luvshines on 2011-07-06
If the separator is fixed as : and the email is to appear in the 2nd column always,then awk should help```
awk -F':' '{print $2}' <path-to-current-file> > <path-to-new-file>
```

---

### Post by diesch on 2011-07-06
```
grep -o '[^:]*@[^:]*' file.txt 
```

---

### Post by zerobravo83 on 2011-07-06
Tnx, I did it.

---

