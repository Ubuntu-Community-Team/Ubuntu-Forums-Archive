---
title: "Another &quot;would it be possible?&quot; question"
date: 2009-11-04
forum: Security
---

### Post by suitedaces on 2009-11-04
Would it be possible to set up "dual passwords", that is, have one really strong password for logging in, and another easier one for working within ubuntu (eg, after sudo)? 

I ask because I never leave my computer logged on unsupervised, and have a really strong password, but those numbers and different cases can become a pita when needing to enter password during a session.

---

### Post by NoaHall on 2009-11-04
Yes.

---

### Post by suitedaces on 2009-11-04
Excellent. 

How so?

---

### Post by NoaHall on 2009-11-04
Well, you can either create a different user just for sudo, or enable root. I'm not allowed to tell you how on the forums. But it's not too hard, after a quick google.

---

### Post by suitedaces on 2009-11-04
Thanks, I won't ask you to break forum rules.

---

### Post by Agent ME on 2009-11-04
No need to enable root account. Instead, you could set up another account in the admin group you use just for admin stuff.

Then, when you're logged in on your main account, in a terminal, type "su other-account-name", and then enter that account's password. Then type "sudo mycommand". This will probably require you to enter the second account's password a second time, but you can probably find a way to disable this in sudo's settings.

---

### Post by Lars Noodén on 2009-11-05
> **Agent ME said:**
> No need to enable root account. Instead, you could set up another account in the admin group you use just for admin stuff.

Then, when you're logged in on your main account, in a terminal, type "su other-account-name", and then enter that account's password. Then type "sudo mycommand". This will probably require you to enter the second account's password a second time, but you can probably find a way to disable this in sudo's settings.

+1

"su **-** other-account-name" will even set the environment variables and change the directory.  

You can also enable fast user switching and switch accounts for action that requires sudo.

---

### Post by TheForumTroll on 2009-11-05
Wouldn't that defeat the whole purpose? Then there would be no need to break the hard password as there is another account with a weaker password with the same permissions (root access). As I understand it what there is being asked is a way to have one password at login and then another for admin use while logged in which is not able to log in on its own.

---

### Post by shaggy999 on 2009-11-06
What you want is:

Limited Account w/ easy password
Admin account w/ tough password


You already have an admin account with a tough password. So just create a limited account (no sudo access) w/ an easy password and use that for regular logon stuff.

---

