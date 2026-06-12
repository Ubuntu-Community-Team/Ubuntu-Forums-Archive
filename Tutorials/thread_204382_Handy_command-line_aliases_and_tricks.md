---
title: "Handy command-line aliases and tricks"
date: 2006-06-26
forum: Tutorials
---

### Post by mssever on 2006-06-26
I often find that filesystem tasks are quicker from the command line. So, I've compiled some of my favorite aliases and tricks. Note that these have only been tested in bash (bash is the default shell--or command interpreter--in most flavors of Linux, including Ubuntu).

[CENTER][SIZE=3]**Command Editing**[/SIZE]
[/CENTER]
**Tab completion:** type part of a command name or filename and hit tab. Bash will automatically fill in as much as it can unambiguously. If you hit tab twice, bash will show you a list of commands/filenames that match what you've typed so far.

**Searching through your history:** If you hit ^R (Ctrl+R) then start typing, bash will display the last match from your command history. Hit enter to execute the displayed command, left or right arrow to edit the command, or ^C to cancel.

[CENTER][SIZE=3]**Job Control**[/SIZE][/CENTER]
Typing ^Z stops a program without exiting and gives you back a command line. You can use this to do several things at once. Type [FONT=courier new][COLOR=green]fg[/COLOR][/FONT] to bring the program back to the front or [FONT=courier new][COLOR=green]bg[/COLOR][/FONT] to tell it to resume in the background. Append an ampersand (&) to the end of a command to start a program in the background. Type [FONT=courier new][COLOR=green]jobs[/COLOR][/FONT] for a list of current jobs.

> **userundefine said:**
> Let's not forget to mention one of the greatest tips -- how to cancel any running program in CLI ! Ctrl+C.

[CENTER][SIZE=3]**Aliases**[/SIZE]
[/CENTER]
Aliases are shortcuts to commands you use often. They can save you from having to remember certain options that you usually use. To create an alias, type [FONT=Courier New][COLOR=Green]alias alias_name='aliased_command --options'[/COLOR][/FONT], making substitutions where appropriate. type [FONT=Courier New][COLOR=Green]unalias alias_name[/COLOR][/FONT] to remove an alias and [FONT=Courier New][COLOR=Green]alias[/COLOR][/FONT] without any options to see the aliases that are currently defined.

**Examples:** Here are some of the aliases I use.
```
[COLOR=DarkOrange]#Aliases for improved directory listings
#The --color=tty option shows items in different colors according to their type.
#For example, directories are blue, executable files are green, symlinks are cyan, etc.
#The -F option appends a symbol after entries to indicate their types.
#You might not like both options at the same time.[/COLOR]
alias ls='ls -F --color=tty' [COLOR=DarkOrange]#regular ls[/COLOR]
alias l.='ls -dF .[a-zA-Z0-9]* --color=tty' [COLOR=DarkOrange]#only show dotfiles[/COLOR]
alias ll='ls -lhF --color=tty' [COLOR=DarkOrange]#long listing[/COLOR]

[COLOR=DarkOrange]#Make these commands ask before clobbering a file. Use -f to override.[/COLOR]
alias rm="rm -i"
alias cp="cp -i"
alias mv="mv -i"

[COLOR=DarkOrange]#Use human-readable filesizes[/COLOR]
alias du="du -h"
alias df="df -h"

[COLOR=DarkOrange]#Miscellaneous[/COLOR]
alias bzip2='bzip2 -v'
alias j=jobs
alias cd..="cd .." [COLOR=DarkOrange]#work around a common typo[/COLOR]

[COLOR=DarkOrange]#Automatically do an ls after each cd[/COLOR]
cd() {
  if [ -n "$1" ]; then
    builtin cd "$@" && ls
  else
    builtin cd ~ && ls
  fi
}

```**Saving for future use:** There are a number of ways to do this, but the way I prefer is to create a file in your home directory called [FONT=Courier New][COLOR=Green].alias[/COLOR][/FONT] and put all your aliases there. Then insert the following at the end of [FONT=Courier New][COLOR=Green]$HOME/.bashrc[/COLOR][/FONT]
```
[COLOR=DarkOrange]# Source the aliases, if a separate file exists[/COLOR]
if [ -e $HOME/.alias ]; then
  [ -n "$PS1" ] && . $HOME/.alias
fi

```To apply your changes to the current session, type [COLOR=Green]source [/COLOR][FONT=Courier New][COLOR=Green]$HOME/.bashrc[/COLOR][/FONT]

[CENTER][SIZE=3][B]Setting the Prompt
[/B][/SIZE][LEFT]You can change your prompt by setting $PS1 and $PS2 in ~/.bashrc. There are many ways to do this. Here's what I have in my .bashrc:
```
[FONT=Courier New][COLOR=DarkOrange]# Set the prompt[/COLOR][/FONT][FONT=Courier New]
function setPrompt {
  local COLOR1="\[\033[1;33m\]"     [/FONT][FONT=Courier New][COLOR=DarkOrange]#First color[/COLOR][/FONT][FONT=Courier New]
  local COLOR2="\[\033[0;33m\]"     [/FONT][FONT=Courier New][COLOR=DarkOrange]#Second color[/COLOR][/FONT][FONT=Courier New]
  local NO_COLOR="\[\033[0m\]"      [/FONT][FONT=Courier New][COLOR=DarkOrange]#Transparent - don't change[/COLOR][/FONT][FONT=Courier New]

  case $TERM in
    xterm*)
      local TITLEBAR="\[\033]0;\h - \w\007\]"
      ;;
    *)
      local TITLEBAR=""
      ;;
  esac

  PS1="${TITLEBAR}${COLOR1}\w${COLOR2}:\\$ ${NO_COLOR}"
  PS2="${COLOR2}--${COLOR1}> ${NO_COLOR}"
}

setPrompt
unset setPrompt[/FONT]
```I set different colors for different machines. For example, I have ```
local COLOR1="\[\033[1;32m\]"
local COLOR2="\[\033[1;34m\]"
``` on my server and ```
local COLOR1="\[\033[7;1;31m\]"
local COLOR2="\[\033[7;1;31m\]"
``` for my root prompt. For root, I also set ```
local TITLEBAR="\[\033]0;ROOT - \w - \u@\h - ROOT\007\]"
```Attached is a script that lists some of the various color codes.

