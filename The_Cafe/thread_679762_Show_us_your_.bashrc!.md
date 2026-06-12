---
title: "Show us your .bashrc!"
date: 2008-01-27
forum: The Cafe
---

### Post by urukrama on 2008-01-27
I've only recently started playing with the ~/.bashrc file and want more ideas to play with. Please share your bashrc file and show all of us what cool and handy things you can do with bash.

Here is my bashrc:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='[${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\h\[\033[00m\]] \[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='[${debian_chroot:+($debian_chroot)}\h] \w\$ '
    ;;
esac

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

#netinfo - shows network information for your system
netinfo ()
{
echo "--------------- Network Information ---------------"
/sbin/ifconfig | awk /'inet addr/ {print $2}'
/sbin/ifconfig | awk /'Bcast/ {print $3}'
/sbin/ifconfig | awk /'inet addr/ {print $4}'
/sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'
myip=`lynx -dump -hiddenlinks=ignore -nolist http://checkip.dyndns.org:8245/ | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g' `
echo "${myip}"
echo "---------------------------------------------------"
}

#dirsize - finds directory sizes and lists them for the current directory
dirsize ()
{
du -shx * .[a-zA-Z0-9_]* 2> /dev/null | \
egrep '^ *[0-9.]*[MG]' | sort -n > /tmp/list
egrep '^ *[0-9.]*M' /tmp/list
egrep '^ *[0-9.]*G' /tmp/list
rm -rf /tmp/list
}

#copy and go to dir
cpg (){
  if [ -d "$2" ];then
    cp $1 $2 && cd $2
  else
    cp $1 $2
  fi
}

#move and go to dir
mvg (){
  if [ -d "$2" ];then
    mv $1 $2 && cd $2
  else
    mv $1 $2
  fi
}

# Directory navigation aliases
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

export OOO_FORCE_DESKTOP=gnome
```

---

### Post by ~LoKe on 2008-01-27
That looks somewhat familiar. ;)

```
## LoKe's ~/.bashrc
[ -z "$PS1" ] && return

# Basic options
export HISTCONTROL=ignoredups
export COLORFGBG='default;default'

shopt -s checkwinsize
eval "$(dircolors -b /etc/dircolors)"

# Aliases
alias ls='ls -h --color=auto'
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'
alias svim='sudo vim'
alias h='cd'
alias ..='cd ..'
alias cd..='cd ..'
alias ...='cd ../..'
alias cim='vim'
alias back='cd $OLDPWD'
alias root='sudo su'
alias runlevel='sudo /sbin/init'
alias grep='grep --color=auto'
alias dfh='df -h'
alias gvim='gvim -geom 84x26'
alias start='dbus-launch startx'

# Prompt
BGREEN='\[\033[1;32m\]'
GREEN='\[\033[0;32m\]'
BRED='\[\033[1;31m\]'
RED='\[\033[0;31m\]'
BBLUE='\[\033[1;34m\]'
BLUE='\[\033[0;34m\]'
NORMAL='\[\033[00m\]'
PS1="${BLUE}(${RED}\w${BLUE}) ${NORMAL}\h ${RED}\$ ${NORMAL}"

# Paths
PATH=$PATH:${HOME}/bin:/usr/lib/wine/bin:/sbin:/usr/sbin
export PATH=$PATH:/usr/local/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/wine/lib:/usr/local/lib
export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig

# X Terminal titles
case "$TERM" in
xterm*|rxvt*)
	PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
	;;
*)
	;;
esac

# Functions
extract () {
	if [ -f $1 ] ; then
		case $1 in
			*.tar.bz2)	tar xjf $1		;;
			*.tar.gz)	tar xzf $1		;;
			*.bz2)		bunzip2 $1		;;
			*.rar)		rar x $1		;;
			*.gz)		gunzip $1		;;
			*.tar)		tar xf $1		;;
			*.tbz2)		tar xjf $1		;;
			*.tgz)		tar xzf $1		;;
			*.zip)		unzip $1		;;
			*.Z)		uncompress $1	;;
			*)			echo "'$1' cannot be extracted via extract()" ;;
		esac
	else
		echo "'$1' is not a valid file"
	fi
}
ziprm () {
	if [ -f $1 ] ; then
		unzip $1
		rm $1
	else
		echo "Need a valid zipfile"
	fi
}
psgrep() {
	if [ ! -z $1 ] ; then
		echo "Grepping for processes matching $1..."
		ps aux | grep $1 | grep -v grep
	else
		echo "!! Need name to grep for"
	fi
}
grab() {
	sudo chown -R ${USER} ${1:-.}
}

# Bash completion
if [ -f /etc/bash_completion ]; then
	. /etc/bash_completion
fi

# Locale and editor
export EDITOR=nano
export BROWSER="firefox '%s' &"
```

---

### Post by Ebuntor on 2008-01-27
What does the .bashrc file do actually? What's its function?

---

### Post by mali2297 on 2008-01-27
> **Ebuntor said:**
> What does the .bashrc file do actually? What's its function?

It is a configuration file that is read every time that you open the terminal. As an example of its use, you can create an alias like
```

alias rm='rm -iv'

```
Now, every time you use the command *rm*, bash will in reality execute *rm -iv* which means that you will be asked to confirm any removals. You will also get an output that tells you what has been done.

---

### Post by ssam on 2008-01-27
> **Ebuntor said:**
> What does the .bashrc file do actually? What's its function?

bash reads it as it starts (eg when you start a terminal). it lets you customise how the terminal works, and set up shortcuts

i like these handy shortcuts
```

alias h="history|grep "
alias f="find . |grep "
alias p="ps aux |grep "
alias o="gnome-open "

```
first three let you search command line history, files in current directory and subdirs, and running processes. the 'o' lets you open a file in what ever it would use if you double clicked it.

```

alias pc='python -ic "from __future__ import division; from math import *"'

```
opens python with settings that make it useful for quick calculations. (similar to bc, but i am used to python syntax. the future division but means that 1/2 = 0.5 instead of 0).

```

alias ps1_short="PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\W\[\033[00m\]\$ '"
alias ps1_long="PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '"

```

switches between shown the whole path in the prompt, and just the top bit. i like to see where i am, but sometimes it just gets too deep.

---

### Post by urukrama on 2008-01-27
> **Ebuntor said:**
> What does the .bashrc file do actually? What's its function?

It is the configuration file of [bash]("http://en.wikipedia.org/wiki/Bash"). You can use the bashrc file to add functions or aliases to bash.

For example, in my bashrc file the "extract" section allows me to extract any archived file from the command line with the command extract, for example "extract example.tar.gz". These aliases basically tell bash to run certain applications, in this example the tar command, with certain options as specified in the bashrc file, in this case xzf.

Have a look at the bashrc files posted in this thread. Most of the aliases should make sense as they are. 

You can also use the bashrc file to change your terminal header (generally "username@computer-name ~$" in Ubuntu). See [here]("http://ubuntuforums.org/showthread.php?t=674446") for more on that.

EDIT: Seems I was a bit slow...:-s

---

### Post by mali2297 on 2008-01-27
... here is my entire .bashrc:

```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# the prompt information
export PS1="[\w]\$ "

# leave some commands out of history log
export HISTIGNORE="&:??:[ ]*:clear:exit:logout"

# default editor
export EDITOR=jmacs

# define color to additional file types
export LS_COLORS=$LS_COLORS:"*.wmv=01;35":"*.wma=01;35":"*.flv=01;35":"*.m4a=01;35"


# Alias definitions.

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto' 
    alias dir='ls --color=auto --format=vertical'
    alias vdir='ls --color=auto --format=long'
fi

# user-defined aliases
alias rm='rm -vi'
alias cp='cp -vi'
alias mv='mv -vi'
alias clean='rm -f "#"* "."*~ *~ *.bak *.dvi *.aux *.log'
alias nano='nano -w'
alias psi='ps h -eo pmem,comm | sort -nr | head'
alias sucs='sudo jmacs'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi     

```

---

### Post by Ebuntor on 2008-01-27
Thanks to all of you for explaining. Sure sounds like a very handy config file. :)

---

### Post by urukrama on 2008-01-28
Anyone else?

---

### Post by andrek on 2008-02-02
[IMG]http://xs224.xs.to/xs224/08056/bash772.png[/IMG]

/home/user/.bashrc [http://pastebin.com/f628171ce](http://pastebin.com/f628171ce)
/root/.bashrc [http://pastebin.com/f5c1c0405](http://pastebin.com/f5c1c0405) (in case you're using 'su' instead of 'sudo')

---

### Post by el mariachi on 2008-02-02
uuuuu great thread idea Urukrama!
mine is oh so simple...
just one line...  i need to setup some aliases they really help.
```
PS1='[\u\W] \[\e[0;30m\]//\[\e[1;37m\] '
```

---

### Post by bobbocanfly on 2008-02-02
Thanks urukrama! Great thread and extract() from your .bashrc is very useful. 

Heres mine:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
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
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

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
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

#Extract things. Thanks to urukrama, Ubuntuforums.org	
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

alias mnt-mp3="sudo mount penguin:/media/Media ~/Media"
alias mnt-www="sudo mount penguin:/var/www ~/www"
alias mnt-docs="sudo mount penguin:/home/bobbo ~/Documents"
alias mnt="mnt-docs; mnt-www; mnt-mp3"
alias dopewars="dopewars -bt"
alias kff="killall firefox-bin" #Because killall firefox-bin is far too long to type the amount i type it
alias mpd="sudo mpd && sudo mpdscribble&"
```

Basically default Ubuntu but with my nfs mounting, firefox killing and mpd initialising aliases. Oh and extract().

---

### Post by supertux on 2008-02-04
> **andrek said:**
> [IMG]http://xs224.xs.to/xs224/08056/bash772.png[/IMG]

