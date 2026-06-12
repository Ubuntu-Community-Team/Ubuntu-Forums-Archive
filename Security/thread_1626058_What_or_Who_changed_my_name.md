---
title: "What or Who changed my name?"
date: 2010-11-19
forum: Security
---

### Post by VcDeveloper on 2010-11-19
I just notice my name I use to install is now "Web server admin".  Was this changed when I installed LAMP packes?

---

### Post by cariboo on 2010-11-20
Can you log in as Web server admin?

---

### Post by CharlesA on 2010-11-20
What's the output of this:

```
whoami
```

```
cat /etc/passwd | grep $(whoami)
```

---

### Post by VcDeveloper on 2010-11-20
> **cariboo907 said:**
> Can you log in as Web server admin?
Yes, I can still log in.  My login name is still the same, its my full name that was changed.

> **CharlesA said:**
> What's the output of this:

whoami
cat /etc/passwd | grep $(whoami)

whoami:
My login name was listed, which is the one I created during install.

cat /etc/passwd | grep $(whoami)
nothing

---

### Post by CharlesA on 2010-11-20
Huh. Try just grepping your username you login with. It should be shown in the passwd file.

Is it listed correctly in "About Me" ?

---

### Post by VcDeveloper on 2010-11-21
> **CharlesA said:**
> Huh. Try just grepping your username you login with. It should be shown in the passwd file.

Is it listed correctly in "About Me" ?

I didn't understand how your grep line was constructed until I removed @(whoami) and just put my login name and got this:
```
<my-correct-login-name>:x:1000:1000:Web server admin:/home/<my-correct-login-name>:/bin/bash
```

---

### Post by CharlesA on 2010-11-21
Ok. That's just yer "name" not yer username. You can change it if you like.

If you've got a GUI, you can change it in About Me, I believe.

---

### Post by VcDeveloper on 2010-11-21
OK, Thanks for your help!  How was this changed from my user name I used during install to this name?

---

### Post by CharlesA on 2010-11-21
Don't know, probably changed when you installed something. *shrug*

At least it's easy to change back.

---

### Post by VcDeveloper on 2010-11-21
> **CharlesA said:**
> Don't know, probably changed when you installed something. *shrug*

At least it's easy to change back.

I apologize, but I'm not up on all the linux acronyms, but what is *shrug*?

---

### Post by CharlesA on 2010-11-21
Text version of a shrug.

Not a linux thing. :)

---

### Post by VcDeveloper on 2010-11-21
Ok thanks!... :)

---

