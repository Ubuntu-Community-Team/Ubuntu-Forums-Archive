---
title: "Should user shell configs = system shell configs?"
date: 2010-01-20
forum: System76 Support
---

### Post by watchpocket on 2010-01-20
In my limited time with Ubuntu (about 2 months) I've seen that the [FONT=Courier New]**sudo**[/FONT] command gets invoked a whole lot for all sorts of almost daily admin tasks.

But once I invoke [FONT=Courier New]**sudo**[/FONT], i am abruptly yanked out of my familiar customized user shell environment, and suddenly, with me operating now as admin or super-user, the interface is clunky and not what I'm used to, and my fingers will instinctively type aliases that, all of a sudden, don't work when I'm over here in [FONT=Courier New]**sudo**[/FONT]-land.

So I want to copy all or most of my user zsh config files ( ~/.zshenv and ~/.zshrc , basically ) to the system /etc/zshenv and /etc/zshrc (which are currently empty, or nearly so) so that user configuration and system configuration match, or mostly match.

My only question:  Is there any reason not to do that?  Seems like it would make life a lot easier, though I can see might have to be careful when setting up, as root, an environment machine-wide.

---

### Post by jdb on 2010-01-20
> **watchpocket said:**
> In my limited time with Ubuntu (about 2 months) I've seen that the [FONT=Courier New]**sudo**[/FONT] command gets invoked a whole lot for all sorts of almost daily admin tasks.

But once I invoke [FONT=Courier New]**sudo**[/FONT], i am abruptly yanked out of my familiar customized user shell environment, and suddenly, with me operating now as admin or super-user, the interface is clunky and not what I'm used to, and my fingers will instinctively type aliases that, all of a sudden, don't work when I'm over here in [FONT=Courier New]**sudo**[/FONT]-land.

So I want to copy all or most of my user zsh config files ( ~/.zshenv and ~/.zshrc , basically ) to the system /etc/zshenv and /etc/zshrc (which are currently empty, or nearly so) so that user configuration and system configuration match, or mostly match.

My only question:  Is there any reason not to do that?  Seems like it would make life a lot easier, though I can see might have to be careful when setting up, as root, an environment machine-wide.

Your shell environment comes from the .bashrc in your home directory.
Roots shell environment comes from the .bashrc in roots home directory which is /root.

You can make the root environment just like yours by copying your .bashrc to root.

```
# go to your home directory by typing
cd
# save roots original .bashrc
sudo mv /root.bashrc /root.bashrc.bak
# copy your .bashrc to roots home directory
sudo cp .bashrc /root
```

jdb

---

### Post by watchpocket on 2010-01-20
What is the role or purpose, then, of /etc/zshrc and the other /etc/zsh config files?  I'd thought those were the system shell configs.  If I had an /etc/zshrc file, what would that do? Would it also effect system-wide configs?  

What's the difference between /root.zshrc and /etc/zshrc ??

I'd assumed that copying, e.g., ~/.zshrc to /etc/zshrc would do the trick, but I'll do it the way you describe.

Also, I use zsh, not bash, so I'm guessing there is no pre-existing root.zshrc.

I'm guessing, if the active default system shell is bash, that I can:

```

sudo mv /root.bashrc /root.bashrc.bak
sudo cp .zshrc /root
```

---

### Post by jdb on 2010-01-20
> **watchpocket said:**
> What is the role or purpose, then, of /etc/zshrc and the other /etc/zsh config files?  I'd thought those were the system shell configs.  If I had an /etc/zshrc file, what would that do? Would it also effect system-wide configs?  

What's the difference between /root.zshrc and /etc/zshrc ??

I'd assumed that copying, e.g., ~/.zshrc to /etc/zshrc would do the trick, but I'll do it the way you describe.

Also, I use zsh, not bash, so I'm guessing there is no pre-existing root.zshrc.

I'm guessing, if the active default system shell is bash, that I can:

```

sudo mv /root.bashrc /root.bashrc.bak
sudo cp .zshrc /root
```

