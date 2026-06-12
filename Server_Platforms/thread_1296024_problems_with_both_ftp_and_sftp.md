---
title: "problems with both ftp and sftp"
date: 2009-10-20
forum: Server Platforms
---

### Post by tominated on 2009-10-20
Hi,
It's my first post here, and I'm having a fair bit of trouble on an unmanaged vps i just signed up for that runs ubuntu 9.04. The problem I'm having is that I cannot connect to my server with sftp (although I can ssh in with no problems) and ftp wont work either (I have vsftpd installed too). I have scoured the web and can't find anything. No matter what I do, i always get a connection refused error. Any help would be greatly appreciated. Also of note, I am a bit of a beginner with linux. I know my way around most of it thanks to a couple of years messing on mac os x (not the same, but close enough), but try and keep it simple please!

Thanks in advance!

---

### Post by dvlchd3 on 2009-10-20
Who setup the VPS?  It seems they have not configured it correctly to allow for FTP connections.

Since you can ssh, you could always use scp (secure copy).  This allows the transport of files through the ssh protocol.  If you are using Windows and have downloaded putty, you should already have the secure copy client installed.

```

scp [from file] [username]@[domain name OR ip address]:[to folder]

```
(not sure, but I believe a -r option will allow you to copy entire directories recursively)

---

### Post by Lars Noodén on 2009-10-20
You may not need VSFTP if you only want to transfer files using SFTP.  SFTP file transfer is build into SSH.  If that is the case, try unistalling vsftp.  

vsftp would be of use if you want to publish material for download via the old insecure FTP.  That's find for some activities.

---

### Post by tominated on 2009-10-21
> **dvlchd3 said:**
> Who setup the VPS?  It seems they have not configured it correctly to allow for FTP connections.

Since you can ssh, you could always use scp (secure copy).  This allows the transport of files through the ssh protocol.  If you are using Windows and have downloaded putty, you should already have the secure copy client installed.

```

scp [from file] [username]@[domain name OR ip address]:[to folder]

```
(not sure, but I believe a -r option will allow you to copy entire directories recursively)

The host i got it from pretty much only had ssh and apache installed by default i think. I've been following the tutorial at [http://www.matejunkie.com/howto-nginx-with-php-and-passenger-mod_rails-at-once/](http://www.matejunkie.com/howto-nginx-with-php-and-passenger-mod_rails-at-once/) to get rails and php going (just in case i need php) under nginx if that may have screwed anything up. 

I tried sftp, but I'm getting the error "Received message too long." I've searched around a bit and most sites point to [http://www.snailbook.com/faq/sftp-corruption.auto.html](http://www.snailbook.com/faq/sftp-corruption.auto.html), but I don't know what to do. my .bashrc is the following:

```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
#export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\$
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033$

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
if [ "$TERM" != "dumb" ]; then
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

```

any suggestions?

p.s. I use a mac locally, so i can run most unix commands

---

