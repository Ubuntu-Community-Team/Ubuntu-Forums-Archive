---
title: "Passwordless Application"
date: 2010-09-20
forum: Security
---

### Post by gripple on 2010-09-20
Is it possible to make an application for normal users run as a root without requiring a password?

---

### Post by CharlesA on 2010-09-20
I doubt it. 

If it was possible it would be a very bad idea.

---

### Post by sisco311 on 2010-09-20
> **gripple said:**
> Is it possible to make an application for normal users run as a root without requiring a password?

Yes, take a look at:
[thread=1132821]HowTO: Sudoers Configuration[/thread]

EDIT: Oh, and welcome to the forums!

---

### Post by DZ* on 2010-09-20
Try this

Edit bodhi.zazen - removed code. It was harmless, but maxes out CPU.

---

### Post by Rubi1200 on 2010-09-20
> **DZ* said:**
> Try this

Edit bodhi.zazen - code removed, see above.


Very interesting, but could you please elaborate and explain what each line does?

Thanks in advance.

---

### Post by Bachstelze on 2010-09-20
chmod +s sets the setuid bit on an executable. It means that whenever a user (any user) runs the executable, it will run with the privileges of its owner. Here, since the file was chown'ed to root, it will always run as root, regadless of which user actually runs it. This is how sudo is able to give you root privileges, for example.

Obviously, this should be used with care.

---

### Post by The Cog on 2010-09-20
He's trying to get you to compile a small program that just eats up CPU doing nothing, and change it to run as root regardless of whoever launches it. But it probably won't work because he forgot to suggest installing a compiler first. And that's not the best way anyway - using sudoers is probably the safer way to go. Read the link that sisco311 gave you.

---

### Post by Rubi1200 on 2010-09-20
@ Bachstelze: thanks for the explanation

@ The Cog: ditto, but I am not the OP. Thanks for the advice anyway.

---

### Post by bodhi.zazen on 2010-09-20
Note : after review by the staff, we decided the discussion had run it's course and the exmaple code was removed.

---

