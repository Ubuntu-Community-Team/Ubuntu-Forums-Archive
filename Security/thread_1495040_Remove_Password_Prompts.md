---
title: "Remove Password Prompts"
date: 2010-05-27
forum: Security
---

### Post by Johnathannn on 2010-05-27
I know, everyone will tell me this is a horrible idea! Please do not tell me I already know lol, but I was wondering how!? Whenever I try to install a program, etc, I get the annoying "Enter your password to perform administrative tasks" prompt. I want to know how to disable this, and use Ubuntu password free!?

---

### Post by dv3500ea on 2010-05-27
It does that for security reasons so that programs can't damage your system without your permission. Even as an administrator you need to enter a password to do anything that alters your system for all users. The only possible way to unsolve security problems is to enable a root user, which isn't generally done on ubuntu - it uses sudo as a replacement. I don't actually know how to do this but you could enable root user and log on as root. Research this at your own peril.

---

### Post by Johnathannn on 2010-05-27
Yeah, I did and I found out you have to edit "sudoers", so I went in the terminal, typed in "sudo visudo" and then edited a line that had "%admin....." and other words, and put in "NOPASSWD", but I do not know how to save this file?

---

### Post by bodhi.zazen on 2010-05-27
> **Johnathannn said:**
> Yeah, I did and I found out you have to edit "sudoers", so I went in the terminal, typed in "sudo visudo" and then edited a line that had "%admin....." and other words, and put in "NOPASSWD", but I do not know how to save this file?

I assume the editor is vi, so use these keys :

Esc

:wq

See : [http://heather.cs.ucdavis.edu/~matloff/UnixAndC/Editors/ViIntro.html](http://heather.cs.ucdavis.edu/~matloff/UnixAndC/Editors/ViIntro.html)

Or any of the online vi (vim) guides.

---