/home/user/.bashrc - [http://rafb.net/p/gKjiGI85.txt](http://rafb.net/p/gKjiGI85.txt)
/root/.bashrc - [http://rafb.net/p/FAl1VB26.txt](http://rafb.net/p/FAl1VB26.txt) (in case you're using 'su' instead of 'sudo')

they arent there, can you re-upload them?

---

### Post by ice60 on 2008-02-04
i went a bit crazy with mine.
```
[ -z "$PS1" ] && return

# Bash completion
if [ -f /etc/bash_completion ]; then
	. /etc/bash_completion
fi

# Define a few Colours
BLACK='\e[0;30m'
BLUE='\e[0;34m'
GREEN='\e[0;32m'
CYAN='\e[0;36m'
RED='\e[0;31m'
PURPLE='\e[0;35m'
BROWN='\e[0;33m'
LIGHTGRAY='\e[0;37m'
DARKGRAY='\e[1;30m'
LIGHTBLUE='\e[1;34m'
LIGHTGREEN='\e[1;32m'
LIGHTCYAN='\e[1;36m'
LIGHTRED='\e[1;31m'
LIGHTPURPLE='\e[1;35m'
YELLOW='\e[1;33m'
WHITE='\e[1;37m'
NC='\e[0m'              # No Color

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

###############
### aliases ###
###############

# General
alias df='df -h'
alias h='history'
alias d='cd /home/iceni60/Desktop'
alias duck='du -skc * | sort -rn'
alias open='gnome-open'
alias chm='kchmviewer'
alias nb='nano ~/.bashrc'

# screenshots
alias screenshot='import -window root ~/Desktop/`date +%Y%m%d%H%M`.png'

# System info
alias cpuu="ps -e -o pcpu,cpu,nice,state,cputime,args --sort pcpu | sed '/^ 0.0 /d'"
alias memu='ps -e -o rss=,args= | sort -b -k1,1n | pr -TW$COLUMNS'
alias pg='ps aux | grep'  #requires an argument

# weather
alias weather='/home/iceni60/scripts/conky_scripts/weather.sh UKXX0085'

# Music
alias ncmpc='ncmpc -cm'

# apt
#alias search='apt-cache search'
#alias agi='sudo apt-get install'
#alias agr='sudo apt-get remove'
#alias agu='sudo apt-get update'
#alias agg='sudo apt-get upgrade'
#alias sources='gksudo gedit /etc/apt/sources.list'

# interactive
alias cp='cp -vi'
alias mv='mv -vi'
alias rm='mv --target-directory=$HOME/.Trash/'

# Directory navigation aliases
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

# display facts of the day
alias today='grep -h -d skip `date +%m/%d` /home/iceni60/Ubuntu/usr/share/calendar/*'

# network
alias net1='watch --interval=2 "sudo netstat -apn -l -A inet"'
alias net2='watch --interval=2 "sudo netstat -anp --inet --inet6"'  
alias net3='sudo lsof -i'
alias net4='watch --interval=2 "sudo netstat -p -e --inet --numeric-hosts"'
alias net5='watch --interval=2 "sudo netstat -tulpan"'
alias net6='sudo netstat -tulpan'
alias net7='watch --interval=2 "sudo netstat -utapen"'
alias net8='watch --interval=2 "sudo netstat -ano -l -A inet"'
alias netl='sudo nmap -sT -O localhost' # more here http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/security-guide/s1-server-ports.html
alias ping='ping -c 10'
alias currports='wine /home/iceni60/Desktop/Desktop_Folder/Network_Tools/currports/cports.exe'
alias winwhois='wine /home/iceni60/Desktop/Desktop_Folder/Network_Tools/win32whois_0_9_13/win32whois.exe'
alias xnews='wine /home/iceni60/Desktop/Desktop_Folder/Network_Tools/XNews/XNEWS.EXE'
alias whois='whois -H'

# listings
alias ls='ls --color=auto'
alias lh='ls -lah'                # human readable (sizes) long and all ;-)
alias lls='ls -l -h -g -F --color=auto'
alias lc='ls -aCF'
alias lsam='ls -am'               # List files horizontally
alias lr='ls -lR'                 # recursive
alias lsx='ls -ax'                # sort right to left rather then in columns
alias lss='ls -shAxSr'            # sort by size
alias lt='ls -lAtrh'              # sort by date and human readable
alias lm='ls -al |more'           # pipe through 'more'

# scripts
alias calc='sh /home/iceni60/scripts/calc.sh'
alias whatsmyip='/home/iceni60/scripts/whatsmyip.sh'
alias unpack='/home/iceni60/scripts/unpack2dir.sh'

# chmod and permissions commands
alias mx='chmod a+x'
alias 000='chmod 000'
alias 644='chmod 644'
alias 755='chmod 755'
alias perm='stat --printf "%a %n \n "' # requires a file name e.g. perm file

# lynx web browser
alias bbc='lynx http://news.bbc.co.uk/text_only.stm'
alias nytimes='lynx http://nytimes.com'
alias dmregister='lynx http://desmoinesregister.com'
alias google='lynx http://google.co.uk'

# these, below, are without colour
#alias bbc='lynx -term=vt100 http://news.bbc.co.uk/text_only.stm'
#alias nytimes='lynx -term=vt100 http://nytimes.com'
#alias dmregister='lynx -term=vt100 http://desmoinesregister.com'
#alias google='lynx -term=vt100 http://google.co.uk'

# WELCOME SCREEN
#######################################################

clear

echo -ne "${LIGHTGREEN}" "Hello, $USER. today is, "; date
echo -e "${WHITE}"; cal ;  
echo -ne "${CYAN}";
echo -ne "${LIGHTPURPLE}Sysinfo:";uptime ;echo ""


# NOTES
#######################################################

# To temporarily bypass an alias, we preceed the command with a \  
# EG:  the ls command is aliased, but to use the normal ls command you would 
# type \ls 

#################
### FUNCTIONS ###
#################

function    ff               { find . -name $@ -print; }

function    rmd              { rm -fr $@; }

function    osr              { shutdown -r now; }
function    osh              { shutdown -h now; }

function    mfloppy          { mount /dev/fd0 /mnt/floppy; }
function    umfloppy         { umount /mnt/floppy; }

function    mdvd             { mount -t iso9660 -o ro /dev/dvd /mnt/dvd; }
function    umdvd            { umount /mnt/dvd; }

function    mcdrom           { mount -t iso9660 -o ro /dev/cdrom /mnt/cdrom; }
function    umcdrom          { umount /mnt/cdrom; }

function    psa              { ps aux $@; }
function    psu              { ps  ux $@; }

function    dub              { du -sclb $@; }
function    duk              { du -sclk $@; }
function    dum              { du -sclm $@; }

function    dfk              { df -PTak $@; }
function    dfm              { df -PTam $@; }
function    dfh              { df -PTah $@; }
function    dfi              { df -PTai $@; }

# SPECIAL FUNCTIONS
#######################################################

# clock - A bash clock that can run in your terminal window. 
clock () 
{ 
while true;do clear;echo "===========";date +"%r";echo "===========";sleep 1;done 
}

netinfo ()
{
echo "--------------- Network Information ---------------"
/sbin/ifconfig | awk /'inet addr/ {print $2}'
echo ""
/sbin/ifconfig | awk /'Bcast/ {print $3}'
echo ""
/sbin/ifconfig | awk /'inet addr/ {print $4}'

# /sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'
echo "---------------------------------------------------"
}

# Define a word - USAGE: define dog
define ()
{
lynx -dump "http://www.google.com/search?hl=en&q=define%3A+${1}&btnG=Google+Search" | grep -m 3 -w "*"  | sed 's/;/ -/g' | cut -d- -f1 > /tmp/templookup.txt
			if [[ -s  /tmp/templookup.txt ]] ;then	
				until ! read response
					do
					echo "${response}"
					done < /tmp/templookup.txt
				else
					echo "Sorry $USER, I can't find the term \"${1} \""				
			fi	
\rm -f /tmp/templookup.txt
}

#####################################
# ##### ENVIRONMENT VARIABLES ##### #
#####################################

declare -x HISTFILE=~/.bash_history
declare -x HISTCONTROL=ignoredups
declare -x HISTFILESIZE=100000
declare -x HISTSIZE=100000




############################## ##################################
# ##### PROMPT SECTION ##### ####################################
############################## ##################################

##PS1="\[[32m\]\u:\w > \[[39m\]"
##PS1="\[[31m\][\[[32m\]\u\[[31m\]]\[[32m\]\w > \[[39m\]"
#PS1="\[[40;1;31m\][\[[1;32m\]\u\[[1;31m\]]\[[49;1;32m\]\w > \[[22;39m\]"
#PS1="\[[1;31m\][\[[1;32m\]\[[47m\]\u\[[1;31m\]\[[49m\]]\[[1;32m\]\w > \[[22;39m\]"
##PS1="\[[31m\][\[[36m\]\u\[[31m\]]\[[36m\]\w > \[[39m\]"
#PS1="\[[32m\]\u \[[39m\]\$\[[32m\] \w \[[39m\]"

###################### the above is a separate prompt which can be used instead of below. NOTE: only ONE line at a time should be uncommented. so there are 6 different prompts above!!!!!

# color_name='\[\033[ color_code m\]'

rgb_restore='\[\033[00m\]'
rgb_black='\[\033[00;30m\]'
rgb_firebrick='\[\033[00;31m\]'
rgb_red='\[\033[01;31m\]'
rgb_forest='\[\033[00;32m\]'
rgb_green='\[\033[01;32m\]'
rgb_brown='\[\033[00;33m\]'
rgb_yellow='\[\033[01;33m\]'
rgb_navy='\[\033[00;34m\]'
rgb_blue='\[\033[01;34m\]'
rgb_purple='\[\033[00;35m\]'
rgb_magenta='\[\033[01;35m\]'
rgb_cadet='\[\033[00;36m\]'
rgb_cyan='\[\033[01;36m\]'
rgb_gray='\[\033[00;37m\]'
rgb_white='\[\033[01;37m\]'

rgb_std="${rgb_white}"

if [ `id -u` -eq 0 ]
then
    rgb_usr="${rgb_red}"
else
    rgb_usr="${rgb_green}"
fi

[ -n "$PS1" ] && PS1="${rgb_usr}`whoami`${rgb_std} \W ${rgb_usr}\\\$${rgb_restore} "

unset   rgb_restore   \
        rgb_black     \
        rgb_firebrick \
        rgb_red       \
        rgb_forest    \
        rgb_green     \
        rgb_brown     \
        rgb_yellow    \
        rgb_navy      \
        rgb_blue      \
        rgb_purple    \
        rgb_magenta   \
        rgb_cadet     \
        rgb_cyan      \
        rgb_gray      \
        rgb_white     \
        rgb_std       \
        rgb_usr

```
here's a screenshot with a couple of the things -

[[IMG]http://img295.imageshack.us/img295/4259/termyy0.th.png[/IMG]](http://img295.imageshack.us/my.php?image=termyy0.png)

---

### Post by supertux on 2008-02-04
Can you post the details for that login message you have?

---

### Post by urukrama on 2008-02-04
supertux, it is all in his/her bashrc file.

---

### Post by ice60 on 2008-02-04
> **supertux said:**
> Can you post the details for that login message you have?

do this -
gedit ~/.bashrc

and add this at the bottom, then open a new terminal -
# WELCOME SCREEN
#######################################################

clear

echo -ne "${LIGHTGREEN}" "Hello, $USER. today is, "; date
echo -e "${WHITE}"; cal ;  
echo -ne "${CYAN}";
echo -ne "${LIGHTPURPLE}Sysinfo:";uptime ;echo ""

---

### Post by supertux on 2008-02-04
> **ice60 said:**
> do this -
gedit ~/.bashrc

and add this at the bottom, then open a new terminal -
# WELCOME SCREEN
#######################################################

clear

echo -ne "${LIGHTGREEN}" "Hello, $USER. today is, "; date
echo -e "${WHITE}"; cal ;  
echo -ne "${CYAN}";
echo -ne "${LIGHTPURPLE}Sysinfo:";uptime ;echo ""
very nice! thx!

---

### Post by ice60 on 2008-02-04
> **supertux said:**
> very nice! thx!

sorry, i forgot. add this anywhere above that last bit you put in. just delete what you added and start again and add this instead -

# Define a few Colours
BLACK='\e[0;30m'
BLUE='\e[0;34m'
GREEN='\e[0;32m'
CYAN='\e[0;36m'
RED='\e[0;31m'
PURPLE='\e[0;35m'
BROWN='\e[0;33m'
LIGHTGRAY='\e[0;37m'
DARKGRAY='\e[1;30m'
LIGHTBLUE='\e[1;34m'
LIGHTGREEN='\e[1;32m'
LIGHTCYAN='\e[1;36m'
LIGHTRED='\e[1;31m'
LIGHTPURPLE='\e[1;35m'
YELLOW='\e[1;33m'
WHITE='\e[1;37m'
NC='\e[0m'              # No Color

# WELCOME SCREEN
################################################## #####

clear

echo -ne "${LIGHTGREEN}" "Hello, $USER. today is, "; date
echo -e "${WHITE}"; cal ; 
echo -ne "${CYAN}";
echo -ne "${LIGHTPURPLE}Sysinfo:";uptime ;echo ""

---

### Post by corney91 on 2008-02-04
I haven't changed my .bashrc but...

```
dan@dan-laptop:~$ cat .bash_aliases 
#aliases
alias aliases='(gedit ~/.bash_aliases &)'

#urxvt
alias urxvt='urxvt -depth 32 -bg rgba:0000/0000/0000/dddd +sb -fn "fixed:pixelsize=9" &'

#remote desktop
alias school='(rdesktop [school IP] &)'

#cd
alias m='cd ~/Music'
alias p='cd ~/Pictures'
alias h='cd ~/Homework'
alias d='cd ~/Desktop'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

#ls
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'
alias ldir='ls -p | grep \/'

#delete
alias del='mv --target-directory=/home/dan/.Trash/'

#apt
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias purge='sudo apt-get remove --purge'
alias update='sudo apt-get update && sudo apt-get upgrade'
alias upgrade='sudo apt-get upgrade'
alias clean='sudo apt-get autoclean && sudo apt-get autoremove'
alias search='apt-cache search'
alias show='apt-cache show'
alias sources='(gksudo gedit /etc/apt/sources.list &)'

#ln
alias ln='ln -s'

#df
alias dfh='df -h'

#wc
alias count='wc -l'

#tar
alias tarz='tar -xvzf'
alias tarb='tar -xvjf'

#xorg
alias xorg='(gksudo gedit /etc/X11/xorg.conf &)'

#compiz
alias c='(compiz --replace &)'

#conky
alias conkyreset='killall -SIGUSR1 conky'
alias conkyrc='(gedit ~/.conkyrc ~/.conkyrc2 ~/.conkyrc3 &)'
alias conkyall='/home/dan/.conkyall'

#on this day
alias today='grep -h -d skip `date +%m/%d` /usr/share/calendar/*'

#folding@home
alias fahstart='sudo /etc/init.d/foldingathome start'
alias fahstop='sudo /etc/init.d/foldingathome stop'
alias fahrestart='sudo /etc/init.d/foldingathome restart'
alias fahsend='sudo /etc/init.d/foldingathome send'
alias fahstatus='sudo /etc/init.d/foldingathome status'
alias fah='ps -ef | grep -i fah'

#fluxbox
alias fluxmenu='gedit ~/.fluxbox/menu &'
alias fluxkeys='gedit ~/.fluxbox/keys &'
alias fluxstart='gedit ~/.fluxbox/startup &'
alias fluxstyle='gedit ~/.fluxbox/styles/Modified\ Nyz &'

```

---

### Post by andrek on 2008-02-04
> **supertux said:**
> they arent there, can you re-upload them?

Sorry for a long delay..
/home/user/.bashrc [http://pastebin.com/f628171ce](http://pastebin.com/f628171ce)
/root/.bashrc [http://pastebin.com/f5c1c0405](http://pastebin.com/f5c1c0405)

---

### Post by grte on 2008-02-04
How about a zshrc?  Most of this stuff will work in bash, anyhow.

```
# Compinstall generated options
source $HOME/.config/zsh/compinstall

# Options
source $HOME/.config/zsh/environment

# Prompt colours and style
source $HOME/.config/zsh/prompt

# Aliases
source $HOME/.config/zsh/alias

# Functions
source $HOME/.config/zsh/function

# Login options
source $HOME/.config/zsh/zlogin

# Keybinds
source $HOME/.config/zsh/keys

``` 

Okay, more seriously, here's a cat of the sourced files:

```
# The following lines were added by compinstall

zstyle ':completion:*' completer _expand _complete _correct _approximate
zstyle ':completion:*' completions 1
zstyle ':completion:*' expand prefix suffix
zstyle ':completion:*' format 'Completing %d'
zstyle ':completion:*' glob 1
zstyle ':completion:*' ignore-parents parent
zstyle ':completion:*' insert-unambiguous true
zstyle ':completion:*' list-colors ''
zstyle ':completion:*' matcher-list '' 'r:|[._-]=* r:|=*' 'l:|=* r:|=*'
zstyle ':completion:*' max-errors 2
zstyle ':completion:*' menu select=long
zstyle ':completion:*' original true
zstyle ':completion:*' preserve-prefix '//[^/]##/'
zstyle ':completion:*' prompt 'Errors: %e'
zstyle ':completion:*' select-prompt %SScrolling active: current selection at %p%s
zstyle ':completion:*' substitute 1
zstyle :compinstall filename '/home/avatar/.zshrc'

autoload -Uz compinit
compinit
# End of lines added by compinstall
# Lines configured by zsh-newuser-install
HISTFILE=~/.config/zsh/histfile
HISTSIZE=32000
SAVEHIST=64000
setopt appendhistory autocd
unsetopt beep extendedglob nomatch notify
bindkey -v
# End of lines configured by zsh-newuser-install
#
############
#
#  Environment Variables
#

export PATH=$PATH:$HOME/bin:/opt
export PAGER='most'
export MANPAGER='most'
export MAILPATH=~/mail
export EDITOR="vim"
export WM="openbox"
export GIMP2_DIRECTORY=$HOME/.config/gimp-2.4
export MOST_INITFILE=$HOME/.config/most/mostrc
export RXVT_SOCKET=/tmp
export MPLAYER_HOME=$HOME/.config/mplayer
export MAIL=$HOME/mail

setopt MAIL_WARN

# Dynamic Mailpath
typeset -a mailpath
for i in ~/mail/list/*(.); do
	mailpath[$#mailpath+1]="${i}?You have new mail in ${i:t}."
done

#gpg-agent says it needs this
export GPG_TTY='tty'

#fortunes at each new shell
#fortune -a

##################
#
# Zsh Keybindings
#
bindkey "\e[1~" beginning-of-line
bindkey "\e[4~" end-of-line
bindkey "\e[5~" beginning-of-history
bindkey "\e[6~" end-of-history
bindkey "\e[3~" delete-char
bindkey "\e[2~" quoted-insert
bindkey "\e[5C" forward-word
bindkey "\eOc" emacs-forward-word
bindkey "\e[5D" backward-word
bindkey "\eOd" emacs-backward-word
bindkey "\e\e[C" forward-word
bindkey "\e\e[D" backward-word
bindkey "^H" backward-delete-word
# for rxvt
bindkey "\e[8~" end-of-line
bindkey "\e[7~" beginning-of-line
# completion in the middle of a line
bindkey '^i' expand-or-complete-prefix

# unbind
bindkey -r main '^['
############
#
# Functions
#

# lcfiles - Lowercase all files in the current directory
lcfiles() {
	print -n 'Really lowercase all files? (y/n) '
	if read -q ; then
		for i in * ; do
			mv $i $i:l
	done
	fi
}

# Compression shortcuts

#tar.gz
tg() {
	tarfile=$1
	shift
	tar -czvf $tarfile $@
}

#tar.bz2
tb() {
	tar --bzip2 -cvf $tarfile $@
}

# Extract various compression formats
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

# Weather by us zip code - Can be called two ways # weather 50315 # weather "Des Moines"
weather ()
{
declare -a WEATHERARRAY
WEATHERARRAY=( `elinks -dump "http://www.google.com/search?hl=en&lr=&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=weather+${1}&btnG=Search" | grep -A 5 -m 1 "Weather for" | sed 's;\[26\]Add to iGoogle\[27\]IMG;;g'`)
echo ${WEATHERARRAY[@]}
}

#copy and go to dir
cpg (){
  if [ -d "$2" ];then
    cp $1 $2 && cd $2
  else
    cp $1 $2
  fi
}

#move and go to dir
mvg (){
  if [ -d "$2" ];then
    mv $1 $2 && cd $2
  else
    mv $1 $2
  fi
}

#dirsize - finds directory sizes and lists them for the current directory
dirsize ()
{
du -shx * .[a-zA-Z0-9_]* 2> /dev/null | \
egrep '^ *[0-9.]*[MG]' | sort -n > /tmp/list
egrep '^ *[0-9.]*M' /tmp/list
egrep '^ *[0-9.]*G' /tmp/list
rm /tmp/list
}

#myip - finds your current IP if your connected to the internet
myip ()
{
elinks -dump http://checkip.dyndns.org:8245/ | awk '{ print $4 }' | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g' 
}

#netinfo - shows network information for your system
netinfo ()
{
echo "--------------- Network Information ---------------"
/sbin/ifconfig | awk /'inet addr/ {print $2}'
/sbin/ifconfig | awk /'Bcast/ {print $3}'
/sbin/ifconfig | awk /'inet addr/ {print $4}'
/sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'
myip=`elinks -dump http://checkip.dyndns.org:8245/ | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g' `
echo "${myip}"
echo "---------------------------------------------------"
}

#bu - Back Up a file. Usage "bu filename.txt" 
bu () { cp $1 ${1}-`date +%Y%m%d%H%M`.backup ; }

# Pacman search colourised by repository
psc() {
  echo -e "$(pacman -Ss $@ | sed \
       -e 's#core/.*#\\033[1;31m&\\033[0;37m#g' \
       -e 's#extra/.*#\\033[0;32m&\\033[0;37m#g' \
       -e 's#community/.*#\\033[1;35m&\\033[0;37m#g' \
       -e 's#^.*/.* [0-9].*#\\033[0;36m&\\033[0;37m#g' )"
}

############
#
#  Prompt
#

function precmd {

    local TERMWIDTH
    (( TERMWIDTH = ${COLUMNS} - 1 ))


    ###
    # Truncate the path if it's too long.
    
    PR_FILLBAR=""
    PR_PWDLEN=""
    
    local promptsize=${#${(%):---(%n@%m:%l)---()--}}
    local pwdsize=${#${(%):-%~}}
    
    if [[ "$promptsize + $pwdsize" -gt $TERMWIDTH ]]; then
	    ((PR_PWDLEN=$TERMWIDTH - $promptsize))
    else
	PR_FILLBAR="\${(l.(($TERMWIDTH - ($promptsize + $pwdsize)))..${PR_HBAR}.)}"
    fi


    ###
    # Get APM info.

    if which ibam > /dev/null; then
	PR_APM_RESULT=`ibam --percentbattery`
    elif which apm > /dev/null; then
	PR_APM_RESULT=`apm`
    fi
}


setopt extended_glob
preexec () {
    if [[ "$TERM" == "screen" ]]; then
	local CMD=${1[(wr)^(*=*|sudo|-*)]}
	echo -n "\ek$CMD\e\\"
    fi
}


setprompt () {
    ###
    # Need this so the prompt will work.

    setopt prompt_subst


    ###
    # See if we can use colors.

    autoload colors zsh/terminfo
    if [[ "$terminfo[colors]" -ge 8 ]]; then
	colors
    fi
    for color in RED GREEN YELLOW BLUE MAGENTA BLUE WHITE; do
	eval PR_$color='%{$terminfo[bold]$fg[${(L)color}]%}'
	eval PR_LIGHT_$color='%{$fg[${(L)color}]%}'
	(( count = $count + 1 ))
    done
    PR_NO_COLOUR="%{$terminfo[sgr0]%}"


    ###
    # See if we can use extended characters to look nicer.
    
    typeset -A altchar
    set -A altchar ${(s..)terminfo[acsc]}
    PR_SET_CHARSET="%{$terminfo[enacs]%}"
    PR_SHIFT_IN="%{$terminfo[smacs]%}"
    PR_SHIFT_OUT="%{$terminfo[rmacs]%}"
    PR_HBAR=${altchar[q]:--}
    PR_ULCORNER=${altchar[l]:--}
    PR_LLCORNER=${altchar[m]:--}
    PR_LRCORNER=${altchar[j]:--}
    PR_URCORNER=${altchar[k]:--}

    
    ###
    # Decide if we need to set titlebar text.
    
    case $TERM in
	xterm*)
	    PR_TITLEBAR=$'%{\e]0;%(!.-=*[ROOT]*=- | .)%n@%m:%~ | ${COLUMNS}x${LINES} | %y\a%}'
	    ;;
	screen)
	    PR_TITLEBAR=$'%{\e_screen \005 (\005t) | %(!.-=[ROOT]=- | .)%n@%m:%~ | ${COLUMNS}x${LINES} | %y\e\\%}'
	    ;;
	*)
	    PR_TITLEBAR=''
	    ;;
    esac
    
    
    ###
    # Decide whether to set a screen title
    if [[ "$TERM" == "screen" ]]; then
	PR_STITLE=$'%{\ekzsh\e\\%}'
    else
	PR_STITLE=''
    fi
    
    
    ###
    # APM detection
    
    if which ibam > /dev/null; then
	PR_APM='$PR_RED${${PR_APM_RESULT[(f)1]}[(w)-2]}%%(${${PR_APM_RESULT[(f)3]}[(w)-1]})$PR_LIGHT_BLUE:'
    elif which apm > /dev/null; then
	PR_APM='$PR_RED${PR_APM_RESULT[(w)5,(w)6]/\% /%%}$PR_LIGHT_BLUE:'
    else
	PR_APM=''
    fi
    
    
    ###
    # Finally, the prompt.

    PROMPT='$PR_SET_CHARSET$PR_STITLE${(e)PR_TITLEBAR}\
$PR_WHITE$PR_SHIFT_IN$PR_ULCORNER$PR_WHITE$PR_HBAR$PR_SHIFT_OUT(\
$PR_YELLOW%(!.%SROOT%s.%n)$PR_YELLOW@%m:%l\
$PR_WHITE)$PR_SHIFT_IN$PR_HBAR$PR_WHITE$PR_HBAR${(e)PR_FILLBAR}$PR_WHITE$PR_HBAR$PR_SHIFT_OUT(\
$PR_YELLOW%$PR_PWDLEN<...<%~%<<\
$PR_WHITE)$PR_SHIFT_IN$PR_HBAR$PR_WHITE$PR_URCORNER$PR_SHIFT_OUT\

$PR_WHITE$PR_SHIFT_IN$PR_LLCORNER$PR_WHITE$PR_HBAR$PR_SHIFT_OUT(\
%(?..$PR_LIGHT_YELLOW%?$PR_WHITE:)\
${(e)PR_APM}$PR_YELLOW%D{%H:%M}\
$PR_LIGHT_WHITE:%(!.$PR_YELLOW.$PR_YELLOW)%#$PR_WHITE)$PR_SHIFT_IN$PR_HBAR$PR_SHIFT_OUT\
$PR_WHITE$PR_SHIFT_IN$PR_HBAR$PR_SHIFT_OUT\
$PR_NO_COLOUR '

    RPROMPT=' $PR_WHITE$PR_SHIFT_IN$PR_HBAR$PR_WHITE$PR_HBAR$PR_SHIFT_OUT\
($PR_YELLOW%D{%a,%b%d}$PR_WHITE)$PR_SHIFT_IN$PR_HBAR$PR_WHITE$PR_LRCORNER$PR_SHIFT_OUT$PR_NO_COLOUR'

    PS2='$PR_WHITE$PR_SHIFT_IN$PR_HBAR$PR_SHIFT_OUT\
$PR_WHITE$PR_SHIFT_IN$PR_HBAR$PR_SHIFT_OUT(\
$PR_LIGHT_YELLOW%_$PR_WHITE)$PR_SHIFT_IN$PR_HBAR$PR_SHIFT_OUT\
$PR_WHITE$PR_SHIFT_IN$PR_HBAR$PR_SHIFT_OUT$PR_NO_COLOUR '
}

setprompt
```

---

### Post by bodhi.zazen on 2008-02-04
+1 zsh 

[[img]http://www.cafelinux.org/OptickleArt/albums/userpics/thumb_xterm.png[/img]](http://www.cafelinux.org/OptickleArt/albums/userpics/xterm.png)

Click on link to see a screen shot of my login screen.

ZSH :

[http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)
	[http://www.ibm.com/developerworks/linux/library/l-z.html?dwzone=linux](http://www.ibm.com/developerworks/linux/library/l-z.html?dwzone=linux)


The other .bashrc threads :

[http://ubuntuforums.org/showthread.php?&t=204382](http://ubuntuforums.org/showthread.php?&t=204382)

[http://www.ubuntuforums.org/showthread.php?t=161312](http://www.ubuntuforums.org/showthread.php?t=161312)

And, to give credit where credit is due, **we should all thank rezza at Arch Linux for that ex script**, I posted it on the Ubuntu Forums here (scroll down a little):

[http://ubuntuforums.org/showpost.php?p=1698783&postcount=25](http://ubuntuforums.org/showpost.php?p=1698783&postcount=25)

---

### Post by Drmgiver on 2008-02-23
Well, I am a newbie (like a matter of 3 days) so I haven't gotten into much customization, however I am sure I will in time, I did so with Litestep under windows.  Though, I did have to post to this, because I laughed my *** off when I read this topic.  The ultimate question is though, does one get tossed a beer when one shows them?

---

### Post by hhhhhx on 2008-02-23
still making mine

---

### Post by ayoli on 2008-02-25
I thought it was impossible to have a bash prompt as fancy as zsh's ones, but I've found a way here's a screenshot of my bash prompt:
[IMG]http://ayozone.org/wp-content/uploads/2008/02/fancy_prompt.png[/IMG]
The whole article is here :
[http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/](http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/)
and the bashrc file (you'll have to rename it) :
[http://ayozone.org/wp-content/uploads/2008/02/bashrc.txt](http://ayozone.org/wp-content/uploads/2008/02/bashrc.txt)

---

### Post by tvlooy on 2008-03-02
> **~LoKe said:**
> 
```

alias back='cd $OLDPWD'
alias root='sudo su'

```

you can also do:
alias back='cd -'
alias root='sudo -i'

---

### Post by thyultimate on 2008-03-03
This sounds amazing!!!!

Going to try and edit it myself..........but does it cause any major damage if I screw it up???

---

### Post by Yes on 2008-03-03
Just backup your current bashrc before starting and you'll be fine.

ayoli, how'd you get the line like that?  Firefox can't seem to figure out what the characters are.

---

### Post by ayoli on 2008-03-03
> **Yes said:**
> Just backup your current bashrc before starting and you'll be fine.

ayoli, how'd you get the line like that?  Firefox can't seem to figure out what the characters are.

browsers can't read these ascii chars but if you just download the bashrc.txt file linked in my previous post it will work.

---

### Post by Yes on 2008-03-03
Ah, ok.  Thanks :)

---

### Post by ayoli on 2008-03-03
> **Yes said:**
> Ah, ok.  Thanks :)
You're welcome :)
Thank you to have shown me that I wasn't clear enough, I've corrected my blog post to clarify this a bit.

---

### Post by Tristam Green on 2008-03-04
I only mess with .bash_aliases as of yet; hopefully I'll understand and get to messing with .bashrc more in the upcoming weeks.

Either way, here are my aliases and the single function I've written thus far:

```
#command-line manipulation
alias new='ls -lt --color=auto | head'
alias rm='rm -v'
alias cp='cp -v'
alias mv='mv -v'

# lynx web browser
alias qcdn='lynx -term=vt100 http://www.qcdn.org/'
alias jtforum='lynx -term=vt100 http://www.z10.invisionfree.com/jammintunes'

#conky
alias smallconky='(conky -c ~/.conkyrc-minimal &)'
alias bigconky='(conky &)'
alias killconky='killall conky'

#script functions
function makescript() { touch ~/bin/"$@" && chmod ~/bin/"$@" -x && gedit ~/bin/"$@"; }

```

---

### Post by corney91 on 2008-03-04
Here's a handy one for conky:
```
alias conkyreset='killall -SIGUSR1 conky'
```
It resets conky from the config, so you don't have to go through killing and restarting after making a minor adjustment.

---

### Post by Tristam Green on 2008-03-04
> **corney91 said:**
> Here's a handy one for conky:
```
alias conkyreset='killall -SIGUSR1 conky'
```
It resets conky from the config, so you don't have to go through killing and restarting after making a minor adjustment.

I imagine that I could likewise do ```
alias conkyreset 'killall -SIGUSR1 (conky -c  ~/.conkyrc-minimal &)'
```
and achieve the same effect? or would a function be more suitable?

```
function conkyreset() { killall conky && (conky -c ~/.conkyrc-minimal &) }
```

---

### Post by corney91 on 2008-03-04
IIRC, because the process is called conky, 'killall -SIGUSR1 conky' is enough even if you use 'conky -c .conkyrc_minimal'

---

### Post by Tristam Green on 2008-03-04
Cool, I didn't know what the -SIGUSR1 part did.

Thanks for that :)

---

### Post by rouge568 on 2008-03-05
```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# To temporarily bypass an alias, we preceed the command with a \
# EG:  the ls command is aliased, but to use the normal ls command you would
# type \ls
#---------------------------------------------------------------------------

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
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
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
	function command_not_found_handle {
                /usr/bin/python /usr/lib/command-not-found -- $1
                return $?
	}
fi

# asks for confirmation everytime 'rm' is used
alias rm='rm -iv'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

#netinfo - shows network information for your system
netinfo ()
{
echo "--------------- Network Information ---------------"
/sbin/ifconfig | awk /'inet addr/ {print $2}'
/sbin/ifconfig | awk /'Bcast/ {print $3}'
/sbin/ifconfig | awk /'inet addr/ {print $4}'
/sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'
myip=`lynx -dump -hiddenlinks=ignore -nolist http://checkip.dyndns.org:8245/ | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g' `
echo "${myip}"
echo "---------------------------------------------------"
}


# Connect to PA's wireless http://student.andover.edu/~adehnert/linux/pawireless
function pawireless
{
    sudo /etc/init.d/dhcp3-server stop
    sudo wpa_supplicant -Dwext -iwlan0 -c /etc/wpa_supplicant/pawireless.conf &
    sleep 5
    sudo dhclient
}

#Use human-readable filesizes
alias du="du -h"
alias df="df -h"

#apt
alias install='sudo apt-get install'
alias uninstall='sudo apt-get remove'
alias reinstall='sudo apt-get --reinstall install'
alias remove='sudo apt-get remove'
alias purge='sudo apt-get remove --purge'
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias clean='sudo apt-get autoclean && sudo apt-get autoremove'
alias search='apt-cache search'
alias show='apt-cache show'
alias sources='(gksudo gedit /etc/apt/sources.list &)'
alias go='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean && sudo apt-get autoremove && exit'

# Other Aliases
#navigation
alias ..='cd ..'
alias cd..='cd ..'
alias ...='cd ../..'
#root
alias root='sudo su'
#lynx 
alias lynx='(lynx -accept_all_cookies http://google.com)'
#xorg
alias xorg='(gksudo gedit /etc/X11/xorg.conf &)'
#bashrc
alias bashrc='(gksudo gedit /etc/bash.bashrc &)'
#lampp
alias lampp='sudo /opt/lampp/lampp'
#winetricks
alias winetricks='sh /home/scott/winetricks'

# Define a few Colours
BLACK='\e[0;30m'
BLUE='\e[0;34m'
GREEN='\e[0;32m'
CYAN='\e[0;36m'
RED='\e[0;31m'
PURPLE='\e[0;35m'
BROWN='\e[0;33m'
LIGHTGRAY='\e[0;37m'
DARKGRAY='\e[1;30m'
LIGHTBLUE='\e[1;34m'
LIGHTGREEN='\e[1;32m'
LIGHTCYAN='\e[1;36m'
LIGHTRED='\e[1;31m'
LIGHTPURPLE='\e[1;35m'
YELLOW='\e[1;33m'
WHITE='\e[1;37m'
NC='\e[0m' # No Color

#------------------------------
# WELCOME SCREEN

clear

echo -ne "${WHITE}""Hello, $USER. Today is, "; date
echo -ne ;
#------------------------------

```

---

### Post by XVII on 2008-03-05
Mine:
```

# MY ALIASES
alias rm='rm -vi'
alias cp='cp -vi'
alias mv='mv -vi'
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias purge='sudo apt-get remove --purge'
alias update='sudo apt-get update && sudo aptitude update'
alias sources='(gksudo gedit /etc/apt/sources.list &)'
alias downloads='ls -ltrh /home/username/Downloads'

# WELCOME SCREEN

clear

. /etc/lsb-release
echo -e "$gras$(uname -r)$fin - $gras$DISTRIB_ID $DISTRIB_RELEASE $DISTRIB_CODENAME$fin"

#PROMPT

PS1="[\u@\h:\W]\n   [\@] $ "

```

---

### Post by PurposeOfReason on 2008-03-06
I feel mine does it's job
```

alias ls='ls --color=auto'
alias search='pacsearch'
alias edit='gedit'
alias calc='gcalctool'
PS1='[\H // \w]\[\e[m\] '

# enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
complete -cf sudo


# Weather by us zip code - Can be called two ways # weather 50315 # weather "Des Moines"
weather ()
{
declare -a WEATHERARRAY
WEATHERARRAY=( `lynx -dump "http://www.google.com/search?hl=en&lr=&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=weather+${1}&btnG=Search" | grep -A 5 -m 1 "Weather for"`)
echo ${WEATHERARRAY[@]}
}

# Stock prices - can be called two ways. # stock novl  (this shows stock pricing)  #stock "novell"  (this way shows stock symbol for novell)
stock ()
{
stockname=`lynx -dump http://finance.yahoo.com/q?s=${1} | grep -i ":${1})" | sed -e 's/Delayed.*$//'`
stockadvise="${stockname} - delayed quote."
declare -a STOCKINFO
STOCKINFO=(` lynx -dump http://finance.yahoo.com/q?s=${1} | egrep -i "Last Trade:|Change:|52wk Range:"`)
stockdata=`echo ${STOCKINFO[@]}`
    if [[ ${#stockname} != 0 ]] ;then
        echo "${stockadvise}"
        echo "${stockdata}"
            else
            stockname2=${1}
            lookupsymbol=`lynx -dump -nolist http://finance.yahoo.com/lookup?s="${1}" | grep -A 1 -m 1 "Portfolio" | grep -v "Portfolio" | sed 's/\(.*\)Add/\1 /'`
                if [[ ${#lookupsymbol} != 0 ]] ;then
                echo "${lookupsymbol}"
                    else
                    echo "Sorry $USER, I can not find ${1}."
                fi
    fi
}

#Translate a Word  - USAGE: translate house spanish  # See dictionary.com for available languages (there are many).
translate ()
{
TRANSLATED=`lynx -dump "http://dictionary.reference.com/browse/${1}" | grep -i -m 1 -w "${2}:" | sed 's/^[ \t]*//;s/[ \t]*$//'`
if [[ ${#TRANSLATED} != 0 ]] ;then
    echo "\"${1}\" in ${TRANSLATED}"
    else
    echo "Sorry, I can not translate \"${1}\" to ${2}"
fi
}

# Define a word - USAGE: define dog
define ()
{
lynx -dump "http://www.google.com/search?hl=en&q=define%3A+${1}&btnG=Google+Search" | grep -m 5 -w "*"  | sed 's/;/ -/g' | cut -d- -f5 > /tmp/templookup.txt
            if [[ -s  /tmp/templookup.txt ]] ;then    
                until ! read response
                    do
                    echo "${response}"
                    done < /tmp/templookup.txt
                else
                    echo "Sorry $USER, I can't find the term \"${1} \""                
            fi    
rm -f /tmp/templookup.txt
}

extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}



```

---

### Post by cardinals_fan on 2008-03-06
Mostly pirated from this thread, but it does what I need :)

```
#bashrc
#cardinals_fan
#3/6/2008

alias ll="ls -al --color"
alias nautilus="nautilus --no-desktop"
alias aterm="aterm -fg white -tr"
export PS1='\u[\W]\$ '
export PAGER="most"

#aliases
alias cdperl='cd /home/jesse/Desktop/Programs/Perl\!\!\!\!\!/'
alias cdphoto='cd /home/jesse/Documents\ \&\ Other\ Cool\ Stuff/Pictures/Photos/'
alias zenpanel='gksu zenpanel'
alias gslapt='gksu gslapt'
alias settings='xfce-setting-show'
alias conkyreset='killall -SIGUSR1 conky'

#extracter
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

# Define a few Colours
BLACK='\e[0;30m'
BLUE='\e[0;34m'
GREEN='\e[0;32m'
CYAN='\e[0;36m'
RED='\e[0;31m'
PURPLE='\e[0;35m'
BROWN='\e[0;33m'
LIGHTGRAY='\e[0;37m'
DARKGRAY='\e[1;30m'
LIGHTBLUE='\e[1;34m'
LIGHTGREEN='\e[1;32m'
LIGHTRED='\e[1;31m'
LIGHTPURPLE='\e[1;35m'
YELLOW='\e[1;33m'
WHITE='\e[1;37m'
NC='\e[0m' # No Color

# WELCOME SCREEN

clear

echo -ne "${LIGHTGREEN}""Hello, $USER. today is, "; date
echo -e "${LIGHTGREEN}"; cal ;
echo -e "${WHITE}"; uname -a ;
echo ""

```
Screenshot:

---

### Post by Nythain on 2008-03-12
> **ayoli said:**
> I thought it was impossible to have a bash prompt as fancy as zsh's ones, but I've found a way
The whole article is here :
[http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/](http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/)
and the bashrc file (you'll have to rename it) :
[http://ayozone.org/wp-content/uploads/2008/02/bashrc.txt](http://ayozone.org/wp-content/uploads/2008/02/bashrc.txt)

Great article and prompt, but i have one problem...
Its filling with blocks... here's a screenshot with the terminal open and the relevant section of my bashrc since im sure copy paste will just display wonky characters...

Also, any suggestions on getting that bad boy to work in eterm at all??? eterm apaprently REALLY doesnt like those characters
EDIT: ok, so switching from konsole to rxvt-unicode solved that issue, any reason why konsole is having trouble though???

---

### Post by ayoli on 2008-03-12
> **Nythain said:**
> Great article and prompt, but i have one problem...
Its filling with blocks... here's a screenshot with the terminal open and the relevant section of my bashrc since im sure copy paste will just display wonky characters...

Also, any suggestions on getting that bad boy to work in eterm at all??? eterm apaprently REALLY doesnt like those characters
Actually, I only tested this in gnome-terminal, a known issue is that it doesn't work with many polices (the better one is monospace).
The strange thing in your screenshot is that the char that draw the lines work every where but not in the fill.
I'll try to find a fix for that.
edit : I think it can work only in term that can use truetype fonts (eterm doesn't afaik)

---

### Post by Nythain on 2008-03-12
yeah, its really odd, especially since the opening and trailing -'s display right, just not the fill one, and that it works in rxvt-unicode and gnome-terminal, but not was wonky in konsole (i tried changing from PixelCarnageMonoTT to Monospace and had the same problem) but its really cool, because it forced me to figure out how to set up rxvt-unicode to do what i want

the only reason i defaulted to Eterm to begin with was because i was more familiar with it... i like rxvt better now :)

---

### Post by Lostincyberspace on 2008-03-12
I have my first bash custom set up.

```

# Sample .bashrc for SuSE Linux
# Copyright (c) SuSE GmbH Nuernberg

# There are 3 different types of shells in bash: the login shell, normal shell
# and interactive shell. Login shells read ~/.profile and interactive shells
# read ~/.bashrc; in our setup, /etc/profile sources ~/.bashrc - thus all
# settings made here will also take effect in a login shell.
#
# NOTE: It is recommended to make language settings in ~/.profile rather than
# here, since multilingual X sessions would not work properly if LANG is over-
# ridden in every subshell.

# Some applications read the EDITOR variable to determine your favourite text
# editor. So uncomment the line below and enter the editor of your choice :-)
#export EDITOR=/usr/bin/vim
export EDITOR=/usr/bin/gedit

# For some news readers it makes sense to specify the NEWSSERVER variable here
#export NEWSSERVER=your.news.server

# If you want to use a Palm device with Linux, uncomment the two lines below.
# For some (older) Palm Pilots, you might need to set a lower baud rate
# e.g. 57600 or 38400; lowest is 9600 (very slow!)
#
#export PILOTPORT=/dev/pilot
#export PILOTRATE=115200

PS1='\[\e[01;36m\]Welcome Lostincyberspace \@ \w: \[\e[m\]\[\e[1;37m\]'
alias cdpic='cd /home/lee/Pictures/'
alias cdmedia='cd /home/media/'
alias cddata='cd /home/data/'
alias cdfat='cd /home/media/fat/'
alias sl='ls'
alias cdd='cd /home/lee/Desktop/'
test -s ~/.alias && . ~/.alias || true

```

---

### Post by ayoli on 2008-03-12
> **Nythain said:**
> yeah, its really odd, especially since the opening and trailing -'s display right, just not the fill one, and that it works in rxvt-unicode and gnome-terminal, but not was wonky in konsole (i tried changing from PixelCarnageMonoTT to Monospace and had the same problem) but its really cool, because it forced me to figure out how to set up rxvt-unicode to do what i want

the only reason i defaulted to Eterm to begin with was because i was more familiar with it... i like rxvt better now :)
glad to know you've managed this :)
and thanks for your feedback, I'll add a note about working and non working terms in my article based on your feedback.

---

### Post by Bruce M. on 2008-03-13
***@ urukrama*** - Great thread, I'm learning something new.  :)

> **corney91 said:**
> Here's a handy one for conky:
```
alias conkyreset='killall -SIGUSR1 conky'
```
It resets conky from the config, so you don't have to go through killing and restarting after making a minor adjustment.

Doesn't work for me. I only changed one thing:

```
alias kiacs='killall -SIGUSR1 conky'
```

meaning *K*illed*I*n*A*ction*C*onky*S*tart

Conky doesn't stop or restart
```

bruloo@bruloo:~$ kiacs
bruloo@bruloo:~$ 

```

Normally I use:

```

killall conky
./.startconky

```

Just what is: **-SIGUSR1**

In layman terms please, I'm a green bean here.

Bruce

---

### Post by corney91 on 2008-03-13
> **Bruce M. said:**
> 

Just what is: **-SIGUSR1**

In layman terms please, I'm a green bean here.


I believe it just means 'reload config'

---

### Post by blithen on 2008-03-13
[http://ubuntuforums.org/showthread.php?t=616875](http://ubuntuforums.org/showthread.php?t=616875)
Already an epic thread on this subject.

---

### Post by Bruce M. on 2008-03-13
> **corney91 said:**
> I believe it just means 'reload config'

But it's not doing anything that I can see.

EDIT: From file:///usr/share/doc/conky/docs.html
> 
You Should Know

An easy way to force Conky to reload your ~/.conkyrc: "killall -SIGUSR1 conky". Saves you the trouble of having to kill and then restart.


Wherein lies my problem I think, I'm not using **~/.conkyrc**

So I changed the alias I have ( **c**onky **i**n **a**ction):

```
alias cia='killall conky && ./.startconky'
```

---

### Post by corney91 on 2008-03-13
> **Bruce M. said:**
> But it's not doing anything that I can see.

EDIT: From file:///usr/share/doc/conky/docs.html

Hmm, I'm using two conkys (or conkies?;)) and it reloads both of them...


> **Bruce M. said:**
> 
Wherein lies my problem I think, I'm not using **~/.conkyrc**

So I changed the alias I have ( **c**onky **i**n **a**ction):

```
alias cia='killall conky && ./.startconky'
```
Meh, it's essentially the same thing, so I guess you're sorted :)

---

### Post by celliott on 2008-03-14
Hi all,

Just wondering how the code below works when added to the bashrc file.

Thanks

:)

#Extract things. Thanks to urukrama, Ubuntuforums.org	
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

---

### Post by ayoli on 2008-03-14
> **celliott said:**
> Hi all,

Just wondering how the code below works when added to the bashrc file.

Thanks

:)

#Extract things. Thanks to urukrama, Ubuntuforums.org	
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

use it in your terminal like this for ex :
```
extract whateverfile.bz2
```

---

### Post by olejorgen on 2008-03-14
To all of you using the extract script: there is a convenient package called **atool** that does the same. (probably more robust)

---

### Post by Bruce M. on 2008-03-14
I like this thread.

Now for a question:
```
alias clean='rm -f "#"* "."*~ *~ *.bak *.dvi *.aux *.log'
```

This I have:
```
       -f, --force
              ignore nonexistent files, never prompt

```
These are probably like that other OS:
* = wildcard
[LIST]
[*]**[SIZE="3"]*~[/SIZE]** = any_file_ending_with**[SIZE="3"]~[/SIZE]**
[*]**[SIZE="3"]*.~[/SIZE]** = any_file_ending_with**[SIZE="3"].~[/SIZE]**
[*]**[SIZE="3"]*.dvi[/SIZE]** = any_file_ending_with**[SIZE="3"].dvi[/SIZE]**
[*]**[SIZE="3"]*.aux[/SIZE]** = any_file_ending_with**[SIZE="3"].aux[/SIZE]**
[/LIST]

What do these do:
[SIZE="3"]**"#"* "."*~**[/SIZE]

And last but not least.
What folder does this work in or is it the entire drive?

Thanks
Bruce

---

### Post by ayoli on 2008-03-14
> **Bruce M. said:**
> I like this thread.

Now for a question:
```
alias clean='rm -f "#"* "."*~ *~ *.bak *.dvi *.aux *.log'
```

This I have:
```
       -f, --force
              ignore nonexistent files, never prompt

```
These are probably like that other OS:
* = wildcard
[LIST]
[*]**[SIZE="3"]*~[/SIZE]** = any_file_ending_with**[SIZE="3"]~[/SIZE]**
[*]**[SIZE="3"]*.~[/SIZE]** = any_file_ending_with**[SIZE="3"].~[/SIZE]**
[*]**[SIZE="3"]*.dvi[/SIZE]** = any_file_ending_with**[SIZE="3"].dvi[/SIZE]**
[*]**[SIZE="3"]*.aux[/SIZE]** = any_file_ending_with**[SIZE="3"].aux[/SIZE]**
[/LIST]

What do these do:
[SIZE="3"]**"#"* "."*~**[/SIZE]

And last but not least.
What folder does this work in or is it the entire drive?

Thanks
Bruce

should work only on the current folder where you stand in your term.
"#"* should mean a file starting with a #
and "."*~ should mean a file with an extension (eg txt) ended with a ~

---

### Post by Bruce M. on 2008-03-14
> **ayoli said:**
> should work only on the current folder where you stand in your term.
"#"* should mean a file starting with a #
and "."*~ should mean a file with an extension (eg txt) ended with a ~

OK, that sound reasonable.

Time to create a test folder with test files and instead of:
```
rm -f
```
for test purposes ....
```
rm -i 
```

Thanks ayoli
Bruce

---

### Post by mali2297 on 2008-03-14
> **ayoli said:**
> should work only on the current folder where you stand in your term.
"#"* should mean a file starting with a #
and "."*~ should mean a file with an extension (eg txt) ended with a ~

You're absolutely right except for the last one,  "."*~ (or \.*~) should catch hidden backup files that start with a dot and end with tilde.

I don't have much use of that command nowadays since I have figured out how to stop nano, emacs et cetera to make backups.

---

### Post by Bruce M. on 2008-03-14
> **ayoli said:**
> should work only on the current folder where you stand in your term.
"#"* should mean a file starting with a #
and "."*~ should mean a file with an extension (eg txt) ended with a ~

> **mali2297 said:**
> You're absolutely right except for the last one,  "."*~ (or \.*~) should catch hidden backup files that start with a dot and end with tilde.

I don't have much use of that command nowadays since I have figured out how to stop nano, emacs et cetera to make backups.

And it works well, thanks guys.
BRuce

---

### Post by mali2297 on 2008-03-14
> **Bruce M. said:**
> 
Time to create a test folder with test files and instead of:
```
rm -f
```
for test purposes ....
```
rm -i 
```


I've got
```

alias rm='rm -vi'

```
in my .bashrc. This means that the default behavior of rm is to ask for confirmation before removal. When I don't want that, I can override the -i flag by using
```

rm -f

```

---

### Post by corney91 on 2008-03-14
I use ```
alias del='mv --target-directory=/home/dan/.Trash/'
```
Generally I use del and only sometimes rm. Of course, you could use ```
alias rm='mv --target-directory=/home/[***USER***]/.Trash/'
```

---

### Post by chick on 2008-03-15
Here is my .zshrc with a screenshot of the prompt and terminal.

```
#___________________________________________________________________________
# zsh options

HISTFILE=~/.histfile
HISTSIZE=2000
SAVEHIST=2000

setopt correct
setopt extendedglob
setopt autopushd pushdminus pushdsilent pushdtohome
setopt no_clobber           # don't overwrite files when redirect
setopt share_history
setopt hist_verify          # verify when using !
setopt hist_ignore_space    # prepend ' ' to not be saved
setopt nohup               # don't kill bg jobs when tty quits
setopt nocheckjobs          # don't complain about background jobs on exit
setopt printexitvalue       # print exit value from jobs

unsetopt bgnice            # don't nice bg command

autoload -U compinit
compinit

#___________________________________________________________________________
# zsh zle key bindings

bindkey -e                      # emacs since vi just doesn't fit here :(

bindkey ' ' magic-space         # also do history expansion on space

bindkey '^z' undo               # C-x-u is overkill

bindkey ';5D' backward-word     # C-left
bindkey ';5C' forward-word      # C-right

# vi-ish bindings
bindkey '^w' kill-word
bindkey '^b' backward-kill-word

# fish/ipython-ish bindings
bindkey '\e[A' history-beginning-search-backward    # up arrow
bindkey '\e[B' history-beginning-search-forward     # down arrow

#___________________________________________________________________________
# alias

# zsh global aliases
alias -g H='--help'
alias -g L='| less'
alias -g M='| most'
alias -g G='| grep'
alias -g GC='| grep -C 2'

alias ..='cd ..'

alias ls='ls -FC --color=auto'
alias ll='ls -lh'
alias la='ls -A'
alias lal='ls -Alh'

alias dirs='dirs -v'                    # zsh dir stack

alias hist='history | grep'             # take an argument

alias cp='cp -iv'
alias mv='mv -iv'
alias rm='mv -ft $HOME/.trash'

alias du='du -h'
alias df='df -h'

alias pkgs='aptitude search'
alias pkg='dpkg -s'                     # faster than aptitude!
alias inst='sudo aptitude install'
alias uninst='sudo aptitude purge'

alias pscpu='ps -eo pcpu,nice,stat,time,pid,cmd --sort=-pcpu,-time \
             | sed "/^ 0.0 /d"'
alias psmem='ps -eo rss,vsz,pid,cmd --sort=-rss,-vsz \
             | awk "{ if (\$1 > 10000) print }"'

alias vi='vi -g -geom 80x40'
alias op='opera -newpage'
alias jacks='jackd -R -d alsa -p 128 &'

# facts of the day
alias today='grep -h -d skip `date +%m/%d` /usr/share/calendar/*'

# Commands frequency counts
alias cmdfreq='cut -d " " -f 1 < $HISTFILE | sort | uniq -c | sort -nr | head -n 10'

#___________________________________________________________________________
# generic functions

# do ls right after cd
cd () {
  if [ -n $1 ]; then
    builtin cd "$@" && ls
  else
    builtin cd ~ && ls
  fi
}

# list files only
lf () { ls -1p $@ | grep -v '\/$' }

# grep process by name and list the results nicely
pg () {
    if pgrep -f $@ > /dev/null;
    then
        pgrep -f $@ | xargs ps -o user,pid,stat,rss,vsz,pcpu,args \
                               --sort -pcpu,-rss;
    else 
        exit 1;
    fi
}

# compile lilypond file and view pdf
ly () { lilypond $@ && evince $(basename $1 .ly).pdf; }

# look in WordNet and Webster
d () { curl dict://dict.org/d:${1}:wn; }
wd () { curl dict://dict.org/d:${1}:web1913; } 

# find matches of $1, with optional strat $2 and optional db $3
ref () 
{
    if [[ -z $3 ]]; then
        curl dict://dict.org/m:${1}:english:${2};
    else
        curl dict://dict.org/m:${1}:${3}:${2};
    fi
}

# define $1 using optional db of $2
def () { curl dict://dict.org/d:${1}:${2} }

# local WordNet lookups
syn () { wn $1 -synsn; wn $1 -synsv; wn $1 -synsa; wn $1 -synsr; }
ant () { wn $1 -antsn; wn $1 -antsv; wn $1 -antsa; wn $1 -antsr; }

# Set a pretty zsh prompt, taking 0..5 args as colors
setprompt ()
{
    # load this to use $fg
    autoload -U colors
    colors

    c1="%{${1:-"$fg[green]"}%}"             # main color for cmd, cwd, hist
    c2="%{${2:-"$fg_no_bold[cyan]"}%}"      # color for user@host
    c3="%{${3:-"$fg_bold[grey]"}%}"         # color for =,()
    c4="%{${4:-"$fg[white]"}%}"             # time and arrow color
    c5="%{${5:-"$fg[red]"}%}"               # root color

    now="$c3($c4%D{%H:%M} %D{%a %b %d}$c3)"
    userhost="%(!.$c5.$c2)%n$c3@$c2%m"

    line2="$userhost ${c3}[$c1%h$c3] ${c4}--> %(!.$c5.$c1)"
    newline=$'\n%{\r%}'

    # truncate and pad line1 appropiately
    precmd () {
        local cwdrealwidth=${#${(%):-%~}}
        
        # length of $line1 w/o $cwd = 22
        if [[ "$cwdrealwidth + 22" -gt $COLUMNS ]]; 
        then
            # truncate
            local cwdwidth = (( $COLUMNS - 22 ))
        else
            # pad
            local padding="${(l.(($COLUMNS - 22 - $cwdrealwidth )))..-.)}"
        fi
        
        local cwd="$c1%$cwdwidth<...<%~%<<"
        local line1="$c3-($cwd$c3)-${padding}$now"
        export PROMPT="${line1}$newline$line2"
    }
       
    preexec () { print -n "$reset_color" }
}

#___________________________________________________________________________
# env

export EDITOR=vi
export LS_COLORS='di=92:ex=33'
export GREP_OPTIONS='--color=auto'

# e.g. do 'PM man $@' to read colorized man pages
alias PM='PAGER=most' 

safecolors () 
{
    setprompt $fg[green] $fg[blue] $fg[white]
    export LS_COLORS='di=32:ex=35'
}

#___________________________________________________________________________
# execute

uptime
vmstat
echo ${(l.77..-.)}
fortune
setprompt

```

---

### Post by Bruce M. on 2008-03-15
> **chick said:**
> Here is my .zshrc with a screenshot of the prompt and terminal.

```
#___________________________________________________________________________
# zsh options

HISTFILE=~/.histfile
HISTSIZE=2000
SAVEHIST=2000

setopt correct
setopt extendedglob
setopt autopushd pushdminus pushdsilent pushdtohome
setopt no_clobber           # don't overwrite files when redirect
setopt share_history
setopt hist_verify          # verify when using !
setopt hist_ignore_space    # prepend ' ' to not be saved
setopt nohup               # don't kill bg jobs when tty quits
setopt nocheckjobs          # don't complain about background jobs on exit
setopt printexitvalue       # print exit value from jobs

unsetopt bgnice            # don't nice bg command

autoload -U compinit
compinit

#___________________________________________________________________________
# zsh zle key bindings

bindkey -e                      # emacs since vi just doesn't fit here :(

bindkey ' ' magic-space         # also do history expansion on space

bindkey '^z' undo               # C-x-u is overkill

bindkey ';5D' backward-word     # C-left
bindkey ';5C' forward-word      # C-right

# vi-ish bindings
bindkey '^w' kill-word
bindkey '^b' backward-kill-word

# fish/ipython-ish bindings
bindkey '\e[A' history-beginning-search-backward    # up arrow
bindkey '\e[B' history-beginning-search-forward     # down arrow

#___________________________________________________________________________
# alias

# zsh global aliases
alias -g H='--help'
alias -g L='| less'
alias -g M='| most'
alias -g G='| grep'
alias -g GC='| grep -C 2'

alias ..='cd ..'

alias ls='ls -FC --color=auto'
alias ll='ls -lh'
alias la='ls -A'
alias lal='ls -Alh'

alias dirs='dirs -v'                    # zsh dir stack

alias hist='history | grep'             # take an argument

alias cp='cp -iv'
alias mv='mv -iv'
alias rm='mv -ft $HOME/.trash'

alias du='du -h'
alias df='df -h'

alias pkgs='aptitude search'
alias pkg='dpkg -s'                     # faster than aptitude!
alias inst='sudo aptitude install'
alias uninst='sudo aptitude purge'

alias pscpu='ps -eo pcpu,nice,stat,time,pid,cmd --sort=-pcpu,-time \
             | sed "/^ 0.0 /d"'
alias psmem='ps -eo rss,vsz,pid,cmd --sort=-rss,-vsz \
             | awk "{ if (\$1 > 10000) print }"'

alias vi='vi -g -geom 80x40'
alias op='opera -newpage'
alias jacks='jackd -R -d alsa -p 128 &'

# facts of the day
alias today='grep -h -d skip `date +%m/%d` /usr/share/calendar/*'

# Commands frequency counts
alias cmdfreq='cut -d " " -f 1 < $HISTFILE | sort | uniq -c | sort -nr | head -n 10'

#___________________________________________________________________________
# generic functions

# do ls right after cd
cd () {
  if [ -n $1 ]; then
    builtin cd "$@" && ls
  else
    builtin cd ~ && ls
  fi
}

# list files only
lf () { ls -1p $@ | grep -v '\/$' }

# grep process by name and list the results nicely
pg () {
    if pgrep -f $@ > /dev/null;
    then
        pgrep -f $@ | xargs ps -o user,pid,stat,rss,vsz,pcpu,args \
                               --sort -pcpu,-rss;
    else 
        exit 1;
    fi
}

# compile lilypond file and view pdf
ly () { lilypond $@ && evince $(basename $1 .ly).pdf; }

# look in WordNet and Webster
d () { curl dict://dict.org/d:${1}:wn; }
wd () { curl dict://dict.org/d:${1}:web1913; } 

# find matches of $1, with optional strat $2 and optional db $3
ref () 
{
    if [[ -z $3 ]]; then
        curl dict://dict.org/m:${1}:english:${2};
    else
        curl dict://dict.org/m:${1}:${3}:${2};
    fi
}

# define $1 using optional db of $2
def () { curl dict://dict.org/d:${1}:${2} }

# local WordNet lookups
syn () { wn $1 -synsn; wn $1 -synsv; wn $1 -synsa; wn $1 -synsr; }
ant () { wn $1 -antsn; wn $1 -antsv; wn $1 -antsa; wn $1 -antsr; }

# Set a pretty zsh prompt, taking 0..5 args as colors
setprompt ()
{
    # load this to use $fg
    autoload -U colors
    colors

    c1="%{${1:-"$fg[green]"}%}"             # main color for cmd, cwd, hist
    c2="%{${2:-"$fg_no_bold[cyan]"}%}"      # color for user@host
    c3="%{${3:-"$fg_bold[grey]"}%}"         # color for =,()
    c4="%{${4:-"$fg[white]"}%}"             # time and arrow color
    c5="%{${5:-"$fg[red]"}%}"               # root color

    now="$c3($c4%D{%H:%M} %D{%a %b %d}$c3)"
    userhost="%(!.$c5.$c2)%n$c3@$c2%m"

    line2="$userhost ${c3}[$c1%h$c3] ${c4}--> %(!.$c5.$c1)"
    newline=$'\n%{\r%}'

    # truncate and pad line1 appropiately
    precmd () {
        local cwdrealwidth=${#${(%):-%~}}
        
        # length of $line1 w/o $cwd = 22
        if [[ "$cwdrealwidth + 22" -gt $COLUMNS ]]; 
        then
            # truncate
            local cwdwidth = (( $COLUMNS - 22 ))
        else
            # pad
            local padding="${(l.(($COLUMNS - 22 - $cwdrealwidth )))..-.)}"
        fi
        
        local cwd="$c1%$cwdwidth<...<%~%<<"
        local line1="$c3-($cwd$c3)-${padding}$now"
        export PROMPT="${line1}$newline$line2"
    }
       
    preexec () { print -n "$reset_color" }
}

#___________________________________________________________________________
# env

export EDITOR=vi
export LS_COLORS='di=92:ex=33'
export GREP_OPTIONS='--color=auto'

# e.g. do 'PM man $@' to read colorized man pages
alias PM='PAGER=most' 

safecolors () 
{
    setprompt $fg[green] $fg[blue] $fg[white]
    export LS_COLORS='di=32:ex=35'
}

#___________________________________________________________________________
# execute

uptime
vmstat
echo ${(l.77..-.)}
fortune
setprompt

```

Hate to be a pest, but I'm green behind the ears here.

Could you tell me "exactly" what is needed to change the prompt like you have it please?
Thanks
Bruce

---

### Post by chick on 2008-03-15
> **Bruce M. said:**
> Hate to be a pest, but I'm green behind the ears here.

Could you tell me "exactly" what is needed to change the prompt like you have it please?
Thanks
Bruce

Sure. First, you will need zsh.
```
sudo aptitude install zsh
```

Then put this into the file '~/.zshrc'
```

HISTFILE=~/.histfile
HISTSIZE=2000
SAVEHIST=2000

# Set a pretty zsh prompt, taking 0..5 args as colors
setprompt ()
{
    # load this to use $fg
    autoload -U colors
    colors

    c1="%{${1:-"$fg[green]"}%}"             # main color for cmd, cwd, hist
    c2="%{${2:-"$fg_no_bold[cyan]"}%}"      # color for user@host
    c3="%{${3:-"$fg_bold[grey]"}%}"         # color for =,()
    c4="%{${4:-"$fg[white]"}%}"             # time and arrow color
    c5="%{${5:-"$fg[red]"}%}"               # root color

    now="$c3($c4%D{%H:%M} %D{%a %b %d}$c3)"
    userhost="%(!.$c5.$c2)%n$c3@$c2%m"

    line2="$userhost ${c3}[$c1%h$c3] ${c4}--> %(!.$c5.$c1)"
    newline=$'\n%{\r%}'

    # truncate and pad line1 appropiately
    precmd () {
        local cwdrealwidth=${#${(%):-%~}}
        
        # length of $line1 w/o $cwd = 22
        if [[ "$cwdrealwidth + 22" -gt $COLUMNS ]]; 
        then
            # truncate
            local cwdwidth = (( $COLUMNS - 22 ))
        else
            # pad
            local padding="${(l.(($COLUMNS - 22 - $cwdrealwidth )))..-.)}"
        fi
        
        local cwd="$c1%$cwdwidth<...<%~%<<"
        local line1="$c3-($cwd$c3)-${padding}$now"
        export PROMPT="${line1}$newline$line2"
    }
       
    preexec () { print -n "$reset_color" }
}

setprompt

```

Now, load up zsh by just executing 'zsh'.

If you don't like my colors you can change it! Do sth like,
```
setprompt $fg[green] $fg[blue] $fg[white]
```

zsh also comes with a number of prompt themes. Try,
```

autoload promptinit
prompinit
prompt -h

```

If you like it you can change the shell permanently by executing 'chsh' and then enter '/bin/zsh'.

Of course zsh has tons of other features to explore! Check out [http://www.acm.uiuc.edu/workshops/zsh/toc.html](http://www.acm.uiuc.edu/workshops/zsh/toc.html)

---

### Post by Bruce M. on 2008-03-15
> **mali2297 said:**
> I've got
```

alias rm='rm -vi'

```
in my .bashrc. This means that the default behavior of rm is to ask for confirmation before removal. When I don't want that, I can override the -i flag by using
```

rm -f

```

I changed the **-f** to **-i** for test purposes. It's interactive and therefore verbose. The **-v** isn't really needed in this case.

However **-vf** would do it automatically and show you what's going on at the same time.  :)

Using **-i**
```

bruloo@bruloo:~$ cd test
bruloo@bruloo:~/test$ clean
rm: cannot lstat `#*': No such file or directory
rm: cannot lstat `.*~': No such file or directory
rm: remove regular file `%gconf.xml~'? y
rm: remove regular file `QStart.~'? y
rm: remove regular file `mkdev.bak'? y
rm: cannot lstat `*.dvi': No such file or directory
rm: cannot lstat `*.aux': No such file or directory
rm: cannot lstat `*.log': No such file or directory
bruloo@bruloo:~/test$ 

```

---

### Post by Bruce M. on 2008-03-15
> **chick said:**
> If you like it you can change the shell permanently by executing 'chsh' and then enter '/bin/zsh'.

Executing 'chsh' and changing /bin/bash to  /bin/zsh didn't do it.  :(
```

bruloo@bruloo:~$ chsh
Password: 
Changing the login shell for bruloo
Enter the new value, or press ENTER for the default
        Login Shell [/bin/zsh]: 

```
hmmm ... OK, [Ctrl]+[Alt]+[Backspace] maybe?

Will try that right after [Submit Reply].  :)

> **chick said:**
> Of course zsh has tons of other features to explore! Check out [http://www.acm.uiuc.edu/workshops/zsh/toc.html](http://www.acm.uiuc.edu/workshops/zsh/toc.html)

Thanks for the link.
Also got the DOCs and Tips and Tricks file too.

**EDIT: YES!** - [Ctrl]+[Alt]+[Backspace] did the trick.  " Me :) "

---

### Post by urukrama on 2008-03-30
I have made some minor changes to my bashrc. Here is what it looks like now:

> # ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize


# Alias definitions.
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# Programmable completion features
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

#Prompt
BGREEN='\[\033[1;32m\]'
GREEN='\[\033[0;32m\]'
BRED='\[\033[1;31m\]'
RED='\[\033[0;31m\]'
BBLUE='\[\033[1;34m\]'
BLUE='\[\033[0;34m\]'
NORMAL='\[\033[00m\]'
PS1="${NORMAL}[${NORMAL}\h${NORMAL}] ${NORMAL}\w ${RED}\$ ${NORMAL}"

alias netrestart='sudo /etc/init.d/networking restart'
alias ping='ping -c 10'

alias rm='rm -vi'
alias cp='cp -vi'
alias mv='mv -vi'

# Directory navigation aliases
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

alias Desktop='cd /home/urukrama/Desktop/'
alias Bin='cd /home/urukrama/Desktop/Bin/'
alias torrents='cd /home/urukrama/Desktop/torrents/'
alias Desktops='cd /home/urukrama/Images/Desktops/'
alias Images='cd /home/urukrama/Desktop/Images'

# Extract archives
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

unpack () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjvf $1        ;;
             *.tar.gz)    tar xzvf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xvf $1        ;;
             *.tbz2)      tar xjvf $1      ;;
             *.tgz)       tar xzvf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via unpack()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

#Netinfo - shows network information for your system
netinfo ()
{
echo "--------------- Network Information ---------------"
/sbin/ifconfig | awk /'inet addr/ {print $2}'
/sbin/ifconfig | awk /'Bcast/ {print $3}'
/sbin/ifconfig | awk /'inet addr/ {print $4}'
/sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'
myip=`lynx -dump -hiddenlinks=ignore -nolist [http://checkip.dyndns.org:8245/](http://checkip.dyndns.org:8245/) | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g' `
echo "${myip}"
echo "---------------------------------------------------"
}

#Dirsize - finds directory sizes and lists them for the current directory
dirsize ()
{
du -shx * .[a-zA-Z0-9_]* 2> /dev/null | \
egrep '^ *[0-9.]*[MG]' | sort -n > /tmp/list
egrep '^ *[0-9.]*M' /tmp/list
egrep '^ *[0-9.]*G' /tmp/list
rm -rf /tmp/list
}

#Copy and go to dir
cpg (){
  if [ -d "$2" ];then
    cp $1 $2 && cd $2
  else
    cp $1 $2
  fi
}

#Move and go to dir
mvg (){
  if [ -d "$2" ];then
    mv $1 $2 && cd $2
  else
    mv $1 $2
  fi
}

export OOO_FORCE_DESKTOP=gnome

---

### Post by Bruce M. on 2008-03-30
I'm curious, can an "alias" accept variables?
Is it hard to tell I'm green behind the ears here :?:

For example the alias **m2t** (man to txt)

at the prompt:
```
m2t chmod
```
it will treat "chmod" as the variable **$v** and put it in:

man **$v** >~/Manuals/man_**$v**.txt

and then it will do this:

```
man chmod >~/Manuals/man_chmod.txt
```

Just a thought.
In case you're wondering I'm still new enough to Linux that I'm collecting Man Pages to read at leasure.  :)

---

### Post by chick on 2008-03-30
> **Bruce M. said:**
> I'm curious, can an "alias" accept variables?
Is it hard to tell I'm green behind the ears here :?:

For example the alias **m2t** (man to txt)

at the prompt:
```
m2t chmod
```
it will treat "chmod" as the variable **$v** and put it in:

man **$v** >~/Manuals/man_**$v**.txt

and then it will do this:

```
man chmod >~/Manuals/man_chmod.txt
```

Just a thought.
In case you're wondering I'm still new enough to Linux that I'm collecting Man Pages to read at leasure.  :)

No, alias only expand the left hand side to the right. If you want to use arguments use a function.

BTW if you just want man to dump output to the terminal then just do

```

#man use the default pager in the environment variable $PAGER, the default is 'less'
#to not use it, do
PAGER="" man chmod

```

A simple redirection can save the output.

---

### Post by Bruce M. on 2008-03-30
Thanks for the reply.

> **chick said:**
> No, alias only expand the left hand side to the right. If you want to use arguments use a function.

OK, that answers that question.
Now to find out what a "function" is.
I have NO programming skills and have just started creating aliases because of this thread.
I'm so green behind the ears that Mother Nature is jealous of me.

> **chick said:**
> BTW if you just want man to dump output to the terminal then just do

I think you misunderstood me, if I'm reading this right.
I know I can "man foo" and read everything in the terminal, I want to create a text file of man pages I look at.

What do you mean by:
> dump output to the terminal

> **chick said:**
> ```

#man use the default pager in the environment variable $PAGER, the default is 'less'
#to not use it, do
PAGER="" man chmod

```

A simple redirection can save the output.

Wouldn't:
```
man chmod >man_chmod.txt
```
be simpler for my purposes?

---

### Post by chick on 2008-03-30
> **Bruce M. said:**
> 
I know I can "man foo" and read everything in the terminal

Man let you read the manual through a 'pager' program so that you can go back and forth and search for pattern etc. It does a number of things under the surface to format the page, e.g. wraping the text for different terminal size. Then it 'pipe' the output to the pager program. Usually this is the program called 'less'.

Under the surface, it does sth similar to
```

cat somefile | less    # pipe the content to through 'less', vs.
cat somefile           # dump the content to the file to terminal

```

Just to illustrate what I was trying to say, try this and see the difference when changing MANWIDTH
```

PAGER="" MANWIDTH=100 man chmod

```

This gets into the topic of environment variable in shell scripting, which I won't try to explain. Many excellent tutorials exist.

---

### Post by Bruce M. on 2008-03-30
> **chick said:**
> Man let you read the manual through a 'pager' program so that you can go back and forth and search for pattern etc. It does a number of things under the surface to format the page, e.g. wraping the text for different terminal size. Then it 'pipe' the output to the pager program. Usually this is the program called 'less'.

Under the surface, it does sth similar to
```

cat somefile | less    # pipe the content to through 'less', vs.
cat somefile           # dump the content to the file to terminal

```

Just to illustrate what I was trying to say, try this and see the difference when changing MANWIDTH
```

PAGER="" MANWIDTH=100 man chmod

```

This gets into the topic of environment variable in shell scripting, which I won't try to explain. Many excellent tutorials exist.

Now that is nice ... learned something today  :)
Thanks

---

### Post by myle on 2008-05-11
Most of the ideas are taken from this thread

```

# ~/.bashrc: executed by bash(1) for non-login shells.
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

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

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
    . /etc/bash_completion# Define a word - USAGE: define dog
define ()
{
lynx -dump "http://www.google.com/search?hl=en&q=define%3A+${1}&btnG=Google+Search" | grep -m 5 -w "*"  | sed 's/;/ -/g' | cut -d- -f5 > /tmp/templookup.txt
            if [[ -s  /tmp/templookup.txt ]] ;then    
                until ! read response
                    do
                    echo "${response}"
                    done < /tmp/templookup.txt
                else
                    echo "Sorry $USER, I can't find the term \"${1} \""                
            fi    
rm -f /tmp/templookup.txt
}

fi

# extract files
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

#myip - finds your current IP if your connected to the internet
myip ()
{
elinks -dump http://checkip.dyndns.org:8245/ | awk '{ print $4 }' | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g' 
}

# Define a word - USAGE: define dog
define ()
{
lynx -dump "http://www.google.com/search?hl=en&q=define%3A+${1}&btnG=Google+Search" | grep -m 5 -w "*"  | sed 's/;/ -/g' | cut -d- -f5 > /tmp/templookup.txt
            if [[ -s  /tmp/templookup.txt ]] ;then    
                until ! read response
                    do
                    echo "${response}"
                    done < /tmp/templookup.txt
                else
                    echo "Sorry $USER, I can't find the term \"${1} \""                
            fi    
rm -f /tmp/templookup.txt
}

```

---

### Post by FuturePilot on 2008-05-11
This is a pretty crazy one. I wouldn't recommend using it on a local machine because it will be very annoying every time you open a terminal. But it's really cool for a machine that you never log in to locally, but over SSH.
It's based on the default .bashrc of Ubuntu but with some modifications.

```
# ~/.bashrc: executed by bash(1) for non-login shells.
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
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

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
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# Colors

Black="$(tput setaf 0)"
BlackBG="$(tput setab 0)"
DarkGrey="$(tput bold ; tput setaf 0)"
LightGrey="$(tput setaf 7)"
LightGreyBG="$(tput setab 7)"
White="$(tput bold ; tput setaf 7)"
Red="$(tput setaf 1)"
RedBG="$(tput setab 1)"
LightRed="$(tput bold ; tput setaf 1)"
Green="$(tput setaf 2)"
GreenBG="$(tput setab 2)"
LightGreen="$(tput bold ; tput setaf 2)"
Brown="$(tput setaf 3)"
BrownBG="$(tput setab 3)"
Yellow="$(tput bold ; tput setaf 3)"
Blue="$(tput setaf 4)"
BlueBG="$(tput setab 4)"
LightBlue="$(tput bold ; tput setaf 4)"
Purple="$(tput setaf 5)"
PurpleBG="$(tput setab 5)"
Pink="$(tput bold ; tput setaf 5)"
Cyan="$(tput setaf 6)"
CyanBG="$(tput setab 6)"
LightCyan="$(tput bold ; tput setaf 6)"
NC="$(tput sgr0)"       # No Color

# Functions

spin ()
{
echo -ne "$White-"
echo -ne "$LightGray\b|"
echo -ne "$LightGreen\bx"
sleep .02
echo -ne "$LightBlue\b+$RC"
}

typetext1 ()
{
sleep .02
echo -ne "$LightGreen W"
sleep .02
echo -ne e
sleep .02
echo -ne l
sleep .02
echo -ne c
sleep .02
echo -ne o
sleep .02
echo -ne m
sleep .02
echo -ne e
sleep .02
echo -ne " "
sleep .02
echo -ne t
sleep .02
echo -ne o
sleep .02
echo -ne " "
sleep .02
echo -ne "$HOSTNAME $NC"
sleep .02
}

typetext2 ()
{
sleep .02
echo -ne "$LightGreen E"
sleep .02
echo -ne n
sleep .02
echo -ne j
sleep .02
echo -ne o
sleep .02
echo -ne y
sleep .02
echo -ne " "
sleep .02
echo -ne y
sleep .02
echo -ne o
sleep .02
echo -ne u
sleep .02
echo -ne r
sleep .02
echo -ne " "
sleep .02
echo -ne s
sleep .02
echo -ne t
sleep .02
echo -ne a
sleep .02
echo -ne y
sleep .02
echo -ne "! "
sleep .02
}

dots ()
{
sleep .5
echo -ne "$LightGreen ."
sleep .5
echo -ne .
sleep .5
echo -ne .
sleep .8
echo -ne "$LightBlue done"
}

#Distribution
DISTRO="Unknown Distro"
DISTRO='Ubuntu 8.04 "Hardy Heron"'

memfree="`cat /proc/meminfo | grep MemFree | cut -d: -f2 | cut -dk -f1`";
memtotal="`cat /proc/meminfo | grep MemTotal | cut -d: -f2 | cut -dk -f1`";
memfreepcnt=$(echo "scale=5; $memfree/$memtotal*100" | bc -l);

# Welcome screen

clear;
echo -e "";
for i in `seq 1 15` ; do spin; done; typetext1; for i in `seq 1 15` ; do spin; done ;echo "";
echo "";
echo -ne "$LightBlue Hello $LightGreen$USER $LightBlue!";
echo ""; sleep .3;
echo "";
echo -ne "$LightBlue Today is: $LightGreen`date`";
echo ""; sleep .3;
echo -ne "$LightBlue Last login:$LightGreen `lastlog | grep $USER | awk '{print $4" "$6" "$5" "$9}'`$LightBlue at$LightGreen `lastlog | grep $USER | awk '{print $7}'`$LightBlue from$LightGreen `lastlog | grep $USER | awk '{print $3}'`";
echo ""; sleep .3;
echo "";
echo -ne "$LightBlue Loading system information"; dots; 
echo ""; sleep .3;
echo "";
echo -ne "$LightBlue Distro: $LightGreen $DISTRO";
echo "";
echo -ne "$LightBlue Kernel: $LightGreen `uname -smr`";
echo "";
echo -ne "$LightBlue CPU:   $LightGreen `grep "model name" /proc/cpuinfo | cut -d : -f2`";
echo "";
echo -ne "$LightBlue Speed:  $LightGreen`grep "cpu MHz" /proc/cpuinfo | cut -d : -f2` MHz"; 
echo "";
echo -ne "$LightBlue Load:   $LightGreen `w | grep up | awk '{print $10" "$11" "$12}'`";
echo "";
echo -ne "$LightBlue RAM:    $LightGreen `cat /proc/meminfo | head -n 1 | awk '/[0-9]/ {print $2}'` KB";
echo "";
echo -ne "$LightBlue Usage:  $LightGreen $memfreepcnt %"
echo "";
echo -ne "$LightBlue IP:     $LightGreen `/sbin/ip addr show ath0 | grep 'inet ' | cut -d t -f2 | cut -d / -f1 | cut -b 2-`";
echo "";
echo -ne "$LightBlue Uptime: $LightGreen `uptime | awk {'print $3" "$4" "$5'} | sed 's/:/ hours, /' | sed -r 's/,$/ minutes/'`";
echo ""; sleep .3;
echo "";
for i in `seq 1 21` ; do spin; done; typetext2; for i in `seq 1 20` ; do spin; done ;echo "";
echo "" $NC;

# Fancy bash

PS1='\[$LightBlue\]\[$LightGreen\]\u\[$LightBlue\]@\[$LightGreen\]\h\[$LightBlue\]:\[$LightGreen\]\w\[$LightBlue\]\$\[$NC\] '

```

There's a few little glitches I've been trying to work out.
[LIST]
[*]The hard coded Distro name should not be hard coded
[*]The Previous login host is actually displayed as the current host you're logging in from
[*]Displaying amount of RAM in MB instead of KB
[/LIST]
This is really cool for remote logins. :)

---

### Post by ghindo on 2008-05-11
I only have a few areas of customization in my .bashrc - a few aliases and a custom header.```
alias update='sudo apt-get update && sudo apt-get upgrade'
alias clean='sudo apt-get autoclean && sudo apt-get autoremove && sudo deborphan -Z && sudo apt-get clean'
``````
PS1='[\u\W] \[\e[0;30m\]//\[\e[1;37m\] '
```Great thread.  It's taught me a lot! :)

**EDIT:**  Attached a screenshot - nothing fancy.

---

### Post by andrewsomething on 2008-05-26
Haven't changed much. Added some aliases though:

```
#fix my most common typos
alias cd..='cd ..'
alias cd~='cd ~'

#get to the desktop
alias desktop='cd ~/Desktop'

#save some time typing apt commands
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias get='sudo apt-get install'
alias remove='sudo apt-get remove --purge'
alias apt-search='apt-cache search'
alias apt-policy='apt-cache policy'
alias sources='gksudo gedit /etc/apt/sources.list'


#quick updates from bzr

alias update-awn="cd ~/source-installs/awn-core-bzr/ && bzr pull"
alias upgrade-awn="cd ~/source-installs/awn-core-bzr/ && bzr pull && 
./autogen.sh && make && sudo make install && make clean"

alias update-extras="cd ~/source-installs/awn-extras-bzr/ && bzr pull"
alias upgrade-extras="cd ~/source-installs/awn-extras-bzr/ && bzr pull && 
./autogen.sh && make && sudo make install && make clean"

alias update-screenlets="cd ~/source-installs/screenlets-bzr/ && bzr pull"
alias upgrade-screenlets="cd ~/source-installs/screenlets-bzr/ && bzr pull && sudo make install && make clean"

#pbuilder stuff
alias pbuilder="sudo pbuilder-dist"
alias update-sid="sudo pbuilder-dist sid update"
alias update-intrepid="sudo pbuilder-dist intrepid update"
alias update-hardy="sudo pbuilder-dist hardy update"

#alias to remember aliases, heh
alias aka='cat ~/.bashrc |grep alias'

#don't delete things by accident
#alias rm='rm -i'
alias del='gvfs-trash'

#su-like root acces
alias su='sudo -s'
```

---

### Post by KIAaze on 2008-06-18
It's not very clean, but the comments should be enough.
Interesting features:
-Special PS1 only for Konsole terminal putting directory name in the tabs. Otherwise I get errors when using it in other terminals.
-Play sound everytime you run a command (commented out, there's also a thread about it somewhere)
-Command numbering

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

#########################################
#function powerprompt()
# {
#     _powerprompt()
#     {
#         #LOAD=$(uptime|sed -e "s/.*: \([^,]*\).*/\1/" -e "s/ //g")
#	LOAD=$(mplayer /home/kiaaze/desktop_merge/Tank/opening.wav 1>/dev/null 2>&1)
#     }
#
#    PROMPT_COMMAND=_powerprompt
#     case $TERM in
#         *term | rxvt  )
#             PS1="${HILIT}[\A \$LOAD]$NC\n[\h \#] \W > \[\033]0;\${TERM} [\u@\h] \w\007\]" ;;
#         linux )
#             PS1="${HILIT}[\A - \$LOAD]$NC\n[\h \#] \w > " ;;
#         * )
#             PS1="[\A - \$LOAD]\n[\h \#] \w > " ;;
#     esac
# }
#
# powerprompt     # this is the default prompt - might be slow
#                 # If too slow, use fastprompt instead....
#########################################

playsound()
{
	mplayer ~/desktop_merge/Tank/ttawht00.wav 1>/dev/null 2>&1 &
}

#PROMPT_COMMAND="echo -n [$(date +%H%M)]"

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    #PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    PS1="\e[0;1;33;41m[\u@\h:\w]\$ \e[m "
    ;;
*)
	#That's the one I really use.
    #PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    #PS1="\$(playsound)\e[0;1;33;41m[\u@\h:\w]\$ \e[m "
    #PS1="\e[0;1;33;41m[\u@\h:\w]\$ \e[m "
    PS1="\[\e[0;1;33;41m\][\#][\w]\$ \[\e[m\] "
    ;;
esac

    # set a fancy prompt
    #PS1="\e[0;31m[\u@\h \W]\$ \e[m "
    #PS1="\e[0;1;33;41m[\u@\h:\w]\$ \e[m "
    #PS1='\u@\h:\w\$ '

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\#@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#PS1="\[\e[0;1;33;41m\]testing\[\e[00m\]"
#PS1="\[\e[0;1;33;41m[\w]\$ \e[00m\]"

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
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
alias laf='ls -laF'
alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'
alias rm='rm -iv'
alias mv='mv -iv'
alias cp='cp -iv' 

#alias sudo='sudo -s'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

#export CVS_RSH=ssh
#export CVSROOT=:ext:zohn@alliancemanager.cvs.sourceforge.net:/cvsroot/alliancemanager

#set current directory as session name! :D
#export PS1=$PS1"\[\e]30;\H:\W\a\]"
#export PS1=prompt"\[\e]30;tabname\a\]"
#export PS1=prompt"\[\e];tabname\a\]"

#Special PS1 string only for Konsole and Yakuake, so it shows the name of the current directory in the tab (for Konsole at least)
if [ $KONSOLE_DCOP ] && [ ! $COLORTERM ] ; then
	echo "You are using a KDE terminal."
	export PS1=$PS1"\[\e]30;\H:\W\a\]"
fi


#for the dirkdashing game
#export PATH=$PATH:/home/kiaaze/dirkdashing

#GDHE for the robot
export GDHE=/usr/local/share/gdhe

#prepare ROOT environment
export LD_LIBRARY_PATH=.:/usr/local/lib/root/:$LD_LIBRARY_PATH
export ROOTSYS=/usr/local/
export PYTHONPATH=$PYTHONPATH:$ROOTSYS/lib/root:$ROOTSYS/gdml

#display a short random fortune :)
#fortune -s

#fancy python stuff like tab completion and history :)
#export PYTHONSTARTUP=/home/kiaaze/.pythonrc:/home/kiaaze/.pystartup
#export PYTHONSTARTUP=/home/kiaaze/.pythonrc
export PYTHONSTARTUP=/home/kiaaze/.pystartup

#prepare GEANT environment
#source ~/bin/prepare_environment.sh >/dev/null

#Use a real editor :p
export EDITOR=vim

```

---

### Post by el mariachi on 2008-07-16
how can I do this:
[[COLOR=DarkOrange]mariachi[COLOR=Black]@[COLOR=DarkOrange] ~[/COLOR][/COLOR][/COLOR][COLOR=Black]]  where mariachi is my username, ~ is the path (full path) and black is white.[/COLOR]

---

### Post by mali2297 on 2008-07-16
> **el mariachi said:**
> how can I do this:
[[COLOR=DarkOrange]mariachi[COLOR=Black]@[COLOR=DarkOrange] ~[/COLOR][/COLOR][/COLOR][COLOR=Black]]  where mariachi is my username, ~ is the path (full path) and black is white.[/COLOR]

Assuming your default terminal colors are white on black, then
```
export PS1="[\[\e[33m\]\u\[\e[0m\]@ \[\e[33m\]\w\[\e[0m\]] "
```

For an explanation, see
[http://www.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www.ibm.com/developerworks/linux/library/l-tip-prompt/)

---

### Post by Sykes2222 on 2008-07-17
Hi FuturePilot,

Thanks, that was fun. :)

> There's a few little glitches I've been trying to work out.

[*]The hard coded Distro name should not be hard coded

echo -ne "$LightBlue Distro: $LightGreen `lsb_release -sd`";

Should do what you want.
> 
[*]The Previous login host is actually displayed as the current host you're logging in from

Have a look at with $SSH_CONNECTION 

You could probably have a play with sed and grep it from /etc/hosts.


> 
[*]Displaying amount of RAM in MB instead of KB

and checking the info.sh script from [http://ubuntukids.org/blog/?page_id=25](http://ubuntukids.org/blog/?page_id=25)

```
let memtotal=`grep "MemTotal" /proc/meminfo|cut -c 12-22|indent -i0`/1024
echo "Memory Total:   $memtotal mb"
let memfree=`grep "MemFree" /proc/meminfo|cut -c 12-22|indent -i0`/1024
let memcache=`grep "Cached" /proc/meminfo|cut -c 12-22|indent -i0`
let memcache=$memcache/1024
let memfreetotal=$memfree+$memcache
echo "Memory Free:    $memfreetotal mb"
```

will give you MB. You will need to get the indent program thats in the repos to use it as is.

---

### Post by valadil on 2008-07-18
For brevity's sake I'm only including stuff I haven't seen in the last 8 pages.

alias tf='tail -f'
I follow a lot of log files and this one just makes sense.

alias sudo='A=`alias` sudo  '
Runs alias before running sudo, somehow preserving all your alias bindings in the sudo command.  So if I did sudo tf /var/log/file, it would still work even though root doesn't have my alias file.

alias su='su -m'
Preserves my env variables when I switch user.  Useful because it includes my prompt, which flashes red when I'm root.  Sometimes I don't want it so I fall back to /bin/su to ignore the alias.

function lw() { 
         if [ $# -gt 0 ] ; then 
            for bin in $@ ; do ls -lh `which $bin` ; done 
         else 
            echo "lw (ls which) requires more than 0 arguments"
         fi  
}
Lastwhich (lw) is new for me and I'm not sure if I'll keep it.  I use it for finding the path of a symlink.  For instance, lets say I don't know which version of java I'm using and several are installed.  I usually type "which java" and that tells me it's coming from /etc/alternatives/java.  That's not useful so I type "ls -lh `which java`" (the command in the backticks executes first, so I am effectively doing ls -lh /etc/alternatives/java in fewer keypresses).  Since I can't alias a variable into a backtick, this one had to be a function.  I figured I might as well let it do several files at once, hence the for loop, though I'm not sure I'll actually use that feature.  I still feel dirty putting this in my .alias file.

I know this isn't for .bashrc, but fans of screen will appreciate this:
caption always "%{= ..}%-w%{= BW}%n %t%{-}%+w %-= @%H - %D %d %M - %c"

It puts a line at the bottom of your screen session.  That line includes the names and numbers of open windows, so it looks like tabs.  Now I don't need a fancy terminal window as long as screen is installed.  For added fun, it includes the host and date too.

--

I put all these rc files (plus some other fun stuff like my authorized_keys) in a CVS repository.  Whenever I change my .bashrc I can push the change into CVS and then check it out at any machine I might visit later.  Given that I have several dozen accounts this is a huge time saver.

---

### Post by LinuX-M@n1@k on 2008-07-21
> **urukrama said:**
> 
Here is my bashrc:

```
...
myip=`lynx -dump -hiddenlinks=ignore -nolist http://checkip.dyndns.org:8245/ | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g' `
...
```

Just a suggestion:
```
lynx -dump -hiddenlinks=ignore -nolist http://checkip.dyndns.org:8245/ | grep "Current IP Address" | cut -d":" -f2 | cut -d" " -f2
```
It's easier to understand. :)

Can you explain me what exactly
```
sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g'
```
does? I mean, how does it work? Because I cannot understand it.

---

### Post by Visti on 2008-07-21
There's a nice site for stuff like this at [http://dotfiles.org/](http://dotfiles.org/) , but you probably already know that..

I'll pimp mine and post it later!

---

### Post by KIAaze on 2008-07-21
> **LinuX-M@n1@k said:**
> Just a suggestion:
```
lynx -dump -hiddenlinks=ignore -nolist http://checkip.dyndns.org:8245/ | grep "Current IP Address" | cut -d":" -f2 | cut -d" " -f2
```
It's easier to understand. :)

Can you explain me what exactly
```
sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g'
```
does? I mean, how does it work? Because I cannot understand it.

It does 3 things:
1) /^$/d ->remove empty lines (search for pattern "^$" and **d**elete corresponding lines)
2) s/^[ ]*//g ->remove spaces at the beginning of lines (**s**ubstitute matches for "^[ ]*" with "" **g**lobally)
3) s/[ ]*$//g ->remove spaces at the end of lines (**s**ubstitute matches for "[ ]*$" with "" **g**lobally)

regular expression basics:
^:beginning of line
$:end of line
*:repeated any number of times ([ ]*=any number of spaces)

For more details:
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)
[http://www.regular-expressions.info/](http://www.regular-expressions.info/)

And I have a question too:
What IP address does that site/command give?
It's obviously not my local IP address (from ifconfig).
Is it my modem/router's IP address?

P.S: Thanks for the cut command and the dotfiles.org site. :)

---

### Post by urukrama on 2008-07-21
> **KIAaze said:**
> And I have a question too:
What IP address does that site/command give?
It's obviously not my local IP address (from ifconfig).
Is it my modem/router's IP address?

Thanks for giving the detailed explanation. Saves me the time and effort to write it all down myself :)

That first link you gave for sed ([http://www.grymoire.com/Unix/Sed.html]("http://www.grymoire.com/Unix/Sed.html")) is the very best guide for sed I've found; up until I read that a short while ago sed didn't make much sense to me.

I'm not sure what IP address it gives. I haven't used that alias in a long time and no longer have lynx installed. I also did not write the alias myself but found it somewhere online; it initially looked neat, but I found I had no use for it. I haven't bothered to delete it from my bashrc though. (I carry a few other aliases that I haven't used in a while around).

I suppose the router IP address would make sense, though.

---

### Post by LinuX-M@n1@k on 2008-07-21
> **urukrama said:**
> I suppose the router IP address would make sense, though.

Indeed. It shows your public/real IP.

KIAaze, thank you for the detailed explanation! ;)

---

### Post by ice60 on 2008-07-21
> **valadil said:**
> 
alias tf='tail -f'
I follow a lot of log files and this one just makes sense.

i was looking through my bash history to see which options i use with tail most and saw i've got a program called MultiTail. maybe you'd like that??  i'm not sure if i installed it or if it came with this distro?

check out the screenshots of it!!
[http://images.google.com/images?q=MultiTail&hl=en&btnG=Search+Images](http://images.google.com/images?q=MultiTail&hl=en&btnG=Search+Images)

---

### Post by kaiju on 2008-07-22
> **urukrama said:**
> ```

myip=`lynx -dump -hiddenlinks=ignore -nolist http://checkip.dyndns.org:8245/ | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g' `
echo "${myip}"

```

i dropped lynx in favor of w3m (a really great pager/browser) a long time ago. the lines above can be changed to just
```

myip=`w3m -dump http://checkip.dyndns.org:8245/`
echo "${myip}"

```

this is only useful if your ip address is changing frequently (some providers assign a new ip every time you reconnect to their service).

---

### Post by KingTermite on 2008-07-22
> **urukrama said:**
> I've only recently started playing with the ~/.bashrc file and want more ideas to play with. Please share your bashrc file and show all of us what cool and handy things you can do with bash.
Another similar thread already, here:
[http://ubuntuforums.org/showthread.php?t=616875](http://ubuntuforums.org/showthread.php?t=616875)

---

### Post by BryanFRitt on 2008-08-02
I have my PS1 set like this:
[I]
PS1='\n\D{%Y-%m-%d_%H:%M:%S_%a}, \!\n${debian_chroot:+($debian_chroot)}\u@\H:\ncd \"\w/\"\n'[/I]

Thinking it would help, being able to cd by copying and pasting, or using middle click, to this output to change the directory, but in directory ~/, etc it outputs
*cd "~/"*
pasted(or middle click) + Enter key gives
*bash: cd: ~/: No such file or directory*

**How can I get cd "~/" etc... working or get it to display the full path without the "~/"?**

p.s. it looks like this:

[I]2008-08-02_16:38:38_Sat, 505
bryan@bryan-laptop:
cd "~/"[/I]

with the time going from largest value to smallest value followed by day of week, comma space, then followed by history number and a new line, then my user info, colon, and a new line, then cd and the path of the directory, and another newline.

This is also good for copying and pasting date/time for sorting purposes.

---

### Post by BryanFRitt on 2008-08-02
Other variations on this 
(these might seam weird, and you might end up trying to backspace where nothing will happen!):

[I]PS1='\n\D{%Y-%m-%d_%H:%M:%S_%a}, \!\n${debian_chroot:+($debian_chroot)}\u@\H:\n\w/\n\w/'
PS1='\n\D{%Y-%m-%d_%H:%M:%S_%a}, \!\n${debian_chroot:+($debian_chroot)}\u@\H:\n\w/\n'
PS1='\n\D{%Y-%m-%d_%H:%M:%S_%a}, \!\n${debian_chroot:+($debian_chroot)}\u@\H:\n\w/'[/I]
Now with color:
*PS1='\n\[\033[01;33m\]\D{%Y-%m-%d_%H:%M:%S_%a}, \!\n${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\H:\n\[\033[01;34m\]\w\[\033[01;37m\]/'*
#found Color info here: [http://ubuntuforums.org/showthread.php?t=674446](http://ubuntuforums.org/showthread.php?t=674446)

Note: this add an extra *'/'* which works fine for all directories except for the *'/'* directory.
Anybody know how to fix this?

---

### Post by BryanFRitt on 2008-08-02
My Alias section:
# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'
#list file details and names recursively
alias lllll='ls -alFR1'
#list file names recursively
alias llll='ls -R'
#list file details and name
alias lll='ls -alF1'
#list file names in one column
alias ll='ls -1'
#list names in multiple columns
alias l='ls'
#list file names in one column
alias 1='ls -1'

#the following idea came from
#[http://eklhad.net/linux/app/onehand.html](http://eklhad.net/linux/app/onehand.html)
#alias asdf="loadkeys /usr/lib/kbd/keytables/dvorak.map"
#alias aoeu="loadkeys /usr/lib/kbd/keytables/us.map"
#didn't work - must be a different command?
#Trying #it worked neat... # got these from the KDE Control Module Layout tab in the bottom where it says Command:
alias asdf="setxkbmap -layout us -variant dvorak"
alias aoeu="setxkbmap -layout us -variant basic"

---

### Post by cardinals_fan on 2008-08-02
Will you kill me if I post my .zshrc here?

```
# Lines configured by zsh-newuser-install
HISTFILE=~/.histfile
HISTSIZE=1000
SAVEHIST=1000
bindkey -e
# End of lines configured by zsh-newuser-install
# The following lines were added by compinstall
zstyle :compinstall filename '/home/jesse/.zshrc'

autoload -Uz compinit
compinit
# End of lines added by compinstall

PROMPT='[%n@%m %~]$ '

alias conkyreset="killall -SIGUSR1 conky"
alias c="clear"
alias scores='lynx -nonumbers -dump http://scores.espn.go.com/mlb/scoreboard | egrep -i -A12 -B2 "St. Louis"'
alias javaws="/opt/java/jre/bin/javaws"
alias java="/opt/java/jre/bin/java"
alias ls='ls --color=auto'
```

---

### Post by Bruce M. on 2008-08-02
> **cardinals_fan said:**
> Will you kill me if I post my .zshrc here?

Nope ... But I'd fill /dev/null with Blue Jays  :lolflag:

I'm outta here...
Bruce

Oh wait ... can't leave yet .... 
The favorite and most used part of my "Alias" section:
```
# my aliases
alias conke='(gedit ~/.startconky ~/Conky/conkymain ~/Conky/conkyforecast ~/Conky/conkyemail ~/Conky/fortune ~/Conky/scripts/SP_Forecast.py ~/Conky/scripts/EN_Forecast.py ~/Conky/scripts/mail/conkyEmail.py ~/Conky/scripts/myweather.template &)'
alias cia='killall conky && ./.startconky'
alias killc='killall conky'
alias stc='~/.startconky'
```
yea ... I'm a conky nut.

Have a nice day
Bruce

---

### Post by jimi_hendrix on 2008-08-02
whats a .bashrc

---

### Post by cardinals_fan on 2008-08-02
> **Bruce M. said:**
> Nope ... But I'd fill /dev/null with Blue Jays  :lolflag:

I'm outta here...
Bruce

Oh wait ... can't leave yet .... 
The favorite and most used part of my "Alias" section:
```
# my aliases
alias conke='(gedit ~/.startconky ~/Conky/conkymain ~/Conky/conkyforecast ~/Conky/conkyemail ~/Conky/fortune ~/Conky/scripts/SP_Forecast.py ~/Conky/scripts/EN_Forecast.py ~/Conky/scripts/mail/conkyEmail.py ~/Conky/scripts/myweather.template &)'
alias cia='killall conky && ./.startconky'
alias killc='killall conky'
alias stc='~/.startconky'
```
yea ... I'm a conky nut.

Have a nice day
Bruce
I just use```
alias conkyreset="killall -SIGUSR1 conky"

```
> **jimi_hendrix said:**
> whats a .bashrc
The file in your home directory that changes your Bash settings.  Bash is the default shell in most Linux distros.  I use Zsh.

---

### Post by Bruce M. on 2008-08-02
> **jimi_hendrix said:**
> whats a .bashrc

Type:
[code]man bash[/bash]
to see the manual (man)
It the: Borne Again SHell

Try this:  [Bash]("http://en.wikipedia.org/wiki/Bash")

**[COLOR="Red"]NOTE:[/COLOR]** Make a backup if you plan on changing anything in it.

Have a nice day
Bruce

---

### Post by jimi_hendrix on 2008-08-02
so whats the point of messing with it?

---

### Post by Bruce M. on 2008-08-02
> **cardinals_fan said:**
> I just use```
alias conkyreset="killall -SIGUSR1 conky"
```

Linux: 101 ways to do the same thing.

That didn't work on my old P-III for some reason, so I came up with this workaround. Never thought to change it.

Have a nice day.
Bruce

---

### Post by Bruce M. on 2008-08-02
> **jimi_hendrix said:**
> so whats the point of messing with it?

Well, instead of always typing long commands like:
```
gedit ~/.startconky ~/Conky/conkymain ~/Conky/conkyforecast ~/Conky/conkyemail ~/Conky/scripts/SP_Forecast.py ~/Conky/scripts/EN_Forecast.py ~/Conky/scripts/mail/conkyEmail.py ~/Conky/scripts/myweather.template
```
when I want to edit my conky stuff I created an **alias** in my bashrc:

**conk** for conky + **e** for edit
```
conke
```
actually does this:
```
alias conke='(gedit ~/.startconky ~/Conky/conkymain ~/Conky/conkyforecast ~/Conky/conkyemail ~/Conky/fortune ~/Conky/scripts/SP_Forecast.py ~/Conky/scripts/EN_Forecast.py ~/Conky/scripts/mail/conkyEmail.py ~/Conky/scripts/myweather.template ~/Conky/scripts/argentina.template ~/Conky/scripts/otherweather.template &)'
```
Saves a LOT of typing.

Have a nice day
Bruce

---

### Post by jimi_hendrix on 2008-08-02
so it makes commands

---

### Post by KIAaze on 2008-08-02
It's a shellscript that's run every time you open a terminal, so it can do much more powerful things than just "make a command". ;)

-You can change your command prompt.
-You can set environment variables.
-You can display some info as a welcome message.
-You can create specific prompts depending on the terminal used.
-You can make terminal tabs/title bars display your current directory.
-You can add sounds for every command you enter. (my favorite, altough not practical for general use. :roll: )
...

---

### Post by cardinals_fan on 2008-08-02
> **KIAaze said:**
> It's a shellscript that's run every time you open a terminal, so it can do much more powerful things than just "make a command". ;)

-You can change your command prompt.
-You can set environment variables.
-You can display some info as a welcome message.
-You can create specific prompts depending on the terminal used.
-You can make terminal tabs/title bars display your current directory.
-You can add sounds for every command you enter. (my favorite, altough not practical for general use. :roll: )
...
And if you use Zsh, that's only the beginning :)

*flame-war started*

---

### Post by bodhi.zazen on 2008-08-03
zsh ftw :)

The biggest problem with zsh is finding a decent .zshrc :

[http://zsh.dotsrc.org/Contrib/startup/std/zshrc](http://zsh.dotsrc.org/Contrib/startup/std/zshrc)

use google to find others :)

then read through them to understand what you are doing and make a few adjustments ....


[http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)

This is what a good .zshrc can do for you (although there are better, if you look close you will see that is zsh on cygwin in Windows):

[IMG]http://img127.imageshack.us/img127/9751/zshdx1.png[/IMG]

---

### Post by el mariachi on 2008-08-14
anyone know how to make an alias for the "mount iso" procedure? I just want to input "miso data.iso" and ta-dah iso file is mounted to my ~/nomada dir

---

### Post by ayoli on 2008-08-14
> **el mariachi said:**
> anyone know how to make an alias for the "mount iso" procedure? I just want to input "miso data.iso" and ta-dah iso file is mounted to my ~/nomada dir

what about : 
```
alias miso='sudo mount -o loop'
```
which you can use like that :
```
miso /path/ti/iso /path/to /mount/point
```
(alias don't take vars, but take all input taht come after).

---

### Post by kaiju on 2008-08-16
> **el mariachi said:**
> anyone know how to make an alias for the "mount iso" procedure? I just want to input "miso data.iso" and ta-dah iso file is mounted to my ~/nomada dir

while aliases can't take variables, functions sure can. since i liked the idea, and it seemed to be good exercise for a beginner like me, here it is:
```
miso()#mount iso file
{
_mountpoint=/home/weirdo/iso
if [ -z $1 ]; then
  echo -e "usage:\tmiso file.iso\n\tmiso -u"
elif [ $1 = "-u" ]; then
  sudo umount $_mountpoint && echo "$_mountpoint unmounted."
elif [ -r $1 ] && [ ! -z `echo $1 | grep -i .iso$` ]; then
  if [ `ls $_mountpoint | wc -w` -ne 0 ]; then
    echo "error: $_mountpoint is not empty."
  else
    sudo mount -o loop $1 $_mountpoint && echo "'$1' mounted to $_mountpoint."
  fi
else
  echo "error: '$1' is not a readable iso file."
fi
}
```

shell functions can be specified right inside the ~/.bashrc file. there are a few really useful ones in this thread :)

---

### Post by el mariachi on 2008-08-16
interesting :D
does that alias also unmounts the iso? thanks!

---

### Post by ayoli on 2008-08-16
> **el mariachi said:**
> interesting :D
does that alias also unmounts the iso? thanks!

The function (not an alias) posted by kaiju above does this, yes (using -u switch).

---

### Post by AndEat on 2008-08-22
my bash alias file culled from here and elsewhere, still a work in progress:

#bash aliases

#BASH environment
shopt -s histappend
shopt -s cmdhist
export PROMPT_COMMAND="history -n" #; history -a
export HISTIGNORE="&:ls:[bf]g:exit"
export HISTCONTROL="ignoreboth:ignorespace:erasedups"
#PS1='\[\e[0;32m\]\u@\h\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[1;32m\]\$ \[\e[m\]\[\e[1;37m\] '
#PS1='\[\e[1;37m\]\@\e[m\] \[\e[0;33m\]\u\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[1;32m\]\$ \[\e[m\]'

##################
#users and groups#
##################

uinf(){
echo "current directory="`pwd`;
echo "you are="`whoami`
echo "groups in="`id -n -G`;
tree -L 1 -h $HOME;
echo "terminal="`tty`;
}

#################
#search and find#
#################

alias ww="which"

#search and grep
g(){
cat $1|grep $2
}

#find
ff(){ 
find . -name $@ -print;
}

######################
#directory navigation#
###################### 

alias c="cd"
alias u="cd .."
alias cdt="cd $1&&tree -L 3 -h"
alias c-="cd -"

##ls when cd 
cd(){
if [ -n "$1" ]; then
    builtin cd "$@"&&ls -la --color=auto
  else
    builtin cd ~&&ls -la --color=auto
  fi
}

#######################
#directory information#
#######################

alias du="du -h"
alias ds="du -h|sort -n"
alias dusk="du -s -k -c *| sort -rn"
alias dush="du -s -k -c -h *| sort -rn"
alias t3="tree -L 3 -h"
alias t="tree"
alias dir="dir --color=auto"

#ls
alias ls="ls --color=auto"
alias ll="ls -l"
alias l="ls -CF"
alias la="ls -la"
alias li="ls -ai1|sort"         # sort by index number
alias lt="ls -alt|head -20"     # 20, all, long listing, modification time 
alias lh="ls -Al"               # show hidden files
alias lx="ls -lXB"              # sort by extension
alias lk="ls -lSr"              # sort by size
alias lss="ls -shAxSr"          # sort by size
alias lc="ls -lcr"              # sort by change time
alias lu="ls -lur"              # sort by access time
alias ld="ls -ltr"              # sort by date
alias lm="ls -al|more"          # pipe through ‘more’
alias lsam="ls -am"             # List files horizontally
alias lr="ls -lR"               # recursive
alias lsx="ls -ax"              # sort right to left rather then in columns
alias lh="ls -lAtrh"            # sort by date and human readable

#top10 largest in directory
t10(){
pwd&&du -ab $1|sort -n -r|head -n 10
}

#top10 apparent size 
t10a(){
pwd&&du -ab --apparent-size $1|sort -n -r|head -n 10
}

#dsz - finds directory sizes and lists them for the current directory
dsz (){
du -shx * .[a-zA-Z0-9_]* 2> /dev/null | \
egrep '^ *[0-9.]*[MG]' | sort -n > /tmp/list
egrep '^ *[0-9.]*M' /tmp/list
egrep '^ *[0-9.]*G' /tmp/list
rm /tmp/list
}

#################################
#file and directory manipulation#
#################################
 
alias n="nano"
alias rm="rm -i"
alias cp="cp -i"
alias mv="mv -i"
alias dclr="find . -maxdepth 1 -type f -exec rm {} \;" #clean out directory,leaving intact


#remove from startup but keep init script handy 
sym(){
update-rc.d -f $1 remove
}

#force directory rm
rmd(){
rm -fr $@;
}

#makes a directory, then changes into it
#mkcd (){
#mkdir -p $1&& cd $1
#} 

# makes directory($1), and moves file in current (pwd+$2) to new directory and changes to new directory
mkcd(){
THIS=`pwd`
mkdir -p $1&&mv $THIS/$2 $1&&cd $1
}

#changes to the parent directory, then removes the one you were just in.
cdrm(){
THIS=`pwd`
cd ..
rmd $THIS
}

##########
#archives#
##########

# Extract files from any archive
ex () {
if [ -f $1 ] ; then
case $1 in
*.tar.bz2) tar xjf $1 ;;
*.tar.gz) tar xzf $1 ;;
*.bz2) bunzip2 $1 ;;
*.rar) rar x $1 ;;
*.gz) gunzip $1 ;;
*.tar) tar xf $1 ;;
*.tbz2) tar xjf $1 ;;
*.tgz) tar xzf $1 ;;
*.zip) unzip $1 ;;
*.Z) uncompress $1 ;;
*.7z) 7z x $1 ;;
*) echo "'$1' cannot be extracted via extract()" ;;
esac
else
echo "'$1' is not a valid file"
fi
}

#######################
#processes and sysinfo#
#######################

alias fr="free -otm"
alias d="df"
alias df="df -h"
alias h="htop"
alias pst="pstree"
alias psx="ps auxw|grep $1"
alias pss="ps --context ax"
alias psu="ps -eo pcpu -o pid -o command -o user|sort -nr|head"
alias cpuu="ps -e -o pcpu,cpu,nice,state,cputime,args --sort pcpu | sed '/^ 0.0 /d'"
alias memu='ps -e -o rss=,args= | sort -b -k1,1n | pr -TW$COLUMNS'
alias ducks='ls -A | grep -v -e '\''^\.\.$'\'' |xargs -i du -ks {} |sort -rn |head -16 | awk '\''{print $2}'\'' | xargs -i du -hs {}' # useful alias to browse your filesystem for heavy usage quickly

#system roundup
sys(){
if [ `id -u` -ne  0 ]; then  echo "you are not root"&&exit;fi;
uname -a
echo "runlevel" `runlevel` 
uptime
last|head -n 5;
who;
echo "============= CPUs ============="
grep "model name" /proc/cpuinfo #show CPU(s) info
cat /proc/cpuinfo | grep 'cpu MHz'
echo ">>>>>current process"
pstree
echo "============= MEM ============="
#KiB=`grep MemTotal /proc/meminfo | tr -s ' ' | cut -d' ' -f2`
#MiB=`expr $KiB / 1024`
#note various mem not accounted for, so round to appropriate sizeround=32
#echo "`expr \( \( $MiB / $round \) + 1 \) \* $round` MiB"
free -otm;
echo "============ NETWORK ============"
ip link show
/sbin/ifconfig | awk /'inet addr/ {print $2}'
/sbin/ifconfig | awk /'Bcast/ {print $3}'
/sbin/ifconfig | awk /'inet addr/ {print $4}'
/sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'
echo "============= DISKS =============";
df -h;
echo "============= MISC =============="
echo "==<kernel modules>=="
lsmod|column -t|awk '{print $1}';
echo "=======<pci>========"
lspci -tv;
echo "=======<usb>======="
lsusb;
}

#readable df
dfh(){
df -PTah $@
}

#Locate processes
function pspot () { 
echo  `ps auxww | grep $1 | grep -v grep`
}

#Nuke processes
function pk () {
   killing=`ps auxww | grep $1 | grep -v grep |  cut -c10-16`
   echo "Killing $killing"
   kill -9 $killing 
}

#########
#network#
#########

alias d.="sudo ifdown eth0"
alias u.="sudo ifup eth0"
alias if.="sudo iftop -Pp -i eth0"
alias i.="ifconfig"
alias r.="route"
alias ipt.="sudo iptstate -l -1"
alias iptq.="sudo iptstate -l -1|grep $1"
alias n1.='netstat -tua'
alias n2.="netstat -alnp --protocol=inet|grep -v CLOSE_WAIT|cut -c-6,21-94|tail"
alias n3.='watch --interval=2 "sudo netstat -apn -l -A inet"'
alias n4.='watch --interval=2 "sudo netstat -anp --inet --inet6"'  
alias n5.='sudo lsof -i'
alias n6.='watch --interval=2 "sudo netstat -p -e --inet --numeric-hosts"'
alias n7.='watch --interval=2 "sudo netstat -tulpan"'
alias n8.='sudo netstat -tulpan'
alias n9.='watch --interval=2 "sudo netstat -utapen"'
alias n10.='watch --interval=2 "sudo netstat -ano -l -A inet"'
alias n11.='netstat -an | sed -n "1,/Active UNIX domain sockets/ p" | more'

#network information
ni.(){
echo "--------------- Network Information ---------------"
/sbin/ifconfig | awk /'inet addr/ {print $2}'
/sbin/ifconfig | awk /'Bcast/ {print $3}'
/sbin/ifconfig | awk /'inet addr/ {print $4}'
/sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'
echo "---------------------------------------------------"
}

#####
#apt#
#####

alias update="sudo apt-get update"
alias upgrade="sudo apt-get update&&sudo apt-get dist-upgrade"
alias apt="sudo apt-get install"
alias remove="sudo apt-get autoremove"
alias search="apt-cache search"

######
#misc#
######

alias .a="nano ~/.bash_alias" #personal shortcut for editing aliases
alias .a2="kwrite ~/.bash_alias&"
alias .x="xset dpms force off" # turns off lcd screen
alias .mpd="synclient TouchpadOff=1"
alias .mpu="synclient TouchpadOff=0"

#2nd life
2l(){
esd&
~/SL/SecondLife_i686_1_20_14_92115_RELEASECANDIDATE/secondlife
}

#email sort from text e.g. webpage source html 
address(){
cat $1|grep $2|perl -wne'while(/[\w\.\-]+@[\w\.\-]+\w+/g){print "$&\n"}'| sort -u > address.txt
} 

#parse links from html LINKS is a perl script 
#or ?
#remove most HTML tags (accommodates multiple-line tags)
#sed -e :a -e 's/<[^>]*>//g;/</N;//ba'
links(){
links $1|sort -u>>./parsedlinks.txt
}

#analyze your bash usage
check(){
cut -f1 -d" " .bash_history | sort | uniq -c | sort -nr | head -n 30
}

# clock - A bash clock that can run in your terminal window. 
clock (){ 
while true;do clear;echo "===========";date +"%r";echo "===========";sleep 1;done 
}

#Welcome Screen#
clear
echo -ne "${GREEN}" "Hello, $USER. today is, "; date
echo -e "${WHITE}"; cal;  
echo -ne "${CYAN}";
echo -ne "${BRIGHT_VIOLET}Sysinfo:";uptime ;echo ""
##

# Define a word - USAGE: define dog
define (){
lynx -dump "http://www.google.com/search?hl=en&q=define%3A+${1}&btnG=Google+Search" | 
grep -m 3 -w "*"  | sed 's/;/ -/g' | cut -d- -f1 > /tmp/templookup.txt
			if [[ -s  /tmp/templookup.txt ]] ;then	
				until ! read response
					do
					echo "${response}"
					done < /tmp/templookup.txt
				else
					echo "Sorry $USER, I can't find the term 
\"${1} \""				
			fi	
\rm -f /tmp/templookup.txt
}

#py template
py(){
  echo -e '#!/usr/bin/python\n# -*- coding: UTF-8 -*-\n#\n#\n'>$1.py
  chmod +x $1.py
  nano $1.py
}






















##################################################################################
#to be determined#
# regex for email?  
#  ^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,6}$
# regex for httpaddresses?
#  /<a\s[^>]*href=(\"??)([^\" >]*?)\\1[^>]*>(.*)<\/a>/siU
#  /<a\s[^>]*href\s*=\s*(\"??)([^\" >]*?)\\1[^>]*>(.*)<\/a>/siU
#
#lcfiles - Lowercase all files in the current directory
#lcfiles() {
#read -p "Really lowercase all files? (y/n)"
#[$REPLY=="y"]||exit
#for i in *
#do mv $i $i:l
#echo "done";
#fi

#alias lup='/etc/rc.d/lighttpd start'
#alias lup.='/etc/rc.d/lighttpd restart'
#alias t3="tree"
#PS1='[\d \u@\h:\w]'
#PS1='[\u@\h \W]\$ '
#PS1="\[\033[1;30m\][\[\033[1;34m\]\u\[\033[1;30m\]@\[\033[0;35m\]\h\[\033[1;30m\]]\[\033[0;37m\]\W \[\033[1;30m\]\$\[\033[0m\]"
#cool colors for manpages
#alias man="TERMINFO=~/.terminfo TERM=mostlike LESS=C PAGER=less man"
#alias sl="/home/wind/SL/SL/secondlife"

# Compress the cd, ls -l series of commands.
#alias lc="cl"
#function cl () {
#   if [ $# = 0 ]; then
#      cd && ll
#   else
#      cd "$*" && ll
#   fi
#}

#readln prompt default
#
#function readln () {
#	if [ "$DEFAULT" = "-d" ]; then
#		echo "$1"
#		ans=$2
#	else
#		echo -n "$1"
#		IFS='@' read ans </dev/tty || exit 1
#		[ -z "$ans" ] && ans=$2
#	fi
#}


#[http://seanp2k.com/?p=13](http://seanp2k.com/?p=13)
#It’s for running scp with preset variables, you could maybe make a few of 
#these for different servers you use scp to send files to, again a big 
#time-saver.
#    function sshcp {
#    #ssh cp function by seanp2k
#    FNAME=$1
#    #the name of the file or files you want to copy
#    PORTNUM=”22&#8243;
#    #the port number for ssh, usually 22
#    HOSTNAM=”192.168.1.1&#8243;
#    #the host name or IP you are trying to ssh into
#    if [ $2 ]
#    then
#    RFNAME=”:$2&#8243;
#    else
#    RFNAME=”:”
#    fi
#    #if you specify a second argument, i.e. sshcp foo.tar blah.tar,
#    #it will take foo.tar locally and copy it to remote file bar.tar
#    #otherwise, just use the input filename
#    USRNAME=”root”
#    #you should never allow root login via ssh, so change this username
#
#    scp -P “$PORTNUM” “$FNAME” “$USRNAME@$HOSTNAM$RFNAME”
#
#    }

#[http://seanp2k.com/?p=13](http://seanp2k.com/?p=13)
#searches through the text of all the files in your current directory. #Very useful for, say, debugging a PHP script you didn’t write and can’t #trackdown where that damn MySQL connect string actually is.
#function grip {
#grep -ir “$1&#8243; “$PWD”
#}

##top10 again *only produces one line still needs work 
#t10(){
#du -ks $1|sort -n -r|head -n 10
#}


#found but not yet tested 
#
#################
### FUNCTIONS ###
#################
#
#function    ff               { find . -name $@ -print; }
#

#function    osr              { shutdown -r now; }
#function    osh              { shutdown -h now; }

#function    mfloppy          { mount /dev/fd0 /mnt/floppy; }
#function    umfloppy         { umount /mnt/floppy; }

#function    mdvd             { mount -t iso9660 -o ro /dev/dvd /mnt/dvd; }
#function    umdvd            { umount /mnt/dvd; }

#function    mcdrom           { mount -t iso9660 -o ro /dev/cdrom /mnt/cdrom; }
#function    umcdrom          { umount /mnt/cdrom; }

#function    psa              { ps aux $@; }
#function    psu              { ps  ux $@; }

#function    dub              { du -sclb $@; }
#function    duk              { du -sclk $@; }
#function    dum              { du -sclm $@; }

#function    dfk              { df -PTak $@; }
#function    dfm              { df -PTam $@; }

#function    dfi              { df -PTai $@; }

#copy and go to dir
#cpg (){
#  if [ -d "$2" ];then
#    cp $1 $2 && cd $2
#  else
#    cp $1 $2
#  fi
#}

#move and go to dir
#mvg (){
#  if [ -d "$2" ];then
#    mv $1 $2 && cd $2
#  else
#    mv $1 $2
#  fi

---

### Post by kaiju on 2008-08-23
tres cool!

> **AndEat said:**
> 
alias .a="nano ~/.bash_alias" #personal shortcut for editing aliases


you could add source to update your aliases right after closing nano, without having to restart bash: '$EDITOR ~/.bash_aliases && source ~/.bash_aliases'

---

### Post by BryanFRitt on 2009-02-08
> **kaiju said:**
> while aliases can't take variables, functions sure can. since i liked the idea, and it seemed to be good exercise for a beginner like me, here it is:
```
miso()#mount iso file
{
_mountpoint=/home/weirdo/iso
if [ -z $1 ]; then
  echo -e "usage:\tmiso file.iso\n\tmiso -u"
elif [ $1 = "-u" ]; then
  sudo umount $_mountpoint && echo "$_mountpoint unmounted."
elif [ -r $1 ] && [ ! -z `echo $1 | grep -i .iso$` ]; then
  if [ `ls $_mountpoint | wc -w` -ne 0 ]; then
    echo "error: $_mountpoint is not empty."
  else
    sudo mount -o loop $1 $_mountpoint && echo "'$1' mounted to $_mountpoint."
  fi
else
  echo "error: '$1' is not a readable iso file."
fi
}
```

shell functions can be specified right inside the ~/.bashrc file. there are a few really useful ones in this thread :)

I tried this with a filename that has spaces (miso "My File Name with spaces and with or without Path in quotes.iso") and get 
[I]bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
error: 'My File Name with spaces and with or without Path in quotes.iso' is not a readable iso file.[/I]

It did work with my File that didn't have any spaces in it's name and path, rather or not I used quotes.

p.s. I changed "/home/weirdo/iso" to "/Drives/Mounted_iso/Default"

---

### Post by yabbadabbadont on 2009-02-08
> **BryanFRitt said:**
> I tried this with a filename that has spaces (miso "My File Name with spaces and with or without Path in quotes.iso") and get 
[I]bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
error: 'My File Name with spaces and with or without Path in quotes.iso' is not a readable iso file.[/I]

It did work with my File that didn't have any spaces in it's name and path, rather or not I used quotes.

p.s. I changed "/home/weirdo/iso" to "/Drives/Mounted_iso/Default"

Put quotes around all instances of $1

Edit: Except for the last one as it is already quoted.

---

### Post by phaed on 2009-02-10
Is there a way to make your bash prompt and any text that you type after it a different color?  When using bash, I'll often get a lot of text back and it's hard to find where it starts (at the last prompt).  It would be useful to color the prompts.

---

### Post by yabbadabbadont on 2009-02-10
> **phaed said:**
> Is there a way to make your bash prompt and any text that you type after it a different color?  When using bash, I'll often get a lot of text back and it's hard to find where it starts (at the last prompt).  It would be useful to color the prompts.

Yes.  It involves sending a terminal control sequence using "\[" as part of your PS1 prompt variable.  The actual sequence that has to be sent varies depending upon the actual terminal that is being used (console/xterm/gnome-terminal/etc), but I think most use the same escape sequences for setting the colors.  Search google for "color bash prompt" and you will find several guides on how to do it.

---

### Post by BryanFRitt on 2009-02-10
> **yabbadabbadont said:**
> Put quotes around all instances of $1

Edit: Except for the last one as it is already quoted.

did that, still getting the last error

error: 'My File Name with spaces and with or without Path in quotes.iso' is not a readable iso file.

double quotes (",") worked for names without spaces, but single quotes (',') didn't even work for that.
```
miso()#mount iso file
{
_mountpoint="/Drives/Mounted_iso/Default"
if [ -z "$1" ]; then
  echo -e "usage:\tmiso file.iso\n\tmiso -u"
elif [ "$1" = "-u" ]; then
  sudo umount $_mountpoint && echo "$_mountpoint unmounted."
elif [ -r "$1" ] && [ ! -z `echo "$1" | grep -i .iso$` ]; then
  if [ `ls $_mountpoint | wc -w` -ne 0 ]; then
    echo "error: $_mountpoint is not empty."
  else
    sudo mount -o loop "$1" $_mountpoint && echo "'$1' mounted to $_mountpoint."
  fi
else
  echo "error: '$1' is not a readable iso file."
fi
}
```Seems like it's this line that causes the error:
```
elif [ -r "$1" ] && [ ! -z `echo "$1" | grep -i .iso$` ]; then
```

---

### Post by kaiju on 2009-02-16
> **BryanFRitt said:**
> did that, still getting the last error

error: 'My File Name with spaces and with or without Path in quotes.iso' is not a readable iso file.

In order to make the shell treat spaces as non-separating characters, you can set the internal field separator to newline, just make sure you reset it to the original value before the process exits (very important if used in a bash function).

```

# save the original IFS
_ifs=$IFS
# change the value to newline
IFS='
'
### rest
### of
### the
### script
# reset IFS to the original value
IFS=$_ifs

```

Note: To unset the variables that were used in a shell function, you can use unset -v VARIABLE (without the leading '$'), so that the variables don't clutter up the environment and are recreated every time the function is run, just as if it were a normal script.

---

### Post by BryanFRitt on 2009-02-17
> **kaiju said:**
> In order to make the shell treat spaces as non-separating characters, you can set the internal field separator to newline, just make sure you reset it to the original value before the process exits (very important if used in a bash function).

```

# save the original IFS
_ifs=$IFS
# change the value to newline
IFS='
'
### rest
### of
### the
### script
# reset IFS to the original value
IFS=$_ifs

```

Note: To unset the variables that were used in a shell function, you can use unset -v VARIABLE (without the leading '$'), so that the variables don't clutter up the environment and are recreated every time the function is run, just as if it were a normal script.

I tried that an it didn't work.  However, I did try getting rid of the line(s) that I thought were causing the problem and it worked.  What did that line do?  Was it just a check to see if the file ended in .iso, or did it do anything else?  Anybody know if this will this cause any problems?

---

### Post by BryanFRitt on 2009-02-17
Here's a version without the line that I thought was causing the problem.
Seams to work for me. Anybody see any problems, or better ways to do this?
```
miso() #mount iso file
{
_mountpoint="/Drives/Mounted_iso/Default"
if [ -z "$1" ]; then
  echo -e "usage:\tmiso file.iso\n\tmiso -u"
elif [ "$1" = "-u" ]; then
  sudo umount $_mountpoint && echo "$_mountpoint unmounted."
else
  if [ `ls $_mountpoint | wc -w` -ne 0 ]; then
    echo "error: $_mountpoint is not empty."
  else
    sudo mount -o loop "$1" $_mountpoint && echo "'$1' mounted to $_mountpoint."
  fi
fi
}
```

---

### Post by adamlau on 2009-02-17
```
eval `dircolors -b`

PS1='\[\e[0;00m\]\u\[\e[m\] \[\e[0;00m\]\w\[\e[m\] \[\e[1;32m\]\$\[\e[0;00m\] '

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

---

### Post by kaiju on 2009-02-27
> **BryanFRitt said:**
> [...] What did that line do?  Was it just a check to see if the file ended in .iso, or did it do anything else?

short answer: it should check whether '$1' is a readable with its file name ending in '.iso' (or .ISO, .Iso, etc.)


elif [ -r "$1" ] && [ ! -z `echo "$1" | grep -i .iso$` ]; then

"elif" and "; then": part of the if-then-else logic
"[ -r $1 ]": true if '$1' is a readable file; just to avoid passing mistyped words
"`echo "$1" | grep -i .iso$`": true if the file name has '.iso' at the end ($), case-insensitively (grep -i); to avoid passing anything but iso files
"[ ! -z `TEST` ]": true if the string returned by `TEST` is non-zero (that will mean that grep found the file name to be ending with '.iso')

i suspect the problem to have been caused by the latter part - with the string returned by grep, '[ ! -z File Name With Spaces.iso ]' will error out
this can probably be circumvented by enclosing the `TEST` part within double quotes

then again, this whole part might not be necessary at all, i just like doing tests to make sure my scripts return somewhat informative error messages

---

### Post by kaiju on 2009-02-27
> **adamlau said:**
> ```
PS1='\[\e[0;00m\]\u\[\e[m\] \[\e[0;00m\]\w\[\e[m\] \[\e[1;32m\]\$\[\e[0;00m\] '
```

expanding on this and another version that gives a different color if you're root, i have

```

# set prompt
if [ "$SSH_CONNECTION" ]; then # grey ssh connection
  PS1='\[\033[01;30m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\W\[\033[00m\]\$ '
elif [ $(id -u) -eq 0 ]; then # red root
  PS1='\[\033[01;31m\]\u\[\033[00m\]:\[\033[01;35m\]\W\[\033[00m\]\$ '
else # green regular user
  PS1='\[\033[01;32m\]\u\[\033[00m\]:\[\033[01;34m\]\W\[\033[00m\]\$ '
fi

```

$SSH_CONNECTION will only be set if bash is running in an ssh client, so its value can be used to detect an ssh session
the root part will only work if we're using the root account with sudo (e.g. 'sudo -s' or 'sudo bash'); using su will lead to /root/.bashrc being sourced instead of the current ~/.bashrc

i didn't yet figure out how to test for the case when i'm both logged in through ssh and using the root account, so that i can have a red \u@\h:\W for the prompt, instead of the plain \u:\W
any ideas anyone?

---

### Post by BryanFRitt on 2009-03-02
Thanks kaiju
That fixed it!
and now I also modified the code to accept a mountpoint that has spaces in them.
```
miso() # mount iso file
{
_mountpoint="/Drives/Mounted_iso/Default"
if [ -z "$1" ]; then
  echo "usage:"
  echo "  miso file.iso to   mount FILE.iso at   '$_mountpoint'"
  echo "  miso -u       to unmount FILE.iso from '$_mountpoint'"
  echo "  Where FILE.iso is the name, or path and name, of the iso file to mount"
elif [ "$1" = "-u" ]; then
  sudo umount "$_mountpoint"
  echo "'$_mountpoint' unmounted."
# if you don't want to verify if the file name ends in a .iso 
# (case insensitive, -i) remove
# && [ ! -z "`echo "$1" | grep -i .iso$`" ]
elif [ -r "$1" ] && [ ! -z "`echo "$1" | grep -i .iso$`" ]; then
  if [ `ls "$_mountpoint" | wc -w` -ne 0 ]; then
    echo -e "error: '$_mountpoint' is not empty, \ntry miso -u to unmount it"
  else
    sudo mount -o loop "$1" "$_mountpoint" 
    echo -e "'$1'\n  is mounted at\n'$_mountpoint'"
  fi
else
  echo "error: '$1' is not a readable *.iso file."
fi
}
```

---

### Post by kaiju on 2009-03-02
a way to quickly list, view, edit and source a ~/.bash_functions file
of course it will only work with an editor that will take +N FILENAME to mean that we want to open FILENAME at line N (nano and vim work fine)
```

func(){ #view and edit ~/.bash_functions
if [ "$1" = "ed" ]; then
  _LINEN=`grep -n ^${2}.*\(\)\{\ \# ~/.bash_functions | head -n 1 | sed 's/:.*//'`
  $EDITOR +${_LINEN} ~/.bash_functions
  source ~/.bash_functions && echo "info: ~/.bash_functions sourced"
elif [ "$1" = "ls" ]; then
  less ~/.bash_functions
else
  grep \(\)\{\ \# ~/.bash_functions | sed -e 's/(){//' -e 's/ #/ - /' | sort
fi
unset -v _LINEN
}

```
as you can see from the grep line, the pattern searching part is tuned to the format of the first line - that line is used to find out where a given function starts (for jumping to the first function that matches $2 when editing) and also to provide a quick description (for when we're just listing the functions contained in the file)

---

### Post by k2t0f12d on 2009-03-02
**~/.bashrc**```
alias ls='ls --color=auto'
PROMPT_COMMAND="source /etc/profile.d/color-prompt.inc"
```**/etc/profile.d/color-prompt.inc**```
## -*-shell-script-*-

## FILE /etc/profile.d/color-prompt.inc
#
# implement a function that will randomly colorize
# individual characters in a bash prompt
#

## COPYING
#
# color-prompt is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or (at your
# option) any later version.
#
# color-prompt is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
# or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for
# more details.
#
# You should have received a copy of the GNU General Public License along with
# color-prompt.  If not, see <http://www.gnu.org/licenses/>.
#
## END COPYING

## INCLUDED FILES
#

#
## END INCLUDED FILES

## MAIN color-prompt
#
# randomly colorize individual characters in a bash prompt
#

#printf "debug: entering color_prompt.inc\n"

index=$(( ${#USER} - 1 ))
colorized_name=""
brightness=
hue=
last_hue=
dir=
i="0"

while test "$i" -le "$index"; do

	brightness=$RANDOM
	let "brightness %= 2"

	hue="0"

	# shuffle colours..don't repeat and don't pick black
	while test "$hue" -eq "0" || \
	      test "$hue" = "$last_hue"; do
		hue=$RANDOM
		let "hue %= 8"
	done

	this_color="\[\e[${brightness};3${hue}m\]"

	last_hue="$hue"

	if test -z "$colorized_name"; then
		colorized_name="${this_color}${USER:${i}:1}"
	else
		colorized_name="${colorized_name}${this_color}${USER:${i}:1}"
	fi

	i="$(( $i + 1 ))"

done

tput sgr0

if test "$PWD" = "/home/${USER}"; then
	dir="~"
else
	dir=$(basename "$PWD")
fi

export PS1="[${colorized_name}\[$(tput sgr0)\]@${HOSTNAME} ${dir}]$ "

unset index colorized_name brightness hue last_hue dir i

#
#
#
## END OF FILE /etc/profile.d/color-prompt.inc
```

---

### Post by WhiskyChris on 2009-03-03
Hi all,

I've just been modifying my default out-of-the-box .bashrc with some of the suggestions above and seem to have messed something up so that when I type a command of a certain length, instead of looping onto a new line it overtypes what I've just written... It only does this once, if I keep on typing then (what should be the 3rd line) loops onto line 2.

Any ideas what I've done? See my .bashrc below:

```
## Chris's ~/.bashrc

# Define a few Colours
BLACK='\e[0;30m'
BLUE='\e[0;34m'
GREEN='\e[0;32m'
CYAN='\e[0;36m'
RED='\e[0;31m'
PURPLE='\e[0;35m'
BROWN='\e[0;33m'
LIGHTGRAY='\e[0;37m'
DARKGRAY='\e[1;30m'
LIGHTBLUE='\e[1;34m'
LIGHTGREEN='\e[1;32m'
LIGHTCYAN='\e[1;36m'
LIGHTRED='\e[1;31m'
LIGHTPURPLE='\e[1;35m'
YELLOW='\e[1;33m'
WHITE='\e[1;37m'
NC='\e[0m'              # No Color

## Some Basics
export HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
export HISTCONTROL=ignoreboth
shopt -s histappend
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"


## Setup Prompt
PS1="${BLUE}(${RED}\W${BLUE}) ${NORMAL}\h ${RED}\$ ${NC}"


# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"

    ;;
*)
    ;;
esac


# Aliases
alias ls='ls --color=auto'
alias ll='ls -l --color=auto'
alias la='ls -A --color=auto'
alias l='ls -CF --color=auto'
alias ..='cd ..'
alias gerp='grep --color=auto'
alias del='rm --target-directory=$HOME/.Trash/'

# Bash Completion
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# Functions
extract () {
	if [ -f $1 ] ; then
		case $1 in
			*.tar.bz2)	tar xjf $1		;;
			*.tar.gz)	tar xzf $1		;;
			*.bz2)		bunzip2 $1		;;
			*.rar)		rar x $1		;;
			*.gz)		gunzip $1		;;
			*.tar)		tar xf $1		;;
			*.tbz2)		tar xjf $1		;;
			*.tgz)		tar xzf $1		;;
			*.zip)		unzip $1		;;
			*.Z)		uncompress $1	;;
			*)		echo "'$1' cannot be extracted via extract()" ;;
		esac
	else
		echo "'$1' is not a valid file"
	fi
}


# WELCOME SCREEN
################################################## #####

clear

echo -ne "${LIGHTBLUE}" "Hello, $USER. Today is, "; date
echo -e "${BLACK}"; cal -3;
#echo -ne "${CYAN}";
```

---

### Post by dbbolton on 2009-03-03
Here's mine :guitar:

```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

#dbbolton

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

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
#case "$TERM" in
#xterm-color)
#    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#    ;;
#*)
#    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
#    ;;
#esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

PS1='${debian_chroot:+($debian_chroot)}\[\033[0;38;5;32m\][\[\033[0;38;5;202m\] \w \[\033[0;38;5;32m\]]\[\033[00m\] '

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
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

alias install='sudo aptitude install'
alias ntrgn='nitrogen --sort=alpha /home/daniel/Images/Wallpaper'
alias up='cd ..'
alias update='sudo aptitude update'
alias upgrade='sudo aptitude safe-upgrade'
alias gmail='/home/daniel/bin/Scripts/checkgmail'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```

---

### Post by KIAaze on 2009-03-04
> **WhiskyChris said:**
> Hi all,

I've just been modifying my default out-of-the-box .bashrc with some of the suggestions above and seem to have messed something up so that when I type a command of a certain length, instead of looping onto a new line it overtypes what I've just written... It only does this once, if I keep on typing then (what should be the 3rd line) loops onto line 2.

Any ideas what I've done? See my .bashrc below:


I had the same problem once.
It's because you didn't use the '\[' and '\]' to indicate beginning and end of a sequence of non-printing characters.

Here's a fixed version of your .bashrc:
```
## Chris's ~/.bashrc

# Define a few Colours for PS1
BLACK='\[\e[0;30m\]'
BLUE='\[\e[0;34m\]'
GREEN='\[\e[0;32m\]'
CYAN='\[\e[0;36m\]'
RED='\[\e[0;31m\]'
PURPLE='\[\e[0;35m\]'
BROWN='\[\e[0;33m\]'
LIGHTGRAY='\[\e[0;37m\]'
DARKGRAY='\[\e[1;30m\]'
LIGHTBLUE='\[\e[1;34m\]'
LIGHTGREEN='\[\e[1;32m\]'
LIGHTCYAN='\[\e[1;36m\]'
LIGHTRED='\[\e[1;31m\]'
LIGHTPURPLE='\[\e[1;35m\]'
YELLOW='\[\e[1;33m\]'
WHITE='\[\e[1;37m\]'
NC='\[\e[0m\]'              # No Color

# Define a few Colours for echo
_BLACK='\e[0;30m'
_BLUE='\e[0;34m'
_GREEN='\e[0;32m'
_CYAN='\e[0;36m'
_RED='\e[0;31m'
_PURPLE='\e[0;35m'
_BROWN='\e[0;33m'
_LIGHTGRAY='\e[0;37m'
_DARKGRAY='\e[1;30m'
_LIGHTBLUE='\e[1;34m'
_LIGHTGREEN='\e[1;32m'
_LIGHTCYAN='\e[1;36m'
_LIGHTRED='\e[1;31m'
_LIGHTPURPLE='\e[1;35m'
_YELLOW='\e[1;33m'
_WHITE='\e[1;37m'
_NC='\e[0m'              # No Color

## Some Basics
export HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
export HISTCONTROL=ignoreboth
shopt -s histappend
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"


## Setup Prompt
PS1="${BLUE}(${RED}\W${BLUE}) ${NORMAL}\h ${RED}\$ ${NC}"


# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"

    ;;
*)
    ;;
esac


# Aliases
alias ls='ls --color=auto'
alias ll='ls -l --color=auto'
alias la='ls -A --color=auto'
alias l='ls -CF --color=auto'
alias ..='cd ..'
alias gerp='grep --color=auto'
alias del='rm --target-directory=$HOME/.Trash/'

# Bash Completion
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# Functions
extract () {
	if [ -f $1 ] ; then
		case $1 in
			*.tar.bz2)	tar xjf $1		;;
			*.tar.gz)	tar xzf $1		;;
			*.bz2)		bunzip2 $1		;;
			*.rar)		rar x $1		;;
			*.gz)		gunzip $1		;;
			*.tar)		tar xf $1		;;
			*.tbz2)		tar xjf $1		;;
			*.tgz)		tar xzf $1		;;
			*.zip)		unzip $1		;;
			*.Z)		uncompress $1	;;
			*)		echo "'$1' cannot be extracted via extract()" ;;
		esac
	else
		echo "'$1' is not a valid file"
	fi
}