**Exit status:** In addition, the following code displays the exit status of the last command, if nonzero: ```
[FONT=Courier New][COLOR=DarkOrange]#Not my code; I don't remember where I got it.
#Determine and display the exit Status of the last command, if non-zero.[/COLOR]
function checkExitStatus() {
  local status="$?"
  local signal=""
  local COLOR1="\033[0;0;33m"     [COLOR=DarkOrange]#First color[/COLOR]
  local COLOR2="\033[0;0;36m"     [COLOR=DarkOrange]#Second color[/COLOR]
  local NO_COLOR="\033[0m"        [COLOR=DarkOrange]#Transparent - don't change[/COLOR]

  if [ ${status} -ne 0 -a ${status} != 128 ]; then
    [COLOR=DarkOrange]# If process exited by a signal, determine name of signal.[/COLOR]
    if [ ${status} -gt 128 ]; then
      signal="$(builtin kill -l $((${status} - 128)) 2>/dev/null)"
      if [ "$signal" ]; then
        signal="$signal"
      fi
    fi
    echo -e "${COLOR1}[Exit ${COLOR2}${status} ${signal}${COLOR1}]${NO_COLOR}" 1>&2 ${COLOR2}${signal}${COLOR1}]${NO_COLOR} " 1>&2
    fi
  return 0
}

PROMPT_COMMAND=checkExitStatus[/FONT]
```[/LEFT]
[SIZE=3][B]Scripts
[/B][/SIZE][LEFT]Here are a couple of other scripts that are handy: 

**Listing processes:** This script is a shortcut to [FONT=Courier New][COLOR=SeaGreen]ps -ef | grep foo[/COLOR][/FONT]. Save in in your path as p and make it executable. For usage instructions, type [FONT=Courier New][COLOR=SeaGreen]p --help[/COLOR][/FONT]. ```
[FONT=Courier New]#!/bin/bash
#
# Shortcut to ps -ef | grep foo

GREP="|grep"
CMD="ps -ef"
CMD2=
finalStr=
commandStr="/bin/bash $0"

printHelp() {
    echo -e "Shortcut to \"ps -ef | grep foo\"\n"
    echo "Usage: $(basename "$0") [-i] [-v] pattern1 [pattern2 [pattern3 [...]]]"
    echo "-i: case-insensitive grep"
    echo "-v: inverse grep: return lines that do NOT match the pattern"
    exit
}

for i in "$@"; do commandStr="$commandStr $i"; done

for i in "$@"; do
    getopts ivh option
    if   [ $option == i ]; then GREP="${GREP} -i"
    elif [ $option == v ]; then GREP="${GREP} -v"
    elif [ $option == h -o "$i" == "--help" ]; then printHelp; fi
done

for i in "$@"; do
    if [ "$i" == "-i" -o "$i" == "-v" -o "$i" == "-vi" -o "$i" == "-iv" ]; then shift
    else break; fi
done

for i in "$@"; do CMD2="${CMD2}${GREP} \"$i\""; done

finalStr="${CMD}${CMD2} | grep -v 'ps -ef' | grep -v ' grep ' | grep -v '/grep ' | grep -v '$commandStr'"

eval $finalStr[/FONT]
```**Recursive Shredding:** The shred command securely erases files. Great. But it doesn't work recursively (you can't give it a directory, for example). This script does. Save in in your path and make it executable. Do name_you_called_it --help for instructions. ```
[FONT=Courier New]#!/bin/bash

EXIT_VAL=0
progName="$(basename "$0")"
verStr="Recursive Shredder 0.1"

FILE_COLOR="\033[4;34m"
ERROR_COLOR="\033[0;31m"
DONE_COLOR="\033[0;32m"
NO_COLOR="\033[0m" #Transparent - don't change

licTxt() {
    echo "Copyright (c) 2006 by Scott Severance"
    echo "Licensed under the terms of the GNU General Public License"
    echo
    echo "This software is provided \"AS-IS\" and carries NO WARRANTY. Use it at your own risk."
}

shredThis() {
    #echo "press any key"
    #read -sn 1
    if [ -d "$1" -a "$1" != "." -a "$1" != ".." ]; then
        local oldDir="$(pwd)"
        builtin cd "$1"
        echo -e "Entering directory: ${FILE_COLOR}$(pwd)${NO_COLOR}"
        #pwd
        for i in * .*; do
            if [ "$i" != "." -a "$i" != ".." -a "$i" != "*" ]; then
                shredThis "$i"
            fi
            done
        builtin cd "$oldDir"
        echo -e "Removing directory: ${FILE_COLOR}${1}${NO_COLOR}"
        echo -ne $ERROR_COLOR
        rmdir "$1"
        echo -ne $NO_COLOR
        #echo -n "Returning to "
        #pwd
    
[/FONT][FONT=Courier New]
    elif [ -L "$1" -o -p "$1" -o -S "$1" ]; then # test for symlinks, fifos, and sockets
        echo -ne "Deleting special file ${FILE_COLOR}${1}${NO_COLOR}... "
        echo -ne $ERROR_COLOR
        rm "$1"
        echo -ne $NO_COLOR
        local rslt="$?"
        if [ "$rslt" -ne "0" ]; then
            echo -e "${ERROR_COLOR}### ERROR deleting ${FILE_COLOR}${1}${ERROR_COLOR}: rm exited with status ${rslt}. Aborting. ###${NO_COLOR}" > /dev/stderr
            exit 127
        fi
        echo -e "${DONE_COLOR}Done${NO_COLOR}"

[/FONT][FONT=Courier New]     elif [ -f "$1" ]; then
        echo -ne "Shredding ${FILE_COLOR}${1}${NO_COLOR}... "
        echo -ne $ERROR_COLOR
        shred --zero --remove "$1"
        echo -ne $NO_COLOR
        local rslt="$?"
        if [ "$rslt" -ne "0" ]; then
            echo -e "${ERROR_COLOR}### ERROR shredding ${FILE_COLOR}${1}{$ERROR_COLOR}: shred exited with status ${rslt}. Aborting. ###${NO_COLOR}" > /dev/stderr
            exit 127
        fi
        echo -e "${DONE_COLOR}Done${NO_COLOR}"

    else
        echo -e "${ERROR_COLOR}### NOTICE: The file ${FILE_COLOR}${1}${ERROR_COLOR} is not a regular file. Skipping. ###${NO_COLOR}" > /dev/stderr
        EXIT_VAL=3
    fi
}

if [ "$1" = "--no-color" ]; then
    FILE_COLOR=""
    ERROR_COLOR=""
    DONE_COLOR=""
    NO_COLOR=""
    shift
fi

if [ "$#" = "0" -o "$1" = "--help" ]; then
    echo -e "${DONE_COLOR}${verStr}${NO_COLOR}" > /dev/stderr
    echo > /dev/stderr
    echo "Usage: $progName [--no-color] file-or-directory-1 file-or-directory-2 ..." > /dev/stderr
    echo "       $progName --help" > /dev/stderr
    echo "       $progName --version" > /dev/stderr
    EXIT_VAL=1

elif [ "$1" = "--version" ]; then
    echo -e "${DONE_COLOR}${verStr}${NO_COLOR}"
    echo
    licTxt
    EXIT_VAL=2

else
    for i in "$@"; do
        if [ "$i" = "." ]; then i="$(pwd)"; fi
        shredThis "$i"
    done
fi

exit $EXIT_VAL[/FONT]
```[/LEFT]
[SIZE=3]**Other Tips**[/SIZE]
[/CENTER]
If you have any other aliases, etc. that might be useful to others, please add them here.

