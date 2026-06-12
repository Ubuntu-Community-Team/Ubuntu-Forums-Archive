---
title: "Post your .zshrc here with a description of what it does!"
date: 2007-08-23
forum: The Cafe
---

### Post by smartboyathome on 2007-08-23
I am wondering what everyone is using for their zshrc files (zsh is a shell similar to bash, for everyone who doesn't know). I will start this off by posting mine:
```

######################################################################
#           jdong's zshrc file, based on:
#		      mako's zshrc file, v0.1
#
# 
######################################################################

# next lets set some enviromental/shell pref stuff up
# setopt NOHUP
#setopt NOTIFY
#setopt NO_FLOW_CONTROL
setopt INC_APPEND_HISTORY SHARE_HISTORY
setopt APPEND_HISTORY
# setopt AUTO_LIST		# these two should be turned off
# setopt AUTO_REMOVE_SLASH
# setopt AUTO_RESUME		# tries to resume command of same name
unsetopt BG_NICE		# do NOT nice bg commands
setopt CORRECT			# command CORRECTION
setopt EXTENDED_HISTORY		# puts timestamps in the history
# setopt HASH_CMDS		# turns on hashing
#
setopt MENUCOMPLETE
setopt ALL_EXPORT

# Set/unset  shell options
setopt   notify globdots correct pushdtohome cdablevars autolist
setopt   correctall autocd recexact longlistjobs
setopt   autoresume histignoredups pushdsilent 
setopt   autopushd pushdminus extendedglob rcquotes mailwarning
unsetopt bgnice autoparamslash

# Autoload zsh modules when they are referenced
zmodload -a zsh/stat stat
zmodload -a zsh/zpty zpty
zmodload -a zsh/zprof zprof
zmodload -ap zsh/mapfile mapfile


PATH="/opt/local/bin:/opt/local/sbin:/usr/local/bin:/usr/local/sbin/:$PATH"
TZ="America/New_York"
HISTFILE=$HOME/.zhistory
HISTSIZE=1000
SAVEHIST=1000
HOSTNAME="`hostname`"
PAGER='less'
EDITOR='vim'
    autoload colors zsh/terminfo
    if [[ "$terminfo[colors]" -ge 8 ]]; then
   colors
    fi
    for color in RED GREEN YELLOW BLUE MAGENTA CYAN WHITE; do
   eval PR_$color='%{$terminfo[bold]$fg[${(L)color}]%}'
   eval PR_LIGHT_$color='%{$fg[${(L)color}]%}'
   (( count = $count + 1 ))
    done
    PR_NO_COLOR="%{$terminfo[sgr0]%}"
PS1="[$PR_BLUE%n$PR_MAGENTA@$PR_RED%U%m%u$PR_NO_COLOR:$PR_RED%2c$PR_NO_COLOR]%(!.#.$) "
RPS1="$PR_LIGHT_YELLOW(%D{%m-%d %H:%M})$PR_NO_COLOR"
#LANGUAGE=
LC_ALL='en_US.UTF-8'
LANG='en_US.UTF-8'
LC_CTYPE=C

if [ $SSH_TTY ]; then
  MUTT_EDITOR=vim
else
  MUTT_EDITOR=emacsclient.emacs-snapshot
fi

unsetopt ALL_EXPORT
# # --------------------------------------------------------------------
# # aliases
# # --------------------------------------------------------------------

alias slrn="slrn -n"
alias man='LC_ALL=C LANG=C man'
alias f=finger
alias ll='ls -al'
alias ls='ls --color=auto '
alias offlineimap-tty='offlineimap -u TTY.TTYUI'
alias hnb-partecs='hnb $HOME/partecs/partecs-hnb.xml'
alias rest2html-css='rst2html --embed-stylesheet --stylesheet-path=/usr/share/python-docutils/s5_html/themes/default/print.css'
#if [[ $HOSTNAME == "kamna" ]] {
#	alias emacs='emacs -l ~/.emacs.kamna'
#}	

# alias	=clear

#chpwd() {
#     [[ -t 1 ]] || return
#     case $TERM in
#     sun-cmd) print -Pn "\e]l%~\e\\"
#     ;;
#    *xterm*|screen|rxvt|(dt|k|E)term) print -Pn "\e]2;%~\a"
#    ;;
#    esac
#}

#chpwd

autoload -U compinit
compinit
bindkey "^?" backward-delete-char
bindkey '^[OH' beginning-of-line
bindkey '^[OF' end-of-line
bindkey '^[[5~' up-line-or-history
bindkey '^[[6~' down-line-or-history
bindkey "^r" history-incremental-search-backward
bindkey ' ' magic-space    # also do history expansion on space
bindkey '^I' complete-word # complete on tab, leave expansion to _expand
zstyle ':completion::complete:*' use-cache on
zstyle ':completion::complete:*' cache-path ~/.zsh/cache/$HOST

zstyle ':completion:*' list-colors ${(s.:.)LS_COLORS}
zstyle ':completion:*' list-prompt '%SAt %p: Hit TAB for more, or the character to insert%s'
zstyle ':completion:*' menu select=1 _complete _ignored _approximate
zstyle -e ':completion:*:approximate:*' max-errors \
    'reply=( $(( ($#PREFIX+$#SUFFIX)/2 )) numeric )'
zstyle ':completion:*' select-prompt '%SScrolling active: current selection at %p%s'

# Completion Styles

# list of completers to use
zstyle ':completion:*::::' completer _expand _complete _ignored _approximate

# allow one error for every three characters typed in approximate completer
zstyle -e ':completion:*:approximate:*' max-errors \
    'reply=( $(( ($#PREFIX+$#SUFFIX)/2 )) numeric )'
    
# insert all expansions for expand completer
zstyle ':completion:*:expand:*' tag-order all-expansions

# formatting and messages
zstyle ':completion:*' verbose yes
zstyle ':completion:*:descriptions' format '%B%d%b'
zstyle ':completion:*:messages' format '%d'
zstyle ':completion:*:warnings' format 'No matches for: %d'
zstyle ':completion:*:corrections' format '%B%d (errors: %e)%b'
zstyle ':completion:*' group-name ''

# match uppercase from lowercase
zstyle ':completion:*' matcher-list 'm:{a-z}={A-Z}'

# offer indexes before parameters in subscripts
zstyle ':completion:*:*:-subscript-:*' tag-order indexes parameters

# command for process lists, the local web server details and host completion
# on processes completion complete all user processes
zstyle ':completion:*:processes' command 'ps -au$USER'

## add colors to processes for kill completion
zstyle ':completion:*:*:kill:*:processes' list-colors '=(#b) #([0-9]#)*=0=01;31'

#zstyle ':completion:*:processes' command 'ps -o pid,s,nice,stime,args'
#zstyle ':completion:*:urls' local 'www' '/var/www/htdocs' 'public_html'
#
#NEW completion:
# 1. All /etc/hosts hostnames are in autocomplete
# 2. If you have a comment in /etc/hosts like #%foobar.domain,
#    then foobar.domain will show up in autocomplete!
zstyle ':completion:*' hosts $(awk '/^[^#]/ {print $2 $3" "$4" "$5}' /etc/hosts | grep -v ip6- && grep "^#%" /etc/hosts | awk -F% '{print $2}') 
# Filename suffixes to ignore during completion (except after rm command)
zstyle ':completion:*:*:(^rm):*:*files' ignored-patterns '*?.o' '*?.c~' \
    '*?.old' '*?.pro'
# the same for old style completion
#fignore=(.o .c~ .old .pro)

# ignore completion functions (until the _ignored completer)
zstyle ':completion:*:functions' ignored-patterns '_*'
zstyle ':completion:*:*:*:users' ignored-patterns \
        adm apache bin daemon games gdm halt ident junkbust lp mail mailnull \
        named news nfsnobody nobody nscd ntp operator pcap postgres radvd \
        rpc rpcuser rpm shutdown squid sshd sync uucp vcsa xfs avahi-autoipd\
        avahi backup messagebus beagleindex debian-tor dhcp dnsmasq fetchmail\
        firebird gnats haldaemon hplip irc klog list man cupsys postfix\
        proxy syslog www-data mldonkey sys snort
# SSH Completion
zstyle ':completion:*:scp:*' tag-order \
   files users 'hosts:-host hosts:-domain:domain hosts:-ipaddr"IP\ Address *'
zstyle ':completion:*:scp:*' group-order \
   files all-files users hosts-domain hosts-host hosts-ipaddr
zstyle ':completion:*:ssh:*' tag-order \
   users 'hosts:-host hosts:-domain:domain hosts:-ipaddr"IP\ Address *'
zstyle ':completion:*:ssh:*' group-order \
   hosts-domain hosts-host users hosts-ipaddr
zstyle '*' single-ignored show

```

It is basically the zshrc from [here]("http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/") with edited colors. Is there any way to get the colors to be dark gray (username), gray (@), and light gray (computer name)? I tried editing the colors to include that, but it didn't work.

---

### Post by bonzodog on 2007-08-23
```

######################################################################
#           jdong's zshrc file v0.2.1 , based on:
#		      mako's zshrc file, v0.1
#
# 
######################################################################

# next lets set some enviromental/shell pref stuff up
# setopt NOHUP
#setopt NOTIFY
#setopt NO_FLOW_CONTROL
setopt INC_APPEND_HISTORY SHARE_HISTORY
setopt APPEND_HISTORY
# setopt AUTO_LIST		# these two should be turned off
# setopt AUTO_REMOVE_SLASH
# setopt AUTO_RESUME		# tries to resume command of same name
unsetopt BG_NICE		# do NOT nice bg commands
setopt CORRECT			# command CORRECTION
setopt EXTENDED_HISTORY		# puts timestamps in the history
# setopt HASH_CMDS		# turns on hashing
#
setopt MENUCOMPLETE
setopt ALL_EXPORT

# Set/unset  shell options
setopt   notify globdots correct pushdtohome cdablevars autolist
setopt   correctall autocd recexact longlistjobs
setopt   autoresume histignoredups pushdsilent 
setopt   autopushd pushdminus extendedglob rcquotes mailwarning
unsetopt bgnice autoparamslash

# Autoload zsh modules when they are referenced
zmodload -a zsh/stat stat
zmodload -a zsh/zpty zpty
zmodload -a zsh/zprof zprof
zmodload -ap zsh/mapfile mapfile


PATH="/usr/local/bin:/usr/local/sbin/:/bin:/sbin:/usr/bin:/usr/sbin:$PATH"
#TZ="etc/Dublin"
HISTFILE=$HOME/.zhistory
HISTSIZE=1000
SAVEHIST=1000
HOSTNAME="`hostname`"
PAGER='less'
EDITOR='nano'
    autoload colors zsh/terminfo
    if [[ "$terminfo[colors]" -ge 8 ]]; then
   colors
    fi
    for color in RED GREEN YELLOW BLUE MAGENTA CYAN WHITE; do
   eval PR_$color='%{$terminfo[bold]$fg[${(L)color}]%}'
   eval PR_LIGHT_$color='%{$fg[${(L)color}]%}'
   (( count = $count + 1 ))
    done
    PR_NO_COLOR="%{$terminfo[sgr0]%}"
PS1="%~-> "
RPS1="[%T]"
#LANGUAGE=
LC_ALL='en_IE.UTF-8'
LANG='en_IE.UTF-8'
LC_CTYPE=C

if [ $SSH_TTY ]; then
  MUTT_EDITOR=nano
else
  MUTT_EDITOR=emacsclient.emacs-snapshot
fi

unsetopt ALL_EXPORT
# # --------------------------------------------------------------------
# # aliases
# # --------------------------------------------------------------------

alias slrn="slrn -n"
alias man='LC_ALL=C LANG=C man'
alias f=finger
alias ll='ls -al'
alias ls='ls --color=auto '
alias offlineimap-tty='offlineimap -u TTY.TTYUI'
alias hnb-partecs='hnb $HOME/partecs/partecs-hnb.xml'
alias rest2html-css='rst2html --embed-stylesheet --stylesheet-path=/usr/share/python-docutils/s5_html/themes/default/print.css'
#if [[ $HOSTNAME == "kamna" ]] {
#	alias emacs='emacs -l ~/.emacs.kamna'
#}	

# alias	=clear

#chpwd() {
#     [[ -t 1 ]] || return
#     case $TERM in
#     sun-cmd) print -Pn "\e]l%~\e\\"
#     ;;
#    *xterm*|screen|rxvt|(dt|k|E)term) print -Pn "\e]2;%~\a"
#    ;;
#    esac
#}
selfupdate(){
        URL="http://stuff.mit.edu/~jdong/misc/zshrc"
        echo "Updating zshrc from $URL..."
        echo "Press Ctrl+C within 5 seconds to abort..."
        sleep 5
        cp ~/.zshrc ~/.zshrc.old
        wget $URL -O ~/.zshrc
        echo "Done; existing .zshrc saved as .zshrc.old"
}
#chpwd

autoload -U compinit
compinit
bindkey "^?" backward-delete-char
bindkey '^[OH' beginning-of-line
bindkey '^[OF' end-of-line
bindkey '^[[5~' up-line-or-history
bindkey '^[[6~' down-line-or-history
bindkey "^r" history-incremental-search-backward
bindkey ' ' magic-space    # also do history expansion on space
bindkey '^I' complete-word # complete on tab, leave expansion to _expand
zstyle ':completion::complete:*' use-cache on
zstyle ':completion::complete:*' cache-path ~/.zsh/cache/$HOST

zstyle ':completion:*' list-colors ${(s.:.)LS_COLORS}
zstyle ':completion:*' list-prompt '%SAt %p: Hit TAB for more, or the character to insert%s'
zstyle ':completion:*' menu select=1 _complete _ignored _approximate
zstyle -e ':completion:*:approximate:*' max-errors \
    'reply=( $(( ($#PREFIX+$#SUFFIX)/2 )) numeric )'
zstyle ':completion:*' select-prompt '%SScrolling active: current selection at %p%s'

# Completion Styles

# list of completers to use
zstyle ':completion:*::::' completer _expand _complete _ignored _approximate

# allow one error for every three characters typed in approximate completer
zstyle -e ':completion:*:approximate:*' max-errors \
    'reply=( $(( ($#PREFIX+$#SUFFIX)/2 )) numeric )'
    
# insert all expansions for expand completer
zstyle ':completion:*:expand:*' tag-order all-expansions

# formatting and messages
zstyle ':completion:*' verbose yes
zstyle ':completion:*:descriptions' format '%B%d%b'
zstyle ':completion:*:messages' format '%d'
zstyle ':completion:*:warnings' format 'No matches for: %d'
zstyle ':completion:*:corrections' format '%B%d (errors: %e)%b'
zstyle ':completion:*' group-name ''

# match uppercase from lowercase
zstyle ':completion:*' matcher-list 'm:{a-z}={A-Z}'

# offer indexes before parameters in subscripts
zstyle ':completion:*:*:-subscript-:*' tag-order indexes parameters

# command for process lists, the local web server details and host completion
# on processes completion complete all user processes
zstyle ':completion:*:processes' command 'ps -au$USER'

## add colors to processes for kill completion
zstyle ':completion:*:*:kill:*:processes' list-colors '=(#b) #([0-9]#)*=0=01;31'

#zstyle ':completion:*:processes' command 'ps -o pid,s,nice,stime,args'
#zstyle ':completion:*:urls' local 'www' '/var/www/htdocs' 'public_html'
#
#NEW completion:
# 1. All /etc/hosts hostnames are in autocomplete
# 2. If you have a comment in /etc/hosts like #%foobar.domain,
#    then foobar.domain will show up in autocomplete!
zstyle ':completion:*' hosts $(awk '/^[^#]/ {print $2 $3" "$4" "$5}' /etc/hosts | grep -v ip6- && grep "^#%" /etc/hosts | awk -F% '{print $2}') 
# Filename suffixes to ignore during completion (except after rm command)
zstyle ':completion:*:*:(^rm):*:*files' ignored-patterns '*?.o' '*?.c~' \
    '*?.old' '*?.pro'
# the same for old style completion
#fignore=(.o .c~ .old .pro)

# ignore completion functions (until the _ignored completer)
zstyle ':completion:*:functions' ignored-patterns '_*'
zstyle ':completion:*:*:*:users' ignored-patterns \
        adm apache bin daemon games gdm halt ident junkbust lp mail mailnull \
        named news nfsnobody nobody nscd ntp operator pcap postgres radvd \
        rpc rpcuser rpm shutdown squid sshd sync uucp vcsa xfs avahi-autoipd\
        avahi backup messagebus beagleindex debian-tor dhcp dnsmasq fetchmail\
        firebird gnats haldaemon hplip irc klog list man cupsys postfix\
        proxy syslog www-data mldonkey sys snort
# SSH Completion
zstyle ':completion:*:scp:*' tag-order \
   files users 'hosts:-host hosts:-domain:domain hosts:-ipaddr"IP\ Address *'
zstyle ':completion:*:scp:*' group-order \
   files all-files users hosts-domain hosts-host hosts-ipaddr
zstyle ':completion:*:ssh:*' tag-order \
   users 'hosts:-host hosts:-domain:domain hosts:-ipaddr"IP\ Address *'
zstyle ':completion:*:ssh:*' group-order \
   hosts-domain hosts-host users hosts-ipaddr
zstyle '*' single-ignored show

```

This is more or less jdongs file, with a minor mod to the PS1 prompts, and the timezone/locale adjusted. I have zsh set as the default shell for my user account, but root still has bash as SLiM plays up if I try to run it from zsh as well.

---

### Post by bonzodog on 2008-02-19
I am going to bump this one :D

Does anyone else use zsh as their shell?

---

### Post by detgar on 2008-02-19
I use Zsh instead of Bash simply to avoid a few annoying bugs + better tab-completion, so this is nothing advanced or well thought out, but it works well for me.

```
setopt appendhistory autocd nomatch
unsetopt beep
zstyle :compinstall filename '/home/chris/.zshrc'

autoload -Uz compinit
compinit

fpath=(~/.zsh_fns $fpath)
autoload -U promptinit
promptinit
prompt adam2

## emacs key bindings
bindkey -e

## The file to save the history in when an interactive shell exits.
## If unset, the history is not saved.
HISTFILE=

## The maximum number of events stored in the internal history list.
HISTSIZE=100

## Stuff from ~/.bashrc

## If not running interactively, don't do anything
[ -z "$PS1" ] && return

## make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

## case-insensitive (uppercase from lowercase) completion
zstyle ':completion:*' matcher-list 'm:{a-z}={A-Z}'

## make less colourful
export LESS_TERMCAP_mb=$'\E[01;31m'
export LESS_TERMCAP_md=$'\E[01;31m'
export LESS_TERMCAP_me=$'\E[0m'
export LESS_TERMCAP_se=$'\E[0m'
export LESS_TERMCAP_so=$'\E[01;44;33m'
export LESS_TERMCAP_ue=$'\E[0m'
export LESS_TERMCAP_us=$'\E[01;32m'
## /Stuff

## Alias
	alias	ls='ls --color=auto -F'
	alias	sl='ls'
	alias	lsa='ls --color=auto -FA'
	alias	lsl='ls --color=auto -Fl'
	alias	ap='sudo aptitude'
	alias	apu='sudo aptitude update'
	alias	apsu='sudo aptitude safe-upgrade'
	alias	apfu='sudo aptitude full-upgrade'
	alias	aps='aptitude search'
	alias	apss='aptitude show'
	alias	api='sudo aptitude install'
	alias	apurge='sudo aptitude purge'
## /Alias
```

Some lines are from the beginner-config thing, some are from the default Ubuntu .bashrc file, some are stuff I found online.

---

### Post by smartboyathome on 2008-08-27
My new .zshrc, compiling a bunch of pieces or .zshrcs from around the web with my own customizations. Based originally off of jdong's zshrc. Best thing in here is that it includes aliases which change directories, does a few things, then goes back to the directory you were in. There are other things as well, but I don't feel like explaining them. :p

```
######################################################################
#          smartboyathome's .zshrc v0.1, based on:                   #
#           jdong's zshrc file v0.2.1 , based on:                    #
#		      mako's zshrc file, v0.1                        #
#                                                                    #
#                                                                    #
######################################################################

# next lets set some enviromental/shell pref stuff up
# setopt NOHUP
#setopt NOTIFY
#setopt NO_FLOW_CONTROL
setopt INC_APPEND_HISTORY SHARE_HISTORY
setopt APPEND_HISTORY
# setopt AUTO_LIST		# these two should be turned off
# setopt AUTO_REMOVE_SLASH
# setopt AUTO_RESUME		# tries to resume command of same name
unsetopt BG_NICE		# do NOT nice bg commands
setopt CORRECT			# command CORRECTION
setopt EXTENDED_HISTORY		# puts timestamps in the history
# setopt HASH_CMDS		# turns on hashing
#
setopt MENUCOMPLETE
setopt ALL_EXPORT

# Set/unset  shell options
setopt   notify globdots correct pushdtohome cdablevars autolist
setopt   correctall autocd recexact longlistjobs
setopt   autoresume histignoredups pushdsilent 
setopt   autopushd pushdminus extendedglob rcquotes mailwarning
unsetopt bgnice autoparamslash

# Autoload zsh modules when they are referenced
zmodload -a zsh/stat stat
zmodload -a zsh/zpty zpty
zmodload -a zsh/zprof zprof
zmodload -ap zsh/mapfile mapfile


PATH="/usr/local/bin:/usr/local/sbin/:/bin:/sbin:/usr/bin:/usr/sbin:$PATH"
TZ="America/Los_Angeles"
HISTFILE=$HOME/.zhistory
HISTSIZE=1000
SAVEHIST=1000
HOSTNAME="`hostname`"
PAGER='less'
EDITOR='gedit'
BROWSER='firefox'
    autoload colors zsh/terminfo
    if [[ "$terminfo[colors]" -ge 8 ]]; then
   colors
    fi
    for color in RED GREEN YELLOW BLUE MAGENTA CYAN WHITE; do
   eval PR_$color='%{$terminfo[bold]$fg[${(L)color}]%}'
   eval PR_LIGHT_$color='%{$fg[${(L)color}]%}'
   (( count = $count + 1 ))
    done
    PR_NO_COLOR="%{$terminfo[sgr0]%}"
PS1="$PR_RED($PR_GREEN%U%n@%m%u: $PR_BLUE%2c$PR_RED)%(!.#.$) $PR_NO_COLOR"
#LANGUAGE=
LC_ALL='en_US.UTF-8'
LANG='en_US.UTF-8'
LC_CTYPE=C

unsetopt ALL_EXPORT
# # --------------------------------------------------------------------
# # aliases
# # --------------------------------------------------------------------
##Helpful Arch Linux Aliases
alias install='yaourt -S'
alias update='yaourt -Sy'
alias upgrade='yaourt -Syu'
alias remove='yaourt -R'
alias group-install='sudo pacman -S'

##Other aliases
alias su='sudo -i'
alias upesvn='_CURRENTDIR=`pwd` && cd ~/ecvs/esvn/ && svn update && cd ~/ecvs/esvn-backup/ && svn update && cd $_CURRENTDIR' # Saves your current directory, changes to e17's svn directory, as well as the backup directory, and updates both, then goes back to your current directory
alias gotoesvn='cd ~/ecvs/esvn/trunk/' # Changes to E17's svn trunk folder
alias mknewe17theme='_CURRENTDIR=`pwd` && cd ~/ecvs/esvn/trunk/THEMES/b_and_w/ && edje_cc theme.edc new_e17.edj && cp new_e17.edj ~/.e/e/themes && enlightenment_remote -restart && cd $_CURRENTDIR' # Updates the new e17 theme and then changes back to the working directory

#if [[ $HOSTNAME == "kamna" ]] {
#	alias emacs='emacs -l ~/.emacs.kamna'
#}	

# alias	=clear

#chpwd() {
#     [[ -t 1 ]] || return
#     case $TERM in
#     sun-cmd) print -Pn "\e]l%~\e\\"
#     ;;
#    *xterm*|screen|rxvt|(dt|k|E)term) print -Pn "\e]2;%~\a"
#    ;;
#    esac
#}
#chpwd

autoload -U compinit
compinit
bindkey "^?" backward-delete-char
bindkey '^[OH' beginning-of-line
bindkey '^[OF' end-of-line
bindkey '^[[5~' up-line-or-history
bindkey '^[[6~' down-line-or-history
bindkey "^r" history-incremental-search-backward
bindkey ' ' magic-space    # also do history expansion on space
bindkey '^I' complete-word # complete on tab, leave expansion to _expand
zstyle ':completion::complete:*' use-cache on
zstyle ':completion::complete:*' cache-path ~/.zsh/cache/$HOST

zstyle ':completion:*' list-colors ${(s.:.)LS_COLORS}
zstyle ':completion:*' list-prompt '%SAt %p: Hit TAB for more, or the character to insert%s'
zstyle ':completion:*' menu select=1 _complete _ignored _approximate
zstyle -e ':completion:*:approximate:*' max-errors \
    'reply=( $(( ($#PREFIX+$#SUFFIX)/2 )) numeric )'
zstyle ':completion:*' select-prompt '%SScrolling active: current selection at %p%s'

# Completion Styles

# list of completers to use
zstyle ':completion:*::::' completer _expand _complete _ignored _approximate

# allow one error for every three characters typed in approximate completer
zstyle -e ':completion:*:approximate:*' max-errors \
    'reply=( $(( ($#PREFIX+$#SUFFIX)/2 )) numeric )'
    
# insert all expansions for expand completer
zstyle ':completion:*:expand:*' tag-order all-expansions

# formatting and messages
zstyle ':completion:*' verbose yes
zstyle ':completion:*:descriptions' format '%B%d%b'
zstyle ':completion:*:messages' format '%d'
zstyle ':completion:*:warnings' format 'No matches for: %d'
zstyle ':completion:*:corrections' format '%B%d (errors: %e)%b'
zstyle ':completion:*' group-name ''

# match uppercase from lowercase
zstyle ':completion:*' matcher-list 'm:{a-z}={A-Z}' 'm:{a-zA-Z}={A-Za-z}'

# offer indexes before parameters in subscripts
zstyle ':completion:*:*:-subscript-:*' tag-order indexes parameters

# command for process lists, the local web server details and host completion
# on processes completion complete all user processes
# zstyle ':completion:*:processes' command 'ps -au$USER'

## add colors to processes for kill completion
zstyle ':completion:*:*:kill:*:processes' list-colors '=(#b) #([0-9]#)*=0=01;31'

#zstyle ':completion:*:processes' command 'ps ax -o pid,s,nice,stime,args | sed "/ps/d"'
zstyle ':completion:*:*:kill:*:processes' command 'ps --forest -A -o pid,user,cmd'
zstyle ':completion:*:processes-names' command 'ps axho command' 
#zstyle ':completion:*:urls' local 'www' '/var/www/htdocs' 'public_html'
#
#NEW completion:
# 1. All /etc/hosts hostnames are in autocomplete
# 2. If you have a comment in /etc/hosts like #%foobar.domain,
#    then foobar.domain will show up in autocomplete!
zstyle ':completion:*' hosts $(awk '/^[^#]/ {print $2 $3" "$4" "$5}' /etc/hosts | grep -v ip6- && grep "^#%" /etc/hosts | awk -F% '{print $2}') 
# Filename suffixes to ignore during completion (except after rm command)
zstyle ':completion:*:*:(^rm):*:*files' ignored-patterns '*?.o' '*?.c~' \
    '*?.old' '*?.pro'
# the same for old style completion
#fignore=(.o .c~ .old .pro)

# ignore completion functions (until the _ignored completer)
zstyle ':completion:*:functions' ignored-patterns '_*'
zstyle ':completion:*:*:*:users' ignored-patterns \
        adm apache bin daemon games gdm halt ident junkbust lp mail mailnull \
        named news nfsnobody nobody nscd ntp operator pcap postgres radvd \
        rpc rpcuser rpm shutdown squid sshd sync uucp vcsa xfs avahi-autoipd\
        avahi backup messagebus beagleindex debian-tor dhcp dnsmasq fetchmail\
        firebird gnats haldaemon hplip irc klog list man cupsys postfix\
        proxy syslog www-data mldonkey sys snort
# SSH Completion
zstyle ':completion:*:scp:*' tag-order \
   files users 'hosts:-host hosts:-domain:domain hosts:-ipaddr"IP\ Address *'
zstyle ':completion:*:scp:*' group-order \
   files all-files users hosts-domain hosts-host hosts-ipaddr
zstyle ':completion:*:ssh:*' tag-order \
   users 'hosts:-host hosts:-domain:domain hosts:-ipaddr"IP\ Address *'
zstyle ':completion:*:ssh:*' group-order \
   hosts-domain hosts-host users hosts-ipaddr
zstyle '*' single-ignored show
```

---

### Post by Alasdair on 2008-08-27
My zshrc is based of a load of things I found of the web, and some stuff I did myself. The prompt is a heavily modified (read: simplified) version of Phil's classic zsh prompt. I don't know how anyone could use bash when zsh exists. :)