# WELCOME SCREEN
################################################## #####

clear

echo -ne "${_LIGHTBLUE}" "Hello, $USER. Today is, "; date
echo -e "${_BLACK}"; cal -3;
#echo -ne "${_CYAN}";

```

I had to add other color commands for the echo command because otherwise it displays '\[\]' for each color command.
There may be a better way to do this like using several echo commands, but this works. :)

---

### Post by WhiskyChris on 2009-03-04
Thanks for your help KIAaze, works nicely now!

---

### Post by bodhi.zazen on 2009-03-04
Nice to see this thread getting some traffic.

[KIAaze]("http://ubuntuforums.org/member.php?u=240158"): you hit the nail on the head , very nice solution as well. I am going to add that to my blog and .bashrc.

See this page, look at the most recent comments at the bottom :

[http://blog.bodhizazen.net/linux/shared-terminal-sessions-over-ssh/](http://blog.bodhizazen.net/linux/shared-terminal-sessions-over-ssh/)

---

### Post by ranthal on 2009-05-01
After a long time of intending to sit down and create a nice bashrc for myself I finally sat down today and went through this thread to do it.  It's still a work in progress so I'm still not quite posting the full thing, however, I really liked the netinfo function in urukrama's 1st post but wanted to make it more readable so I'm posting that.  I hadn't worked much with awk so I used this as a nice little primer and also tried to brush up on my bash scripting.  Here it is:

```
netinfo()
{
n=1     # Placeholder

# Grab ethernet interface
for x in $(ifconfig | awk '/eth/ {print $1}')
do
    eth[n]=$x
    let "n += 1"
done

# Grab HW address
let "n = 1"
for x in $(ifconfig | awk '/eth/ {print $5}')
do
    hwAddr[n]=$x
    let "n += 1"
done

# Grab IP address
let "n = 1"
for x in $(ifconfig | awk '/inet addr/ {print $2}')
do
    y=$(echo $x | awk -F : '{print $2}')
    ipAddr[n]=$y
    let "n += 1"
done

# Grab broadcast address
let "n = 1"
for x in $(ifconfig | awk '/Bcast/ {print $3}')
do
    y=$(echo $x | awk -F : '{print $2}')
    bAddr[n]=$y
    let "n += 1"
done

# Grab mask
let "n = 1"
for x in $(ifconfig | awk '/Mask/ {print $4}')
do
    y=$(echo $x | awk -F : '{print $2}')
    mask[n]=$y
    let "n += 1"
done

echo "----------- Network Information ---------"
let "n = 1"
echo
for x in ${eth[@]}
do
    echo "Ethernet Interface: ${eth[n]}"
    echo "HW Addr:            ${hwAddr[n]}"
    echo "IP Address:         ${ipAddr[n]}"
    echo "Broadcast Address:  ${bAddr[n]}"
    echo "Mask:               ${mask[n]}"
    echo
    let "n += 1"
done
echo "-----------------------------------------"
}
```

Can you tell I do a lot of C?  Haha

Anyways, I turned a less than 10-liner into around 60 lines and the looping in it is sloppy :-?.  But I'm tired so hopefully by posting it somebody else can improve more on it :lol:

---

### Post by Sublime Porte on 2009-05-02
> alias back='cd $OLDPWD'[FONT=monospace]
This already exists in bash, just type 'cd -' and you'll go back to your previous wd.

For anyone who wants to find some good lines for your bashrc, check out [commandlinefu](http://www.commandlinefu.com/)
[/FONT]

---

### Post by crush304 on 2009-05-02
```
#search through history on C-P , C-N
bind "C-p":history-search-backward
bind "C-n":history-search-forward

