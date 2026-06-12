---
title: "What are your favorite BASH aliases?"
date: 2009-04-23
forum: The Cafe
---

### Post by pw_f100_220 on 2009-04-23
Just curious if anyone came up with any fun ones as well as downright ingenious.  I mostly use Fluxbox so i use xrandr to work with dual monitors on my laptop:

alias mirror='xrandr --output LVDS --auto --output VGA --auto --same-as LVDS'
alias right='xrandr --output VGA --auto --right-of LVDS'
alias left='xrandr --output VGA --auto --left-of LVDS'

One I'm not quite as proud of, but in my earliest days of Ubuntu, I looked forever for the command to delete directories only to find it's an option of rm...so I named the alias to reflect my frustration:

alias ****='rm -rf'  

It really is rather poetic when deleting a bad movie...~$ **** Hitman

:)

---

### Post by Tibuda on 2009-04-23
```
alias ..='cd ..'
alias ~='cd ~'
alias ?='man'
alias !='sudo'
alias +='pager'
alias open='xdg-open'
alias browser='x-www-browser'
alias edit='gedit'
alias apt='sudo aptitude'
alias todo='grep -n TODO *.*'
```

---

### Post by monsterstack on 2009-05-06
Reviving old thread because I' always interested in adding extra stuff to my aliases files.

I've been using zsh for quite a while now. I like not having to use the *cd* command to switch directories. Still I fire up Bash every now and again and my aliases files for both zsh and bash are largely similar, so I'll post it here.

```

######################################
# ****'s super awesome bash aliases. #
# Includes bits and pieces from all  #
# over the web. Sharing is caring.   # 
######################################


###############################################################
# Directories and college stuff.                              #
###############################################################
alias ..='cd ..'
alias met='cd ~/classnotes/meteorology && ls'
alias stab='cd ~/classnotes/stability && ls'
alias law='cd ~/classnotes/law && ls'
alias biz='cd ~/classnotes/business && ls'
alias mkgo='mkdir $1 && cd $1'

###############################################################
# Lists and greps.                                            #
###############################################################
alias lh='ls -cd .*'              # Hidden files only.
alias ll='ls -lh'                 # Long list.
alias la='ls -ca'                 # List everything.
alias ld='ls -cd */'              # Directories only.
alias lda='ls -cda */'            # Directories only (including hidden ones).
alias ldh='ls -cda .*/'           # Hidden directories only.
alias lf='ls -p | grep -v "/$"'   # Files only.
alias lfa='ls -ap | grep -v "/$"' # Files only (including hidden ones).

alias gg='grep --color=auto'          # grep.
alias gi='grep --color=auto -i'       # grep sans case-sensitivity.
alias gv='grep -v'                    # Exclusive grep.
alias gvi='grep -vi'                  # Exclusive grep sans case-sensitivity.


###############################################################
# I can make noises.                                          #
###############################################################
alias beep='echo -en "\007"'

###############################################################
# Loadry, unloadry stuff.                                     #
# Standard apt-get install, remove. Nuke, well, nukes stuff.  #
###############################################################
function loadry () { if [ $(whoami) != "root" ] ; then sudo apt-get install $@; else apt-get install $@; fi; }
function deaden () { if [ $(whoami) != "root" ] ; then sudo apt-get remove $@; else apt-get remove $@; fi; }
function nuke() { if [ $(whoami) != "root" ] ; then 
   for x in $@; do sudo apt-get autoremove --purge $x; done; else 
   for x in $@; do apt-get autoremove --purge $x; done; fi; }
function search() { apt-cache search $@; }
function show() { for x in $@; do apt-cache show $x; done; }

###############################################################
# Productivity!                                               #
###############################################################

# Adds date to the beginning of selected file names,
# in year-month-day format. Used the for loop to skip
# over files that don't exist or are mis-spelled.
function datestamp() { for x in $@; do
   if [ -e $x ]; then mv $x $(date +'%F')-$x; echo "Renamed $x successfully."; else
   echo "$x? File doesn't exist, fool."; fi; done; }

# Put a batch of images in a pdf file for emailing.
#
function pdfit() { convert -adjoin -page A4 *.jpg $1.pdf; }

# Extract archives quickly
function ex ()
{
  if [ -f "$1" ] ; then
    case "$1" in
      *.tar)                tar xf $1        ;;
      *.tar.bz2 | *.tbz2 )  tar xjvf $1        ;;
      *.tar.gz | *.tgz )    tar xzvf $1     ;;
      *.bz2)                bunzip2 $1       ;;
      *.rar)                unrar x $1     ;;
      *.gz)                 gunzip $1     ;;
      *.zip)                unzip $1     ;;
      *.Z)                  uncompress $1  ;;
      *.7z)                 7z x $1    ;;
      *)   echo ""${1}" cannot be extracted via extract()" ;;
     esac
   else
     echo ""${1}" is not a valid file"
   fi
}



###############################################################
# Fun stuff.                                                  #
###############################################################

# Random Futurama quote.
#
function futurama() { curl -Is slashdot.org | egrep '^X-(F|B|L)' | cut -d \- -f 2; }

```

---