[PHP]### Alasdair's zshrc

autoload -Uz compinit

## If not running interactively, do nothing
[ -z "$PS1" ] && return

## Emacs style key bindings
bindkey -e

## History
HISTSIZE=1000
SAVEHIST=1000
HISTFILE=~/.zshhist

setopt hist_ignore_dups extended_history inc_append_history no_hist_beep

## Completion settings
# from compinstall
zstyle ':completion:*' completer _expand _complete _correct
zstyle ':completion:*' list '' #list-color for colored completion
zstyle ':completion:*' matcher-list '' 'm:{a-z}={A-Z}' 'm:{a-zA-Z}={A-Za-z}' 'r:|[._-]=** r:|=**'
zstyle ':completion:*' max-errors 3 numeric
zstyle ':completion:*' menu select=1
zstyle ':completion:*' select-prompt %SScrolling active: current selection at %p%s

zstyle :compinstall filename '/home/alasdair/.zshrc'

compinit

setopt prompt_subst

## Load colors
autoload colors zsh/terminfo
if [[ "$terminfo[colors]" -ge 8 ]]; then
    colors
fi
for color in RED GREEN YELLOW BLUE MAGENTA CYAN WHITE; do
    eval PR_B_$color='%{$terminfo[bold]$fg[${(L)color}]%}'
    eval PR_$color='%{$fg[${(L)color}]%}'
    (( count = $count + 1 ))