```

---

### Post by gorfou on 2009-05-11
Hi!

I manually searched each page of this topic for 'cd' but it seems that few people thought that you could take the 'back' (as an alias of 'cd $OLDPWD') process one step further.

This is my first solution:

```

HISTORY=-1
export HISTORY

HISTORYARRAY[0]=$PWD
export HISTORYARRAY

# aliases
alias cd='HISTORY=$(($HISTORY+1)); HISTORYARRAY[$HISTORY]="$PWD" ;cd'

alias back='if [ $HISTORY -lt 0 ];then echo "cannot go back before initial position";else builtin cd ${HISTORYARRAY[$HISTORY]}; HISTORY=$(($HISTORY-1)); fi'

```

but this solution didn't support spaces in paths. Reading things through  the web gave me this more pleasant solution:

```

alias cd='pushd'
alias back='popd'

```

It would be more user-transparent if names of directories wouldn't appear when changin' directory. This would be resolved by converting it into a function with output redirection, but I prefer remembering that I'm using pushd.

Someone recently suggested me an 'next' but I don't fell like trying to do it now.

---

### Post by BryanFRitt on 2009-05-13
> **Sublime Porte said:**
> [FONT=monospace]
For anyone who wants to find some good lines for your bashrc, check out [commandlinefu](http://www.commandlinefu.com/)
[/FONT]

Thanks for the tip, I've now added this to my *~/.bashrc* file

```
#http://www.commandlinefu.com/commands/browse
#http://www.commandlinefu.com/commands/view/2158/add-timestamp-to-history
#Adds date and time to history
#export HISTTIMEFORMAT="%F %T "
#http://www.linuxquestions.org/questions/linux-general-1/history-333207/
#export HISTTIMEFORMAT='%Y-%b-%d::%Hh:%Mm:%Ss '
#Makes history display in YYYY-MM-DD_HH:MM:SS_3CharWeekdaySpaceSpace format
export HISTTIMEFORMAT="%Y-%m-%d_%H:%M:%S_%a  "
```

```
#http://www.thegeekstuff.com/2008/10/6-awesome-linux-cd-command-hacks-productivity-tip3-for-geeks/
#makes a directory and goes into it
function mkdircd () { mkdir -p "$@" && eval cd "\"\$$#\""; }
```

```
#http://www.thegeekstuff.com/2008/10/6-awesome-linux-cd-command-hacks-productivity-tip3-for-geeks/
#helps with spelling directories
shopt -s cdspell
```

---

### Post by BryanFRitt on 2009-05-13
> **gorfou said:**
> Hi!
Reading things through  the web gave me this more pleasant solution:

```

