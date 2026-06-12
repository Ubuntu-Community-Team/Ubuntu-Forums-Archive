---
title: "Howto: Add custom color to directory listings."
date: 2005-06-13
forum: Tutorials
---

### Post by skoal on 2005-06-13
You ever fire up an xterm and perform an "ls" command?  Sure you have!  If so, did you ever wish that:
[list]
[*]certain files would "stand out" with a *custom* color, and **not** the *defaults*?
[*]you can add other filename extensions to the database with their own custom color as well?
[/list]
Well, here's how...

NOTE: All [COLOR=DarkRed]commands[/COLOR] to be entered in a terminal shell or [COLOR=DarkRed]changes[/COLOR] made to a file are hilighted in red.  You only need to cut/paste those items which are hilighted, the surrounding text is left for illustration purposes.

1. **Edit the '.bashrc' file**.  You need to make a few small changes to the existing bash script.
[list=i]
[*](optional) **Backup the file**.  Copy your existing '.bashrc' file in case you wish to restore it at a latter time.  For example,
```
skoal@morpheus:///tmp $ [COLOR=DarkRed]cd && cp .bashrc .bashrc~[/COLOR]
skoal@morpheus://~ $ ls .bashrc*
.bashrc  .bashrc~
```
[*]**Modify the file**.  Using your favorite text editor, open the file '~/.bashrc' and make the following changes hilighted in red (which should appear somewhere near the top of that file - line 17 if no prior alterations were made).  You will basically be modifying one line and adding two more above it.
```
skoal@morpheus:///tmp $ [COLOR=DarkRed]gedit ~/.bashrc[/COLOR]
```
and make these changes in the file,
```
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    [COLOR=DarkRed][ -e "$HOME/.dircolors" ] && DIR_COLORS="$HOME/.dircolors"
    [ -e "$DIR_COLORS" ] || DIR_COLORS=""
    eval "`dircolors -b $DIR_COLORS`"[/COLOR]
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi
```
[*](alternative to step 1.ii) **Patch the file**.  Using the attched 'bashrc.patch' file, patch the current '~/.bashrc' file instead of cutting/pasting with an editor.
```
skoal@morpheus:///tmp $ [COLOR=DarkRed]bunzip2 bashrc.patch.bz2[/COLOR]
skoal@morpheus:///tmp $ [COLOR=DarkRed]cp bashrc.patch ~[/COLOR]
skoal@morpheus:///tmp $ [COLOR=DarkRed]cd && patch -p0 < bashrc.patch[/COLOR]
patching file .bashrc
Hunk #1 succeeded at 19 (offset 5 lines).
```
[/list]
2. **Create the '.dircolors' file**.  The '.dircolors' file is created by using the 'dircolors' program.  It will generate a default color scheme to be used with the "LS_COLORS" environment variable, which gives the colored output while using "ls".
```
skoal@morpheus:///tmp $ [COLOR=DarkRed]cd && dircolors -p > .dircolors[/COLOR]
```
3. **Edit the '.dircolors' file**.  Here is where you will be modifying/creating new color schemes to reflect your own unique style.

NOTE: Lines 34-41 within this file give you the color codes for three specific keys: attribute, text, and background.  You can choose to use all three keys, or simply pick and choose only those keys you wish to apply.  Look at some of the pre-defined ones you may already recognize as a good example to follow.  
[list=i]
[*]**Modify existing color schemes**.  For example, I can't stand big bold blue directory listings, so I change the bold attribute from "01" to "00" (none) but keep the blue color.  It will lighten things up a bit.
```
FILE 00         # normal file
DIR [COLOR=DarkRed]00[/COLOR];34       # directory
LINK 01;36      # symbolic link.
```
or, change the "01" to an "07", making your debian packages really stand out!
```
.gz  01;31
.bz2 01;31
[COLOR=DarkRed].deb 07;31[/COLOR]
.rpm 01;31
.jar 01;31
```
which will "reverse" the red (31) foreground color - basically making it black text inside a red box!  Whoa!  Ugly but effective, no?