---

### Post by Lil_Eagle on 2006-06-27
Thank you.  The alias cd..=cd .. is really handy.  Don't know why I couldn't think of that.

---

### Post by b0bby on 2006-06-29
i find 
```
df='df -h'
ls='ls -hal'
du='du -sh'
```
very usefull

---

### Post by simplyw00x on 2006-06-29
My aliases:
alias agi='sudo apt-get install'
alias agr='sudo apt-get remove'
alias agu='sudo apt-get update'
alias agdu='sudo apt-get dist-upgrade'
alias acs='apt-cache search'
alias acsh='apt-cache show'
alias sdi='sudo dpkg -i'
alias neogeo='gngeo -H --scale=2 -e hq2x'
alias neighbour='shell-fm lastfm://user/simplyw00x/neighbours'

(the last two are a little frivolous :p)

---

### Post by evilhomer on 2006-07-09
they all work great, except ls

no matter what i do, ls is always the same - i want to add the -F

i upgraded to dapper from breezy and as far as i can recall, i always had colors for file types.

so i'm wondering if there's a universal setting that .alias can't take priority over or something?

---

### Post by mssever on 2006-07-09
> **evilhomer said:**
> they all work great, except ls

no matter what i do, ls is always the same - i want to add the -F

i upgraded to dapper from breezy and as far as i can recall, i always had colors for file types.

so i'm wondering if there's a universal setting that .alias can't take priority over or something?

Have you tried [FONT="Courier New"][COLOR="Green"]alias ls='ls -F'[/COLOR][/FONT]? enter it directly in the command line first to see if the alias works. Also, make sure that your .bashrc sources .alias (it needs to either contain a line with [FONT="Courier New"][COLOR="Green"]source .alias[/COLOR][/FONT] or [FONT="Courier New"][COLOR="Green"]. .alias[/COLOR][/FONT]

Also, I would put the call to .alias at the bottom of your .bashrc

---

### Post by evilhomer on 2006-07-09
ah, you showed me where to go!  the alias from the command line worked, then i went to move .alias in .bashrc and in scrolling down, i saw .bashrc has the ls alias hardcoded into it.

thanks!

---

### Post by dmwit on 2006-07-10
```

~% alias
...=../..
....=../../..
.....=../../../..
......=../../../../..
.......=../../../../../..
:e=vim
e=vim
grep='grep --color=auto'
k=killall
l=less
la='ls -A'
ll='ls -l'
ls='ls --color=auto'
n=nautilus
p=popd
q=exit
run-help=man
t=cat
vi=vim
which-command=whence
```
I'm not sure where run-help and which-command came from, but the others are mine.  Of course, some are more useful under other shells than bash... =)

~d

---

### Post by sublimeprogie on 2006-07-17
do you have to do anything to get your aliases activated, i read to put my aliases in my .bash_profile.  but i have restarted my computer and everything and they dont seem to work.  

this is what i have right now

```
# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

alias today='date +"%A, %B %-d, %Y"'

alias l='ls -l'

```

thanks

---

### Post by mssever on 2006-07-18
Put the aliases in ~/.bashrc, not ~/.bash_profile. .bash_profile only gets read by login shells (e.g., at the console or via ssh). All shells, however, read .bashrc.

EDIT: You don't have to restart your computer. Type exit and restart the shell, and if your aliases are in the right place, they will be available.

---

### Post by userundefine on 2006-07-18
Let's not forget to mention one of the greatest tips -- how to cancel any running program in CLI ! Ctrl+C.  I realize you mention it with bash history search, but people might take it to be a function of *just* that search.

---

### Post by sublimeprogie on 2006-07-18
> **mssever said:**
> Put the aliases in ~/.bashrc, not ~/.bash_profile. .bash_profile only gets read by login shells (e.g., at the console or via ssh). All shells, however, read .bashrc.

EDIT: You don't have to restart your computer. Type exit and restart the shell, and if your aliases are in the right place, they will be available.

worked like a charm, thanks for the information, that would have drove me nuts all day tomorrow.  also, thanks for explaining why, helps a ton:)

