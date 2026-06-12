---
title: "Upgraded from Dapper to 8.04 - Bash Completion Broken?"
date: 2008-05-27
forum: Server Platforms
---

### Post by Altrezia on 2008-05-27
Hello chaps,

Sorry to bother you for something which is probably easy to fix - but I've run out of ideas.

I upgraded from Dapper Drake to Hardy, using the CLI upgrade. Now I can't use the arrow keys or tab-completion. 

Any ideas how to fix it? I've tried googling to no avail.

Thanks in advance.

-al.

---

### Post by windependence on 2008-05-27
```
twincactus@Mako:~$ sudo nano /etc/bash.bashrc
```

Uncomment the following lines under enable bash completion in interactive shells:


```
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

```


Remove the # to uncomment the above lines.

Log out and log back in.


Enjoy.


-Tim

---

### Post by Altrezia on 2008-05-27
Thanks for that. Tried, but it still doesn't work. When pushing tab, it actually tabs - adds whitespace. Arrow keys give this: ^[[A

Here's my bash.bashrc file as it stands:

[PHP]
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
[/PHP]

Cheers

---

### Post by windependence on 2008-05-27
This is a bug in hardy. To fix it you need to replace your /etc/bash-completion file with the one from Gutsy.

[https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/194860](https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/194860)


-Tim

---

### Post by Altrezia on 2008-05-27
Thanks for the link, but it doesnt fix my issue.

I tried using the bash_completion file in that 'fix' but the problem is still there. 

All I have is the $, no user or current directory. Very frustrating !

---

### Post by nazgum on 2008-06-20
I have the same issue, its only with a normal user this occurs for, tab completion and prompt and everything works fine as the root user.

Anyone who knows how to fix this and can post here would be greatly appreciated =)

---

### Post by nazgum on 2008-06-20
figured it out, just do:

sudo unlink /bin/sh
sudo ln -s /bin/bash /bin/sh

(by default it was linked to dash)

---

### Post by Altrezia on 2008-06-21
You star. I will try this when I get back to work on monday.
Thanks!

---