[*]**Create new color schemes**. I like to program, yet for some reason, there are no default colors for well known language extensions.  I like my c/c++ source to show up as green and my header files as yellow.  Here's how I added these extensions to the bottom of that file:
```
# audio formats
.ogg 01;35
.mp3 01;35
.wav 01;35

[COLOR=DarkRed]# programming languages
.c 00;32
.cc 00;32
.cpp 00;32
.h 00;33[/COLOR]
```
[/list]
4. **Source the '.bashrc' file**.  In order for your changes to take effect within the current shell, you need to source the '.bashrc' file.
```
skoal@morpheus:///tmp $ [COLOR=DarkRed]cd && . .bashrc[/COLOR]
```
**** END of Howto ****

and, just to see your handy work, look at these two environmental variables:
```
skoal@morpheus://~ $ [COLOR=DarkRed]set | grep 'DIR_COLORS\|LS_COLORS'[/COLOR]
DIR_COLORS=/home/skoal/.dircolors
LS_COLORS='no=00:fi=00:di=00;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.ogg=01;35:*.mp3=01;35:*.wav=01;35:*.c=00;32:*.cc=00;32:*.cpp=00;32:*.h=00;33:'
```
NOTE: These color changes will be preserved upon each reboot or login.  If you wish to revert to the original color scheme, just delete the file '.dircolors' in your $HOME directory (or, alternatively, restore your backup file made in step 1.i).
```
skoal@morpheus:///tmp $ [COLOR=DarkRed]rm -f ~/.dircolors[/COLOR]
```
NOTE: I've only tested this with a plain 'ole vanilla stock 'xterm'.  I do not use gnome-terminal, kterm(?), or any other variants but it should work equally well with them.  I do not use any file managers of any sort, so without some MIME associated icon staring me in the face, these colors really help.  Using 'dircolors' is old as dirt, and I'm surprised no one else hadn't mentioned this yet.  Am I the only one who thinks CLI+color > [insert favorite File Manager here]? Surely, I'm not alone.  Or am I...

\\//_

---

### Post by agapito on 2005-12-10
Thanx for the nice HOWTO!

By the way, to get syntax highlight on VI  you can edit the "filetype.vim" file, located in /usr/share/vim/"vim version"/. Just change the line:

[INDENT][I]au BufNewFile,BufRead .dir_colors,/etc/DIR_COLORS    setf dircolors
[/I][/INDENT]

to

[INDENT][I]au BufNewFile,BufRead .dir_colors,[COLOR="Red"].dircolors,[/COLOR]/etc/DIR_COLORS    setf dircolors
[/I][/INDENT]

Alternatively you can name the file ".dir_colors" insted of ".dircolors".  

VI rules! ;)

---

### Post by ubz on 2007-06-21
Hi, I've tried applying the instructions from this somewhat dated Howto creating a .dircolors file in my home directory, modifing the ~$ .bashrc file and then sourcing it.
~$ . .bashrc
Errors occurred on two attempts after editing and then sourcing the bashrc file.  One was something like unescaped fi the other was unexpected end of file at line 75.

Here is the original feisty bashrc code:
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

Here is the modified code I inserted:
      # enable color support of ls and also add handy aliases

      if [ "$TERM" != "dumb" ]; then

          [ -e "$HOME/.dircolors" ] && DIR_COLORS="$HOME/.dircolors"

          [ -e "$DIR_COLORS" ] || DIR_COLORS=""

          eval "`dircolors -b $DIR_COLORS`"

          alias ls='ls --color=auto'

          #alias dir='ls --color=auto --format=vertical'

          #alias vdir='ls --color=auto --format=long'

      fi


I don't know if it's something I'm doing wrong or changes to Ubunutu Feisty making the code unworkable.

---

### Post by spratelboing on 2008-03-14
Unfortunately this tutorial didn't work for me (ubuntu gutsy gibbon), too. here is my .bashrc
perhaps someone knows the issue?

p.s. the last line I dropped in by myself.

thanx in advance!

