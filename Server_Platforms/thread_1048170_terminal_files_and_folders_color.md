---
title: "terminal files and folders color"
date: 2009-01-23
forum: Server Platforms
---

### Post by any.linux12 on 2009-01-23
Hi

I have two system that I access via ssh and I did some changes today in both. Was just to change users name and id with webmin

After that I loged out and in once again and in one system everything is like before but in the other I can't see diferent colors when I type ls.
like folders should be blue, x file light green and tar red etc...but everything is black. Why? what can I do becouse I don't see diferences between the users options.
And by the way, when I do sudo su I have colors again
thanks

---

### Post by Dr Small on 2009-01-23
Probably ls has not been aliased for colors. Simply put this at the bottom of the ~/.bashrc file for the user, logout, log back in and try it now:
```
alias ls='ls --color=auto'
```

Also, if you want colorful manpages, you can use this one :)
```
# For colourful man pages (CLUG-Wiki style)
# http://wiki.clug.org.za/wiki/Colour_on_the_command_line#Colourful_manpages_.28
export LESS_TERMCAP_mb=$'\E[01;31m'
export LESS_TERMCAP_md=$'\E[01;31m'
export LESS_TERMCAP_me=$'\E[0m'
export LESS_TERMCAP_se=$'\E[0m'
export LESS_TERMCAP_so=$'\E[01;44;33m'
export LESS_TERMCAP_ue=$'\E[0m'
export LESS_TERMCAP_us=$'\E[01;32m'
```

---

### Post by any.linux12 on 2009-01-26
OH cool thks a lot :D

---

