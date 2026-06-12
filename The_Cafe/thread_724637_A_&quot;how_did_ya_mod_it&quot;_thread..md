---
title: "A &quot;how did ya mod it&quot; thread."
date: 2008-03-14
forum: The Cafe
---

### Post by LeoSolaris on 2008-03-14
This one is a little different, since it is a good deal more geeky than just the looks of your desktop. Thats something that everyone does.

However... not many people bother to mod their terminal. I first stumbled across it in my O'Reilly book, and after trying it out with non-persistent in terminal commands, I found a HowTo  on the forum from PurposeOfReason:

[http://ubuntuforums.org/showthread.php?t=674446](http://ubuntuforums.org/showthread.php?t=674446)

To start things out, my terminal's PS1 line looks like this 
```
07:56:36 on Fri Mar 14 - {user name removed}:~$
```

The little ~ will expand to the dir I am currently in.

Leo S.

---

### Post by D-EJ915 on 2008-03-15
here's mine in tcsh ```
username@hostname /home/username/pictures
>
```
bash ```
username~/pictures $:
```

---

### Post by herbster on 2008-03-15
```
~ #
```

---

### Post by hhhhhx on 2008-03-15
```
xhhux ~ $  
```

---

### Post by klange on 2008-03-15
[img]http://random.ogunderground.com/workstation/mar_13/prompt.png[/img]

---

### Post by LaRoza on 2008-03-15
```

~$ 
~$ cd /media/STORAGE/code/cCode
/media/STORAGE/code/cCode$ 

```

---

### Post by LeoSolaris on 2008-03-16
Well thank ya, I was starting to feel silly for having posted this thread, since it's such a little modification.

Leo

---

### Post by PurposeOfReason on 2008-03-16
I'm pretty sure you can figure it all out from looking at it. ;)

---

### Post by argie on 2008-03-16
username@hostname in green, path in blue. The first bit changes to yellow when in administrator user, and red when in root. When I ssh into the computer in the other room, it becomes light blue. (: Simple

---

### Post by popch on 2008-03-16
This thread made me chuckle quite a bit.

Guess what we did in times bygone in MSDOS and later in the command prompt in Windows?

---

### Post by banewman on 2008-03-16
What I see when starting a terminal
```
     March 2008     
Su Mo Tu We Th Fr Sa
                   1
 2  3  4  5  6  7  8
 9 10 11 12 13 14 15
16 17 18 19 20 21 22
23 24 25 26 27 28 29
30 31
Sun Mar 16 07:53 PM
 Working-@-Command Line:~$ 

```
edit - the forum won't show the cal properly...
edit - now it looks better
:)

---

### Post by popch on 2008-03-16
> **banewman said:**
> What I see when starting a terminal

edit - the forum won't show the cal properly...
:)

Perhaps you'd better use 'code' tags instead of 'quote' ?

---

### Post by delfick on 2008-03-16
*look at attachment* 

:)

and it works in tty as well :)

here is my .bashrc file 

```
#!/bin/bash
# based on a function found in bashtstyle-ng 5.0b1
# Original author Christopher Roy Bratusek (http://www.nanolx.org)
# Last modified by ayoli (http://ayozone.org) 2008-02-04 17:16:43 +0100 CET

if [ -f /etc/bashrc ]; then
	. /etc/bashrc
fi

function pre_prompt {

newPWD="${PWD/#$HOME/~}"
user="whoami"
host=$(echo -n $HOSTNAME | sed -e "s/[\.].*//")
datenow=$(date "+%a, %d %b %y")
let promptsize=$(echo -n "--($user@$host, DD mmm)---(${PWD/#$HOME/~})---" | wc -c | tr -d " ")
let fillsize=${COLUMNS}-${promptsize}-3
fill=""
while [ "$fillsize" -gt "0" ]
do
    fill="${fill}&#9472;"
	let fillsize=${fillsize}-1
done
if [ "$fillsize" -lt "0" ]
then
    let cutt=3-${fillsize}
    newPWD="...$(echo -n ${PWD/#$HOME/~} | sed -e "s/\(^.\{$cutt\}\)\(.*\)/\2/")"
fi

}

PROMPT_COMMAND=pre_prompt




export black="\[\033[0;38;5;0m\]"
export red="\[\033[0;38;5;1m\]"
export green="\[\033[0;38;25;2m\]"
export yellow="\[\033[0;38;5;3m\]"
export blue="\[\033[0;38;25;4m\]"
export magenta="\[\033[0;38;5;55m\]"
export cyan="\[\033[0;38;5;6m\]"
export white="\[\033[0;38;5;7m\]"
export coldblue="\[\033[0;38;5;33m\]"
export smoothblue="\[\033[0;38;5;111m\]"
export iceblue="\[\033[0;38;5;45m\]"
export turqoise="\[\033[0;38;5;50m\]"
export smoothgreen="\[\033[0;38;5;42m\]"

PS1="$blinkOff\n$green&#9484;&#9472;($blue\u@\h, \$(date \"+%d %b\")$green)&#9472;\${fill}&#9472;($blue\$newPWD\
$green)&#9472;&#9472;&#9472;&#9472;&#9488;\n$green&#9492;&#9472;($blue\$(date \"+%H:%M\")$green)$blue\$$black "



# bash_history settings: size and no duplicates and no lines w/ lead spaces
exportHISTCONTROL="ignoreboth"
export HISTCONTROL="ignoredups"
export HISTSIZE=1024

# aliases #############################################

# enable color support of ls and also add handy aliases
eval `dircolors -b`
alias ls='ls --color=auto'
alias dir='ls --color=auto --format=vertical'
alias vdir='ls --color=auto --format=long'

# some more ls aliases
alias ll='ls -lhX'
alias la='ls -A'
alias ldir='ls -lhA |grep ^d'
alias lfiles='ls -lhA |grep ^-'
#alias l='ls -CF'

# To see something coming into ls output: lss
alias lss='ls -lrt | grep $1'

# To check a process is running in a box with a heavy load: pss
alias pss='ps -ef | grep $1'

# usefull alias to browse your filesystem for heavy usage quickly
alias ducks='ls -A | grep -v -e '\''^\.\.$'\'' |xargs -i du -ks {} |sort -rn |head -16 | awk '\''{print $2}'\'' | xargs -i du -hs {}'

# cool colors for manpages
alias man="TERMINFO=~/.terminfo TERM=mostlike LESS=C PAGER=less man"

##########################################################
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi


```

(this is a very slightly modified version of one I found...

can't remember where I found it though, but I'll see if I can find it...

EDIT : here it is :) [http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/](http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/)

---

### Post by LeoSolaris on 2008-03-16
> **delfick said:**
> *look at attachment* 

:)

and it works in tty as well :)

here is my .bashrc file 

```
#!/bin/bash
# based on a function found in bashtstyle-ng 5.0b1
# Original author Christopher Roy Bratusek (http://www.nanolx.org)
# Last modified by ayoli (http://ayozone.org) 2008-02-04 17:16:43 +0100 CET

if [ -f /etc/bashrc ]; then
    . /etc/bashrc
fi

function pre_prompt {

newPWD="${PWD/#$HOME/~}"
user="whoami"
host=$(echo -n $HOSTNAME | sed -e "s/[\.].*//")
datenow=$(date "+%a, %d %b %y")
let promptsize=$(echo -n "--($user@$host, DD mmm)---(${PWD/#$HOME/~})---" | wc -c | tr -d " ")
let fillsize=${COLUMNS}-${promptsize}-3
fill=""
while [ "$fillsize" -gt "0" ]
do
    fill="${fill}&#9472;"
    let fillsize=${fillsize}-1
done
if [ "$fillsize" -lt "0" ]
then
    let cutt=3-${fillsize}
    newPWD="...$(echo -n ${PWD/#$HOME/~} | sed -e "s/\(^.\{$cutt\}\)\(.*\)/\2/")"
fi

}

PROMPT_COMMAND=pre_prompt




export black="\[\033[0;38;5;0m\]"
export red="\[\033[0;38;5;1m\]"
export green="\[\033[0;38;25;2m\]"
export yellow="\[\033[0;38;5;3m\]"
export blue="\[\033[0;38;25;4m\]"
export magenta="\[\033[0;38;5;55m\]"
export cyan="\[\033[0;38;5;6m\]"
export white="\[\033[0;38;5;7m\]"
export coldblue="\[\033[0;38;5;33m\]"
export smoothblue="\[\033[0;38;5;111m\]"
export iceblue="\[\033[0;38;5;45m\]"
export turqoise="\[\033[0;38;5;50m\]"
export smoothgreen="\[\033[0;38;5;42m\]"

PS1="$blinkOff\n$green&#9484;&#9472;($blue\u@\h, \$(date \"+%d %b\")$green)&#9472;\${fill}&#9472;($blue\$newPWD\
$green)&#9472;&#9472;&#9472;&#9472;&#9488;\n$green&#9492;&#9472;($blue\$(date \"+%H:%M\")$green)$blue\$$black "



# bash_history settings: size and no duplicates and no lines w/ lead spaces
exportHISTCONTROL="ignoreboth"
export HISTCONTROL="ignoredups"
export HISTSIZE=1024

# aliases #############################################

# enable color support of ls and also add handy aliases
eval `dircolors -b`
alias ls='ls --color=auto'
alias dir='ls --color=auto --format=vertical'
alias vdir='ls --color=auto --format=long'

# some more ls aliases
alias ll='ls -lhX'
alias la='ls -A'
alias ldir='ls -lhA |grep ^d'
alias lfiles='ls -lhA |grep ^-'
#alias l='ls -CF'

# To see something coming into ls output: lss
alias lss='ls -lrt | grep $1'

# To check a process is running in a box with a heavy load: pss
alias pss='ps -ef | grep $1'

# usefull alias to browse your filesystem for heavy usage quickly
alias ducks='ls -A | grep -v -e '\''^\.\.$'\'' |xargs -i du -ks {} |sort -rn |head -16 | awk '\''{print $2}'\'' | xargs -i du -hs {}'

# cool colors for manpages
alias man="TERMINFO=~/.terminfo TERM=mostlike LESS=C PAGER=less man"

##########################################################
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi


```(this is a very slightly modified version of one I found...

can't remember where I found it though, but I'll see if I can find it...

EDIT : here it is :) [http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/](http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/)


Cool! I rather like that one, definitely different.

Ya, I know what ya mean, popch, when I was a little kid, all My old Tandy had was DOS, so I customized the crap out of it, just because it freaked my mother out. I remember being grounded for that one, and mom reformatting it because she wouldn't listen.

:lolflag:
Leo

---

### Post by spupy on 2008-03-16
This is my Lost Hatch Terminal:
```
alias lostterm='export PS1="\[\033[01;32m\]>: "'
```
[Looks like this:]("http://vesso.marv.lafka.net/screens/screens18/2008-03-16-233627_602x392_scrot.png")

---

### Post by intense.ego on 2008-03-16
> **delfick said:**
> *look at attachment* 

:)

and it works in tty as well :)

here is my .bashrc file 

```
#!/bin/bash
# based on a function found in bashtstyle-ng 5.0b1
# Original author Christopher Roy Bratusek (http://www.nanolx.org)
# Last modified by ayoli (http://ayozone.org) 2008-02-04 17:16:43 +0100 CET

if [ -f /etc/bashrc ]; then
	. /etc/bashrc
fi

function pre_prompt {

newPWD="${PWD/#$HOME/~}"
user="whoami"
host=$(echo -n $HOSTNAME | sed -e "s/[\.].*//")
datenow=$(date "+%a, %d %b %y")
let promptsize=$(echo -n "--($user@$host, DD mmm)---(${PWD/#$HOME/~})---" | wc -c | tr -d " ")
let fillsize=${COLUMNS}-${promptsize}-3
fill=""
while [ "$fillsize" -gt "0" ]
do
    fill="${fill}&#9472;"
	let fillsize=${fillsize}-1
done
if [ "$fillsize" -lt "0" ]
then
    let cutt=3-${fillsize}
    newPWD="...$(echo -n ${PWD/#$HOME/~} | sed -e "s/\(^.\{$cutt\}\)\(.*\)/\2/")"
fi

}

PROMPT_COMMAND=pre_prompt




export black="\[\033[0;38;5;0m\]"
export red="\[\033[0;38;5;1m\]"
export green="\[\033[0;38;25;2m\]"
export yellow="\[\033[0;38;5;3m\]"
export blue="\[\033[0;38;25;4m\]"
export magenta="\[\033[0;38;5;55m\]"
export cyan="\[\033[0;38;5;6m\]"
export white="\[\033[0;38;5;7m\]"
export coldblue="\[\033[0;38;5;33m\]"
export smoothblue="\[\033[0;38;5;111m\]"
export iceblue="\[\033[0;38;5;45m\]"
export turqoise="\[\033[0;38;5;50m\]"
export smoothgreen="\[\033[0;38;5;42m\]"

PS1="$blinkOff\n$green&#9484;&#9472;($blue\u@\h, \$(date \"+%d %b\")$green)&#9472;\${fill}&#9472;($blue\$newPWD\
$green)&#9472;&#9472;&#9472;&#9472;&#9488;\n$green&#9492;&#9472;($blue\$(date \"+%H:%M\")$green)$blue\$$black "



# bash_history settings: size and no duplicates and no lines w/ lead spaces
exportHISTCONTROL="ignoreboth"
export HISTCONTROL="ignoredups"
export HISTSIZE=1024

# aliases #############################################

# enable color support of ls and also add handy aliases
eval `dircolors -b`
alias ls='ls --color=auto'
alias dir='ls --color=auto --format=vertical'
alias vdir='ls --color=auto --format=long'

# some more ls aliases
alias ll='ls -lhX'
alias la='ls -A'
alias ldir='ls -lhA |grep ^d'
alias lfiles='ls -lhA |grep ^-'
#alias l='ls -CF'

# To see something coming into ls output: lss
alias lss='ls -lrt | grep $1'

# To check a process is running in a box with a heavy load: pss
alias pss='ps -ef | grep $1'

# usefull alias to browse your filesystem for heavy usage quickly
alias ducks='ls -A | grep -v -e '\''^\.\.$'\'' |xargs -i du -ks {} |sort -rn |head -16 | awk '\''{print $2}'\'' | xargs -i du -hs {}'

# cool colors for manpages
alias man="TERMINFO=~/.terminfo TERM=mostlike LESS=C PAGER=less man"

##########################################################
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi


```

(this is a very slightly modified version of one I found...

can't remember where I found it though, but I'll see if I can find it...

EDIT : here it is :) [http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/](http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/)

If I were to copy that code and replace my bashrc file with it, would there be any errors? I'm just not good enough (or too lazy) to create ,my own and I quite like yours.

---

### Post by kerry_s on 2008-03-16
```
PS1="\e[37;1m\d \@ \e[37;1m  [\e[34;1m\w\e[37;1m]\e[32;1m\n> \e[37;1m" 
```

---

### Post by bonzodog on 2008-03-17
I use zsh as my default shell, so my prompt codes look like this:
```

# Prompt
#local BLUE="%{"$'\e[0;34m'"%}"
#local white="%{"$'\e[1;37m'"%}"
#local CYAN="%{"$'\e[0;36m'"%}"
#export PS1="${CYAN}%50<...<       ******<%/>*****
#:${white} "
#export RPS1=" ${CYAN}<%T>"
#PS1="%~-> "
autoload -U colors && colors
RPS1="%{$fg[cyan]%}<%T>"
PS1="%{$fg[green]%}<%/>
%{$fg[cyan]%}:"

```

---

### Post by LeoSolaris on 2008-03-17
> **spupy said:**
> This is my Lost Hatch Terminal:
```
alias lostterm='export PS1="\[\033[01;32m\]>: "'
```[Looks like this:]("http://vesso.marv.lafka.net/screens/screens18/2008-03-16-233627_602x392_scrot.png")


I bet my fiancée would love it! She is a major Lost fan. I'll steal that for her when I install it this week if ya don't mind? Would you post your full bashrc or at least send it to me... I am still somewhat new at this, and it would save me a ton of trial and error.

Thanks!
Leo

P.S. I wonder if Lost used Linux as a thin client in text only mode to effect that old style computer terminal. Maybe with an instant messaging system built into it for the messages that Locke received...

---