---

### Post by mlind on 2006-07-18
> **mssever said:**
> Put the aliases in ~/.bashrc, not ~/.bash_profile. .bash_profile only gets read by login shells (e.g., at the console or via ssh). All shells, however, read .bashrc.

EDIT: You don't have to restart your computer. Type exit and restart the shell, and if your aliases are in the right place, they will be available.

I suggest to use .bash_aliases for custom aliases. This file can be sourced from ~/.bashrc by uncommenting the following
```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

I recently found handly command line trick, Ctrl-w for cut last word and Ctrl-y to paste it back.
I often find myself renaming/copying files to slightly different name, and this comes very handy for that purpose.

Maybe my most often used alias is
```

alias lsd='ls -d */'

```

---

### Post by sublimeprogie on 2006-07-18
this isnt exactly alias, but i tried to make a function that shows the date (i found it on a site)  and i put it into .bashrc just like alias' and nothing happened. Any suggestions?

---

### Post by kabus on 2006-07-18
> **mssever said:**
> 
If you have any other aliases, etc. that might be useful to others, please add them here.

[B][CENTER]Use history expansion to save typing
[/CENTER][/B]
As an example, let's assume I want to install a program foobar:

```
apt-get install foobar
```

That fails because I forgot sudo. Now I could hit the up-arrow to go back to the last command, scroll to the beginning of the line and add sudo, but it's easier to just type this:

```
sido !!
```

!! will be substituted with the entire last command in the history, so it is equivalent to:

```
sido apt-get install foobar
```

Which still won't work because I misspelled sudo.
Typing

```
^i^u
```

will replace the first occurance of i in the previous command with u, thus fixing the mistake:

```
sudo apt-get install foobar
```


Now to run the program foobar I just type:

```
!$
```

which will be substituted with the last argument of the previous command, i.e. foobar.

Info on more advanced history expansion can be found in the bash manual:
[http://www.gnu.org/software/bash/manual/bashref.html#SEC114](http://www.gnu.org/software/bash/manual/bashref.html#SEC114)

---

### Post by kabus on 2006-07-18
> **sublimeprogie said:**
> this isnt exactly alias, but i tried to make a function that shows the date (i found it on a site)  and i put it into .bashrc just like alias' and nothing happened. Any suggestions?

Post the relevant part from your .bashrc, it's hard to tell what could be wrong without the specifics.

---

### Post by mssever on 2006-07-18
> **kabus said:**
> [B][CENTER]Use history expansion to save typing
[/CENTER][/B]

Great tip! Thanks.

---

### Post by sublimeprogie on 2006-07-18
> **kabus said:**
> Post the relevant part from your .bashrc, it's hard to tell what could be wrong without the specifics.

sorry, forgot to post that along with it

```

function today {echo "Today's date is:"date +"%A, %B %-d, %Y"}

alias l='ls -la'

```

---

### Post by mssever on 2006-07-18
> **sublimeprogie said:**
> ```

function today {echo "Today's date is:"date +"%A, %B %-d, %Y"}

```

Try this: ```
function today { echo -n "Today's date is: "; date +"%A, %B %-d, %Y"; }
```
Alternatively, you can display it thus:
```
function today {
    echo -n "Today's date is: "
    date +"%A, %B %-d, %Y"
}
```

The single-line version requires each line to be terminated with a semicolon.

---

### Post by sublimeprogie on 2006-07-18
> **mssever said:**
> Try this: ```
function today { echo -n "Today's date is: "; date +"%A, %B %-d, %Y"; }
```
Alternatively, you can display it thus:
```
function today {
    echo -n "Today's date is: "
    date +"%A, %B %-d, %Y"
}
```

The single-line version requires each line to be terminated with a semicolon.

thanks alot, i figured something was just missing from the funtion, i just had no clue what it would be

*edit:  ok that didnt seem to take either

this shows up when i open my terminal

```
bash: /home/me/.bashrc: line 11: syntax error near unexpected token `}'
bash: /home/me/.bashrc: line 11: `}'

