---
title: "Installed Perl but no /usr/bin/perl"
date: 2007-05-19
forum: Server Platforms
---

### Post by Double-X on 2007-05-19
Hi all,

I installed Perl 5.8.8 but a folder named /usr/bin/perl doesn't exist.
How can I correct this?

Hope someone can help me with this....

Thanks in advanced.

---

### Post by Jussi Kukkonen on 2007-05-19
The installation must have gone wrong somehow -- /usr/bin/perl executable gets installed from perl-base which is a dependency of perl. Can you provide some info on where you installed it from and what OS version you are running?

---

### Post by Double-X on 2007-05-20
What I used was
 Sudo aptitude install perl 

Feisty 7.04


I'm going to reinstall anyway :p I messed up to much.

---