---------------------------/.bashrc--------------------------------

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
    [ -e "$HOME/.dircolors" ] && DIR_COLORS="$HOME/.dircolors"
    [ -e "$DIR_COLORS" ] || DIR_COLORS=""
    eval "`dircolors -b $DIR_COLORS`"
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

PS1='\[\e[1;33m\]\n[\A]\[\e[0;34m\]\u@\h > \W\$\[\e[m\] '

-----------------------------------------------------------------------------------------

---

### Post by dmgExP on 2008-04-24
For anybody battling with dircolors here is a great little shell-script that displays every available colour combination for you to select from.

To execute type **bash ttycolors.sh**

---

### Post by pdxvampire on 2008-12-26
dmgExP - That script is excellent, thank you!  It saved me quite a bit of time in setting up dircolors for my various terminals, each of which has a different solid color background.  No more guessing, just fired up that script and was able to see what would work instantly!

---

### Post by cooltoddy on 2009-06-09
I know its been over 4 years after this post was made, but am trying my luck. Can you help me with the attachment you are talking about.

Thanks
CoolToddy!
> **skoal said:**
> 
....

[*](alternative to step 1.ii) **Patch the file**.  Using the attched 'bashrc.patch' file, patch the current '~/.bashrc' file instead of cutting/pasting with an editor.
```
skoal@morpheus:///tmp $ [COLOR=DarkRed]bunzip2 bashrc.patch.bz2[/COLOR]
skoal@morpheus:///tmp $ [COLOR=DarkRed]cp bashrc.patch ~[/COLOR]
skoal@morpheus:///tmp $ [COLOR=DarkRed]cd && patch -p0 < bashrc.patch[/COLOR]
patching file .bashrc
Hunk #1 succeeded at 19 (offset 5 lines).
```



---

### Post by tmllvs on 2009-06-17
[SIZE=2]Help, I followed the instructions from skoal (Thank You skoal).
 All my suffixes are changing to the correct color except for my
( .java, .c and .cpp ) suffixes. These suffixes are staying [COLOR=Lime]bright green.

[COLOR=Black]I set .java to [COLOR=Green]green[/COLOR] 00;32    .c to [COLOR=Sienna]brown[/COLOR] 00;36    and  .cpp to [COLOR=Cyan]cyan[/COLOR] 00;36

So when I type the ls command I would like to see:
$ls
 [COLOR=Sienna]foo.c[/COLOR]   [COLOR=Cyan] foo.cpp[/COLOR]    [COLOR=Green]foo.java

[COLOR=Black]however what I see is:
[/COLOR][/COLOR][/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=Lime][COLOR=Black]$ls
[COLOR=Lime] [/COLOR][COLOR=Lime]foo.c   [/COLOR][COLOR=Lime] foo.cpp    [/COLOR][COLOR=Lime]foo.java[/COLOR][/COLOR][/COLOR][/SIZE]

[SIZE=2]Is there anyway to be able to change these suffixes to the correct color?[/SIZE]

[SIZE=2]Below is my .dircolors file and .bashrc file:[/SIZE][B][SIZE=1]

.dircolor file

# Configuration file for dircolors, a utility to help you set the
# LS_COLORS environment variable used by GNU ls with the --color option.
# Copyright (C) 1996, 1999-2008
# Free Software Foundation, Inc.
# Copying and distribution of this file, with or without modification,
# are permitted provided the copyright notice and this notice are preserved.
# The keywords COLOR, OPTIONS, and EIGHTBIT (honored by the
# slackware version of dircolors) are recognized but ignored.
# Below, there should be one TERM entry for each termtype that is colorizable
TERM Eterm
TERM ansi
TERM color-xterm
TERM con132x25
TERM con132x30
TERM con132x43
TERM con132x60
TERM con80x25
TERM con80x28
TERM con80x30
TERM con80x43
TERM con80x50
TERM con80x60
TERM cons25
TERM console
TERM cygwin
TERM dtterm
TERM eterm-color
TERM gnome
TERM gnome-256color
TERM konsole
TERM kterm
TERM linux
TERM linux-c
TERM mach-color
TERM mlterm
TERM putty
TERM rxvt
TERM rxvt-cygwin
TERM rxvt-cygwin-native
TERM rxvt-unicode
TERM screen
TERM screen-256color
TERM screen-bce
TERM screen-w
TERM screen.linux
TERM vt100
TERM xterm
TERM xterm-16color
TERM xterm-256color
TERM xterm-88color
TERM xterm-color
TERM xterm-debian
# Below are the color init strings for the basic file types. A color init
# string consists of one or more of the following numeric codes:
# Attribute codes:
# 00 none 01 bold 04 underscore 05 blink 07 reverse 08 concealed
# Text color codes:
# 30 black 31 red 32 green 33 yellow 34 blue 35 magenta 36 cyan 37 white
# Background color codes:
# 40 black 41 red 42 green 43 yellow 44 blue 45 magenta 46 cyan 47 white
NORMAL 00 # global default, although everything should be something.
FILE 00 # normal file
DIR 01;34 # directory
LINK 01;36 # symbolic link. (If you set this to 'target' instead of a
 # numerical value, the color is as for the file pointed to.)