Sorry, I don't know anything about zsh, I use bash.
I didn't know what zsh was when I read your first post.

jdb

---

### Post by watchpocket on 2010-01-21
okay then, same question for bash.  I'm wondering about the distinction between, say,/etc/bashrc and /root.bashrc.

What's the diff?

---

### Post by riseringseeker on 2010-01-21
> **watchpocket said:**
> okay then, same question for bash.  I'm wondering about the distinction between, say,/etc/bashrc and /root.bashrc.

What's the diff?

_[http://www.linuxquestions.org/questions/linux-general-1/etcprofile-v.s.-etcbashrc-273992/](http://www.linuxquestions.org/questions/linux-general-1/etcprofile-v.s.-etcbashrc-273992/)_

Does a pretty good job of explaining them.

---

### Post by jdb on 2010-01-21
> **watchpocket said:**
> okay then, same question for bash.  I'm wondering about the distinction between, say,/etc/bashrc and /root.bashrc.

What's the diff?

This is from

```
man bash
```

```
 When bash is invoked as an interactive login shell, or as a  non-inter&#8208;
active  shell with the --login option, it first reads and executes com&#8208;
mands from the file /etc/profile, if that file exists.   After  reading
that file, it looks for ~/.bash_profile, ~/.bash_login, and ~/.profile,
in that order, and reads and executes commands from the first one  that
exists  and  is  readable.  The --noprofile option may be used when the
shell is started to inhibit this behavior.

....

FILES
       /bin/bash
              The bash executable
       /etc/profile
              The systemwide initialization file, executed for login shells
       /etc/bash.bashrc
              The systemwide per-interactive-shell startup file
       /etc/bash.bash.logout
              The  systemwide  login shell cleanup file, executed when a login
              shell exits
       ~/.bash_profile
              The personal initialization file, executed for login shells
       ~/.bashrc
              The individual per-interactive-shell startup file
       ~/.bash_logout
              The individual login shell cleanup file, executed when  a  login
              shell exits
       ~/.inputrc
              Individual readline initialization file



```

jdb

---

### Post by watchpocket on 2010-01-21
None of this says anything about

**/root**.bashrc

which was the main focus of my question.  I don't remember the bash (or zsh) manpages talking about /**root**.bashrc.  

/etc/bashrc (and so on), **yes**.

But, jdb, you said:

*Roots shell environment comes from the .bashrc in roots home directory which is /root.*

*You can make the root environment just like yours by copying your .bashrc to root.*


I did that, and now my prompt is  **rj-home/:**

instead of  **rj-home~:**

Of course, I *want* **rj-home~:**

Also, when I type **ls**
my home dir is displayed with colors I've set distinguishing files from subdirs, and a slash to the right of all subdirs, an asterisk to the right of executables, and everything else according to my shell configs.

But when I type **sudo ls**, I get raw white-text output according either to system default bash settings or no settings at all.  

And I'd like things to look & act the same when I use sudo.

Question:  Once I've put my config files in **/etc/zsh/**,  where (and with what command -- exec zsh -l ?? -- ) do I tell the system to read from them **instead of** from the system's default bash config-files?

And do I need to put the config files in **both** /etc/zsh/ and **/root.zshrc**

(and is that supposed to be **/root.zshrc** or **/root/.zshrc** ???

Thanks to anyone who can help sort through this.

---

### Post by jdb on 2010-01-21
> **watchpocket said:**
> None of this says anything about

**/root**.bashrc

which was the main focus of my question.  I don't remember the bash (or zsh) manpages talking about /**root**.bashrc.  

/etc/bashrc (and so on), **yes**.

But, jdb, you said:

*Roots shell environment comes from the .bashrc in roots home directory which is /root.*

*You can make the root environment just like yours by copying your .bashrc to root.*


I did that, and now my prompt is  **rj-home/:**

instead of  **rj-home~:**

Of course, I *want* **rj-home~:**

Also, when I type **ls**
my home dir is displayed with colors I've set distinguishing files from subdirs, and a slash to the right of all subdirs, an asterisk to the right of executables, and everything else according to my shell configs.

But when I type **sudo ls**, I get raw white-text output according either to system default bash settings or no settings at all.  

And I'd like things to look & act the same when I use sudo.

Question:  Once I've put my config files in **/etc/zsh/**,  where (and with what command -- exec zsh -l ?? -- ) do I tell the system to read from them **instead of** from the system's default bash config-files?

And do I need to put the config files in **both** /etc/zsh/ and **/root.zshrc**

(and is that supposed to be **/root.zshrc** or **/root/.zshrc** ???

Thanks to anyone who can help sort through this.


This is an example of what I have in my .bashrc files.
I use a conditional statement to make root look different.
My stuff is just appended to the end of of the stock file.
I've never run across a file root.bashrc, could it be root/.bashrc ??

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

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
#force_color_prompt=yes

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
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

###################### my stuff ################################################

umask 0022
export EDITOR=vi
if [ ! $NOTFIRSTDOGFISH ]
  then
  export NOTFIRSTDOGFISH=1
  export PATH=/boota/data/scripts:$PATH
  fi
if [ ${EUID} == 0 ]
   then
   export PROMPT_COMMAND='PS1="\[\e[1;35m\]"`date +%H:%M:%S`" "`pwd`"\[\e[00m\] "'
else
   export PROMPT_COMMAND='PS1="\[\e[1;36m\]"`date +%H:%M:%S`" \W\[\e[00m\] "'
    if [ `mount | grep -w data | wc -l | cut -d\  -f1` -ne 0 ] ; then
      when
      fi
   fi
cat /who.txt

alias pk='echo -e "`ps -eo user,pid,ppid,tty,stime,s,ni,rss,cmd`\nUSER       PID  PPID TTY      STIME S  NI   RSS CMD"'
alias hg='history | grep'
alias s='sudo bash'
alias ss='sudo -i -H'
alias darter='sudo mount darter:/ /darter ; sudo mount darter:/data /darter/data ; sudo mount darter:/backup /darter/backup ; sudo mount darter:/dogs /darter/dogs'
alias udarter='sudo umount /darter/dogs ; sudo umount /darter/data ; sudo umount /darter/backup ; sudo umount /darter'
alias bullet='sudo mount bullet:/ /bullet ; sudo mount bullet:/boota /bullet/boota'
alias ubullet='sudo umount /bullet/boota ; sudo umount /bullet'
alias family='sudo mount family:/ /family ; sudo mount family:/data /family/data'
alias ufamily='sudo umount /family/data ; sudo umount /family'
alias win='sudo mount win:/ /win ; sudo mount win:/boota /win/boota ; sudo mount win:/dogs /win/dogs'
alias uwin='sudo umount /win/dogs ; sudo umount /win/boota ; sudo umount /win'
alias rmtil='sudo find / /data -xdev -name "*~" -exec rm {} \; -print'
alias findtil='sudo find / /data -xdev -name "*~"'
alias e='emelfm2 &>/dev/null &'

```

jdb

---

### Post by watchpocket on 2010-01-21
> [I]I've never run across a file root.bashrc, could it be root/.bashrc ??

[/I]Probably.  I was just quoting you from above:

[FONT=Courier New]> sudo mv /root.bashrc /root.bashrc.bak[/FONT]

Maybe you meant to put a slash where you'd put the dot & it's a typo.

Meanwhile I still haven't quite figured out how to get the system's and my user configs to match. . . .

---

### Post by jdb on 2010-01-21
> **watchpocket said:**
> > [I]I've never run across a file root.bashrc, could it be root/.bashrc ??

[/I]Probably.  I was just quoting you from above:

[FONT=Courier New]> sudo mv /root.bashrc /root.bashrc.bak[/FONT]

Maybe you meant to put a slash where you'd put the dot & it's a typo.

Meanwhile I still haven't quite figured out how to get the system's and my user configs to match. . . .

Yea my typo, I left out a slash.

I don't know about zsh, but in bash the stuff in the users config file is applied after the stuff in the system config file.
New stuff is added, existing stuff is overwritten.

To log in using your environment:
```
sudo su
```
To log in using roots environment:
```
sudo - su
```

It will pick a shell by using $SHELL, /etc/passwd or /bin/sh

To see what shell your using at any given time:
```
echo $0
```

You can find the full path to zsh using which:
```
which zsh
```

Then force sudo to use it, the full path is required:

```
sudo su -s /bin/zsh
```

That may make things look more like you want them to.

jdb

---

### Post by watchpocket on 2010-01-23
That's useful info, thanks.  I knew about 'which' but not the others.

Though your [COLOR=Blue]sudo - su[/COLOR] gave me:  [COLOR=Blue]sudo: -: command not found[/COLOR]

Should that be[COLOR=Blue] sudo -su[/COLOR] ??  (In other words, without a space between[COLOR=Red] [COLOR=Blue]-[/COLOR][/COLOR] and [COLOR=Blue]su[/COLOR])

Your last example,

[COLOR=Blue]sudo su -s /bin/zsh
[/COLOR]
is more along the lines of what I've been looking for.

Would anyone happen to know where might I put that so that by default whenever I
type a command after typing '[COLOR=Blue]sudo[/COLOR]', the output is the same as my user-configs?

I.e., so that the output of
[COLOR=Blue]
ls[/COLOR]

and 

[COLOR=Blue]sudo ls[/COLOR]

would be identical?

---

### Post by jdb on 2010-01-23
> **watchpocket said:**
> > [I]I've never run across a file root.bashrc, could it be root/.bashrc ??

[/I]Probably.  I was just quoting you from above:

[FONT=Courier New]> sudo mv /root.bashrc /root.bashrc.bak[/FONT]

Maybe you meant to put a slash where you'd put the dot & it's a typo.

Meanwhile I still haven't quite figured out how to get the system's and my user configs to match. . . .

Read what I mean, not what I type :lolflag:

That should have been sudo su -
The minus is a su option, not a sudo option.

The last field of your user entry in /etc/passwd is your default shell.
Change it from /bin/bash to /bin/zsh.
It won't take until you log out of Ubuntu & log back in or you can just reboot.

jdb

---

### Post by watchpocket on 2010-01-23
> **jdb said:**
> The last field of your user entry in /etc/passwd is your default shell.  Change it from /bin/bash to /bin/zsh.

That's already set at /bin/zsh  (see line beginning 'rj').

I'm thinking what I need to do, is do that for the top line (the one that begins 'root').

And maybe also for 'couchdb' which also is set to bash.  In other words change (to zsh) everything that's set to bash.

Here's my /etc/passwd file:

```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:102::/home/syslog:/bin/false
messagebus:x:102:106::/var/run/dbus:/bin/false
hplip:x:103:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:105:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:106:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
haldaemon:x:107:114:Hardware abstraction layer,,,:/var/run/hald:/bin/false
speech-dispatcher:x:108:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
saned:x:110:116::/home/saned:/bin/false
pulse:x:111:117:PulseAudio daemon,,,:/var/run/pulse:/bin/false
gdm:x:112:119:Gnome Display Manager:/var/lib/gdm:/bin/false
rj:x:1000:1000:rj,,,,:/home/rj:/bin/zsh
ntp:x:113:121::/home/ntp:/bin/false
vdr:x:114:122:VDR user,,,:/var/lib/vdr:/bin/false
Debian-exim:x:115:123::/var/spool/exim4:/bin/false
```

---

### Post by jdb on 2010-01-23
That sounds like a plan.
Changing root won't cause any problems.

Changing some of the entries could cause problems though if that particular entry depends on syntax that isn't in zsh.

For example a lot of the scripts I write for bash will fail if I run them in dash.

jdb

---

