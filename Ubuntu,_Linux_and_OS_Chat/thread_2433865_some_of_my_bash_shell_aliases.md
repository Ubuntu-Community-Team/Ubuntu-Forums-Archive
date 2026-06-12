---
title: "some of my bash shell aliases"
date: 2019-12-27
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-12-27
hey _command line_ / _bash shell_ users out there:  these are my latest aliases for the [COLOR=#0000cd][FONT=courier new]**chmod**[/FONT][/COLOR] command that i am using.  feel free to _steal_ this if you like it.  you know how to *source* it in your [COLOR=#006400][FONT=courier new]**.bashrc**[/FONT][/COLOR], right?  please let me know of any you think i should add.
```

x()         { /bin/chmod -c 0100 "$@";}
xx()        { /bin/chmod -c 0110 "$@";}
xxx()       { /bin/chmod -c 0111 "$@";}
r()         { /bin/chmod -c 0400 "$@";}
rr()        { /bin/chmod -c 0440 "$@";}
rrr()       { /bin/chmod -c 0444 "$@";}
rx()        { /bin/chmod -c 0500 "$@";}
rxx()       { /bin/chmod -c 0510 "$@";}
rxxx()      { /bin/chmod -c 0511 "$@";}
rxr()       { /bin/chmod -c 0540 "$@";}
rxrx()      { /bin/chmod -c 0550 "$@";}
rxrxx()     { /bin/chmod -c 0551 "$@";}
rxrr()      { /bin/chmod -c 0544 "$@";}
rxrxr()     { /bin/chmod -c 0554 "$@";}
rxrxrx()    { /bin/chmod -c 0555 "$@";}
rw()        { /bin/chmod -c 0600 "$@";}
rwr()       { /bin/chmod -c 0640 "$@";}
rwrr()      { /bin/chmod -c 0644 "$@";}
rwrw()      { /bin/chmod -c 0660 "$@";}
rwrwr()     { /bin/chmod -c 0664 "$@";}
rwrwrw()    { /bin/chmod -c 0666 "$@";}
rwx()       { /bin/chmod -c 0700 "$@";}
rwxx()      { /bin/chmod -c 0710 "$@";}
rwxxx()     { /bin/chmod -c 0711 "$@";}
rwxrx()     { /bin/chmod -c 0750 "$@";}
rwxrxx()    { /bin/chmod -c 0751 "$@";}
rwxrxr()    { /bin/chmod -c 0754 "$@";}
rwxrxrx()   { /bin/chmod -c 0755 "$@";}
rwxrwx()    { /bin/chmod -c 0770 "$@";}
rwxrwxx()   { /bin/chmod -c 0771 "$@";}
rwxrwxr()   { /bin/chmod -c 0774 "$@";}
rwxrwxrx()  { /bin/chmod -c 0775 "$@";}
rwxrwxrwx() { /bin/chmod -c 0777 "$@";}
rwxrwxrwt() { /bin/chmod -c 1777 "$@";}
rwxrwsrwx() { /bin/chmod -c 2777 "$@";}
rwsrwxrwx() { /bin/chmod -c 4777 "$@";}
rwsrwsrwx() { /bin/chmod -c 6777 "$@";}
rwsrwsrwt() { /bin/chmod -c 7777 "$@";}

```

---

### Post by kevdog on 2019-12-27
Seems like I should be able to incorporate these into zsh without a problem -- just need to verify syntax

---

### Post by Skaperen on 2019-12-28
it just matters how [COLOR=#0000cd][FONT=courier new]**zsh**[/FONT][/COLOR] does functions or aliases.  i'm sure you could make any needed changes in one [COLOR=#0000cd][FONT=courier new]**sed**[/FONT][/COLOR] command.

---

### Post by TheFu on 2019-12-28
Be very careful using the last 5. They have unintended consequences as you will see, if you haven't already. Best not to use absolute octal for some settings. Instead, use additive chmod +x or chmod +t or chmod g+s aliases.

---

### Post by Skaperen on 2019-12-30
do not use any setting without fully understanding every aspect of it and also having a specific reason to use that setting.  if you want to make a minor change to a [COLOR=#0000cd][FONT=courier new]**chmod**[/FONT][/COLOR] setting, the symbolic arguments for [COLOR=#0000cd][FONT=courier new]**chmod**[/FONT][/COLOR] are generally the most useful.  my aliases are useful for making settings you see on your screen from [COLOR=#0000cd][FONT=courier new]**ls**[/FONT][/COLOR] output.  these aliases are intended for cases where i was using absolute octal based on what i was seeing on the screen.  if you do not thoroughly understand the effects of these setting combinations, or the octal values, then do not use them.

---