done
PR_NO_COLOR="%{$terminfo[sgr0]%}"
PR_B='%{$terminfo[bold]%}'

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
PR_LEND=${altchar[u]:--}
PR_REND=${altchar[t]:--}
 
# Standard blue prompt. Color can be changed using the --color4 urxvt option or using Xdefaults file
PS1="$PR_B$PR_BLUE$PR_SHIFT_IN$PR_ULCORNER\
$PR_HBAR$PR_HBAR$PR_HBAR$PR_LEND\
$PR_SHIFT_OUT${PR_B}\
[$PR_BLUE$PR_NO_COLOR%l$PR_BLUE${PR_B}]\
[$PR_BLUE$PR_NO_COLOR%/$PR_BLUE${PR_B}]
$PR_BLUE$PR_SHIFT_IN$PR_LLCORNER$PR_HBAR$PR_LEND\
$PR_SHIFT_OUT$PR_NO_COLOR "

# main prompt screws up when not using a terminal in X. Use a simpler one.
test $TERM = 'linux' && PS1="${PR_CYAN}[${PR_NO_COLOR}%l${PR_CYAN}][${PR_NO_COLOR}%/${PR_CYAN}]>${PR_NO_COLOR}"

##aliases
#alias pin="sudo pacman -S"
#alias yin="sudo yaourt -S"
#alias prem="sudo pacman -R"
#alias yrem="sudo yaourt -R"
#alias supg="sudo pacman -Syu"
#alias pcs="pacman -Ss"
#alias ycs="yaourt -Ss"
alias sin="sudo aptitude install"
alias acs="apt-cache search"
alias srem="sudo aptitude remove"
alias ls="ls --color=auto"
alias ll="ls -l"
alias la="ls -a"
alias lla="ls -l -a"
alias cls="clear"