alias cd='pushd'
alias back='popd'

```

It would be more user-transparent if names of directories wouldn't appear when changin' directory. This would be resolved by converting it into a function with output redirection, but I prefer remembering that I'm using pushd.

Someone recently suggested me an 'next' but I don't fell like trying to do it now.

Here's the code with output redirection. For those who want to get rid the directory names appearing, but still want to use the aliases:
```
alias cd='pushd > /dev/null'
alias back='popd > /dev/null'
```

Some more on pushd, popd, and dirs:
(they did allot more on this than my quick "[FONT="Courier New"]> /dev/null[/FONT]" addition)
[http://www.softpanorama.org/Scripting/Shellorama/pushd_and_popd.shtml](http://www.softpanorama.org/Scripting/Shellorama/pushd_and_popd.shtml)

---

### Post by slydog4 on 2009-05-28
> **crush304 said:**
> ```
#search through history on C-P , C-N
bind &quot;C-p&quot;:history-search-backward
bind &quot;C-n&quot;:history-search-forward

```

Thank you so much!  I have been trying to figure out how to do this.  Ubuntu is the first distro I have used that does not have the PageUp and PageDown keys bound to history-search by default.  I have really become accustomed to such a binding.
 
 ```

 bind '"\e[5~"':history-search-backward
 bind '"\e[6~"':history-search-forward
 