```

---

### Post by simplyw00x on 2006-07-18
does it not need to be `funtion today ()`?

---

### Post by sublimeprogie on 2006-07-18
ok, i put in the altered code that was suggested earlier by mssever and it worked, apparently somehow my mouse wheel pastes when it clicks so i had a bunch of random stuff throughout my .bashrc file.  i have it to where it will work now, but there is still something that pops up when i open the terminal

bash: [: /etc/bash_complittle: binary operator expected

i dont know if it is important or not, but it didnt use to show up so i thought i would throw it out there to you guys.  thanks again for all the help

---

### Post by johan.t on 2006-10-16
Well, I have some tricks here in my .bash_aliases. Hope someone can find them useful. ;) 

```
alias +alias='echo alias $1 >> ~/.bash_aliases'
alias aliases='cat -n ~/.bash_aliases'
alias bash-reload='. ~/.bashrc'
alias bash-aliases='gedit ~/.bash_aliases'


alias apti='sudo aptitude install'
alias aptr='sudo aptitude remove'
alias apts='aptitude search'
alias update='sudo aptitude update'
alias upgrade='sudo aptitude upgrade'
alias dist-upgrade='sudo aptitude dist-upgrade'

alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias xx='exit'
alias cc='clear'
alias ccd='cd ~/ && clear'
alias mp3='cd ~/musik'

alias fcc='/opt/firstclass/fcc &'
alias bt='btdownloadgui &'
alias irc='Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=75x30+850+750 -e irssi -c chat.freenode.net --nick=nahoj'

alias forum='firefox http://ubuntu-se.org/forum &'
alias mail='firefox http://gmail.com &'
alias google='firefox http://google.com/linux &'

alias anthony='mocp -c && mocp -a -p ~/musik/anthony_and_the_johnsons/'
alias imabird='mocp -c && mocp -a -p ~/musik/anthony_and_the_johnsons/i_am_a_bird_now/'
alias rhcp='mocp -c && mocp -a -p ~/musik/red_hot_chili_peppers/'
alias soad='mocp -c && mocp -a -p ~/musik/system_of_a_down/'
alias madonna='mocp -c && mocp -a -p ~/musik/madonna/'
alias arctic='mocp -c && mocp -a -p ~/musik/arctic_monkeys/'
alias muse='mocp -c && mocp -a -p ~/musik/muse/'
alias tot='mocp -c && mocp -a -p ~/musik/theatre_of_tradgedy/'
alias killers='mocp -c && mocp -a -p ~/musik/the_killers/'
alias queen='mocp -c && mocp -a -p ~/musik/queen/'
alias creed='mocp -c && mocp -a -p ~/musik/Creed/'
alias hellacopters='mocp -c && mocp -a -p ~/musik/the_hellacopters/'
alias u2='mocp -c && mocp -a -p ~/musik/U2/'
alias wolfmother='mocp -c && mocp -a -p ~/musik/wolfmother/'

alias forw='mocp -f'
alias prev='mocp -r'

alias sources='gksudo gedit /etc/apt/sources.list &'

```

---

### Post by Dangling on 2006-10-16
One trick I find very useful is setting cdpath. Basically if there are folders that you access regularly, you can easily access those directories without typing the entire path. 

For example: I keep my music on my external hard drive. If I wanted to access the folder 'The roots', ordinarily the path would be :
```
cd /media/usbdisk/Music/The_roots
```

To make it easy for me, I set my external hard drive in the cdpath in my .bash_profile and .bashrc :
```
CDPATH=".:~:/media/usbdisk/Music"
```

So when you type cd <some folder>, it first checks the current directory (.) for <some folder>, then my home directory (~) , then finally the music directory on my external hard drive (/media/usbdisk/Music). 

As a result I can directly access my 'The_roots' folder anywhere by typing:
```
cd The_roots
```

Some people like to use aliases to define frequent folders. But I like this method more because I don't have to update the alias list if I add new folders. Also always add the "." in the beginning of the cdpath or else it won't check the present directory for the folder. 

For more info and tips:
[http://www.caliban.org/bash/](http://www.caliban.org/bash/)

---

### Post by bodhi.zazen on 2006-11-01
Here is my "short list"

Propmt:
> For users add the color of your choice:
PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$' #Green

PS1='\[\033[01;34m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$' #Blue 

For root add this to /root/.bashrc
 PS1='\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$' #Red 

Now if you sudo su you will have a red prompt to remind you that you are ROOT. 
command history:
> alias hist='history | grep $1' #Requires one input 

Now: hist <command> will return something like this

    502 <command> 

Just type !502 at the prompt and the command will be repeated. 
colorize grep:
> alias g="grep --color=always"
alias gi="grep -i --color=always" 

Note:grep -i = ignore case 
Archive:
> # Extract files from any archive
# Usage: ex <archive_name>

ex () {
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

# Thanks to rezza at Arch Linux
Mount usb:
> alias usb='sudo mount LABEL=USB /mnt/USB/ -o uid=1000,gid=100,umask=007' 

You can now mount the device, with or without an entry in fstab, by typing:

usb

Note: To determine the label of a device, with the device connected to the usb port

ls /dev/disk/by-label
No clobber:
> set -o noclobber #Prevents redirection of output from overwriting an existing file 

Use >> rather then > to re-direct

> overwrites the file.
>> Adds to the end of the file. 

Note: To override use >|

ie echo new_txt >| <dest_file>

---

### Post by skymt on 2006-11-01
I have a good 34 aliases defined (ZSH):```
..='cd ..'
...='cd ../..'
....='cd ../../..'
:en='2> /dev/null'
:g='| grep'
:l='| less'
:n='&> /dev/null'
:sl='| sort | less'
:sn='1> /dev/null'
apt='sudo aptitude'
apti='sudo aptitude install'
aptr='sudo aptitude remove'
aptu='sudo aptitude update && sudo aptitude upgrade'
du='du -h'
dv='setxkbmap us dvorak'
grep=egrep
la='ls -a'
ll='ls -l'
ls='ls --color=auto'
lsa='ls -ld .*'
lsbig='ls -lSh *(.) | head'
lsd='ls -ld *(-/DN)'
lsnew='ls -lrt *(.) | tail'
lsold='ls -lrt *(.) | head'
lssmall='ls -lSh *(.) | head'
mmv='noglob zmv -W'
open=gnome-open
qw='setxkbmap us'
rc='sudo invoke-rc.d'
ri='noglob ri'
tarbc='tar --bzip2 -cvf'
targc='tar -czvf'
tarx='tar -xvf'
which-command=whence
```

The ones that start with ":" are global aliases, which means I can use them anywhere in a command. For example, to list the files in the zsh package, sort alphabetically, and view in less:```
dpkg -L zsh :sl
```

If you want me to explain any of these, just ask.

---

### Post by Roderik on 2006-11-01
this is a great thread! Maybe someone can help me witht he following, i used to have a little script, aliassed as "vim" that would try to open the file with vim, but if it was readonly use "sudo vim". Unfortunatly i list this script somewhere aling the line and have never been able to find it again.

---

### Post by skymt on 2006-11-01
> **Roderik said:**
> this is a great thread! Maybe someone can help me witht he following, i used to have a little script, aliassed as "vim" that would try to open the file with vim, but if it was readonly use "sudo vim". Unfortunatly i list this script somewhere aling the line and have never been able to find it again.


```
#!/bin/bash
if [ -w $1 ] ; then
    vim $1