## misc
# the one true editor
export EDITOR=emacs

export MANPAGER=most

# if we using an xterm or rxvt set the title to pts/x
case $TERM in
    xterm*|rxvt*)
        print -Pn "\e]0;%l\a"
        ;;
esac[/PHP]

---

### Post by smartboyathome on 2008-08-27
Thanks, Alasdair. Changed
```
# match uppercase from lowercase
zstyle ':completion:*' matcher-list 'm:{a-z}={A-Z}'
```
to
```
# match uppercase from lowercase
zstyle ':completion:*' matcher-list 'm:{a-z}={A-Z}' 'm:{a-zA-Z}={A-Za-z}'
```

---

### Post by Deadmode on 2008-11-20
Awesome thanks!

---

### Post by smartboyathome on 2008-11-20
> **Deadmode said:**
> Awesome thanks!

You're welcome. I have an updated version of my .zshrc, which splits it into two files, one for user-set settings, and one for more default type settings. Here are the two files:
**_.zshrc:_**
```
######################################################################
#          smartboyathome's .zshrc v0.3, based on:                   #
#           jdong's zshrc file v0.2.1 , based on:                    #
#		      mako's zshrc file, v0.1                        #
#                                                                    #
#                                                                    #
######################################################################

# next lets set some enviromental/shell pref stuff up
# setopt NOHUP
#setopt NOTIFY
#setopt NO_FLOW_CONTROL
setopt INC_APPEND_HISTORY SHARE_HISTORY
setopt APPEND_HISTORY
# setopt AUTO_LIST		# these two should be turned off
# setopt AUTO_REMOVE_SLASH
# setopt AUTO_RESUME		# tries to resume command of same name
unsetopt BG_NICE		# do NOT nice bg commands
setopt CORRECT			# command CORRECTION
setopt EXTENDED_HISTORY		# puts timestamps in the history
# setopt HASH_CMDS		# turns on hashing
#
setopt MENUCOMPLETE
setopt ALL_EXPORT

# Set/unset  shell options
setopt   notify globdots correct pushdtohome cdablevars autolist
setopt   correctall autocd recexact longlistjobs
setopt   autoresume histignoredups pushdsilent
setopt   autopushd pushdminus extendedglob rcquotes mailwarning
unsetopt bgnice autoparamslash

# Autoload zsh modules when they are referenced
zmodload -a zsh/stat stat
zmodload -a zsh/zpty zpty
zmodload -a zsh/zprof zprof
zmodload -ap zsh/mapfile mapfile

TZ="America/Los_Angeles"
HISTFILE=$HOME/.zhistory
HISTSIZE=1000
SAVEHIST=1000
HOSTNAME="`hostname`"
PAGER='less'
EDITOR='gedit'
BROWSER='firefox'
    autoload colors zsh/terminfo
    if [[ "$terminfo[colors]" -ge 8 ]]; then
   colors
    fi
    for color in RED GREEN YELLOW BLUE MAGENTA CYAN WHITE; do
   eval PR_$color='%{$terminfo[bold]$fg[${(L)color}]%}'
   eval PR_LIGHT_$color='%{$fg[${(L)color}]%}'
   (( count = $count + 1 ))
    done
    PR_NO_COLOR="%{$terminfo[sgr0]%}"
PS1="$PR_RED($PR_GREEN%U%n@%m%u: $PR_BLUE%2c$PR_RED)%(!.#.$) $PR_NO_COLOR"
#LANGUAGE=
LC_ALL='en_US.UTF-8'
LANG='en_US.UTF-8'
LC_CTYPE=C

unsetopt ALL_EXPORT

#if [[ $HOSTNAME == "kamna" ]] {
#	alias emacs='emacs -l ~/.emacs.kamna'
#}	

# alias	=clear

#chpwd() {
#     [[ -t 1 ]] || return
#     case $TERM in
#     sun-cmd) print -Pn "\e]l%~\e\\"
#     ;;
#    *xterm*|screen|rxvt|(dt|k|E)term) print -Pn "\e]2;%~\a"
#    ;;
#    esac
#}
#chpwd

autoload -U compinit
compinit
bindkey "^?" backward-delete-char
bindkey '^[OH' beginning-of-line
bindkey '^[OF' end-of-line
bindkey '^[[5~' up-line-or-history
bindkey '^[[6~' down-line-or-history
bindkey "^r" history-incremental-search-backward
bindkey ' ' magic-space    # also do history expansion on space
bindkey '^I' complete-word # complete on tab, leave expansion to _expand
zstyle ':completion::complete:*' use-cache on
zstyle ':completion::complete:*' cache-path ~/.zsh/cache/$HOST

zstyle ':completion:*' list-colors ${(s.:.)LS_COLORS}
zstyle ':completion:*' list-prompt '%SAt %p: Hit TAB for more, or the character to insert%s'
zstyle ':completion:*' menu select=1 _complete _ignored _approximate
zstyle -e ':completion:*:approximate:*' max-errors \
    'reply=( $(( ($#PREFIX+$#SUFFIX)/2 )) numeric )'
zstyle ':completion:*' select-prompt '%SScrolling active: current selection at %p%s'

# Completion Styles

# list of completers to use
zstyle ':completion:*::::' completer _expand _complete _ignored _approximate

# allow one error for every three characters typed in approximate completer
zstyle -e ':completion:*:approximate:*' max-errors \
    'reply=( $(( ($#PREFIX+$#SUFFIX)/2 )) numeric )'

# insert all expansions for expand completer
zstyle ':completion:*:expand:*' tag-order all-expansions

# formatting and messages
zstyle ':completion:*' verbose yes
zstyle ':completion:*:descriptions' format '%B%d%b'
zstyle ':completion:*:messages' format '%d'
zstyle ':completion:*:warnings' format 'No matches for: %d'
zstyle ':completion:*:corrections' format '%B%d (errors: %e)%b'
zstyle ':completion:*' group-name ''

# match uppercase from lowercase
zstyle ':completion:*' matcher-list 'm:{a-z}={A-Z}' 'm:{a-zA-Z}={A-Za-z}'

# offer indexes before parameters in subscripts
zstyle ':completion:*:*:-subscript-:*' tag-order indexes parameters

# command for process lists, the local web server details and host completion
# on processes completion complete all user processes
# zstyle ':completion:*:processes' command 'ps -au$USER'

## add colors to processes for kill completion
zstyle ':completion:*:*:kill:*:processes' list-colors '=(#b) #([0-9]#)*=0=01;31'

#zstyle ':completion:*:processes' command 'ps ax -o pid,s,nice,stime,args | sed "/ps/d"'
zstyle ':completion:*:*:kill:*:processes' command 'ps --forest -A -o pid,user,cmd'
zstyle ':completion:*:processes-names' command 'ps axho command'
#zstyle ':completion:*:urls' local 'www' '/var/www/htdocs' 'public_html'
#
#NEW completion:
# 1. All /etc/hosts hostnames are in autocomplete
# 2. If you have a comment in /etc/hosts like #%foobar.domain,
#    then foobar.domain will show up in autocomplete!
zstyle ':completion:*' hosts $(awk '/^[^#]/ {print $2 $3" "$4" "$5}' /etc/hosts | grep -v ip6- && grep "^#%" /etc/hosts | awk -F% '{print $2}') # Filename suffixes to ignore during completion (except after rm command)
zstyle ':completion:*:*:(^rm):*:*files' ignored-patterns '*?.o' '*?.c~' \
    '*?.old' '*?.pro'
# the same for old style completion
#fignore=(.o .c~ .old .pro)

# ignore completion functions (until the _ignored completer)
zstyle ':completion:*:functions' ignored-patterns '_*'
zstyle ':completion:*:*:*:users' ignored-patterns \
        adm apache bin daemon games gdm halt ident junkbust lp mail mailnull \
        named news nfsnobody nobody nscd ntp operator pcap postgres radvd \
        rpc rpcuser rpm shutdown squid sshd sync uucp vcsa xfs avahi-autoipd\
        avahi backup messagebus beagleindex debian-tor dhcp dnsmasq fetchmail\
        firebird gnats haldaemon hplip irc klog list man cupsys postfix\
        proxy syslog www-data mldonkey sys snort
# SSH Completion
zstyle ':completion:*:scp:*' tag-order \
   files users 'hosts:-host hosts:-domain:domain hosts:-ipaddr"IP\ Address *'
zstyle ':completion:*:scp:*' group-order \
   files all-files users hosts-domain hosts-host hosts-ipaddr
zstyle ':completion:*:ssh:*' tag-order \
   users 'hosts:-host hosts:-domain:domain hosts:-ipaddr"IP\ Address *'
zstyle ':completion:*:ssh:*' group-order \
   hosts-domain hosts-host users hosts-ipaddr
zstyle '*' single-ignored show

##Additions to zshrc
if [ -f ~/.zshrc-additions ]; then
    . ~/.zshrc-additions
fi

##THIS MAKES YAOURT WORK, DON'T TAKE IT OUT!
export color=
```