```

---

### Post by m_ad on 2009-05-29
This may be a dumb question, but I'm just starting to learn how to customize using bashrc.


I've managed to modify my prompt using colors, etc., but how do I change the colors of the output of some commands to match my prompt? e.g. ls




EDIT: Aah, are they defined in $HOME/.dir_colors?

---

### Post by KIAaze on 2009-06-02
I've been having a strange behaviour of the cd command for quite some while now and finally found the cause: My .bashrc (which I copied from someone else) contained the following line:
```
export CDPATH=.:$HOME
```

This lead to cd searching through the home directory as well as the current directory when pressing tab multiple times.

In case someone would like such a behaviour, here's more info:
[http://rumour.biology.gatech.edu/Computers/cdpath.shtml](http://rumour.biology.gatech.edu/Computers/cdpath.shtml)

---

### Post by KIAaze on 2009-09-19
I cleaned up my bash files a little bit.
Setting the PATH=something:$PATH in ~/.bashrc is not a good idea, since PATH will keep getting bigger if you launch a new bash from within bash.

So I put all export PATH/LD_LIBRARY_PATH, etc (i.e. all the environment setup) + all private info in ~/.bash_profile. This should also make it easier to use them on other machines: Nothing to change except the contents of ~/.bash_profile (hopefully).

I also split my .bashrc into smaller files for more modularity.

.bashrc
```
# ~/.bashrc

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

##################
#OTHER
##################

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# bash_history settings: size and no duplicates and no lines w/ lead spaces
#exportHISTCONTROL="ignoreboth"
#export HISTSIZE=1024

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

#stop the beep
xset -b

#to stay in the directory visited with mc on exit. :)
source /usr/share/mc/bin/mc.sh

##########################################################

##################
#FUNCTIONS
##################
if [ -f ~/.bash_functions ]; then
    . ~/.bash_functions
fi
##########################################################

##################
#ALIASES
##################
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
##########################################################

##################
#PROMPT
##################
if [ -f ~/.bash_prompt ]; then
    . ~/.bash_prompt
fi
##########################################################

```

.bash_aliases
```
# ~/.bash_aliases

##################
#ALIASES
##################

# OpenFOAM stuff
alias source_openfoam='source $HOME/OpenFOAM/OpenFOAM-1.5/etc/bashrc'
#alias source_openfoam='source $HOME/OpenFOAM/OpenFOAM-1.4.1/.OpenFOAM-1.4.1/bashrc'

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    alias dir='ls --color=auto --format=vertical'
    alias vdir='ls --color=auto --format=long'
fi

# ls aliases
# alias l='ls -CF'
alias la='ls -aA'
alias ll='ls -lhX'
alias laf='ls -laF'
alias lla='ll -a'
alias lrt='ls -lrt'
alias ldir='ls -lhA |grep ^d'
alias lfiles='ls -lhA |grep ^-'
alias lsdot='ls -ld \.[A-Za-z0-9]*'

# To see something coming into ls output: lss
alias lss='ls -lrt | grep $1'

# safety aliases for rm,mv,cp
alias rm='rm -iv'
alias mv='mv -iv'
alias cp='cp -iv' 

# check commands
alias checkcmd='totalnotify.sh "SUCCESS" || ( totalnotify.sh "FAILURE" && false )'
alias mailcmd='mailme "SUCCESS" || mailme "FAILURE" '

# other
alias datefull='date +%Y%m%d_%H%M%S'
alias pmake='make -j$(num_threads)'
# alias h='history'
alias rlogin='slogin -X'
alias astyle_all='astyle *.h *.cpp */*.h */*.cpp'
alias wc_all='wc -l *.h *.cpp */*.h */*.cpp | sort'

# to be able to use aliases under sudo
alias sudo='A=`alias` sudo  '

# rebuild aliases
alias rebuild_all='qmake && make distclean && qmake && make -j$(num_threads) debug release && checkcmd'
alias rebuild_debug='qmake && make distclean && qmake && make -j$(num_threads) debug && checkcmd'
alias rebuild_release='qmake && make distclean && qmake && make -j$(num_threads) release && checkcmd'

#alias git_log_month='echo $1'git log --after="$1 1 2009" --before="Jul 1 2009"
alias profile='valgrind --tool=callgrind --dump-instr=yes --simulate-cache=yes --collect-jumps=yes'
alias git_checkall='git pull && git push && git status'

# plugin testing
# You must have the plugin stuff in a subdirectory named "designer" for this to work
alias test_plugin='export QT_PLUGIN_PATH=$(pwd); designer'

# To check a process is running in a box with a heavy load: pss
alias pss='ps -ef | grep $1'

# usefull alias to browse your filesystem for heavy usage quickly
# alias ducks='ls -A | grep -v -e '\''^\.\.$'\'' |xargs -i du -ks {} |sort -rn |head -16 | awk '\''{print $2}'\'' | xargs -i du -hs {}'
#alias ducks='ls -A | grep -v -e '\''^\.\.$'\'' |xargs -i du -ks {} |sort -rn |head -16 | awk '\''{ all=""; for (i=2; i<=NF; i++) all = $all,$i; print $all;}'\'' | xargs -i du -hs {}'
alias ducks='find . -maxdepth 1 -mindepth 1 -print0  | xargs -0 -n1 du -ks | sort -rn | head -16 | cut -f2 | xargs -i du -hs {}'

# cool colors for manpages
# alias man="TERMINFO=~/.terminfo TERM=mostlike LESS=C PAGER=less man"

# for fun
alias iamcow='fortune | cowsay'
alias iamsurprise='fortune | cowsay -f $(random_cow)'

```
.bash_prompt:
Thanks got to [GepettoBR]("http://ubuntuforums.org/showpost.php?p=7962891&postcount=6708"), [hatten]("http://ubuntuforums.org/showpost.php?p=7967632&postcount=6744") and [ayoli]("http://ubuntuforums.org/showpost.php?p=4403915&postcount=26") for this one. :)

```
# ~/.bash_prompt

#####################################################################################
# PROMPT STYLING
#####################################################################################

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

function funny_face {
  _ret=$?; if test $_ret -ne 0; then echo "0_0->ret=$_ret"; set ?=$_ret; unset _ret; else echo "^_^"; fi
}

function set_command_sound {
  export COMMAND_SOUND=$1
}

play_command_sound()
{
  if [ $COMMAND_SOUND -eq 1 ]
  then
    aplay $SOUNDDIR/Terran/Tank/ttawht00.wav 1>/dev/null 2>&1 &
  fi
}

function pre_prompt {
newRET=$(funny_face)
newPWD=$(pwd | sed "s|$HOME|~|")
user="whoami"
host=$(echo -n $HOSTNAME | sed -e "s/[\.].*//")
datenow=$(date "+%a, %d %b %y")

# play_command_sound

if [ $ANONYMOUS -eq 0 ]
then
  let promptsize=$(echo -n "&#9484;($user@$host ddd., DD mmm YY)($newPWD)&#9488;" | wc -c | tr -d " ")
  let promptsize=$promptsize-3
else
  let promptsize=$(echo -n "&#9484;($newPWD)&#9488;" | wc -c | tr -d " ")
  let promptsize=$promptsize
fi

# echo "<$newPWD>"
# echo promptsize=$promptsize
let fillsize=${COLUMNS}-${promptsize}
# echo fillsize=$fillsize
fill=""
while [ "$fillsize" -gt "0" ]
do 
    fill="${fill}&#9472;"
	let fillsize=${fillsize}-1
done
# echo fill=$fill
if [ "$fillsize" -lt "0" ]
then
    echo "WTF"
    let cutt=3-${fillsize}
    newPWD="...$(echo -n $PWD | sed -e "s/\(^.\{$cutt\}\)\(.*\)/\2/")"
fi

}

export black="\[\033[0;38;5;0m\]"
export red="\[\033[0;38;5;1m\]"
export orange="\[\033[0;38;5;130m\]"
export green="\[\033[0;38;5;2m\]"
export yellow="\[\033[0;38;5;3m\]"
export blue="\[\033[0;38;5;4m\]"
export bblue="\[\033[0;38;5;12m\]"
export magenta="\[\033[0;38;5;55m\]"
export cyan="\[\033[0;38;5;6m\]"
export white="\[\033[0;38;5;7m\]"
export coldblue="\[\033[0;38;5;33m\]"
export smoothblue="\[\033[0;38;5;111m\]"
export iceblue="\[\033[0;38;5;45m\]"
export turqoise="\[\033[0;38;5;50m\]"
export smoothgreen="\[\033[0;38;5;42m\]"

# echo $TERM
load_prompt()
{
 if [ $1 -eq 0 ]
 then
    # non-anonymous prompt
    export ANONYMOUS=0
    PROMPT_COMMAND=pre_prompt
    case "$TERM" in
    xterm)
        PS1="$bblue&#9484;&#9472;($orange\$newPWD$bblue)&#9472;\${fill}&#9472;($orange\u@\h \$(date \"+%a, %d %b %y\")$bblue)&#9472;&#9488;\n$bblue&#9492;&#9472;(\$newRET)(\#)($orange\$(date \"+%H:%M\")$bblue)&#9472;>$white "
        ;;
    screen)
        PS1="$bblue&#9484;&#9472;($orange\$newPWD$bblue)&#9472;\${fill}&#9472;($orange\u@\h \$(date \"+%a, %d %b %y\")$bblue)&#9472;&#9488;\n$bblue&#9492;&#9472;(\$newRET)(\#)($orange\$(date \"+%H:%M\")$bblue)&#9472;>$white "
        ;;    
        *)
        PS1="&#9484;&#9472;(\$newPWD)&#9472;\${fill}&#9472;(\u@\h \$(date \"+%a, %d %b %y\"))&#9472;&#9488;\n&#9492;&#9472;(\$newRET)(\#)(\$(date \"+%H:%M\") )&#9472;> "
        ;;
    esac
  elif [ $1 -eq 1 ]
  then
    # anonymous prompt 1
    export ANONYMOUS=1
    PROMPT_COMMAND=pre_prompt
    case "$TERM" in
    xterm)
        PS1="$bblue&#9484;&#9472;($orange\$newPWD$bblue)&#9472;\${fill}&#9472;&#9472;&#9488;\n$bblue&#9492;&#9472;(\$newRET)(\#)&#9472;>$white "
        ;;
    screen)
        PS1="$bblue&#9484;&#9472;($orange\$newPWD$bblue)&#9472;\${fill}&#9472;&#9472;&#9488;\n$bblue&#9492;&#9472;(\$newRET)(\#)&#9472;>$white "
        ;;
        *)
        PS1="&#9484;&#9472;(\$newPWD)&#9472;\${fill}&#9472;&#9472;&#9488;\n&#9492;&#9472;(\$newRET)(\#)&#9472;> "
        ;;
    esac
  else
    # anonymous prompt 2
    PROMPT_COMMAND=''
    PS1='\[\e[0;1;33;41m\][$(funny_face)][\#][\w]\$ \[\e[m\] '
  fi
  PS1="\$(play_command_sound)$PS1"
}

set_command_sound 0
load_prompt 0

```

.bash_functions
```
# ~/.bash_functions

mailme()
{
	echo "$@" | mail -s "$1" $SERVERMAIL
}

random_cow()
{
  files=(/usr/share/cowsay/cows/*)
  printf "%s\n" "${files[RANDOM % ${#files}]}"
}

num_threads()
{
    cores=`grep cores /proc/cpuinfo | wc -l`
#     echo cores=$cores
    if [ $cores -eq 0 ]; then cores=1; fi
    procs=`grep processor /proc/cpuinfo | wc -l`
#     echo procs=$procs
    thrds=`expr $cores \* $procs`
    thrds=$cores
    echo $thrds;
}

# back up .bash* files
backup_bashfiles()
{
  ARCHIVE="$HOME/bash_dotfiles_$(date +%Y%m%d_%H%M%S).tar.gz";
  cd ~
  tar -czvf $ARCHIVE .bash_profile .bashrc .bash_functions .bash_aliases .bash_prompt
  echo "All backed up in $ARCHIVE";
}

```

You can use "load_prompt 0/1/2/..." to switch prompts + enable/disable sound with "set_command_sound 0/1". :)

---

### Post by earthpigg on 2009-09-19
i use this all the time. super quick, super easy.

must install 'lynx' first -- very small CLI web browser.

```
# Weather by us zip code - Can be called two ways # weather 50315 # weather "Des Moines"
weather ()
{
declare -a WEATHERARRAY
WEATHERARRAY=( `lynx -dump "http://www.google.com/search?hl=en&lr=&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=weather+${1}&btnG=Search" | grep -A 5 -m 1 "Weather for"`)
echo ${WEATHERARRAY[@]}
}

```

i can't remember if 'curl' is installed by default.

```
alias myip='echo My IP is && curl http://www.whatismyip.com/automation/n09230945.asp && echo'
```

---

### Post by Mr. Picklesworth on 2009-09-27
> **bodhi.zazen said:**
> zsh ftw :)

The biggest problem with zsh is finding a decent .zshrc :

I just made my zsh into the best thing ever :)

Here's how to make zsh set an xterm title with the currently running command. For people who like to use the less command and operate lots of xterms at once, I'm sure you'll find a million uses for this!

In zsh, just add the following somewhere:

```
case $TERM in
    xterm*)
      preexec () {
        print -Pn "\e]0;`basename $PWD`: $2\a"
      }
    ;;
esac
```
`basename $PWD` means that the title displays the name of the current directory and none of the trailing directories. Just a bit of context for the important part, which comes from $2, which is provided courtesy of zsh's preexec function. (There are 3 arguments. $1 is what the user typed, $2 and $3 are that formatted in different ways).

Unfortunately it's a bit trickier to accomplish in Bash, but here you go:
[http://www.davidpashley.com/articles/xterm-titles-with-bash.html](http://www.davidpashley.com/articles/xterm-titles-with-bash.html)


The rest of my .zshrc is pretty boring.

---

### Post by KIAaze on 2009-10-28
_[SIZE="4"]bash prompt / PS1 string styling line wrapping troubleshooting:[/SIZE]_

_1) Box drawing characters screwing up line wrapping_
I had some problems with my new bash prompt using [box drawing characters]("http://en.wikipedia.org/wiki/Box-drawing_characters") (&#9472;,&#9484;,&#9488;,&#9492;).

I finally managed to solve it. All you have to do is put "\[" and "\]" around those characters. :)

Here's my new PS1 string:

```
export black="\[\033[0;38;5;0m\]"
export red="\[\033[0;38;5;1m\]"
export orange="\[\033[0;38;5;130m\]"
export green="\[\033[0;38;5;2m\]"
export yellow="\[\033[0;38;5;3m\]"
export blue="\[\033[0;38;5;4m\]"
export bblue="\[\033[0;38;5;12m\]"
export magenta="\[\033[0;38;5;55m\]"
export cyan="\[\033[0;38;5;6m\]"
export white="\[\033[0;38;5;7m\]"
export coldblue="\[\033[0;38;5;33m\]"
export smoothblue="\[\033[0;38;5;111m\]"
export iceblue="\[\033[0;38;5;45m\]"
export turqoise="\[\033[0;38;5;50m\]"
export smoothgreen="\[\033[0;38;5;42m\]"
export defaultcolor="\[\e[m\]"
PS1="$bblue\[&#9484;&#9472;\]($orange\$newPWD$bblue)\[&#9472;\${fill}&#9472;\]($orange\u@\h \$(date \"+%a, %d %b %y\")$bblue)\[&#9472;&#9488;\]\n$bblue\[&#9492;&#9472;\](\$newRET)(\#)($orange\$(date \"+%H:%M\")$bblue)->$defaultcolor "

```
cf my previous post for the full .bashrc. I don't have a clean one I can post here right now.

_2) Unicode/Box drawing characters not displaying correctly in Konsole/Yakuake/etc:_
```
Settings->Encoding->Unicode (utf8)
Settings->Save as default

```

_3)Colors & co screwing up line wrapping:_
Surround the color statements (those beginning with "\e", "\033")(more generally: all "non-printing" characters) with "\[" and "\]".
Also, make sure you end the PS1 string with "\[\e[m\]" if you want to get back to default colors for input.

Just for reference, from man bash:
```

\[     begin  a sequence of non-printing characters, which could
                     be used to embed a terminal  control  sequence  into  the
                     prompt
\]     end a sequence of non-printing characters

```

Note: This should probably be added to some big bash prompt styling guide. :)

---

### Post by Unitux on 2009-11-11
:O

```
#!/bin/bash
export red="\033[0;31m"
export green="\033[0;32m"
export blue="\033[0;34m"
export cyan="\033[0;36m"
export white="\033[0;37m"
export b_red="\033[1;31m"
export b_green="\033[1;32m"
export b_blue="\033[1;34m"
export b_cyan="\033[1;36m"
export b_white="\033[1;37m"
export HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
export HISTCONTROL=ignoreboth
shopt -s histappend
shopt -s checkwinsize
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi
case "$TERM" in
xterm)
    PS1="\[$b_blue\]\$(date \"+%H:%M:%S\") \[$b_blue\][\[$b_white\]\w\[$b_blue\]]\[$b_green\] \u\[$b_white\] $\[$white\] "
    ;;
screen)
    PS1="\[$b_blue\]\$(date \"+%H:%M:%S\") \[$b_blue\][\[$b_white\]\w\[$b_blue\]]\[$b_green\] \u\[$b_white\] $\[$white\] "
    ;;    
*)
    PS1="\[$b_blue\]\$(date \"+%H:%M:%S\") \[$b_blue\][\[$b_white\]\w\[$b_blue\]]\[$b_green\] \u\[$b_white\] $\[$white\] "
    ;;
esac
#header (Superuser).
#case "$TERM" in
#xterm)
#    PS1="\[$red\]\$(date \"+%H:%M:%S\") \[$b_red\][\[$b_red\]\w\[$b_red\]]\[$b_red\] \u\[$b_red\] $\[$red\]"
#    ;;
#screen)
#    PS1="\[$red\]\$(date \"+%H:%M:%S\") \[$b_red\][\[$b_red\]\w\[$b_red\]]\[$b_red\] \u\[$b_red\] $\[$red\]"
#    ;;    
#    *)
#    PS1="\[$red\]\$(date \"+%H:%M:%S\") \[$b_red\][\[$b_red\]\w\[$b_red\]]\[$b_red\] \u\[$b_red\] $\[$red\]"
#    ;;
#esac
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
#welcome screen
GW="192.168.0.1"		#Gateway or w/e u want
pr=`ping -c1 $GW | awk /'time=/ {print $7 $8}'`
rfr=`free | awk /'cache:/ {print $4}'`
rur=`free | awk /'Mem:/ {print $2}'`
sfr=`free | awk /'Swap:/ {print $4*100/$2}'`
cur=`mpstat | awk /'Linux/ {print $2}'`
cir=`mpstat | awk /'all/ {print $11}'`
ute=`uptime | awk -F'( |,)' '{print $4 $5}'`
echo "<><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><>"
echo -e "$b_white""NET""$b_red""	$pr""$b_white""$b_white""		CPU (avg)""$b_red""	$cir""% idle"
tput sgr0
echo -e "$b_white""RAM ""$b_red""	$rfr"" of ""$rur"" free ""$b_white""	UPTIME""$b_red""		$ute"
tput sgr0
echo -e "$b_white""SWAP ""$b_red""	$sfr""% free""$b_white""		KERNEL ""$b_red""		$cur"
tput sgr0
echo "<><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><>"
```

---

### Post by slakkie on 2009-11-11
My bashrc:

```

#
# Bash hack
# This file is sourced by all *interactive* bash shells on startup,
# including some apparently interactive shells such as scp and rcp
# that can't tolerate any output.  So make sure this doesn't display
# anything or bad things will happen !
#
# Test for an interactive shell.  There is no need to set anything
# past this point for scp and rcp, and it's important to refrain from
# outputting anything in those cases.
#if [[ "$-" != *i* ]] ; then
#  return
#fi
# We can also do it like this:
[ ! -t 0 ] && return

source $HOME/.profile

load_env
load_alias
load_shell
set_term
set_ps1
set_shell_options
motd
check_os
# Load some extras
source $HOME/.env.local

```

---

### Post by RageOfOrder on 2010-06-22
I may get **** for reviving an old thread, but here's mine.

[IMG]http://omploader.org/vNHB0dg[/IMG]

.bashrc and .tmux.conf are attached.
You'll want to save them directly (Opening the bashrc in your browser won't display symbols correctly).

Also, you'll have to rename them to remove the .txt from the ends.

Edit: Fixed a bug and added the root .bashrc as well (red instead of blue)

[img]http://omploader.org/vNHB1Nw[/img]

---

### Post by tanque1075 on 2010-09-03
Well, i'm relatively new to Ubuntu, and a colleague decided to teach me lesson while I left my desktop unlocked. He messed with my .bashrc. Despite my attempts of fixing it, I still cannot open my Terminal in Ubuntu Lucid. Can someone help? :confused:

Thanks


# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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


exit

---

### Post by karthick87 on 2010-09-03
Here is my .bashrc

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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
```

---

### Post by tanque1075 on 2010-09-03
It worked. Awesome! Thanks a lot!

---

### Post by Spice Weasel on 2010-09-03
Here's mine:

```

HISTSIZE=100
HISTFILESIZE=200
shopt -s checkwinsize
PS1="\[\033[1;34m\](\[\033[1;37m\]\w\[\033[1;34m\]) \[\033[1;32m\]*\[\033[1;0m\] "
    alias ls='ls --color=auto'
    alias quake3='~/Q3/quake3.x86'
    alias q3dedi='~/Q3/dedi'

```Very damn simple. But the PS1 looks great in my opinion.

[IMG]http://i53.tinypic.com/2lm1het.png[/IMG]

Also, lazy compiling through aliases FTW.

---

### Post by Tekmoor on 2010-09-05
Thanks everyone for sharing, I've learnt a lot from this thread.
Here's mine, it's a cleaner version of this one: [http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/](http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/) (my thanks to the author)

It also shows git branches and a smiley that changes if the previous command errored. Colours are meant to match the 10.04 scheme.
```

################################################################################
# this is my new prompt based on: http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/
 

function pre_prompt {
  newPWD="${PWD}"
  user="whoami"
  host=$(echo -n $HOSTNAME | sed -e "s/[\.].*//")
  datenow=$(date "+%a, %d %b %y")
  let promptsize=$(echo -n "   ${PWD}\!" \
                   | wc -c | tr -d " ")

  let fillsize=${COLUMNS}
  fill=""
  fullfill=""

  while [ "$fillsize" -gt "0" ] 
  do 
      fullfill="${fullfill}_"
      let fillsize=${fillsize}-1
  done

  let fillsize=${COLUMNS}-${promptsize}
  while [ "$fillsize" -gt "0" ] 
  do 
#      fill="${fill}&#9472;"
      fill="${fill} "
      let fillsize=${fillsize}-1
  done

  if [ "$fillsize" -lt "0" ]
  then
      let cutt=3-${fillsize}
      newPWD="...$(echo -n $PWD | sed -e "s/\(^.\{$cutt\}\)\(.*\)/\2/")"
  fi
}

PROMPT_COMMAND=pre_prompt

export black="\[\033[0;38;5;0m\]"
export red="\[\033[0;38;5;1m\]"
export orange="\[\033[0;38;5;130m\]"
export green="\[\033[0;38;5;2m\]"
export yellow="\[\033[0;38;5;3m\]"
export blue="\[\033[0;38;5;4m\]"
export bblue="\[\033[0;38;5;12m\]"
export magenta="\[\033[0;38;5;55m\]"
export cyan="\[\033[0;38;5;6m\]"
export white="\[\033[0;38;5;7m\]"
export coldblue="\[\033[0;38;5;33m\]"
export smoothblue="\[\033[0;38;5;111m\]"
export iceblue="\[\033[0;38;5;45m\]"
export turqoise="\[\033[0;38;5;50m\]"
export smoothgreen="\[\033[0;38;5;42m\]"

export magentabld="\[\033[01;35m\]"
export redbld="\[\033[01;31m\]"

# script from http://progit.org/book/ch2-11.html for autocompletion with git
source ~/.git-completion.bash

GIT_PS1_SHOWDIRTYSTATE=true
GIT_PS1_SHOWSTASHSTATE=true
GIT_PS1_SHOWUNTRACKEDFILES=true

git='`__git_ps1`'
prev=$?

case "$TERM" in
xterm)
    PS1="$magentabld\${fullfill}\n$redbld\$newPWD $magentabld\${fill} \!
$magentabld\`prev=\$?; __git_ps1; if [ \$prev = 0 ]; then echo \[\e[32m\] ^_^\[\e[0m\]; else echo \[\e[31m\] O_o\[\e[0m\]; fi\` $white"
    ;;
    *)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
esac


################################################################################
# welcome

clear

echo -ne "\033[01;35mSysinfo:";uptime
uname -r
cat /etc/issue 
echo -ne "o hai thar $USER!  =^.^=";
echo -ne "\n\n\033[0;38;5;7m";
ls

```

---

### Post by Austin25 on 2010-09-06
mine.
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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

echo "Hello, Austin." | cowsay -f tux

```

---

### Post by stanca on 2010-09-06
Here's mine too::)
 ```
 MY BASHRC FILE ################################### MY BASHRC FILE



##### ORIGINAL CONTENT ----- ORIGINAL CONTENT ----- ORIGINAL CONTENT ----- ORIGINAL CONTENT ----- ORIGINAL CONTENT ----- ORIGINAL CONTENT ##### ORIGINAL



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



##### CUSTOM STARTS HERE ----- CUSTOM STARTS HERE ----- CUSTOM STARTS HERE ----- CUSTOM STARTS HERE ----- CUSTOM STARTS HERE ##### CUSTOM STARTS HERE



### FUNCTIONS ### FUNCTIONS ### FUNCTIONS ### FUNCTIONS ### FUNCTIONS ### FUNCTIONS ### FUNCTIONS ### FUNCTIONS ### FUNCTIONS ### FUNCTIONS ### FUNCTIONS



##### Inserts a flag with the specified content

# Usage: flag "comment"
# If no comment, inserts the date.
function flag(){
    if [ "$1" == "" ];
    then
        echo -e  "\e[0;31m[====== " `date +"%A %e %B %Y"`, `date +"%H"`h`date +"%M"` " ======]\e[0m"
    else
        echo -e  "\e[0;31m[====== " $@ " ======]\e[0m"
    fi
}



##### Inserts a flag and executes the command

# Example: flagcommand ls
function flagcommand(){
    if [ "$1" == "" ];
    then
        return
    else
        flag $@
        $@
    fi
}



##### Weather by us zip code - Can be called two ways # weather 50315 # weather "Des Moines"

weather ()
{
declare -a WEATHERARRAY
WEATHERARRAY=( `lynx -dump http://google.com/search?q=weather+$1 | grep -A 5 '^ *Weather for' | grep -v 'Add to'`)
echo ${WEATHERARRAY[@]}
}



##### Stock prices - can be called two ways. # stock novl  (this shows stock pricing)  #stock "novell"  (this way shows stock symbol for novell)

stock ()
{
stockname=`lynx -dump http://finance.yahoo.com/q?s=${1} | grep -i ":${1})" | sed -e 's/Delayed.*$//'`
stockadvise="${stockname} - delayed quote."
declare -a STOCKINFO
STOCKINFO=(` lynx -dump http://finance.yahoo.com/q?s=${1} | egrep -i "Last Trade:|Change:|52wk Range:"`)
stockdata=`echo ${STOCKINFO[@]}`
   if [[ ${#stockname} != 0 ]] ;then
      echo "${stockadvise}"
      echo "${stockdata}"
         else
         stockname2=${1}
         lookupsymbol=`lynx -dump -nolist http://finance.yahoo.com/lookup?s="${1}" | grep -A 1 -m 1 "Portfolio" | grep -v "Portfolio" | sed 's/\(.*\)Add/\1 /'`
            if [[ ${#lookupsymbol} != 0 ]] ;then
            echo "${lookupsymbol}"
               else
               echo "Sorry $USER, I can not find ${1}."
            fi
   fi
}



##### Translate a Word  - USAGE: translate house spanish  # See dictionary.com for available languages (there are many).

translate ()
{
TRANSLATED=`lynx -dump "http://translate.reference.com/browse/${1}" | grep -i -m 1 -w "${2}:" | sed 's/^[ \t]*//;s/[ \t]*$//'`
if [[ ${#TRANSLATED} != 0 ]] ;then
   echo "\"${1}\" in ${TRANSLATED}"
   else
   echo "Sorry, I can not translate \"${1}\" to ${2}"
fi
}



##### Define a word - USAGE: define dog

define ()
{
lynx -dump "http://www.google.com/search?hl=en&q=define%3A+${1}&btnG=Google+Search" | grep -m 3 -w "*"  | sed 's/;/ -/g' | cut -d- -f1 > /tmp/templookup.txt
         if [[ -s  /tmp/templookup.txt ]] ;then
            until ! read response
               do
               echo "${response}"
               done < /tmp/templookup.txt
            else
               echo "Sorry $USER, I can't find the term \"${1} \""
         fi
rm -f /tmp/templookup.txt
}



##### Dirsize - finds directory sizes and lists them for the current directory

dirsize ()
{
du -shx * .[a-zA-Z0-9_]* 2> /dev/null | \
egrep '^ *[0-9.]*[MG]' | sort -n > /tmp/list
egrep '^ *[0-9.]*M' /tmp/list
egrep '^ *[0-9.]*G' /tmp/list
rm /tmp/list
}



##### Myip - finds your current IP if your connected to the internet

myip ()
{
lynx -dump -hiddenlinks=ignore -nolist [http://checkip.dyndns.org:8245/](http://checkip.dyndns.org:8245/) | awk '{ print $4 }' | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g'
}



##### Clock - A bash clock that can run in your terminal window.

clock ()
{
while true;do clear;echo "===========";date +"%r";echo "===========";sleep 1;done
}



##### Netinfo - shows network information for your system

netinfo ()
{
echo "--------------- Network Information ---------------"
/sbin/ifconfig | awk /'inet addr/ {print $2}'
/sbin/ifconfig | awk /'Bcast/ {print $3}'
/sbin/ifconfig | awk /'inet addr/ {print $4}'
/sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'
myip=`lynx -dump -hiddenlinks=ignore -nolist [http://checkip.dyndns.org:8245/](http://checkip.dyndns.org:8245/) | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g' `
echo "${myip}"
echo "---------------------------------------------------"
}



##### Shot - takes a screenshot of your current window

shot ()
{
import -frame -strip -quality 75 "$HOME/$(date +%s).png"
}



##### Bu - Back Up a file. Usage "bu filename.txt"

bu () { cp $1 ${1}-`date +%Y%m%d%H%M`.backup ; }



##### Extract - extract most common compression types

extract() {
  local e=0 i c
  for i; do
    if [[ -f $i && -r $i ]]; then
        c=''
        case $i in
          *.t@(gz|lz|xz|b@(2|z?(2))|a@(z|r?(.@(Z|bz?(2)|gz|lzma|xz)))))
                 c='bsdtar xvf' ;;
          *.7z)  c='7z x'       ;;
          *.Z)   c='uncompress' ;;
          *.bz2) c='bunzip2'    ;;
          *.exe) c='cabextract' ;;
          *.gz)  c='gunzip'     ;;
          *.rar) c='unrar x'    ;;
          *.xz)  c='unxz'       ;;
          *.zip) c='unzip'      ;;
          *)     echo "$0: cannot extract \`$i': Unrecognized file extension" >&2; e=1 ;;
        esac
        [[ $c ]] && command $c "$i"
    else
        echo "$0: cannot extract \`$i': File is unreadable" >&2; e=2
    fi
  done
  return $e
}