else
    sudo vim $1
fi
```

---

### Post by Roderik on 2006-11-01
THX! you made my day!

---

### Post by fvu on 2006-11-08
Keystrokes can be saved by using shortcuts for changing directories back AND supplying an additional argument: the directory to go forth from there.

It is like making a U-turn:

.. [dir] = cd ../[dir]
... [dir] = cd ../../[dir]
.... [dir] = cd ../../../[dir]
..... [dir] = cd ../../../../[dir]
...... [dir] = cd ../../../../../[dir]
....... [dir] = cd ../../../../../../[dir]
........ [dir] = cd ../../../../../../../[dir]

The directory-argument can be TAB-completed!

Include the script underneath in your ~/.bashrc with the command: source cdots.sh

```
#!/bin/bash
# --- cdots.sh -------------------------------------------------------
# Change directory back - 1-7 times - and forth with TAB-completion.
# Copyright (C) 2006  Freddy Vulto
# Version: 1.0.8
# Usage: ..[.[.[.[.[.[.]]]]]] [dir]
#
# Arguments: [dir]   Directory to go forth - down the directory tree
#
# Example:   $/usr/share> .. local/share/   # .. lo[TAB]/sh[TAB])
#            $/usr/local/share>  
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software 
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, 
# MA  02110-1301, USA
#
# The latest version of this software can be obtained here:
# http://www.fvue.nl/cdots/


CDOTS_DEPTH=7


#--- _cdots() --------------------------------------------------------
# TAB completion for the .. ... .... etc commands
# @see cdots()
_cdots() {
        # ':2' = Ignore two dots at pos 0, $'\012' = newline (\n)
    local dots=${COMP_WORDS[COMP_CWORD-1]:2} IFS=$'\012' i j k=0
    local dir=${dots//./..\/}../  # Replace . with ../
    for j in $(compgen -d -- "$dir${COMP_WORDS[COMP_CWORD]}"); do
            #  If j not dir in current dir, append extra slash '/'
            #  NOTE: If j is also dir in current dir, 'complete -o 
            #+       filenames' automatically appends slash '/'
        [ ! -d ${j#$dir} ] && j="$j/"
        COMPREPLY[k++]="${j#$dir}"
    done
} # _cdots()


#--- cdots() ---------------------------------------------------------
# Change directory to specified directories back, and forth
# @param $1 string   Directory back
# @param $2 string   Directory forth
# @see _cdots() for TAB-completion
function cdots() {
    cd "$1$2"
} # cdots()


    # Define aliases .. ... .... etc
    # NOTE: Functions are not defined directly as .. ... .... etc, 
    #       because these are not valid identifiers under `POSIX'
cdotsAlias=.; cdotsAliases=; cdotsDir=
for ((i = 1; i <= $CDOTS_DEPTH; i++)); do
    cdotsAlias=$cdotsAlias.; cdotsDir=$cdotsDir../
    alias $cdotsAlias="cdots $cdotsDir"
    cdotsAliases="$cdotsAliases $cdotsAlias"
done
    # Set completion of aliases .. ... .... etc to _cdots()
    # -o filenames: Escapes whitespace
complete -o filenames -o nospace -F _cdots $cdotsAliases
unset -v CDOTS_DEPTH cdotsAlias cdotsAliases cdotsDir i
```

See also:
[http://www.fvue.nl/cdots/]("http://www.fvue.nl/cdots/")

Freddy Vulto

---

### Post by mssever on 2006-11-08
> **skymt said:**
> ```
#!/bin/bash
if [ -w $1 ] ; then
    vim $1
else
    sudo vim $1
fi
```
This is handy! I modified it slightly so that it will take more filenames and so that special characters in filenames (eg spaces) won't mess things up: ```
#!/bin/bash
if [ -w "$1" ] ; then vim "$@"
else sudo vim "$@"; fi

```> **bodhi.zazen said:**
> Archive:
```
                              # Extract files from any archive
# Usage: ex <archive_name>

ex () {
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

# Thanks to rezza at Arch Linux
```
Again, modified to accept multiple arguments and funny filenames. Note that my version is a standalone file. ```
#!/bin/bash

# Extract files from any archive
# Usage: ex <archive_name>

ex() {
        if [ -f "$1" ] ; then
                case "$1" in
                        *.tar.bz2) tar xjvf "$1" ;;
                        *.tar.gz) tar xzvf "$1" ;;
                        *.bz2) bunzip2 "$1" ;;
                        *.rar) rar x "$1" ;;
                        *.gz) gunzip "$1" ;;
                        *.tar) tar xvf "$1" ;;
                        *.tbz2) tar xjvf "$1" ;;
                        *.tgz) tar xzvf "$1" ;;
                        *.zip) unzip "$1" ;;
                        *.Z) uncompress "$1" ;;
                        *.7z) 7z x "$1" ;;
                        *) echo "'$1' cannot be extracted via $(basename "$0")" ;;
                esac
        else
                echo "'$1' is not a valid file"
        fi
}