The last 3 lines can be deleted if you aren't on Arch Linux.

**_.zshrc-additions_**
```
##Helpful Arch Linux Aliases
alias install='yaourt -S'
alias update='yaourt -Sy'
alias upgrade='yaourt -Syu'
alias remove='yaourt -R'
alias search='yaourt -Ss'
alias group-install='sudo pacman -S'
alias install-local='sudo pacman -U'

##Helpful Ubuntu Aliases
#alias install='sudo apt-get install'
#alias update='sudo apt-get update'
#alias upgrade='sudo apt-get upgrade'
#alias dist-upgrade='sudo apt-get dist-upgrade'
#alias remove='sudo apt-get remove'
#alias autoremove='sudo apt-get autoremove'
#alias apt-source='apt-get source'
#alias apt-search='apt-cache search'

##Other aliases
alias untarbz2='tar -xvjf'
alias untargz='tar -xvzf'
alias listbz2='tar -tjf'
alias listgz='tar -tzf'
alias edit-cli='$CLIEDITOR'
alias suedit-cli='sudo $CLIEDITOR'
alias edit='$GUIEDITOR'
alias suedit='gksu $GUIEDITOR
alias start-timidity='timidity -iA -B2,8 -Oj -s 44100'
alias su='sudo -i'
#alias upesvn='_CURRENTDIR=`pwd` && cd ~/ecvs/esvn/ && svn update && cd ~/ecvs/esvn-backup/ && svn update && cd $_CURRENTDIR' # Saves your current directory, changes to e17's svn directory, as well as the backup directory, and updates both, then goes back to your current directory
#alias gotoesvn='cd ~/ecvs/esvn/trunk/' # Changes to E17's svn trunk folder
#alias mknewe17theme='_CURRENTDIR=`pwd` && cd ~/ecvs/esvn/trunk/THEMES/b_and_w/ && edje_cc theme.edc new_e17.edj && cp new_e17.edj ~/.e/e/themes && enlightenment_remote -restart && cd $_CURRENTDIR' # Updates the new e17 theme and then changes back to the working directory

##Environment variables
export CLIEDITOR=nano
export GUIEDITOR=gedit

##Commands to run at start
cowsay `fortune`
```