##### :h gets you to the vim help menu or directly to :help wordname

:h() {  vim --cmd ":silent help $@" --cmd "only"; }



##### Add color & formatting to CLI

export PS1="\[\e[35;1m\]\u\[\e[0m\]\[\e[32m\]@\h\[\e[32m\]\w \[\e[33m\]\$ \[\e[0m\]"



##### Makes directory then moves into it

function mkcdr {
    mkdir -p -v $1
    cd $1
}



##### Creates an archive from given directory

mktar() { tar cvf  "${1%%/}.tar"     "${1%%/}/"; }
mktgz() { tar cvzf "${1%%/}.tar.gz"  "${1%%/}/"; }
mktbz() { tar cvjf "${1%%/}.tar.bz2" "${1%%/}/"; }



##### To show Apt Log History

function apt-history(){
      case "$1" in
        install)
              cat /var/log/dpkg.log | grep 'install '
              ;;
        upgrade|remove)
              cat /var/log/dpkg.log | grep $1
              ;;
        rollback)
              cat /var/log/dpkg.log | grep upgrade | \
                  grep "$2" -A10000000 | \
                  grep "$3" -B10000000 | \
                  awk '{print $4"="$5}'
              ;;
        *)
              cat /var/log/dpkg.log
              ;;
      esac
}



##### Reminder for whatever whenever

function remindme()
{
sleep $1 && zenity --info --text "$2" &
}



##### Kill a process by name

# Example: killps firefox-bin
function killps()
{
    local pid pname sig="-TERM" # default signal
    if [ "$#" -lt 1 ] || [ "$#" -gt 2 ]; then
        echo "Usage: killps [-SIGNAL] pattern"
        return;
    fi
    if [ $# = 2 ]; then sig=$1 ; fi
    for pid in $(myps | nawk '!/nawk/ && $0~pat { print $2 }' pat=${!#}) ; do
        pname=$(myps | nawk '$2~var { print $6 }' var=$pid )
        if ask "Kill process $pid <$pname> with signal $sig ? "
            then kill $sig $pid
        fi
    done
}



##### Ask

function ask()
{
    echo -n "$@" '[y/n] ' ; read ans
    case "$ans" in
        y*|Y*) return 0 ;;
        *) return 1 ;;
    esac
}



##### User friendly ps

function psaux {
    [ $# == 1 ] && ps aux | grep $1
}

function my_ps() { ps $@ -u $USER -o pid,%cpu,%mem,bsdtime,command ; }

function pp() { my_ps f | awk '!/awk/ && $0~var' var=${1:-".*"} ; }



##### Change directory and list files

function cds(){
    # only change directory if a directory is specified
    [ -n "${1}" ] && cd $1
    lls
}



##### Advanced ls function

# Counts files, subdirectories and directory size and displays details
# about files depending on the available space
function lls () {
    # count files
    echo -n "<`find . -maxdepth 1 -mindepth 1 -type f | wc -l | tr -d '[:space:]'` files>"
    # count sub-directories
    echo -n " <`find . -maxdepth 1 -mindepth 1 -type d | wc -l | tr -d '[:space:]'` dirs/>"
    # count links
    echo -n " <`find . -maxdepth 1 -mindepth 1 -type l | wc -l | tr -d '[:space:]'` links@>"
    # total disk space used by this directory and all subdirectories
    echo " <~`du -sh . 2> /dev/null | cut -f1`>"
    ROWS=`stty size | cut -d' ' -f1`
    FILES=`find . -maxdepth 1 -mindepth 1 |
    wc -l | tr -d '[:space:]'`
    # if the terminal has enough lines, do a long listing
    if [ `expr "${ROWS}" - 6` -lt "${FILES}" ]; then
        ls
    else
        ls -hlAF --full-time
    fi
}



##### Find a file with a pattern in name in the local directory

function fp()
{
    find . -type f -iname '*'$*'*' -ls ;
}



##### Find a file with pattern $1 in name and Execute $2 on it

function fe() { find . -type f -iname '*'$1'*' -exec "${2:-file}" {} \;  ; }



##### Find pattern in a set of files and highlight them

function fstr()
{
    OPTIND=1
    local case=""
    local usage="fstr: find string in files.
Usage: fstr [-i] \"pattern\" [\"filename pattern\"] "
    while getopts :it opt
    do
        case "$opt" in
        i) case="-i " ;;
        *) echo "$usage"; return;;
        esac
    done
    shift $(( $OPTIND - 1 ))
    if [ "$#" -lt 1 ]; then
        echo "$usage"
        return;
    fi
    local SMSO=$(tput smso)
    local RMSO=$(tput rmso)
    find . -type f -name "${2:-*}" -print0 | xargs -0 grep -sn ${case} "$1" 2>&- | \
sed "s/$1/${SMSO}\0${RMSO}/gI" | more
}



##### Cut last n lines in file, 10 by default

function cuttail()
{
    nlines=${2:-10}
    sed -n -e :a -e "1,${nlines}!{P;N;D;};N;ba" $1
}



##### Move filenames to lowercase

function lowercase()
{
    for file ; do
        filename=${file##*/}
        case "$filename" in
        */*) dirname==${file%/*} ;;
        *) dirname=.;;
        esac
        nf=$(echo $filename | tr A-Z a-z)
        newname="${dirname}/${nf}"
        if [ "$nf" != "$filename" ]; then
            mv "$file" "$newname"
            echo "lowercase: $file --> $newname"
        else
            echo "lowercase: $file not changed."
        fi
    done
}



##### Creates a backup of the file passed as parameter with the date and time

function bak ()
{
  cp $1 $1_`date +%H:%M:%S_%d-%m-%Y`
}



##### Swap 2 filenames around

function swap()
{
    local TMPFILE=tmp.$$
    mv "$1" $TMPFILE
    mv "$2" "$1"
    mv $TMPFILE "$2"
}



##### Edit the svn log at  the given revision

editsvnlog() {
    svn propedit svn:log --revprop -r$1 --editor-cmd gedit
}



##### Remove all files created by latex

function unlatex(){
if [ "$1" == "" ]; then
return
fi
i=${1%%.*}
rm -f $i.aux $i.toc $i.lof $i.lot $i.los $i.?*~ $i.loa $i.log $i.bbl $i.blg $i.glo
rm -f $i.odt $i.tns $i.fax $i.bm $i.out $i.nav $i.snm
rm -f $i.mtc* $i.bmt
mv -f $i.dvi .$i.dvi
mv -f $i.ps .$i.ps
mv -f $i.pdf .$i.pdf
rm -f $i.dvi $i.ps $i.pdf
unset i
}



##### Display private IP

function ippriv()
{
    ifconfig eth0|grep "inet adr"|awk '{print $2}'|awk -F ':' '{print $2}'
}



##### Repeats a command every x seconds

# Usage: repeat PERIOD COMMAND
function repeat() {
    local period
    period=$1; shift;
    while (true); do
        eval "$@";
    sleep $period;
    done
}



##### Size of directories in MB

function ds()
{
    echo "size of directories in MB"
    if [ $# -lt 1 ] || [ $# -gt 2 ]; then
        echo "you did not specify a directy, using pwd"
        DIR=$(pwd)
        find $DIR -maxdepth 1 -type d -exec du -sm \{\} \; | sort -nr
    else
        find $1 -maxdepth 1 -type d -exec du -sm \{\} \; | sort -nr
    fi
}



##### Automatically inputs aliases here in '.bashrc'

# Usage: mkalias <name> "<command>"
# Example: mkalias rm "rm -i"
function mkalias ()
{
        if [[ $1 && $2 ]]
        then
        echo -e "alias $1=\"$2\"" >> ~/.bashrc
        alias $1=$2
        fi
}



### ALIASES  ### ALIASES  ### ALIASES  ### ALIASES  ### ALIASES  ### ALIASES  ### ALIASES  ### ALIASES  ### ALIASES  ### ALIASES  ### ALIASES  ### ALIASES



##### Directory shortcuts

alias home='cd ~/'
alias backgrounds='cd ~/Pictures/Backgrounds'
alias backups='cd ~/Backups'
alias books='cd ~/eBooks'
alias documents='cd ~/Documents'
alias downloads='cd ~/Downloads'
alias drive-c='cd ~/.wine/drive_c'
alias images='cd ~/Images'
alias localhost='cd /var/www'
alias music='cd ~/Music'
alias nautilus-scripts='cd ~/.gnome2/nautilus-scripts'
alias packages='cd ~/Packages'
alias pictures='cd ~/Pictures'
alias ppc='cd ~/PPC'
alias public='cd ~/Public'
alias torrents='cd ~/Torrents'
alias temp='cd ~/Temp'
alias ubuntu-texts='cd ~/Documents/Ubuntu Texts'
alias videos='cd ~/Videos'
alias webdesign='cd ~/Web/Design'
alias back='cd $OLDPWD'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'
alias ......='cd ../../../../..'



##### Command substitution

alias ff='sudo find / -name $1'
alias df='df -h -x tmpfs -x usbfs'
alias psg='ps -ef | grep $1'
alias h='history | grep $1'
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'
alias which='type -all'
alias path='echo -e ${PATH//:/\\n}'
alias vi='vim'
alias du='du -h --max-depth=1'
alias c='clear'
alias e='espeak'
alias kgp='killall gnome-panel'
alias k='kill'
alias kn='killall nautilus'
alias q='exit'
alias n='nautilus & exit'
alias nq='nautilus -q'
alias yt='youtube-dl -t '
alias mc='metacafe-dl -t'
alias updatefont='fc-cache -v -f'
alias sdi='sudo dpkg -i'
alias ps='ps auxf'
alias pg='ps aux | grep'* # requires an argument
alias mountedinfo='df -hT'
alias ping='ping -c 10'
alias mkdir='mkdir -p -v'
alias openports='netstat -nape --inet'
alias ns='netstat -alnp --protocol=inet | grep -v CLOSE_WAIT | cut -c-6,21-94 | tail +2'
alias du1='du -h --max-depth=1'
alias packup='/bin/tar -czvf' # compress a file in tar format
alias unpack='/bin/tar -xzvpf' # uncompress a a Tar file
alias contents='/bin/tar -tzf' # can View the contents of a Tar file
alias mktd='tdir=`mktemp -d` && cd $tdir' # make a temp dir, then immediately cd into it
### some ls aliases
alias ls='ls -hF --color' # add colors for filetype recognition
alias lx='ls -lXB' # sort by extension
alias lk='ls -lSr' # sort by size
alias la='ls -Al' # show hidden files
alias lr='ls -lR' # recursice ls
alias lt='ls -ltr' # sort by date
alias lm='ls -al |more' # pipe through 'more'
alias tree='tree -Cs' # nice alternative to 'ls'
alias ll='ls -l' # long listing
alias l='ls -hF --color' # quick listing
alias lsize='ls --sort=size -lhr' # list by size
alias l?='cat ~/technical/tips/ls'
alias lsd='ls -l | grep "^d"' # list only directories
alias l.='ls -d .[[:alnum:]]* 2> /dev/null || echo "No hidden file here..."' # list only hidden files



##### Miscellaneous

alias edit='nano'
alias bashrc='gedit ~/.bashrc & exit'
alias ebrc='nano ~/.bashrc'
alias ebrcupdate='source ~/.bashrc'
alias repos='gksudo gedit /etc/apt/sources.list'
alias n2r='sudo /etc/init.d/nginx stop && sleep 2 && sudo /etc/init.d/nginx start'
alias someDBdump='sudo mysqldump someDB -uroot -p > /home/username/www/_dbs/someDB.sql'
alias webshare='python -c "import SimpleHTTPServer; SimpleHTTPServer.test();"'
alias wiki='wikipedia2text -p'
alias perm='stat --printf "%a %n \n "'
alias bbc='lynx -term=vt100 [http://news.bbc.co.uk/text_only.stm](http://news.bbc.co.uk/text_only.stm)'
alias nytimes='lynx -term=vt100 [http://nytimes.com](http://nytimes.com)'
alias ip='curl [www.whatismyip.org](www.whatismyip.org)'
alias restart-apache='sudo /etc/init.d/apache2 restart'
alias svnrmallentries='find . -name .svn -print0 | xargs -0 rm -rf' # remove all .svn directories recursively
alias svnaddall='find "$PWD" -exec svn add {} 2>/dev/null \;' # add all files recursively
### easy script callin'
alias show-info='~/.bin/info.pl'
alias show-colors='~/.bin/colors.sh'
### sudo fixes
alias updatedb='sudo updatedb'
alias ppa-purge='sudo ppa-purge'
### terminal notifications
alias alert_helper='history|tail -n1|sed -e "s/^\s*[0-9]\+\s*//" -e "s/;\s*alert$//"'
alias alert='notify-send -i gnome-terminal "Finished Terminal Job" "[$?] $(alert_helper)"'
### truecrypt
alias mtrue='sudo truecrypt /media/usbdisk/me.tc ~/me'
alias utrue='sudo truecrypt -d'
### rsync
alias usbb='rsync -avz /media/usbdisk/ ~/backup/usb/'
alias rsync-me='sudo rsync -a -v --progress --delete --modify-window=1 -s /home/me /home/rsync'



##### Chmod commands

alias mx='chmod a+x'
alias 000='chmod 000'
alias 644='chmod 644'
alias 755='chmod 755'



##### App-specific

alias nano='nano -W -m'
alias audio='ncmpcpp'
alias ftp='ncftp Personal'
alias wget='wget -c'
alias scrot='scrot -c -d 7'
alias tvtime-video0='tvtime-configure -d /dev/video0'
alias tvtime-video1='tvtime-configure -d /dev/video1'
alias tvtime-video2='tvtime-configure -d /dev/video2'
alias tvtime-video3='tvtime-configure -d /dev/video3'
alias tvtime-video4='tvtime-configure -d /dev/video4'
alias tvtime-video5='tvtime-configure -d /dev/video5'
alias ss='gnome-screensaver-command -a'



##### Xterm and Aterm

alias term='xterm -bg AntiqueWhite -fg Black &'
alias termb='xterm -bg AntiqueWhite -fg NavyBlue &'
alias termg='xterm -bg AntiqueWhite -fg OliveDrab &'
alias termr='xterm -bg AntiqueWhite -fg DarkRed &'
alias aterm='xterm -ls -fg gray -bg black'
alias xtop='xterm -fn 6x13 -bg LightSlateGray -fg black -e top &'
alias xsu='xterm -fn 7x14 -bg DarkOrange4 -fg white -e su &'



##### Remote hosts and proxy stuff

alias remote='ssh -p 1234 12.34.56.78' # access some remote host
alias uploads='cd /some/folder' # access some folder
alias dbdumpcp='scp -P 1234 [email]username@12.34.56.78:/home/username/Backup/www/data/someSite/db.sql[/email] /home/username/Backup/data/db.sql' # copy remote db to local
alias proxy1='ssh -p 1234 -D 5678 username@12.34.56.78' # SOCKS proxy .. these anonomise my browsing with a single word - 12.34.56.78
alias proxy2='ssh -p 8765 -D 4321 username@87.65.43.21' # SOCKS proxy .. these anonomise my browsing with a single word - 87.65.43.21
alias sync='java -jar ~/finchsync/finchsync.jar -nogui' # sync to PDA .. well, that'll be a sync then! - start FinchSync SVR
alias syncoff='java -jar ~/Apps/FinchSync/finchsync.jar -stopserver' # sync to PDA .. well, that'll be a sync then! - stop FinchSync SVR
alias finchsync='java -jar ~/finchsync/finchsync.jar' # start FinchSync Admin



##### Information

alias ver='cat /etc/lsb-release' # Ubuntu version detail
alias version='sudo apt-show-versions' # show version
alias space='df -h' # disk space usage
alias free='free -m' # RAM and SWAP detail in MBs
alias hardware='sudo lshw -html > hardware.html' # overview of the hardware in the computer
alias hgrep='history | grep --color=always' # search commands history
alias top-commands='history | awk "{print $2}" | awk "BEGIN {FS="|"} {print $1}" |sort|uniq -c | sort -rn | head -10' # show most popular commands
alias biggest='BLOCKSIZE=1048576; du -x | sort -nr | head -10' # show biggest directories
alias topten='du -sk $(/bin/ls -A) | sort -rn | head -10' # displays the top ten biggest folders/files in the current directory
alias treefind="find . | sed 's/[^/]*\//|   /g;s/| *\([^| ]\)/+--- \1/'" # displays a tree of the arborescence
alias stamp='date "+%Y%m%d%a%H%M"' # timestamps
alias da='date "+%Y-%m-%d %A    %T %Z"'
alias today='date +"%A, %B %-d, %Y"'
alias myps='/bin/ps -u "$USER" -o user,pid,ppid,pcpu,pmem,args|less' # ps



##### Personal help

alias a?='cat ~/.alias.help'
alias f?='cat ~/.function.help'
alias dn='OPTIONS=$(\ls -F | grep /$); select s in $OPTIONS; do cd $PWD/$s; break;done'
alias help='OPTIONS=$(\ls ~/.tips -F);select s in $OPTIONS; do less ~/.tips/$s; break;done'



##### Computer cleanup

alias trash='rm -fr ~/.Trash'
alias orphaned='sudo deborphan | xargs sudo apt-get -y remove --purge'
alias cleanup='sudo apt-get -y autoclean && sudo apt-get -y autoremove && sudo apt-get -y clean && sudo apt-get -y remove && sudo deborphan | xargs sudo apt-get -y remove --purge'



##### Hardware Shortcuts

alias cdo='eject /dev/cdrecorder'
alias cdc='eject -t /dev/cdrecorder'
alias dvdo='eject /dev/dvd'
alias dvdc='eject -t /dev/dvd'
alias scan='scanimage -L'
alias playw='for i in *.wav; do play $i; done'
alias playo='for i in *.ogg; do play $i; done'
alias playm='for i in *.mp3; do play $i; done'
alias dvdrip='vobcopy -i /dev/dvd/ -o ~/DVDs/ -l'



##### Espeak commands

alias espeak-wav-file='espeak -s 150 -w voice.wav -f'
alias espeak-wav='espeak -s 150 -w voice.wav'
alias espeak-us='espeak -v en-us -s 150'
alias espeak-file='espeak -s 150 -f'



##### Package making and installation

alias checkinstall='sudo checkinstall -y --fstrans=no'
alias checkinstall-noinstall='sudo checkinstall -y --fstrans=no --install=no'
alias checkinstall-force='sudo checkinstall --dpkgflags "--force-overwrite"'
alias debinstall='sudo dpkg -i'
alias debinstall-force='sudo dpkg -i --force-overwrite'



##### Chown substitution (change 'me' to your username)

alias chown='sudo chown -R me'
alias chown-backgrounds='sudo chown -R me ~/Pictures/Backgrounds'
alias chown-backups='sudo chown -R me ~/Backups'
alias chown-desktop='sudo chown -R me ~/Desktop'
alias chown-documents='sudo chown -R me ~/Documents'
alias chown-music='sudo chown -R me ~/Music'
alias chown-pictures='sudo chown -R me ~/Pictures'
alias chown-ppc='sudo chown -R me ~/PPC'
alias chown-public='sudo chown -R me ~/Public'
alias chown-temp='sudo chown -R me ~/Temp'
alias chown-videos='sudo chown -R me ~/Videos'



##### Aptitude stuff

alias install='sudo aptitude install'
alias remove='sudo aptitude remove'
alias purge='sudo aptitude purge'
alias hold='sudo aptitude hold'
alias unhold='sudo aptitude unhold'
alias markauto='sudo aptitude markauto'
alias unmarkauto='sudo aptitude unmarkauto'
alias forbid-version='sudo aptitude forbid-version'
alias update='sudo aptitude update'
alias upgrade='sudo aptitude safe-upgrade'
alias full-upgrade='sudo aptitude full-upgrade'
alias build-dep='sudo aptitude build-dep'
alias forget-new='sudo aptitude forget-new'
alias search='sudo aptitude search'
alias show='sudo aptitude show'
alias clean='sudo aptitude clean'
alias autoclean='sudo aptitude autoclean'
alias changelog='sudo aptitude changelog'
alias download='sudo aptitude download'
alias reinstall='sudo aptitude reinstall'
alias why='sudo aptitude why'
alias why-not='sudo aptitude why-not'
alias linux-image='sudo aptitude search linux-image' # linux-image kernel update check



##### Apt-get stuff

alias autoremove='sudo apt-get autoremove'
alias source='sudo apt-get source'
alias dist-upgrade='sudo apt-get dist-upgrade'
alias dselect-upgrade='sudo apt-get dselect-upgrade'
alias check='sudo apt-get check'



##### Apt-cache stuff

alias aptadd='sudo apt-cache add'
alias aptgencaches='sudo apt-cache gencaches'
alias aptshowpkg='sudo apt-cache showpkg'
alias aptshowsrc='sudo apt-cache showsrc'
alias aptstats='sudo apt-cache stats'
alias aptdump='sudo apt-cache dump'
alias aptdumpavail='sudo apt-cache dumpavail'
alias aptunmet='sudo apt-cache unmet'
alias aptsearch='sudo apt-cache search'
alias aptshow='sudo apt-cache show'
alias aptdepends='sudo apt-cache depends'
alias aptrdepends='sudo apt-cache rdepends'
alias aptpkgnames='sudo apt-cache pkgnames'
alias aptdotty='sudo apt-cache dotty'
alias aptxvcg='sudo apt-cache xvcg'
alias aptpolicy='sudo apt-cache policy'



##### Apt-history Stuff

alias history='apt-history'
alias historyi='apt-history install'
alias historyu='apt-history upgrade'
alias historyre='apt-history remove'
alias historyro='apt-history rollback'



##### Secure-delete substitution

alias srm='sudo srm -f -s -z -v'
alias srm-m='sudo srm -f -m -z -v'
alias smem-secure='sudo sdmem -v'
alias smem-f='sudo sdmem -f -l -l -v'
alias smem='sudo sdmem -l -l -v'
alias sfill-f='sudo sfill -f -l -l -v -z'
alias sfill='sudo sfill -l -l -v -z'
alias sfill-usedspace='sudo sfill -i -l -l -v'
alias sfill-freespace='sudo sfill -I -l -l -v'
alias sswap='sudo sswap -f -l -l -v -z'
alias sswap-sda5='sudo sswap -f -l -l -v -z /dev/sda5'
alias swapoff='sudo swapoff /dev/sda5'
alias swapon='sudo swapon /dev/sda5'



##### Shred substitution

alias shred-sda='sudo shred -v -z -n 0 /dev/sda'
alias shred-sdb='sudo shred -v -z -n 0 /dev/sdb'
alias shred-sdc='sudo shred -v -z -n 0 /dev/sdc'
alias shred-sdd='sudo shred -v -z -n 0 /dev/sdd'
alias shred-sde='sudo shred -v -z -n 0 /dev/sde'
alias shred-sdf='sudo shred -v -z -n 0 /dev/sdf'
alias shred-sdg='sudo shred -v -z -n 0 /dev/sdg'
alias shred-sda-r='sudo shred -v -z -n 1 /dev/sda'
alias shred-sdb-r='sudo shred -v -z -n 1 /dev/sdb'
alias shred-sdc-r='sudo shred -v -z -n 1 /dev/sdc'
alias shred-sdd-r='sudo shred -v -z -n 1 /dev/sdd'
alias shred-sde-r='sudo shred -v -z -n 1 /dev/sde'
alias shred-sdf-r='sudo shred -v -z -n 1 /dev/sdf'
alias shred-sdg-r='sudo shred -v -z -n 1 /dev/sdg'



##### DD substitution

alias backup-sda='sudo dd if=/dev/hda of=/dev/sda bs=64k conv=notrunc,noerror' # to backup the existing drive to a USB drive
alias restore-sda='sudo dd if=/dev/sda of=/dev/hda bs=64k conv=notrunc,noerror' # to restore from the USB drive to the existing drive
alias partitioncopy='sudo dd if=/dev/sda1 of=/dev/sda2 bs=4096 conv=notrunc,noerror' # to duplicate one hard disk partition to another hard disk partition
alias cdiso='sudo dd if=/dev/hda of=cd.iso bs=2048 conv=sync,notrunc' # to make an iso image of a CD
alias diskcopy='sudo dd if=/dev/dvd of=/dev/cdrecorder'
alias cdcopy='sudo dd if=/dev/cdrom of=cd.iso' # for cdrom
alias scsicopy='sudo dd if=/dev/scd0 of=cd.iso' # if cdrom is scsi
alias dvdcopy='sudo dd if=/dev/dvd of=dvd.iso' # for dvd
alias floppycopy='sudo dd if=/dev/fd0 of=floppy.image' # to duplicate a floppy disk to hard drive image file
alias dd-sda='sudo dd if=/dev/zero of=/dev/sda conv=notrunc' # to wipe hard drive with zero
alias dd-sdb='sudo dd if=/dev/zero of=/dev/sdb conv=notrunc' # to wipe hard drive with zero
alias dd-sdc='sudo dd if=/dev/zero of=/dev/sdc conv=notrunc' # to wipe hard drive with zero
alias dd-sdd='sudo dd if=/dev/zero of=/dev/sdd conv=notrunc' # to wipe hard drive with zero
alias dd-sde='sudo dd if=/dev/zero of=/dev/sde conv=notrunc' # to wipe hard drive with zero
alias dd-sdf='sudo dd if=/dev/zero of=/dev/sdf conv=notrunc' # to wipe hard drive with zero
alias dd-sdg='sudo dd if=/dev/zero of=/dev/sdg conv=notrunc' # to wipe hard drive with zero
alias dd-sda-r='sudo dd if=/dev/urandom of=/dev/sda bs=102400' # to wipe hard drive with random data option (1)
alias dd-sdb-r='sudo dd if=/dev/urandom of=/dev/sdb bs=102400' # to wipe hard drive with random data option (1)
alias dd-sdc-r='sudo dd if=/dev/urandom of=/dev/sdc bs=102400' # to wipe hard drive with random data option (1)
alias dd-sdd-r='sudo dd if=/dev/urandom of=/dev/sdd bs=102400' # to wipe hard drive with random data option (1)
alias dd-sde-r='sudo dd if=/dev/urandom of=/dev/sde bs=102400' # to wipe hard drive with random data option (1)
alias dd-sdf-r='sudo dd if=/dev/urandom of=/dev/sdf bs=102400' # to wipe hard drive with random data option (1)
alias dd-sdg-r='sudo dd if=/dev/urandom of=/dev/sdg bs=102400' # to wipe hard drive with random data option (1)
alias dd-sda-full='sudo dd if=/dev/urandom of=/dev/sda bs=8b conv=notrunc,noerror' # to wipe hard drive with random data option (2)
alias dd-sdb-full='sudo dd if=/dev/urandom of=/dev/sdb bs=8b conv=notrunc,noerror' # to wipe hard drive with random data option (2)
alias dd-sdc-full='sudo dd if=/dev/urandom of=/dev/sdc bs=8b conv=notrunc,noerror' # to wipe hard drive with random data option (2)
alias dd-sdd-full='sudo dd if=/dev/urandom of=/dev/sdd bs=8b conv=notrunc,noerror' # to wipe hard drive with random data option (2)
alias dd-sde-full='sudo dd if=/dev/urandom of=/dev/sde bs=8b conv=notrunc,noerror' # to wipe hard drive with random data option (2)
alias dd-sdf-full='sudo dd if=/dev/urandom of=/dev/sdf bs=8b conv=notrunc,noerror' # to wipe hard drive with random data option (2)
alias dd-sdg-full='sudo dd if=/dev/urandom of=/dev/sdg bs=8b conv=notrunc,noerror' # to wipe hard drive with random data option (2)

extract-file () {
if [ -f $1 ] ; then
case $1 in
*.tar.bz2) tar xjvf $1 ;;
*.tar.gz) tar xzvf $1 ;;
*.bz2) bunzip2 $1 ;;
*.rar) rar x $1 ;;
*.gz) gunzip $1 ;;
*.tar) tar xf $1 ;;
*.tbz2) tar xjvf $1 ;;
*.tgz) tar xzvf $1 ;;
*.zip) unzip $1 ;;
*.Z) uncompress $1 ;;
*.7z) 7z x $1 ;;
*) echo "'$1' cannot be extracted via extract-file" ;;
esac
else
echo "'$1' is not a valid file"
fi
}
```

---

### Post by TyrantWave on 2010-09-06
Dude. Use code tags, not quote tags.

---

### Post by stanca on 2010-09-07
Sorry.:rolleyes:My mistake.;):)

---

### Post by bodhi.zazen on 2010-09-07
> **stanca said:**
> Sorry.:rolleyes:My mistake.;):)

For long files, consider using an attachment.

---

### Post by Temetka on 2010-10-23
I'll play along.

First for the pretty:

[IMG]http://i27.photobucket.com/albums/c163/Temetka/TerminalWindow.png[/IMG]

Now to the code:

```

[ -z "$PS1" ] && return

# Bash completion
if [ -f /etc/bash_completion ]; then
	. /etc/bash_completion
fi

# Define a few Colours
BLACK='\e[0;30m'
BLUE='\e[0;34m'
GREEN='\e[0;32m'
CYAN='\e[0;36m'
RED='\e[0;31m'
PURPLE='\e[0;35m'
BROWN='\e[0;33m'
LIGHTGRAY='\e[0;37m'
DARKGRAY='\e[1;30m'
LIGHTBLUE='\e[1;34m'
LIGHTGREEN='\e[1;32m'
LIGHTCYAN='\e[1;36m'
LIGHTRED='\e[1;31m'
LIGHTPURPLE='\e[1;35m'
YELLOW='\e[1;33m'
WHITE='\e[1;37m'
NC='\e[0m'              # No Color

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

###############
### aliases ###
###############

# General
alias df='df -hT'
alias h='history'
alias d='cd /home/mike/Desktop'
alias open='gnome-open'
alias chm='kchmviewer'
alias install='sudo apt-get install'

# screenshots
alias screenshot='import -window root ~/Desktop/`date +%Y%m%d%H%M`.png'

# System info
alias cpuu="ps -e -o pcpu,cpu,nice,state,cputime,args --sort pcpu | sed '/^ 0.0 /d'"
alias memu='ps -e -o rss=,args= | sort -b -k1,1n | pr -TW$COLUMNS'
alias pg='ps aux | grep'  #requires an argument

# weather
alias weather='/home/mike/weather.sh'

# Music
alias ncmpc='ncmpc -cm'

# apt
#alias search='apt-cache search'
#alias agi='sudo apt-get install'
#alias agr='sudo apt-get remove'
#alias agu='sudo apt-get update'
#alias agg='sudo apt-get upgrade'
#alias sources='gksudo gedit /etc/apt/sources.list'

# interactive
alias cp='cp -vi'
alias mv='mv -vi'

# Directory navigation aliases
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

# network
alias net1='watch --interval=2 "sudo netstat -apn -l -A inet"'
alias net2='watch --interval=2 "sudo netstat -anp --inet --inet6"'  
alias net3='sudo lsof -i'
alias net4='watch --interval=2 "sudo netstat -p -e --inet --numeric-hosts"'
alias net5='watch --interval=2 "sudo netstat -tulpan"'
alias net6='sudo netstat -tulpan'
alias net7='watch --interval=2 "sudo netstat -utapen"'
alias net8='watch --interval=2 "sudo netstat -ano -l -A inet"'
alias netl='sudo nmap -sT -O localhost' # more here http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/security-guide/s1-server-ports.html
alias ping='ping -c 10'
alias whois='whois -H'

