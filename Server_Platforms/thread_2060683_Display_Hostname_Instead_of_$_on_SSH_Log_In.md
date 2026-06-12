---
title: "Display Hostname Instead of $ on SSH Log In"
date: 2012-09-20
forum: Server Platforms
---

### Post by Xplorer4x4 on 2012-09-20
When I log in to my ubuntu server via SSH, the terminal sits at a $. How do I alter this so it would say username@hostname: $

---

### Post by CharlesA on 2012-09-20
Check .bashrc

[http://bodhizazen.net/Tutorials/bashrc](http://bodhizazen.net/Tutorials/bashrc)

---

### Post by Xplorer4x4 on 2012-09-20
I tried to edit ~\.bashrc (which did not exist, and put that in there. Saved it, rebooted, no change. echo $PS1 gives no output after the edit.

EDIT: I ended up entering the following in to a terminal:
```
PS1="\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$ "
```
Now it displays as:
```
user@hostname:~$ 
```

Thanks for atleast pointing me in the right direction CharlesA.

---

### Post by xdracco on 2012-09-24
Here's my colorful prompt code for .bashrc:

```
# Prompt colors
# Regular
C_RED="\[\e[0;31m\]"
C_GREEN="\[\e[0;32m\]"
C_LIGHT_GRAY="\[\e[0;37m\]"
C_RESET="\[\e[0m\]"
C_BROWN="\[\e[0;33m\]"
C_BLUE="\[\e[0;34m\]"
C_PURPLE="\[\e[0;35m\]"
C_CYAN="\[\e[0;36m\] "
# Bold
C_BOLD_GRAY="\[\e[1;30m\]"
C_BOLD_WHITE="\[\e[1;37m\]"
C_BOLD_YELLOW="\[\e[1;33m\]"
C_BOLD_BLUE="\[\e[1;34m\]"
C_BOLD_CYAN="\[\e[1;36m\]"
C_BOLD_PURPLE="\[\e[1;35m\]"
C_BOLD_RED="\[\e[1; 31m\]"
C_BOLD_GREEN="\[\e[1;32m\]"

# Custom prompt
PS1="${debian_chroot:+($debian_chroot)}${C_BOLD_GREEN}[${C_GREEN}\u@\h:${C_BLUE}\w${C_BOLD_GREEN}]\[\e[m\] ${C_GREEN}\$\[\e[m\] "
```

---

