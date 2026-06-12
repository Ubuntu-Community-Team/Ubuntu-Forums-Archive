---
title: "PGP Encryp Disable Special File Names"
date: 2011-01-03
forum: Security
---

### Post by michf on 2011-01-03
Using windows 7 gpg 2.0.14, system defaulting file names on decrypt to [FONT=Arial]-&12. Found that there is an option for **--enable-special-filenames. **This options enables a mode in which filenames of the form `*-&n*', where n is a non-negative decimal number, refer to the file descriptor n and not to a file with that name.[/FONT]
 
[FONT=Arial]Can not figure out how to disable this option??? Any ideas? Maybe it is something else all together?????[/FONT]

---

### Post by euler_fan on 2011-01-04
> **michf said:**
> Using windows 7 gpg 2.0.14, system defaulting file names on decrypt to [FONT=Arial]-&12. Found that there is an option for **--enable-special-filenames. **This options enables a mode in which filenames of the form `*-&n*', where n is a non-negative decimal number, refer to the file descriptor n and not to a file with that name.[/FONT]
 
[FONT=Arial]Can not figure out how to disable this option??? Any ideas? Maybe it is something else all together?????[/FONT]

Don't use the flag in your command line call to gpg2 or in your gpg.conf file. Because it is an ``enable"-type flag, the option is disabled by default.

see man gpg2

---

### Post by michf on 2011-01-05
It seems that when I installed the software it enabled this option by default (versus disabled) I am using Kleopatra.  Kleopatra does not have this option so on a command line in gpg I tried to disable, I tired disable-special-filenames but it did not work. Thank you.

---