# listings
alias ls='ls --color=auto'
alias lh='ls -lah'                # human readable (sizes) long and all ;-)
alias lls='ls -l -h -g -F --color=auto'
alias lc='ls -aCF'
alias lsam='ls -am'               # List files horizontally
alias lr='ls -lR'                 # recursive
alias lsx='ls -ax'                # sort right to left rather then in columns
alias lss='ls -shAxSr'            # sort by size
alias lt='ls -lAtrh'              # sort by date and human readable
alias lm='ls -al |more'           # pipe through 'more'

# scripts


# chmod and permissions commands
alias mx='chmod a+x'
alias 000='chmod 000'
alias 644='chmod 644'
alias 755='chmod 755'
alias perm='stat --printf "%a %n \n "' # requires a file name e.g. perm file

# lynx web browser
alias bbc='lynx http://news.bbc.co.uk/text_only.stm'
alias nytimes='lynx http://nytimes.com'
alias dmregister='lynx http://desmoinesregister.com'
alias google='lynx http://google.co.uk'

# these, below, are without colour
#alias bbc='lynx -term=vt100 http://news.bbc.co.uk/text_only.stm'
#alias nytimes='lynx -term=vt100 http://nytimes.com'
#alias dmregister='lynx -term=vt100 http://desmoinesregister.com'
#alias google='lynx -term=vt100 http://google.co.uk'

# WELCOME SCREEN
#######################################################

clear

echo -ne "${LIGHTGREEN}" "Greetings, $USER. Todays date and time is, "; date
echo -e "${RED}"; cal ;  
echo -ne "${CYAN}";
echo 
echo -ne "${RED}Sysinfo:";uptime ;echo ""
echo -ne "${LIGHTGREEN}" ; uname -sro

# NOTES
#######################################################

# To temporarily bypass an alias, we preceed the command with a \  
# EG:  the ls command is aliased, but to use the normal ls command you would 
# type \ls 

#################
### FUNCTIONS ###
#################

function    ff               { find . -name $@ -print; }

function    rmd              { rm -fr $@; }

function    osr              { shutdown -r now; }
function    osh              { shutdown -h now; }

function    mfloppy          { mount /dev/fd0 /mnt/floppy; }
function    umfloppy         { umount /mnt/floppy; }

function    mdvd             { mount -t iso9660 -o ro /dev/dvd /mnt/dvd; }
function    umdvd            { umount /mnt/dvd; }

function    mcdrom           { mount -t iso9660 -o ro /dev/cdrom /mnt/cdrom; }
function    umcdrom          { umount /mnt/cdrom; }

function    psa              { ps aux $@; }
function    psu              { ps  ux $@; }

function    dub              { du -sclb $@; }
function    duk              { du -sclk $@; }
function    dum              { du -sclm $@; }

function    dfk              { df -PTak $@; }
function    dfm              { df -PTam $@; }
function    dfh              { df -PTah $@; }
function    dfi              { df -PTai $@; }

# SPECIAL FUNCTIONS
#######################################################
netinfo ()
{
echo "--------------- Network Information ---------------"
/sbin/ifconfig | awk /'inet addr/ {print $2}'
echo ""
/sbin/ifconfig | awk /'Bcast/ {print $3}'
echo ""
/sbin/ifconfig | awk /'inet addr/ {print $4}'

# /sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'
echo "---------------------------------------------------"
}

# Define a word - USAGE: define dog
define ()
{
lynx -dump "http://www.google.com/search?hl=en&q=define%3A+${1}&btnG=Google+Search" | grep -m 3 -w "*"  | sed 's/;/ -/g' | cut -d- -f1 > /tmp/templookup.txt
			if [[ -s  /tmp/templookup.txt ]] ;then	
				until ! read response
					do
					echo "${response}"
					done < /tmp/templookup.txt
				else
					echo "Sorry $USER, I can't find the term \"${1} \""				
			fi	
\rm -f /tmp/templookup.txt
}

#####################################
# ##### ENVIRONMENT VARIABLES ##### #
#####################################

declare -x HISTFILE=~/.bash_history
declare -x HISTCONTROL=ignoredups
declare -x HISTFILESIZE=100000
declare -x HISTSIZE=100000

############################## ##################################
# ##### PROMPT SECTION ##### ####################################
############################## ##################################

PS1="\[[31m\][\[[32m\]\u\[[31m\]]\[[32m\]\w > \[[39m\]"


```

---

### Post by Spice Weasel on 2010-10-23
```

alias nano='nano -S -O'
alias rm='rm -i'

PS1="\[\033[1;34m\](\[\033[1;37m\]\w\[\033[1;34m\]) \[\033[1;32m\]*\[\033[1;0m\] 

```

PS1: (black background, white plaintext)

[COLOR=DeepSkyBlue]([/COLOR]/path/to/directory[COLOR=DeepSkyBlue])[/COLOR] [COLOR=PaleGreen]*[/COLOR] nano

---

### Post by jelle_ on 2010-12-15
Here is mine. It's mainly a collection of commands from this tread. The only new part is the duf function:

```
# show the 10 largest files sorted and in human readable format
function duf {
du -sk "$@" | sort -n | while read size fname; 
	do for unit in k M G T P E Z Y; 
		do if [ $size -lt 1024 ]; 
		then echo -e "${size}${unit}\t${fname}"; 
			break; fi; size=$((size/1024)); 
		done; 
	done | tail -n 10 | tac
}
```

---

### Post by Zero2Nine on 2010-12-16
> **Temetka said:**
> I'll play along.

First for the pretty:

-cut image-

Now to the code:

-cut-

How do you get the terminal to display your name as [name] instead of name@computername? I tried to find that part in your script but can't see it.

---

### Post by bodhi.zazen on 2010-12-16
> **Zero2Nine said:**
> How do you get the terminal to display your name as [name] instead of name@computername? I tried to find that part in your script but can't see it.

in bash the prompt is "PS1"

from the bashrc posted the line, at the bottom, is

> PS1="\[[31m\][\[[32m\]\u\[[31m\]]\[[32m\]\w > \[[39m\]"

See also:

[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

---

### Post by Zero2Nine on 2010-12-17
> **bodhi.zazen said:**
> in bash the prompt is "PS1"

from the bashrc posted the line, at the bottom, is



See also:

[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

Thanks!

---

### Post by The Elite Noob on 2010-12-27
Here's mine, a work in progress, edited over time! 
I like it!

```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

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

#netinfo - shows network information for your system
netinfo ()
{
echo "--------------- Network Information ---------------"
/sbin/ifconfig | awk /'inet addr/ {print $2}'
/sbin/ifconfig | awk /'Bcast/ {print $3}'
/sbin/ifconfig | awk /'inet addr/ {print $4}'
/sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'
myip=`lynx -dump -hiddenlinks=ignore -nolist http://checkip.dyndns.org:8245/ | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g' `
echo "${myip}"
echo "---------------------------------------------------"
}

extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

dirsize ()
{
du -shx * .[a-zA-Z0-9_]* 2> /dev/null | \
egrep '^ *[0-9.]*[MG]' | sort -n > /tmp/list
egrep '^ *[0-9.]*M' /tmp/list
egrep '^ *[0-9.]*G' /tmp/list
rm -rf /tmp/list
}

# clock - A bash clock that can run in your terminal window.
clock (){
while true;do clear;echo "===========";date +"%r";echo "===========";sleep 1;done
}

# custom Bash alias
alias ..="cd .."
alias ...="cd ../.."
alias ....="cd ../../.."
alias .....="cd ../../../.."
alias list="ls -a"
alias man="man -a"
alias delete="rm -iv"
alias rm="rm -iv"
alias trash="rm -rf ~/.local/share/Trash/"
alias autoremove="sudo apt-get autoremove"
alias :q="exit"
alias home="cd ~"
alias unmount="umount"
alias clear="reset"
alias cdopen="eject"
alias cdclose="eject -t"
alias msg="notify-send"
alias update="sudo apt-get update"
alias shutdown="sudo shutdown -h now"
alias upgrade="sudo apt-get upgrade"
alias snano="sudo nano"
alias back="cd $OLDPWD"
alias root="sudo su"
alias ip="ifconfig"
alias purge="sudo apt-get remove --purge"
alias clean="sudo apt-get autoclean"
alias lynx="(lynx -accept_all_cookies)"


# for Websites
alias xkcd="firefox http://www.xkcd.com"
alias google="firefox http://www.google.com/ncr"
alias hackforums="firefox http://www.hackforums.net"
alias twitter="firefox http://www.twitter.com"
alias basilmarket="firefox http://www.basilmarket.com"
alias wiki="firefox http://en.wikipedia.org/wiki/Main_Page"
alias tuts="firefox http://www.tutsplus.com"
alias ubuntu="firefox http://www.ubuntu.com"

```

---

### Post by Quadunit404 on 2010-12-27
Began creating my own .bashrc, inspired by this thread. So far the only really custom part is the aliases part. Here it is so far:

```
# qu404's custom .bashrc. Makes using Linux far easier. Do note that not much has changed, though.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

#Some custom aliases
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias reinstall='sudo apt-get --reinstall install'
alias update='sudo apt-get update'
alias edit='gedit'
alias home='cd /home/tom'
alias downloads='cd /home/tom/Downloads'
alias music='cd /home/tom/Music'
alias documents='cd /home/tom/Documents'
alias copy='cp -vi'
alias remove='rm -vi'
alias move='mv -vi'
alias ping='ping -c 5'
alias addrepo='sudo add-apt-repository'
alias editbash='gedit .bashrc'
alias get='wget'
alias wingpanel=''/home/tom/Wingpanel/wingpanel/wingpanel''

#Extract things. Thanks to urukrama, Ubuntuforums.org
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}
```

---

### Post by ElMoshe on 2011-02-22
These have all been like insanely helpful, but I'm really confused on how do you do color etc.? Thanks!!

---

### Post by Quadunit404 on 2011-02-22
Read up on how to change the colors in your terminal online. It's really not that hard, especially since most browsers have a convenient search bar built-in.

Anyway, anyone look at the [ulitmate .bashrc]("http://ubuntuforums.org/showthread.php?t=1693307") I linked to earlier? Believe me, it's useful as hell.

EDIT: Here's my .bashrc as it currently stands:

```
# qu404's custom .bashrc. Makes using Linux far easier. Now with some custom functionality ripped from the Ulitmate .bashrc!

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Some custom aliases
alias install='sudo apt-get install'
alias uninstall='sudo apt-get remove'
alias reinstall='sudo apt-get --reinstall install'
alias update='sudo apt-get update'
alias edit='gedit'
alias home='cd /home/tom'
alias downloads='cd /home/tom/Downloads'
alias music='cd /home/tom/Music'
alias documents='cd /home/tom/Documents'
alias copy='cp -vi'
alias remove='rm -vi'
alias move='mv -vi'
alias ping='ping -c 5'
alias addrepo='sudo add-apt-repository'
alias editbash='gedit .bashrc'
alias flightgear='python /home/tom/fgo/fgo'
alias gnome-shell=''/home/tom/gnome-shell/install/bin/gnome-shell''
alias reloadterm='source ~/.bashrc'
alias dvdcopy='dvd2iso'

# Extract things. Thanks to urukrama, Ubuntuforums.org
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

# Alternative to "200 lines" kernel patch that does basically the same thing
if [ "$PS1" ] ; then  
   mkdir -p -m 0700 /dev/cgroup/cpu/user/$$ > /dev/null 2>&1
   echo $$ > /dev/cgroup/cpu/user/$$/tasks
   echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi

# Check to see if a site is down for everyone or just me
function downforme() {
	RED='\e[1;31m'
	GREEN='\e[1;32m'
	YELLOW='\e[1;33m'
	NC='\e[0m'
	if [ $# = 0 ]
	then
		echo -e "${YELLOW}usage:${NC} downforme website_url"
	else
		JUSTYOUARRAY=(`lynx -dump http://downforeveryoneorjustme.com/$1 | grep -o "It's just you"`)
		if [ ${#JUSTYOUARRAY} != 0 ]
		then
			echo -e "${RED}It's just you. \n${NC}$1 is up."
		else
			echo -e "${GREEN}It's not just you! \n${NC}$1 looks down from here."
		fi
	fi
}

# Rip audio from video
###### ("$1" for output file & "$2" for input file)
function audioextract()
{
mplayer -ao pcm -vo null -vc dummy -dumpaudio -dumpfile "$1" "$2"
}

# Dump DVDs to ISOs
function dvd2iso()
{
# to get desired device
df -h -x tmpfs -x usbfs
echo -n "Using the information in the terminal window, please enter the appropriate DVD drive:
"
read DVDDEVICE
echo -n "Please enter a name for the ISO file you will create:
"
read XVIDNAME
dd if="$DVDDEVICE" of="$XVIDNAME".iso
}


# Write ISOs
function writeiso() {
	# copyright 2007 - 2010 Christopher Bratusek
	if [[ $CD_WRITER ]]; then
		cdrecord dev=$CD_WRITER "$1"
	else	cdrecord deV=/dev/dvdrw "$1"
	fi
}

# Automagically make aliases
###### Usage: mkalias <name> "<command>"
# Example: mkalias rm "rm -i"
function mkalias()
{
        if [[ $1 && $2 ]]
        then
        echo -e "alias $1=\"$2\"" >> ~/.bashrc
        alias $1=$2
        fi
}

# Translation from the terminal!
function translate() { wget -qO- "http://ajax.googleapis.com/ajax/services/language/translate?v=1.0&q=$1&langpair=%7C${2:-en}" | sed 's/.*{"translatedText":"\([^"]*\)".*/\1\n/'; }



function translate_help() {
cat <<EOF
Language	ISO
(Afan) Oromo	om
Abkhazian	ab
Afar		aa
Afrikaans	af
Albanian	sq
Amharic		am
Arabic		ar
Armenian	hy
Assamese	as
Aymara		ay
Azerbaijani	az
Bashkir		ba
Basque		eu
Bengali		bn
Bhutani		dz
Bihari		bh
Bislama		bi
Breton		br
Bulgarian	bg
Burmese		my
Byelorussian	be
Cambodian	km
Catalan		ca
Chinese		zh
Corsican	co
Croatian	hr
Czech		cs
Danish		da
Dutch		nl
English		en
Esperanto	eo
Estonian	et
Faeroese	fo
Fiji		fj
Finnish		fi
French		fr
Frisian		fy
Galician	gl
Georgian	ka
German		de
Greek		el
Greenlandic	kl
Guarani		gn
Gujarati	gu
Hausa		ha
Hebrew 		he
(former iw)
Hindi		hi
Hungarian	hu
Icelandic	is
Indonesian 	id
(former in)
Interlingua	ia
Interlingue	ie
Inupiak		ik
Inuktitut 	iu
(Eskimo)
Irish		ga
Italian		it
Japanese	ja
Javanese	jw
Kannada		kn
Kashmiri	ks
Kazakh		kk
Kinyarwanda	rw
Kirghiz		ky
Kirundi		rn
Korean		ko
Kurdish		ku
Laothian	lo
Latin		la
Latvian, 	lv
Lettish
Lingala		ln
Lithuanian	lt
Macedonian	mk
Malagasy	mg
Malay		ms
Malayalam	ml
Maltese		mt
Maori		mi
Marathi		mr
Moldavian	mo
Mongolian	mn
Nauru		na
Nepali		ne
Norwegian	no
Occitan		oc
Oriya		or
Pashto, Pushto	ps
Persian		fa
Polish		pl
Portuguese	pt
Punjabi		pa
Quechua		qu
Rhaeto-Romance	rm
Romanian	ro
Russian		ru
Samoan		sm
Sangro		sg
Sanskrit	sa
Scots Gaelic	gd
Serbian		sr
Serbo-Croatian	sh
Sesotho		st
Setswana	tn
Shona		sn
Sindhi		sd
Singhalese	si
Siswati		ss
Slovak		sk
Slovenian	sl
Somali		so
Spanish		es
Sudanese	su
Swahili		sw
Swedish		sv
Tagalog		tl
Tajik		tg
Tamil		ta
Tatar		tt
Tegulu		te
Thai		th
Tibetan		bo
Tigrinya	ti
Tonga		to
Tsonga		ts
Turkish		tr
Turkmen		tk
Twi		tw
Uigur		ug
Ukrainian	uk
Urdu		ur
Uzbek		uz
Vietnamese	vi
Volapuk		vo
Welsh		cy
Wolof		wo
Xhosa		xh
Yiddish 	yi
(former ji)
Yoruba		yo
Zhuang		za
Zulu		zu
EOF
}

# Convert currencies
function currency_convert() { wget -qO- "http://www.google.com/finance/converter?a=$1&from=$2&to=$3&hl=es" | sed '/res/!d;s/<[^>]*>//g'; }



function currency_convert_help() {
cat <<EOF
AED - Emirati Dirham
AFN - Afghan Afghani
ALL - Albanian Lek
AMD - Armenian Dram
ANG - Dutch Guilder
AOA - Angolan Kwanza
ARS - Argentine Peso
AUD - Australian Dollar
AWG - Aruban or Dutch Guilder
AZN - Azerbaijani New Manat
BAM - Bosnian Convertible Marka
BBD - Barbadian or Bajan Dollar
BDT - Bangladeshi Taka
BGN - Bulgarian Lev
BHD - Bahraini Dinar
BIF - Burundian Franc
BMD - Bermudian Dollar
BND - Bruneian Dollar
BOB - Bolivian Boliviano
BRL - Brazilian Real
BSD - Bahamian Dollar
BTN - Bhutanese Ngultrum
BWP - Batswana Pula
BYR - Belarusian Ruble
BZD - Belizean Dollar
CAD - Canadian Dollar
CDF - Congolese Franc
CHF - Swiss Franc
CLP - Chilean Peso
CNY - Chinese Yuan Renminbi
COP - Colombian Peso
CRC - Costa Rican Colon
CUC - Cuban Convertible Peso
CUP - Cuban Peso
CVE - Cape Verdean Escudo
CZK - Czech Koruna
DJF - Djiboutian Franc
DKK - Danish Krone
DOP - Dominican Peso
DZD - Algerian Dinar
EEK - Estonian Kroon
EGP - Egyptian Pound
ERN - Eritrean Nakfa
ETB - Ethiopian Birr
EUR - Euro
FJD - Fijian Dollar
FKP - Falkland Island Pound
GBP - British Pound
GEL - Georgian Lari
GGP - Guernsey Pound
GHS - Ghanaian Cedi
GIP - Gibraltar Pound
GMD - Gambian Dalasi
GNF - Guinean Franc
GTQ - Guatemalan Quetzal
GYD - Guyanese Dollar
HKD - Hong Kong Dollar
HNL - Honduran Lempira
HRK - Croatian Kuna
HTG - Haitian Gourde
HUF - Hungarian Forint
IDR - Indonesian Rupiah
ILS - Israeli Shekel
IMP - Isle of Man Pound
INR - Indian Rupee
IQD - Iraqi Dinar
IRR - Iranian Rial
ISK - Icelandic Krona
JEP - Jersey Pound
JMD - Jamaican Dollar
JOD - Jordanian Dinar
JPY - Japanese Yen
KES - Kenyan Shilling
KGS - Kyrgyzstani Som
KHR - Cambodian Riel
KMF - Comoran Franc
KPW - Korean Won
KRW - Korean Won
KWD - Kuwaiti Dinar
KYD - Caymanian Dollar
KZT - Kazakhstani Tenge
LAK - Lao or Laotian Kip
LBP - Lebanese Pound
LKR - Sri Lankan Rupee
LRD - Liberian Dollar
LSL - Basotho Loti
LTL - Lithuanian Litas
LVL - Latvian Lat
LYD - Libyan Dinar
MAD - Moroccan Dirham
MDL - Moldovan Leu
MGA - Malagasy Ariary
MKD - Macedonian Denar
MMK - Burmese Kyat
MNT - Mongolian Tughrik
MOP - Macau Pataca
MRO - Mauritian Ouguiya
MUR - Mauritian Rupee
MVR - Maldivian Rufiyaa
MWK - Malawian Kwacha
MXN - Mexican Peso
MYR - Malaysian Ringgit
MZN - Mozambican Metical
NAD - Namibian Dollar
NGN - Nigerian Naira
NIO - Nicaraguan Cordoba
NOK - Norwegian Krone
NPR - Nepalese Rupee
NZD - New Zealand Dollar
OMR - Omani Rial
PAB - Panamanian Balboa
PEN - Peruvian Nuevo Sol
PGK - Papua New Guinean Kina
PHP - Philippine Peso
PKR - Pakistani Rupee
PLN - Polish Zloty
PYG - Paraguayan Guarani
QAR - Qatari Riyal
RON - Romanian New Leu
RSD - Serbian Dinar
RUB - Russian Ruble
RWF - Rwandan Franc
SAR - Saudi or Saudi Arabian Riyal
SBD - Solomon Islander Dollar
SCR - Seychellois Rupee
SDG - Sudanese Pound
SEK - Swedish Krona
SGD - Singapore Dollar
SHP - Saint Helenian Pound
SLL - Sierra Leonean Leone
SOS - Somali Shilling
SPL - Seborgan Luigino
SRD - Surinamese Dollar
STD - Sao Tomean Dobra
SVC - Salvadoran Colon
SYP - Syrian Pound
SZL - Swazi Lilangeni
THB - Thai Baht
TJS - Tajikistani Somoni
TMT - Turkmenistani Manat
TND - Tunisian Dinar
TOP - Tongan Pa'anga
TRY - Turkish Lira
TTD - Trinidadian Dollar
TVD - Tuvaluan Dollar
TWD - Taiwan New Dollar
TZS - Tanzanian Shilling
UAH - Ukrainian Hryvna
UGX - Ugandan Shilling
USD - US Dollar
UYU - Uruguayan Peso
UZS - Uzbekistani Som
VEF - Venezuelan Bolivar Fuerte
VND - Vietnamese Dong
VUV - Ni-Vanuatu Vatu
WST - Samoan Tala
XAF - Central African CFA Franc BEAC
XCD - East Caribbean Dollar
XDR - IMF Special Drawing Rights
XOF - CFA Franc
XPF - CFP Franc
YER - Yemeni Rial
ZAR - South African Rand
ZMK - Zambian Kwacha
ZWD - Zimbabwean Dollar
EOF
}

# cp with progress bar
function cp_p() {
	if [ `echo "$2" | grep ".*\/$"` ]
	then
		pv "$1" > "$2""$1"
	else
		pv "$1" > "$2"/"$1"
	fi
}

# Random oneliners
function oneliners()
{
w3m -dump_source http://www.onelinerz.net/random-one-liners/1/ | awk ' /.*<div id=\"oneliner_[0-9].*/ {while (! /\/div/ ) { gsub("\n", ""); getline; }; gsub (/<[^>][^>]*>/, "", $0); print $0}'
}

# Temporarily add directories to PATH
function apath()
{
    if [ $# -lt 1 ] || [ $# -gt 2 ]; then
        echo "Temporarily add to PATH"
        echo "usage: apath [dir]"
    else
        PATH=$1:$PATH
    fi
}

# Temperature conversion from the terminal
function convertatemp()
{
if uname | grep 'SunOS'>/dev/null ; then
  echo "Yep, SunOS, let\'s fix this baby"
  PATH="/usr/xpg4/bin:$PATH"
fi
if [ $# -eq 0 ] ; then
  cat << EOF >&2
Usage: $0 temperature[F|C|K]
where the suffix:
   F	indicates input is in Fahrenheit (default)
   C	indicates input is in Celsius
   K	indicates input is in Kelvin
EOF
fi
unit="$(echo $1|sed -e 's/[-[[:digit:]]*//g' | tr '[:lower:]' '[:upper:]' )"
temp="$(echo $1|sed -e 's/[^-[[:digit:]]*//g')"
case ${unit:=F}
in
  F ) # Fahrenheit to Celsius formula:  Tc = (F -32 ) / 1.8
  farn="$temp"
  cels="$(echo "scale=2;($farn - 32) / 1.8" | bc)"
  kelv="$(echo "scale=2;$cels + 273.15" | bc)"
  ;;
  C ) # Celsius to Fahrenheit formula: Tf = (9/5)*Tc+32
  cels=$temp
  kelv="$(echo "scale=2;$cels + 273.15" | bc)"
  farn="$(echo "scale=2;((9/5) * $cels) + 32" | bc)"
  ;;
  K ) # Celsius = Kelvin + 273.15, then use Cels -> Fahr formula
  kelv=$temp
  cels="$(echo "scale=2; $kelv - 273.15" | bc)"
  farn="$(echo "scale=2; ((9/5) * $cels) + 32" | bc)"
esac
echo "Fahrenheit = $farn"
echo "Celsius    = $cels"
echo "Kelvin     = $kelv"
}

# Tarbomb escape route
function atb() { l=$(tar tf $1); if [ $(echo "$l" | wc -l) -eq $(echo "$l" | grep $(echo "$l" | head -n1) | wc -l) ]; then tar xf $1; else mkdir ${1%.tar.gz} && tar xf $1 -C ${1%.tar.gz}; fi ; }

# Track flights from the command line
function flight_status() { if [[ $# -eq 3 ]];then offset=$3; else offset=0; fi; curl "http://mobile.flightview.com/TrackByRoute.aspx?view=detail&al="$1"&fn="$2"&dpdat=$(date +%Y%m%d -d ${offset}day)" 2>/dev/null |html2text |grep ":"; }

# Get media metadata easily
######   $1 = media file name
function mediainfo() {
    EXT=`echo "${1##*.}" | sed 's/\(.*\)/\L\1/'`
    if [ "$EXT" == "mp3" ]; then
        id3v2 -l "$1"
        echo
        mp3gain -s c "$1"
    elif [ "$EXT" == "flac" ]; then
        metaflac --list --block-type=STREAMINFO,VORBIS_COMMENT "$1"
    else
        echo "ERROR: Not a supported file type."
    fi
}

# jar decompiler
function unjar() { mkdir -p /tmp/unjar/$1 ; unzip -d /tmp/unjar/$1 $1 *class 1>/dev/null && find /tmp/unjar/$1 -name *class -type f | xargs jad -ff -nl -nonlb -o -p -pi99 -space -stat ; rm -r /tmp/unjar/$1 ; }

# Rip DVDs to MPG
function dvd2mpg()
{
# to get desired device
df -h -x tmpfs -x usbfs
echo -n "Using the information in the terminal window, please enter the appropriate DVD drive:
"
read DVDDEVICE
# to get desired title on dvd
# requires lsdvd: sudo apt-get install lsdvd
lsdvd "$DVDDEVICE"
echo -n "Using the information in the terminal window, please enter the title number you will convert (usually the longest one):
"
read DVDTITLE
echo -n "Please enter a name for the MPG/MPEG file you will convert:
"
read MPEGNAME
mplayer dvd://"$DVDTITLE" -dumpstream -alang es -dumpfile "$MPEGNAME".mpg
}

# Convert videos to AVI files
function conv2avi() {
	# copyright 2007 - 2010 Christopher Bratusek
	if [[ $(which mencoder-mt) != "" ]]; then
	mencoder-mt "$1" -lavdopts threads=8 \
	  -ovc xvid -xvidencopts fixed_quant=4 -of avi \
	  -oac mp3lame -lameopts vbr=3 \
	  -o "$1".avi
	else
	mencoder "$1" -lavdopts \
	  -ovc xvid -xvidencopts fixed_quant=4 -of avi \
	  -oac mp3lame -lameopts vbr=3 \
	  -o "$1".avi
	fi
}

# Remount devices
function remount() {
	# copyright 2007 - 2010 Christopher Bratusek
	DEVICE=$1
	shift
	mount -oremount,$@ $DEVICE
}

# Undo apt-get build-dep
function apt-get-remove-dep() { sudo aptitude markauto $(apt-cache showsrc "$1" | grep Build-Depends | perl -p -e 's/(?:[\[(].+?[\])]|Build-Depends:|,|\|)//g'); }

# Bored? Watch some TV!
function anatv()
{
echo -n "What analog/cable tv channel would you like to watch? (1-99)?:
"
read ANALOGSTATION
sh -c "mplayer -tv driver=v4l2:device=/dev/video1:input=0:norm=ntsc:chanlist=us-cable:channel="$ANALOGSTATION" tv:// & sox -r 48000 -t alsa hw:1,0 -t alsa hw:0,0"
}

# Optimize PNG files
function pngoptim()
{
       NAME_="pngoptim"
       HTML_="optimize png files"
    PURPOSE_="reduce the size of a PNG file if possible"
   SYNOPSIS_="$NAME_ [-hl] <file> [file...]"
   REQUIRES_="standard GNU commands, pngcrush"
    VERSION_="1.0"
       DATE_="2004-06-29; last update: 2004-12-30"
     AUTHOR_="Dawid Michalczyk <dm@eonworks.com>"
        URL_="www.comp.eonworks.com"
   CATEGORY_="gfx"
   PLATFORM_="Linux"
      SHELL_="bash"
 DISTRIBUTE_="yes"
# This program is distributed under the terms of the GNU General Public License
usage() {
echo >&2 "$NAME_ $VERSION_ - $PURPOSE_
Usage: $SYNOPSIS_
Requires: $REQUIRES_
Options:
     -h, usage and options (this help)
     -l, see this script"
exit 1
}
# tmp file set up
tmp_1=/tmp/tmp.${RANDOM}$$
# signal trapping and tmp file removal
trap 'rm -f $tmp_1 >/dev/null 2>&1' 0
trap "exit 1" 1 2 3 15
# var init
old_total=0
new_total=0
# arg handling and main execution
case "$1" in
    -h) usage ;;
    -l) more $0; exit 1 ;;
     *.*) # main execution
        # check if required command is in $PATH variable
        which pngcrush &> /dev/null
        [[ $? != 0 ]] && { echo >&2 required \"pngcrush\" command is not in your PATH; exit 1; }
        for a in "$@";do
            if [ -f $a ] && [[ ${a##*.} == [pP][nN][gG] ]]; then
                old_size=$(ls -l $a | { read b c d e f g; echo $f ;} )
                echo -n "${NAME_}: $a $old_size -> "
                pngcrush -q $a $tmp_1
                rm -f -- $a
                mv -- $tmp_1 $a
                new_size=$(ls -l $a | { read b c d e f g; echo $f ;} )
                echo $new_size bytes
                (( old_total += old_size ))
                (( new_total += new_size ))
            else
                echo ${NAME_}: file $a either does not exist or is not a png file
            fi
        done ;;
    *) echo ${NAME_}: skipping $1 ; continue ;;
esac
percentage=$(echo "scale = 2; ($new_total*100)/$old_total" | bc)
reduction=$(echo $(( old_total - new_total )) \
| sed '{ s/$/@/; : loop; s/\(...\)@/@.\1/; t loop; s/@//; s/^\.//; }')
echo "${NAME_}: total size reduction: $reduction bytes (total size reduced to ${percentage}%)"
}
```

Huge innit?

---

### Post by akvik on 2011-05-25
Hi,

As you might know, you can make your own "commands" in the terminal by adding aliases in a file called .bash_aliases in your home directory. 

**You can add more or less useful stuff as bash aliases, and I want to know which ones you have made that makes your life easier?**

Here are mine:
```

alias f='more ~/.bash_history | grep '

```
This one makes it damn easy to find previous commands, just type: **f whatever**, and all commands that contains 'whatever' comes up. I think this works better than CTRL+R and so on.

```

alias suno='sudo nano'

```
Nano as root = suno :)

```

alias upgrade='sudo apt-get update && sudo apt-get upgrade'

```
Typing **upgrade** refreshes the repositories and suggests updates to install.

```

alias ll='ls -lh'
alias la='ls -A'
alias l='ls -CF'

```
These are not mine, but very handy - shortens the use of ls variations.

Keep'em coming!

---

### Post by andrewc6l on 2011-05-25
alias 'cd..'='cd ..'

---

### Post by Tibuda on 2011-05-25
```
alias back='cd - > /dev/null'
alias home='cd ~'

```

---

### Post by bodhi.zazen on 2011-05-25
> **Tibuda said:**
> ```
alias back='cd - > /dev/null'
alias home='cd ~'

```

You do understand the cd , without any arguments, goes to home ?
home is also abbreviated with a tide ~

so 

```
cd
```

is much shorter then typing 'home'

also there is already a .bashrc thread, which I will merge this into ...

---

### Post by Tibuda on 2011-05-25
only if $HOME is set, but yeah I feel stupid

---

### Post by COKEDUDE on 2012-06-01
Lets revive this topic :).

---

### Post by KiwiNZ on 2012-06-01
Back to sleep

---

