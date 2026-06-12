---
title: "error shutdown shows user password"
date: 2012-11-08
forum: Security
---

### Post by GreenChiliRelleno on 2012-11-08
I've had a recent shutdown error and while the system was displaying its stopping services screen, on one of the last few lines, my user password was displayed in plain text. Is this an error/bug/flaw?

Running Ubuntu 12.10 64-bit on a Dell Inspiron 1525 with Gnome 3 desktop shell

---

### Post by CharlesA on 2012-11-09
What was the exact output? It might show your username, but it won't show your password.

---

### Post by lisati on 2012-11-09
> **CharlesA said:**
> What was the exact output? It might show your username, but it won't show your password.

+1: seeing a password in plain view is unusual.

---

### Post by Ms. Daisy on 2012-11-10
...unless you accidentally typed your password in the terminal and hit enter when bash wasn't asking for a password. Then it would show in the terminal history.

Or if you've got some script set up with the password hard-coded into it (like with rsync).

It would be good practice to change the password regardless of what caused it.

---

