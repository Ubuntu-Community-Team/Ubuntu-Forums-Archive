---
title: "Aliases how to create?"
date: 2010-06-08
forum: Server Platforms
---

### Post by SpinningAround on 2010-06-08
In desktop version can you create alias by adding them to .bash_aliases but how does it work in the server version?

---

### Post by NullHead on 2010-06-08
It goes in .bashrc now I guess. 

Just add a line like to the end of the file:
alias customcommand='real command'

---

### Post by capscrew on 2010-06-08
> **SpinningAround said:**
> In desktop version can you create alias by adding them to .bash_aliases but how does it work in the server version?


It works the same way.  The shell is the same in the server as it is on the desktop. If there isn't a .bash_aliases file, then make one and find the relevant stanza in the .bashrc to uncomment.

---

### Post by Backharlow on 2010-06-08
> If there isn't a .bash_aliases file the make one and find the relevant stanza in the .bashrc to uncomment.
Correct. You CAN just put aliases in .bashrc but its considered bad form.
Also watch out for getting too complicated with aliases and watch out for other people trying to use your bash.

---

### Post by FuturePilot on 2010-06-08
You have to uncomment these lines in .bashrc before .bash_aliases will work

```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

---

### Post by SpinningAround on 2010-06-09
Thanks for all the answers :)

---