FIFO 40;33 # pipe
SOCK 01;35 # socket
DOOR 01;35 # door
BLK 40;33;01 # block device driver
CHR 40;33;01 # character device driver
ORPHAN 40;31;01 # symlink to nonexistent file, or non-stat'able file
SETUID 37;41 # file that is setuid (u+s)
SETGID 30;43 # file that is setgid (g+s)
STICKY_OTHER_WRITABLE 30;42 # dir that is sticky and other-writable (+t,o+w)
OTHER_WRITABLE 34;42 # dir that is other-writable (o+w) and not sticky
STICKY 37;44 # dir with the sticky bit set (+t) and not other-writable
# This is for files with execute permission:
EXEC 01;32
# List any file extensions like '.gz' or '.tar' that you would like ls
# to colorize below. Put the extension, a space, and the color init string.
# (and any comments you want to add after a '#')
# If you use DOS-style suffixes, you may want to uncomment the following:
#.cmd 01;32 # executables (bright green)
#.exe 01;32
#.com 01;32
#.btm 01;32
#.bat 01;32
# Or if you want to colorize scripts even if they do not have the
# executable bit actually set.
#.sh 01;32
#.csh 01;32
 # archives or compressed (bright red)
.tar 01;31
.tgz 01;31
.svgz 01;31
.arj 01;31
.taz 01;31
.lzh 01;31
.lzma 01;31
.zip 01;31
.z 01;31
.Z 01;31
.dz 01;31
.gz 01;31
.bz2 01;31
.bz 01;31
.tbz2 01;31
.tz 01;31
.deb 01;31
.rpm 01;31
.jar 01;31
.rar 01;31
.ace 01;31
.zoo 01;31
.cpio 01;31
.7z 01;31
.rz 01;31
# image formats
.jpg 01;35
.jpeg 01;35
.gif 01;35
.bmp 01;35
.pbm 01;35
.pgm 01;35
.ppm 01;35
.tga 01;35
.xbm 01;35
.xpm 01;35
.tif 01;35
.tiff 01;35
.png 01;35
.svg 01;35
.mng 01;35
.pcx 01;35
.mov 01;35
.mpg 01;35
.mpeg 01;35
.m2v 01;35
.mkv 01;35
.ogm 01;35
.mp4 01;35
.m4v 01;35
.mp4v 01;35
.vob 01;35
.qt 01;35
.nuv 01;35
.wmv 01;35
.asf 01;35
.rm 01;35
.rmvb 01;35
.flc 01;35
.avi 01;35
.fli 01;35
.gl 01;35
.dl 01;35
.xcf 01;35
.xwd 01;35
.yuv 01;35
# audio formats
.aac 00;36
.au 00;36
.flac 00;36
.mid 00;36
.midi 00;36
.mka 00;36
.mp3 00;36
.mpc 00;36
.ogg 00;36
.ra 00;36
.wav 00;36
.red 00;31
.green 00;32
.yellow 00;33
.blue 00;34
.magenta 00;35
.cyan 00;36
.blueb 01;34
.blueu 04;34
.bluebi 05;34
.bluer 07;34
.brown 00;33
.blackb 01;30
.redb 01;31
.yellow 01;33
.magentab 01;35
.cyanb 01;36
.gray 00;37
.greenb 01;32
.java 00;32
.c 00;33
.cpp 00;36

