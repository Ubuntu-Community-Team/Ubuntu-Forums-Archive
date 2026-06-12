---
title: "Sudo without password"
date: 2010-09-11
forum: Security
---

### Post by phoenix7 on 2010-09-11
I have a problem with ubuntu lucid's sudo app. I don't want to enter password each time I sudo. Adding the folowing line in sudoers file
```
 user       ALL=(ALL) NOPASSWD: ALL 
```
was working in the previous as far as I remember. But in the current version (lucid lynx) it doesn't work anymore. Is this feature disabled in lucid? or I should just change the line in an appropriate way (how?).

---

### Post by CharlesA on 2010-09-11
Syntax is wrong. You did use visudo to edit /etc/sudoers, right?

From [here]("https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo").

```
<username> ALL=NOPASSWD: ALL
```

---

### Post by phoenix7 on 2010-09-11
!

---

### Post by Bachstelze on 2010-09-12
> **CharlesA said:**
> Syntax is wrong. You did use visudo to edit /etc/sudoers, right?

The syntax is correct. 

@phoenix7: make sure you put your user line *below* the %admin line (or comment the %admin one out). It's a "last match wins", so if the %admin line is last, it will override your user line.

---

### Post by CharlesA on 2010-09-12
> **Bachstelze said:**
> The syntax is correct. 

@phoenix7: make sure you put your user line *below* the %admin line (or comment the %admin one out). It's a "last match wins", so if the %admin line is last, it will override your user line.

Ah. Thanks. I wonder why it spit back an error when I tried it. 

I probably mistyped something.

Would having ALL=(ALL) necessary if you are already in the admin group?

---

### Post by Bachstelze on 2010-09-12
> **CharlesA said:**
> 
Would having ALL=(ALL) necessary if you are already in the admin group?

The fact that you are in the admin group is irrelevant: as I said, if the user line is placed below the %admin line, it will completely override it.

That being said, having ALL=(ALL) is indeed not necessary here: if you can run commands as root, you can run commands as any user. If you try to run a command directly as any user but root, you will have to type your password (assming the %admin line is still there, otherwise you will get permission denied).

---

### Post by CharlesA on 2010-09-12
Thanks! That makes sense now.

---

### Post by phoenix7 on 2010-09-12
Thanks CharlesA & Bachstelze.

---

