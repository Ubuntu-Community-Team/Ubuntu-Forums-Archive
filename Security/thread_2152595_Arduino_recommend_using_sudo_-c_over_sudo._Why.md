---
title: "Arduino recommend using sudo -c over sudo. Why?"
date: 2013-06-08
forum: Security
---

### Post by nitrosrt10 on 2013-06-08
I was installing Arduino environment with the help of their wiki, where they recommended using su -c but I didn't understood their explanation. Their exact words were:

[h=3]A Quick Note about su -c[/h][COLOR=#555555][FONT=Georgia]The accepted convention is to use sudo. However, sudo requires you be a member of the sudoers group. (You could also edit the supplementary files the sudoers file reads from, but this is highly ***NOT*** recommended.) su without the -c option will not accept a command to pass to the root shell, but will instead login to the root account. This can be dangerous, so I recommend using su -c or (if you're already a member of the sudoers group or have an administrator handy) sudo.

What does this exactly mean?[/FONT][/COLOR]

---

### Post by prodigy_ on 2013-06-08
As far as I can tell, they recommend **su -c** or **sudo** over plain **su**, not su -c over sudo. Without the -c option su is (roughly) an equivalent of sudo -i. It gives you an interactive root shell.

Security implications are pretty straightforward. E.g. if someone gets access to an (unlocked) machine with an interactive root shell running, they could execute any command without knowing any passwords.

---

### Post by Soul-Sing on 2013-06-08
recommending sudo over su==> sudo -i would be nice(r)

---

### Post by nitrosrt10 on 2013-06-09
> **prodigy_ said:**
> As far as I can tell, they recommend **su -c** or **sudo** over plain **su**, not su -c over sudo. Without the -c option su is (roughly) an equivalent of sudo -i. It gives you an interactive root shell.

Security implications are pretty straightforward. E.g. if someone gets access to an (unlocked) machine with an interactive root shell running, they could execute any command without knowing any passwords.
Gotcha! Thanks for the explaination.

---

