---
title: "[SOLVED] Bash doesn't show working directory anymore"
date: 2008-10-19
forum: Server Platforms
---

### Post by dacool25 on 2008-10-19
For some reason my bash isn't showing my working directory anymore.  All it shows is ~ after my username and servername.

Attached is my .bashrc

```
#~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples
 
# If not running interactively, don't do anything
[ -z "$PS1" ] && return
 
# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth
 
# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize
 
# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"
 
# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi
 
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac
 
# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_colored_prompt=yes
 
if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        # We have color support; assume it's compliant with Ecma-48
        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
        # a case would tend to support setf rather than setaf.)
        color_prompt=yes
    else
        color_prompt=
    fi
fi
 
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt
 
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac
 
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.
 
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
 
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
 
    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi
 
# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'
 
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

---

### Post by redbrain on 2008-10-19
What do you mean as in your bash prompt doesnt show what dir you are in?

so if you do:

cd ~
your prompt is:
$USER@$HOSTNAME:~$

And if you do like:
cd /var/lib
$USER@$HOSTNAME:/var/lib$

---

### Post by dacool25 on 2008-10-19
Yes, that is the problem if i cd into a directory, it won't show.

All that I get is user@hostname:~$ (no matter what directory i'm in)

---

### Post by Mister.Vash on 2008-10-22
I tested all the PS1= lines from your post and they worked correctly on my machine and show the current directory on the line.

Can you do the following and post it ```
echo $PS1
```

Off the top of my head, it might be that either the system is picking up the variable from another file, or the posting of your .bashrc was not the one being used.

Can you verify that the .bashrc file that you included was from ~/.bashrc just to validate.

If it was the same, can you rename the ~/.bashrc file to ~/bashrc.backup then start a new shell and see if the prompt is the same as before?  Also, double check and see if you have anything in your ~/.bash_profile

---

### Post by dacool25 on 2008-10-22
I had a friend look at it, not too sure what he did, but it works now!

Thank you for your help though

---

### Post by Mister.Vash on 2008-10-22
Glad to hear it's working now - can you mark the thread as resolved then?

---

### Post by dacool25 on 2008-10-22
Ofcourse!

---

