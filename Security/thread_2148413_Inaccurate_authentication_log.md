---
title: "Inaccurate authentication log"
date: 2013-05-25
forum: Security
---

### Post by Yurigisu on 2013-05-25
Hello,

   I am in a position that requires me to check on user login/logout times and login duration. When I used 'last username', the times I got were extremely inaccurate, same with 'last -f wtmp username'. After analyzing full 'last' output, I noticed that the missing time was logged with username 'reboot', 'system boot' in place of tty/pts. In this way, many hours, even days are missing from user's activity journal. Now, is there a way to fix this problem, or should it be reported as bug or something?

forgot the details. Ubuntu 13.04, standard desktop system with intel/nvidia chips.

---

### Post by unspawn on 2013-05-25
> **Yurigisu said:**
> Now, is there a way to fix this problem, or should it be reported as bug or something?
Yes and no. 

The only things here that deserve the qualification "extremely inaccurate" would be your understanding of GNU/Linux and your chosen method of parsing data:
- if you run 'last -f wtmp username' then you're forgetting 'last' parses /var/log/wtmp by default. So supply a leading path (unless you really meant to parse that wtmp file %{deities}-know-who dropped in your cwd ;-p).
- if your reporting tool doesn't take shutdowns and reboots into account you probably should make it expect those events. (Also don't forget about logrotate ;-p)
- elif shutdowns and reboots are not authorized or may only be performed by authorized personnel then you should adapt your system policy accordingly.
With all due respect BTW.

---

### Post by Yurigisu on 2013-05-25
Yeah, sorry, I didn't expect people to be case-sensitive. 'wtmp' was parsed with a path. About your if - my question was exactly 'HOW to fix it' - at least some basic configuration I should inspect under standard ubuntu 13.04 desktop distro without any non-default monitoring tools.
I am not going to deny my knowledge, but hey - the last time I did ubuntu installation, it was encouraging to use forums for questions.

---

### Post by unspawn on 2013-05-25
> **Yurigisu said:**
> (..) some basic configuration I should inspect (..) without any non-default monitoring tools.
I don't know if your definition of "non-default monitoring tool" excludes BSD Accounting but if it doesn't your probably better off parsing output of say 'ac -adpyz --compatibility' for totals.

---