for i in "$@"; do ex "$i"; done

# Thanks to rezza at Arch Linux and bodhi.zazen at ubuntuforums.org
```

---

### Post by mssever on 2006-11-08
I've significantly expanded the first post, adding my method of setting the prompt, the PROMPT_COMMAND variable, a shortcut tp ps-ef | grep foo and recursive shredding.

---

### Post by skymt on 2006-11-08
> **mssever said:**
> This is handy! I modified it slightly so that it will take more filenames and so that special characters in filenames (eg spaces) won't mess things up: ```
#!/bin/bash
if [ -w "$1" ] ; then vim "$@"
else sudo vim "$@"; fi

```

I've modified it further. Your version only checks write permissions for the first argument, but tries to edit all of them. Here's mine:```
#!/bin/bash
for i in "$@" ; do
    if [ ! -w "$i" ] ; then precommand="sudo " ; break ; fi
done

if [ -z $DISPLAY ] ; then
    ${precommand}vim "$@"
else
    ${precommand}gvim "$@"
fi
```This should run gvim if possible. Otherwise, plain vim.

---

### Post by mssever on 2006-11-08
> **skymt said:**
> I've modified it further. Your version only checks write permissions for the first argument, but tries to edit all of them. Here's mine:```
#!/bin/bash
for i in $@ ; do
    if [ ! -w "$i" ] ; then precommand="sudo " ; break ; done
done

if [ -z $DISPLAY ] ; then
    ${precommand}vim
else
    ${precommand}gvim
fi
```This should run gvim if possible. Otherwise, plain vim.

Another version: you forgot to give vi some files to start. Also, you should always use double quotes around "$@" for maximum compatibility. And, I fixed a couple of syntax errors.

I've also dropped gvim, since I don't want graphical apps popping up when I'm using the CLI (personal preference here).
```
#!/bin/bash
for i in "$@" ; do
    if [ ! -w "$i" ] ; then precommand="sudo " ; break ; fi
done

eval ${precommand}vim "$@"
```

---

### Post by skymt on 2006-11-09
> **mssever said:**
> Another version: you forgot to give vi some files to start. Also, you should always use double quotes around "$@" for maximum compatibility. And, I fixed a couple of syntax errors.

I've also dropped gvim, since I don't want graphical apps popping up when I'm using the CLI (personal preference here).

:oops: Fixing now. Sorry. I must have been *really* tired to mix do-done with if-fi.

The eval isn't necessary, though. Try it and see.

As for the extra quotes, zsh doesn't need them, so...

---

### Post by Peepsalot on 2006-11-11
Here's a simple script I just wrote up.  Maybe some will find it useful.

I put this in a script called "/usr/bin/search"
```

#!/bin/bash

if [ -n "$1" ]
then
  if [ -n "$2" ]
  then
    find $1 -iname *$2* 2> /dev/null
  else
    find / -iname *$1* 2> /dev/null
  fi
else
  echo "Usage: search [dir] [partial_file_name]"
fi

```

If one parameter is given, it searches for that file from the root dir.

If two parameters are given, it will search for a file match of the second parameter, starting in the directory specified by the first parameter.

---

### Post by Peepsalot on 2006-11-11
By the way, that Ctrl-R is something really nice that I didn't know about, but is there a way to flip through multiple commands that match your search instead of only the latest one?

---

### Post by bodhi.zazen on 2006-11-11
> **Peepsalot said:**
> By the way, that Ctrl-R is something really nice that I didn't know about, but is there a way to flip through multiple commands that match your search instead of only the latest one?

Hit Ctrl-R
Start typing
You will get the first matching command
If you want a different one, keep hitting Ctrl-R and it will cycle through additional matching commands.

---

### Post by mssever on 2006-11-29
> **mssever said:**
> Another version: you forgot to give vi some files to start. Also, you should always use double quotes around "$@" for maximum compatibility. And, I fixed a couple of syntax errors.

I've also dropped gvim, since I don't want graphical apps popping up when I'm using the CLI (personal preference here).
```
#!/bin/bash
for i in "$@" ; do
    if [ ! -w "$i" ] ; then precommand="sudo " ; break ; fi
done

eval ${precommand}vim "$@"
```

I discovered a bug in this script. If you vi a non-existant file, the test will determine that that file is non-writable. When you save you work, you'll discover that the file is owned by root. Here's the fix: ```
#!/bin/bash
for i in "$@" ; do
    if [ [COLOR=DarkRed]-f "$i" -a[/COLOR] ! -w "$i" ] ; then precommand="sudo " ; break ; fi
done