[COLOR=Red]------------------------- end of .dcolors file   ------------------------------------------[/COLOR]
[/SIZE][/B][SIZE=2][COLOR=Lime][COLOR=Black][COLOR=Green][COLOR=Black]
[B][SIZE=1].bashrc file

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
export HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
export HISTCONTROL=ignoreboth

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

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ] ; then
    [ -e "$HOME/.dircolors" ] && DIR_COLORS="$HOME/.dircolors"
    [ -e "$DIR_COLORS" ] || DIR_COLORS=""
    eval "`dircolors -b $DIR_COLORS`"

    #eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

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

#MY STUFF BELOW HERE.
#------------------------
export PS1="\e[0;31m\! \d \t \u \w\$ \e[m\n"
export CLASSPATH=/home/my/java/myclass;

[COLOR=Red]----------------------------    end of .bashrc file       --------------------------------
[SIZE=2]
[/SIZE][/COLOR][/SIZE][/B][SIZE=1][COLOR=Red][SIZE=2][COLOR=Black]Any help would be greatly appreciated.

Thank You,
tmllvs ;)
[/COLOR][/SIZE][/COLOR][/SIZE][B][SIZE=1][COLOR=Red][SIZE=2][/SIZE]

[/COLOR]
[/SIZE][/B][/COLOR][/COLOR][/COLOR][/COLOR]
[/SIZE]

---

### Post by tmllvs on 2009-06-18
OOPS. I found the problem.
All excutables are [COLOR=Lime]bright-green [/COLOR].
Some how the .java , .cpp, and .c files had executable permissions.
When I took away the executable permissions by typing ( chmod ugo -x  *.java  etc.. )
the colors to my suffixes were the I wanted them.

[SIZE=2]Thanks again to skoal[/SIZE] for the great instructions .
tmllvs

---

### Post by CylnZ on 2009-06-18
\\:D/Excellent!! Thank you skoal  :KS:KS:KS

---

### Post by A_M_S on 2009-09-22
Excellent thread. Thank you!

---

### Post by Josh K on 2010-05-02
Hate to bump an old thread, but I can't seem to get the colors to change. In particular the green hi-light is bugging the crap out of me.

---

### Post by luca.cappelletta on 2010-11-05
> **Josh K said:**
> Hate to bump an old thread, but I can't seem to get the colors to change. In particular the green hi-light is bugging the crap out of me.

look for the 'STICKY_OTHER_WRITABLE' or 'OTHER_WRITABLE' entries

---

### Post by rre12 on 2010-11-15
Sorry to bump this thread, but what would the tcsh equivalent script of that bash script be?

---

### Post by leomeloxp on 2011-04-03
Sorry for bumping it once again, but I doing this customs and I got the same execute permissions problem, but they are with the .mp3 .png and some other extensions... I try to chmod -x the *.mp3 but it doesn't work. Does any one have any clue on how to do it?

Thanks in advance =]

---

### Post by Tehrasha on 2012-03-05
One more bump for the ancient thread..

Default colors, for as long as I can remember, have never worked properly when outputting directory listings to a color xterm.

Generic files are colored grey until a directory or special file-type is highlighted bold, from then on all generic files are bold grey (bright white).

example:::

[COLOR="Silver"]generic file
generic file[/COLOR]
[COLOR="Blue"]directory[/COLOR]
[COLOR="White"]generic file
generic file[/COLOR]
[COLOR="Lime"]special filetype[/COLOR]

..I tend to use black backgrounds, so the white text on white background in the above doesnt happen to me.

I see this behavior in aterm, xterm, putty, and every other color term i have used as far back as Ubuntu 6.06

The only reliable fix i have seen is to alias all ls to ls-a so the first file listed it always   .  in bold.


Surely there must be a better fix for this?

---