Uncomment the Ubuntu lines and comment out the Arch lines if you are on Ubuntu. The e17 commands are commented out but left in as references for basically making a script into an alias. The CLI/GUI Editor variables are for the edit aliases I set to make it easier for myself to remember the command I use no matter what the editor I am using. Finally, the cowsay line just executes cowsay with the output of fortune in it, as what it says can be funny sometimes. ;)

---

### Post by olejorgen on 2008-11-20
I'll clean mine up when I get some time. (after exams :))

---

### Post by smartboyathome on 2008-11-20
> **olejorgen said:**
> I'll clean mine up when I get some time. (after exams :))

Even without cleaning it up, it can be posted. Mine is just well commented because it is left over from jdong's zshrc.

---

### Post by Deadmode on 2008-12-08
> **smartboyathome said:**
> You're welcome. I have an updated version of my .zshrc, which splits it into two files, one for user-set settings, and one for more default type settings. Here are the two files

out of curiosity what should I name the second .zshrc file?

Edit: ehh sorry stupid question lol I'm tired... I have exams this week.  Thanks again.

---

### Post by bobbocanfly on 2008-12-08
```
## David Futcher (bobbo)'s .zshrc
## Heavily based on elcasey's, jdong's and jpds's zshrcs

export LC_ALL="en_GB.UTF-8"             # Use British English...
export LANG="en_GB.UTF-8"               # ...as default language.
export TZ="Europe/London"               # Force our time zone this location.
export EDITOR="vim"                     # Long live vim (as our editor).
export NAME="David Futcher"             # Our name.
export EMAIL="bobbo@ubuntu.com"         # Our email address.
export GPGKEY="0x2A51FBCD"              # Our GnuPG key ID.
export DEBFULLNAME=$NAME                # These are used by Debian packaging...
export DEBEMAIL=$EMAIL                  # ...programs.
export DEBSIGN_KEYID=$GPGKEY            # Key ID for signing Debian packages.
export GIT_AUTHOR_NAME=$NAME            # Use our real name for Git.
export BZR_EMAIL=$EMAIL                 # Override email for Bazaar.
export MPD_HOST="localhost"             # Music playing daemon host
export MPD_PORT="6600"                  # Music playing daemon port

## Some functions to make my life easier

# Launches uTorrent and pipes its debug output (theres a lot of it) to /dev/null
function utorrent() {
    return=$(pwd)
    cd ~/.wine/drive_c/Program\ Files/uTorrent/
    wine uTorrent.exe 2> /dev/null &
    cd $return
}

# Updates the mpd database and restarts the daemon
function mpd-update() {
    sudo mpd --create-db
    sudo /etc/init.d/mpd restart
}

# Starts mpd in a clean way
function mpd-start() {
    if [[ -d /media/truecrypt2/MP3 ]]; then
        if [[ $(ps ax | grep -v "scribble" | grep "/usr/bin/mpd" | grep -v "grep" | wc -l) -gt 0 ]]; 
        then
            echo "MPD already running"
        else          
            sudo /etc/init.d/mpd start     
        fi      
          
        # Now check if mpdscribble is running
        if [[ $(ps ax | grep "/usr/bin/mpdscribble" | grep -v "grep" | wc -l) -lt 0 ]]; 
        then
            sudo /etc/init.d/mpscribble start
        fi   
    else
        echo "You haven't mounted your music yet!"
    fi
}

function pyinst() {
    sudo python setup.py clean
    sudo python setup.py build
    sudo python setup.py install
}

function mount-iso() {
    sudo mount -o loop -t iso9660 $1 $2
}

precmd() {  
    ## Hacky Bazaar and Git info in the prompt
    export VCS=""
    base=""
    
    for i in $(pwd | awk '{ split($0,a,"/"); for (i=1; i<=100; i++) print a[i]}')
    do
        base=$base/$i
        if [[ -d $base/.bzr ]];
        then     
            export VCS="bzr:$(basename $base)@rev$(bzr revno) "
        else
            if [[ -d $base/.git ]];
            then
                export VCS=" git:$(basename $(pwd))@rev$(git-log | grep Date: | wc -l)"
            fi
        fi
    done
        
    export PS1="%{$fg[red]%}%n%{$reset_color%}@%{$fg[blue]%}%m%{$reset_color%}% > "
    export RPROMPT="%{$fg[blue]%} $(pwd) %{$fg[red]%}$VCS%{$reset_color%}" # I'm sure there will be a builtin for this....care
}
## END FUNCTIONS

HISTFILE=~/.histfile
HISTSIZE=1000
SAVEHIST=1717

alias untar="tar xzfvv"           # for tarballs
alias unbz2="tar xvvfj"           # for .bz2 archives
alias ls="ls --classify --color=always"
alias grep="grep --colour=always"

bindkey '\e[3~' delete-char
bindkey -s '^n^p' $'ncmpc\n' # Launch ncmpc pressing CTRL+{N,P}

# Autoload zsh modules when they are referenced
zmodload -a zsh/stat stat
zmodload -a zsh/zpty zpty
zmodload -a zsh/zprof zprof
zmodload -ap zsh/mapfile mapfile
autoload -U colors; colors

# Load the completion system
autoload -U compinit; compinit

zstyle ':completion::complete:*' use-cache on
zstyle ':completion::complete:*' cache-path ~/.zsh/cache/$HOST

zstyle ':completion:*' list-colors ${(s.:.)LS_COLORS}
zstyle ':completion:*' list-prompt '%SAt %p: Hit TAB for more, or the character to insert%s'
zstyle ':completion:*' menu select=1 _complete _ignored _approximate
zstyle -e ':completion:*:approximate:*' max-errors \
    'reply=( $(( ($#PREFIX+$#SUFFIX)/2 )) numeric )'
zstyle ':completion:*' select-prompt '%SScrolling active: current selection at %p%s'

# Completion Styles

# list of completers to use
zstyle ':completion:*::::' completer _expand _complete _ignored _approximate

# allow one error for every three characters typed in approximate completer
zstyle -e ':completion:*:approximate:*' max-errors \
    'reply=( $(( ($#PREFIX+$#SUFFIX)/2 )) numeric )'
    
# insert all expansions for expand completer
zstyle ':completion:*:expand:*' tag-order all-expansions

# formatting and messages
zstyle ':completion:*' verbose yes
zstyle ':completion:*:descriptions' format '%B%d%b'
zstyle ':completion:*:messages' format '%d'
zstyle ':completion:*:warnings' format 'No matches for: %d'
zstyle ':completion:*:corrections' format '%B%d (errors: %e)%b'
zstyle ':completion:*' group-name ''

# match uppercase from lowercase
zstyle ':completion:*' matcher-list 'm:{a-z}={A-Z}'

# offer indexes before parameters in subscripts
zstyle ':completion:*:*:-subscript-:*' tag-order indexes parameters

# command for process lists, the local web server details and host completion
# on processes completion complete all user processes
zstyle ':completion:*:processes' command 'ps -au$USER'

## add colors to processes for kill completion
zstyle ':completion:*:*:kill:*:processes' list-colors '=(#b) #([0-9]#)*=0=01;31'

#zstyle ':completion:*:processes' command 'ps -o pid,s,nice,stime,args'
#zstyle ':completion:*:urls' local 'www' '/var/www/htdocs' 'public_html'
#
#NEW completion:
# 1. All /etc/hosts hostnames are in autocomplete
# 2. If you have a comment in /etc/hosts like #%foobar.domain,
#    then foobar.domain will show up in autocomplete!
zstyle ':completion:*' hosts $(grep "^#%" /etc/hosts | awk -F% '{print $2}') 
# Filename suffixes to ignore during completion (except after rm command)
zstyle ':completion:*:*:(^rm):*:*files' ignored-patterns '*?.o' '*?.c~' \
    '*?.old' '*?.pro'
# the same for old style completion
#fignore=(.o .c~ .old .pro)

# ignore completion functions (until the _ignored completer)
zstyle ':completion:*:functions' ignored-patterns '_*'
zstyle ':completion:*:*:*:users' ignored-patterns \
        adm apache bin daemon games gdm halt ident junkbust lp mail mailnull \
        named news nfsnobody nobody nscd ntp operator pcap postgres radvd \
        rpc rpcuser rpm shutdown squid sshd sync uucp vcsa xfs avahi-autoipd\
        avahi backup messagebus beagleindex debian-tor dhcp dnsmasq fetchmail\
        firebird gnats haldaemon hplip irc klog list man cupsys postfix\
        proxy syslog www-data mldonkey sys snort
# SSH Completion
zstyle ':completion:*:scp:*' tag-order \
   files users 'hosts:-host hosts:-domain:domain hosts:-ipaddr"IP\ Address *'
zstyle ':completion:*:scp:*' group-order \
   files all-files users hosts-domain hosts-host hosts-ipaddr
zstyle ':completion:*:ssh:*' tag-order \
   users 'hosts:-host hosts:-domain:domain hosts:-ipaddr"IP\ Address *'
zstyle ':completion:*:ssh:*' group-order \
   hosts-domain hosts-host users hosts-ipaddr
zstyle '*' single-ignored show  


```

The first little bit sets up env vars, most of it for packaging sofware. Then setup for MPD and some functions because I am lazy. precmd() sets up my prompt. It detects any version control systems being used, then prints the branch name and current version number on the right prompt. The rest of it is some shiny completion stuff.

---

### Post by smartboyathome on 2008-12-08
> **Deadmode said:**
> out of curiosity what should I name the second .zshrc file?

Edit: ehh sorry stupid question lol I'm tired... I have exams this week.  Thanks again.

You can change the name in the last line of the main .zshrc file.

---

### Post by bodhi.zazen on 2008-12-08
I am also a fan of zsh. It is too bad a default install of zsh does not include a "decent" .zshrc :(

At any rate, a few resources ...

[http://grml.org/zsh/](http://grml.org/zsh/)

Tons of excellent links in that first one :)

[http://grml.org/zsh/zsh-lovers.html](http://grml.org/zsh/zsh-lovers.html)

---