${precommand}vim "$@"
```

---

### Post by orange7 on 2007-06-21
I used to have color enabled in ls but disabled it because I prefer to have transparent terminals. Does anyone know how I can force ls to display a '/' after directories so I know what the directories are. I don't mean 
$ls -d /*
because I would like a command that lists all files and directories, but in addition denotes directories with a '/'.

Thanks

---

### Post by bodhi.zazen on 2007-06-21
> **orange7 said:**
> I used to have color enabled in ls but disabled it because I prefer to have transparent terminals. Does anyone know how I can force ls to display a '/' after directories so I know what the directories are. I don't mean 
$ls -d /*
because I would like a command that lists all files and directories, but in addition denotes directories with a '/'.

Thanks

```
ls -p
```

Try (for other effects): 

ls -F

ls --file-type

---

### Post by orange7 on 2007-06-25
> **bodhi.zazen said:**
> ```
ls -p
```

Try (for other effects): 

ls -F

ls --file-type

Thanks. That works exactly as I'd like it to.  I appreciate you taking the time to answer that because although I couldn't figure it out earlier, it seems obvious now from the man pages of ls.

---

### Post by bernardfrancois on 2008-01-12
I like to use **Ctrl+P** (previous) and **Ctrl+N** (next) to browse trough the history of recently executed commands (rather than having to move my hand and using Ctrl+Up and Ctrl+Down).

When I typed a mistake in a command, I move the cursor using **Ctrl+B** (back) and **Ctrl+F** (forward).

(I use this in xterm, but these shortcuts work in may programs - e.g. emacs and nano)

---

### Post by mithbuntu on 2009-04-10
Didn't read whole thread,so I hope this isn't already here, but I have a useful addition:
Script to display total size of files within directory.

ie 
```
.504.[10:41 drew@mithbuntu:~ 1.930Mb]$ 
```
1.930mb in this case.

In .bashrc add this line to your PS1 (see below) customization line:
```

\$(~/Scripts/bin/lsbytesum.sh)Mb

```

And create the file lsbytesum.sh and place it in the directory above (your own path is fine):
```

# !/bin/bash
#     lsbytesum - sum the number of bytes in a directory listing
TotalBytes=0
for Bytes in $(ls -l | grep "^-" | awk '{ print $5 }')
do
    let TotalBytes=$TotalBytes+$Bytes
done
TotalMeg=$(echo -e "scale=3 \n$TotalBytes/1048576 \nquit" | bc)
echo -n "$TotalMeg"

```

Here's my entire command line customization:
```

PS1version=' \[\e[46m\]8.1\[\e[0m\]'
PS1clock='$( date +%H:%M)'
PS1error='$( ret=$? ; test $ret -gt 0 && echo "\[\e[41;93m\]   [$ret]   \[\e[0m\]" )'
PS1user="$( test `whoami` == root && echo '\[\e[101m\]' )\u\[\e[0m\]"
PS1color='\[\e[1;37;44m\]' # color of working directory

PS1="\[\e[1;32m\].\!.\[\e[1;33m\][\[\e[0m\]\[\e[1m\]$PS1clock\[\e[0m\] \[\e[1;35m\]$PS1user\[\e[0m\]\[\e[0;33m\]@\[\e[1;34m\]\h\[\e[0;33m\]:$PS1color\w\[\e[0m\]\[\e[1;30m\] \$(~/Scripts/bin/lsbytesum.sh)Mb\[\e[1;33m\]]\[\e[0;32m\]$\[\e[0m\] "
tty | grep pts > /dev/null && PS1="$PS1\[\e]0;\w - \u@\h\a\]";

```

---

### Post by potsed on 2010-05-27
Hi, thanks for all the great tips.

An alias i use fairly often is:

```
alias hisgrep="history | grep"
```

This allows you search through your bash history for a previously written command.

---

### Post by mssever on 2010-05-30
> **potsed said:**
> Hi, thanks for all the great tips.

An alias i use fairly often is:

```
alias hisgrep="history | grep"
```

This allows you search through your bash history for a previously written command.

Great idea. I'm taking it with a slight modification: ```
alias hgrep='history | egrep'
```I prefer egrep over regular grep because egrep understands regexps better than standard grep.

---

### Post by mssever on 2010-05-31
Here's a further improvement. This version filters the current command from the results, since it's doubtful that you want to see such a command: [php]hgrep() {
  history | egrep "$@" | egrep -v "hgrep $@"
}[/php]In order to implement this, I switched it from an alias to a function, because functions can take arguments which can then be manipulated.

---

### Post by OzzyFrank on 2010-06-12
**[COLOR="DarkRed"]Backup and Restore the Gnome Panel layout[/COLOR]**:

[B]alias panelb='gconftool-2 --dump /apps/panel > ~/Settings/panel_settings'
alias panelr='gconftool-2 --load ~/Settings/panel_settings && killall gnome-panel'[/B]

I had a launcher for the backup, and it worked, then one day noticed that while it went through the motions, it wasn't actually backing it up anymore... but works fine in the terminal.

(PS: The ~/Settings mentioned is a folder I created in my home folder for storing settings for my programs. Makes it easy to keep track of all that junk!)

---

### Post by phapalegaurav on 2013-01-09
> **Lil_Eagle said:**
> Thank you.  The alias cd..=cd .. is really handy.  Don't know why I couldn't think of that.

My favorite
alias ..='cd ..'
yes, am too lazy!

---

### Post by Tinker Tantrum on 2013-09-12
Would it be possible to chain two commands together in an alias? I.E. making an alias for "cat" that uses "less" automatically? Everytime I use "cat", I must append "| less" at the end of every command and that gets annoying.

---

### Post by Tinker Tantrum on 2013-09-14
Bump

---

