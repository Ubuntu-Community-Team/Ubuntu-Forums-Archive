---
title: "Post your bash scripts and aliases!"
date: 2007-11-18
forum: The Cafe
---

### Post by Interestedinthepenguin on 2007-11-18
I have gotten into bash scripting and am having a blast. :) 

I am curious of what others have created.


Here are my scripts (some may need some personalizing tweaks):

_info.sh_ screenshot script (not mine; from [http://ubuntukids.org/blog/?page_id=25](http://ubuntukids.org/blog/?page_id=25)), I modded it to display Beryl theme, font, and conky font

_conky-pack_ creates a conky startup script, tars it and my conky(rc) files, and deletes the newly created script.

_febe-sort_ sorts the files exported by FEBE (Firefox extension), placing them in separate directories.

_port-stylishrdf_ copies the file, stylish.rdf, to another directory as a backup method. (is in my crontab file)

_port-searchp_ ports the Firefox's searchplugins folder as a means of backup

_ls2_ modifies sort order of 'ls' to: directories (numbers, capital, lowercase), files (numbers, capital, lowercase).  ...serves as one of my aliases.

_ls2a_ like ls2, but also lists hidden files.

**aliases:**
ls2=$HOME/scripts/ls2

lsa=$HOME/scripts/ls2a

updatedb='sudo updatedb -v'

ytdl='youtube-dl -t'

srmn='apropos'


Cronjobs are welcome.:)

---

### Post by zman58 on 2007-11-19
One of my most useful scripts is a bash script that provides a neat and orderly way to mount to CIFS shares (Windows network shares). You place  a simple client script in ~/bin/. along with the smb_net include script. The client script contains the user, server, share, domain, and includes (by reference) the smb_net script. The smb_net script contains all of the logic for using the client information and attaching to a CIFS network. smb_net creates a ~/mnt directory and attaches the CIFS share beneath the user account. Once you get your client scripts set up, it makes mounting to specific network shares a breeze! I use this very often.

I attached a tar file that contains several sample client scripts and the smb_net script that is included in each of the clients scripts. Make sure to follow the instructions in the smb_net. You must make sure user account is a member of the "users" group and provide the documented users sudo entry. This needs to be done only once for everything to work properly.

---

### Post by blithen on 2007-11-19
I made a small bash that preloads a hack for Urban Terror then runs the game.
Though I don't think it's really worth attaching to my post.

---

### Post by ice60 on 2007-11-19
i got loads of stuff, most i got from the internet and maybe changed a bit.

here's a clock

```
# clock - A bash clock that can run in your terminal window. 
clock () 
{ 
while true;do clear;echo "===========";date +"%r";echo "===========";sleep 1;done 
}
```

network info
```
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
```

define a word
```
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
```

here's a find function
```
function    ff               { find . -name $@ -print; }
```

here's a welcome message for when i open my terminal
```
clear

echo -ne "${LIGHTGREEN}" "Hello, $USER. today is, "; date
echo -e "${WHITE}"; cal ;  
echo -ne "${CYAN}";
echo -ne "${LIGHTPURPLE}Sysinfo:";uptime ;echo ""
```

here are some colour definitions for the above message
```
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
```

some aliases
```
# screenshots
alias screenshot='import -window root ~/Desktop/`date +%Y%m%d%H%M`.png'

# System info
alias cpuu="ps -e -o pcpu,cpu,nice,state,cputime,args --sort pcpu | sed '/^ 0.0 /d'"
alias memu='ps -e -o rss=,args= | sort -b -k1,1n | pr -TW$COLUMNS'
alias pg='ps aux | grep'  #requires an argument

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
alias today='grep -h -d skip `date +%m/%d` /usr/share/calendar/*'

# network
alias net1='watch --interval=2 "sudo netstat -apn -l -A inet"'
alias net2='watch --interval=2 "sudo netstat -anp --inet --inet6"'  
alias net3='sudo lsof -i'
alias net4='watch --interval=2 "sudo netstat -p -e --inet --numeric-hosts"'
alias net5='watch --interval=2 "sudo netstat -tulpan"'
alias net6='sudo netstat -tulpan'
alias net7='watch --interval=2 "sudo netstat -utapen"'
alias net8='watch --interval=2 "sudo netstat -ano -l -A inet"'
alias netl='sudo nmap -sT -O localhost'
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
alias lss='ls -shaxSr'            # sort by size
alias lt='ls -latr'               # sort by date
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

# weather
alias weather='/home/iceni60/scripts/conky_scripts/weather.sh UKXX0085'

# Music
alias ncmpc='ncmpc -cm'
```

i added the scripts for the weather, whatsmyip, unpack and calculator. probably no one will use them, but if i ever lose everything i can come to this thread lol

MD5     794730399e2acdf0e5983f90a53632cf  scripts.tar.gz

---

### Post by corney91 on 2007-11-19
I've only made one script which deleted all the images from my Music folder, but I lost it when I reinstalled.

I'm cutting back on using aliases cuz I'm getting too dependant:p
Here they are:
```
#aliases
alias aliases='(gedit ~/.bash_aliases &)'

#remote desktop
alias school='(rdesktop [School IP] &)'

#cd
alias m='cd ~/Music'
alias i='cd ~/Pictures'
alias h='cd ~/Homework'
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
alias del='mv --target-directory=~/.Trash/'

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
alias conkyrc='(gedit ~/.conkyrc ~/.conkyrc4 &)'
alias conkyall='conky -c ~/.conkyrc && conky -c ~/.conkyrc4'

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

### Post by ice60 on 2007-11-19
i have got some more too, below. 

but, i was wondering if this alias could cause problems -
```
alias d='cd /home/iceni60/Desktop'
```
because i remember having it in the past and i removed it for some reason, i can't remember why. also, i'd think it's quite an obvious alias to have, but no one else seems to have it??

```
# General
alias df='df -h'
alias h='history'
alias d='cd /home/iceni60/Desktop'
alias duck='du -skc * | sort -rn'
alias open='gnome-open'
alias chm='kchmviewer'
alias nb='nano ~/.bashrc'

# lynx web browser
alias bbc='lynx http://news.bbc.co.uk/text_only.stm'
alias nytimes='lynx http://nytimes.com'
alias google='lynx http://google.co.uk'

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

```

and i made these for my prompt, i really like the way my prompt is 8) can anyone see any problems with them? some i got off the internet and i made the others, those are the ones that might have some mistakes :|

```
############################## ##################################
# ##### PROMPT SECTION ##### ####################################
############################## ##################################

##PS1="\[[32m\]\u:\w > \[[39m\]"
##PS1="\[[31m\][\[[32m\]\u\[[31m\]]\[[32m\]\w > \[[39m\]"
#PS1="\[[40;1;31m\][\[[1;32m\]\u\[[1;31m\]]\[[49;1;32m\]\w > \[[22;39m\]"
#PS1="\[[1;31m\][\[[1;32m\]\[[47m\]\u\[[1;31m\]\[[49m\]]\[[1;32m\]\w > \[[22;39m\]"
##PS1="\[[31m\][\[[36m\]\u\[[31m\]]\[[36m\]\w > \[[39m\]"
#PS1="\[[32m\]\u \[[39m\]\$\[[32m\] \w \[[39m\]"

###################### the above are separate prompts which can be used instead of below. NOTE: only ONE line at a time should be uncommented. so there are 6 different prompts above!!!!!

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
i took a picture showing the welcome message with some of the aliases [img]http://www.websmileys.com/sm/cool/cool24.gif[/img]

---

### Post by toupeiro on 2007-11-19
A lot of my scripts apply to network environments, thus wouldn't be much good to people without a lot of modification. 

I will share a goodie though, for those of you who support or use AMD (AutoMounter Daemon, not Advanced Micro Devices)
```

alias up 'cd $cwd:h/\!*'  #<-- traverse up one logical directory path as opposed to an exported physical path, remounting if necessary.

```

---

### Post by toupeiro on 2007-11-19
[QUOTE=toupeiro;3802415]A lot of my scripts apply to network environments, thus wouldn't be much good to people without a lot of modification. 

I will share a goodie though, for those of you who support or use AMD (AutoMounter Daemon, not Advanced Micro Devices)
[CODE]
alias up 'cd $cwd:h/\!*'  #<-- traverse up one logical directory path as opposed to an exported physical path, remounting if necessary.

---

### Post by Interestedinthepenguin on 2007-11-19
**@ice60**

Nothing appears to be wrong with the cd-to-desktop alias.  

> **ice60 said:**
> ...i'd think it's quite an obvious alias to have, but no one else seems to have it??


It wasn't an obvious alias to me.  ...I don't change to that directory often enough. :)

Nice prompt. :popcorn:  ...but some of the code came out as odd characters.

Here's mine:

```

PS1='${debian_chroot:+($debian_chroot)}\[\033[36;1m\](\l)\[\033[01;32m\]\u@\h:\[\033[37;1m\]\$\[\033[01;34m\]\w/\[\033[00m\]'

```

I just changed it yesterday. :)

The fun part about it is that it shows which terminal I'm in.

---

### Post by ice60 on 2007-11-20
> **Interestedinthepenguin said:**
> **@ice60**

Nothing appears to be wrong with the cd-to-desktop alias.  



It wasn't an obvious alias to me.  ...I don't change to that directory often enough. :)

Nice prompt. :popcorn:  ...but some of the code came out as odd characters.

Here's mine:

```

PS1='${debian_chroot:+($debian_chroot)}\[\033[36;1m\](\l)\[\033[01;32m\]\u@\h:\[\033[37;1m\]\$\[\033[01;34m\]\w/\[\033[00m\]'

```

I just changed it yesterday. :)

The fun part about it is that it shows which terminal I'm in.
i'll keep the d alias then, thanks :)

i always forget most people use their home directory for a lot of their work whereas i use the desktop :|

---

### Post by ice60 on 2007-11-20
look at this
[http://ubuntuforums.org/showthread.php?t=276906](http://ubuntuforums.org/showthread.php?t=276906)

i was thinking earlier if i wanted to change my prompt i'd have to read up on it, i know it only takes a few minutes but that app might help?? i found that page by accident, i was looking up an error message (i'm just trying an ubuntu livecd, i fixed everything now)

---

### Post by aJayRoo on 2007-11-20
A small function that I find quite useful to have in my bashrc. It creates a new directory and then changes to that new directory, simple as that!
```
function mkdcd ()
{
    if [ $# -ne 1 ]; then
        echo 'function takes exactly one argument!'
        return 1
    fi
    mkdir "$1"
    cd "$1"
}
```

---

### Post by ice60 on 2007-11-20
> **aJayRoo said:**
> A small function that I find quite useful to have in my bashrc. It creates a new directory and then changes to that new directory, simple as that!
```
function mkdcd ()
{
    if [ $# -ne 1 ]; then
        echo 'function takes exactly one argument!'
        return 1
    fi
    mkdir "$1"
    cd "$1"
}
```
did you make that? what does this bit mean $#, or the #? i know the variable bit. i tried it out i'll use it too but i'm using a livecd atm.

---

### Post by aJayRoo on 2007-11-20
Yes I wrote the function myself. '$#' is the variable that stores the number of arguments given to the function. That part is just checking that exactly one argument is given to the function.

---

### Post by zach12 on 2007-11-20
I've been working on a wifi config script

---

### Post by bobbocanfly on 2007-11-20
Last script i wrote was for Slax to automount my modules. Pretty flawed though as i had to save it and the modules on another computer, got rid of it when i remembered it was a bit stupid.

The last proper script was FramegrabGTK. A script that uses Zenity, Mplayer and Imagemagick to extract video stills and create a montage of them. Working on that with another person. Quite fun but could probably be done with much less hassle in Python or something.

---

### Post by Interestedinthepenguin on 2007-11-20
**@ice60**:
There's nothing wrong with using the desktop.  I used to use it, but it would get pretty messy, now I just clutter my directories, instead.:lolflag:  
> **ice60 said:**
> look at this
[http://ubuntuforums.org/showthread.php?t=276906](http://ubuntuforums.org/showthread.php?t=276906)

i was thinking earlier if i wanted to change my prompt i'd have to read up on it, i know it only takes a few minutes but that app might help?? ...

It might.  

I prefer to not have some things done automatically.  My #1 reason: It takes some of the fun out.:cool:

If you don't mind changing the prompt by hand check these links out: 

[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html)

[http://www.pantz.org/software/shell/enhancingshellprompt.html](http://www.pantz.org/software/shell/enhancingshellprompt.html)

You can test out your customizations like this: ```
echo $PS1
``` 
copy the output, make changes, and then ```
export PS1=pasteyourmoddedcodehere
```.  

You will see the changes immediately.  If you want to get rid of the changes, close the terminal window (or just open another one).

You can also put the color codes into variables, like this user: 

[http://ubuntuforums.org/showpost.php?p=156019&postcount=3](http://ubuntuforums.org/showpost.php?p=156019&postcount=3)


**@aJayRoo:**

I know I can just google this, but how do functions work; via aliases, bash scripts?

---

### Post by Anonii on 2007-11-20
[http://forums.gentoo.org/viewtopic-t-15443-highlight-aliases+tricks.html](http://forums.gentoo.org/viewtopic-t-15443-highlight-aliases+tricks.html)

---

### Post by Interestedinthepenguin on 2007-11-20
Ooh.  Thanks, Anonii. :D

---

### Post by ssam on 2007-11-20
```

# colour prompt
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

#promt length switching
alias ps1_short="PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\W\[\033[00m\]\$ '"
alias ps1_long="PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '"

# bash history tweaks
export HISTFILESIZE="2000"
export HISTCONTROL="ignoreboth"
export HISTCONTROL="ignoredups"

# useful aliases
alias h="history|grep "
alias f="find . |grep "
alias p="ps aux |grep "
alias o="gnome-open "


```

---

### Post by aJayRoo on 2007-11-21
> **Interestedinthepenguin said:**
> 
**@aJayRoo:**

I know I can just google this, but how do functions work; via aliases, bash scripts?

The function I posted is defined in my '~/.bashrc' file. This means it is defined inside every shell I open. The purpose of using a function for this task is so that once the directory is created I can also change to that directory and stay there once the function is executed. The function executes in the current shell, not in a new one like a script does. Hope that helps.

---

### Post by ice60 on 2007-11-21
> **aJayRoo said:**
> Yes I wrote the function myself. '$#' is the variable that stores the number of arguments given to the function. That part is just checking that exactly one argument is given to the function.
thanks, i wrote some basic when i was about 8 and i never managed to improve from that lol. i've got a few programming books too, but i never use them :(

---

### Post by ice60 on 2007-11-21
> **Interestedinthepenguin said:**
> **@ice60**:
There's nothing wrong with using the desktop.  I used to use it, but it would get pretty messy, now I just clutter my directories, instead.:lolflag:  


It might.  

I prefer to not have some things done automatically.  My #1 reason: It takes some of the fun out.:cool:

If you don't mind changing the prompt by hand check these links out: 

[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html)

[http://www.pantz.org/software/shell/enhancingshellprompt.html](http://www.pantz.org/software/shell/enhancingshellprompt.html)

You can test out your customizations like this: ```
echo $PS1
``` 
copy the output, make changes, and then ```
export PS1=pasteyourmoddedcodehere
```.  

You will see the changes immediately.  If you want to get rid of the changes, close the terminal window (or just open another one).

You can also put the color codes into variables, like this user: 

[http://ubuntuforums.org/showpost.php?p=156019&postcount=3](http://ubuntuforums.org/showpost.php?p=156019&postcount=3)


**@aJayRoo:**

I know I can just google this, but how do functions work; via aliases, bash scripts?i don't know why i posted that, it was just a coincidence i found it i suppose. i'm going to go and read one of my bash scripting books :lolflag:

---

### Post by tdrusk on 2007-11-22
I'm making my grandfather a computer since we are getting him a digital camera for christmas. I got it so when he plugs in the camera it automatically syncs the pictures to a folder, deletes the pictures off the camera, opens a window of all of his pictures and unmounts the drive. ahh old people

```
#!/bin/bash
# Sync Files
rsync -av /media/disk/test /home/tyler/Test
#Delete Files From Camera
rm -r /media/disk/test
#Wait For Indexing To Catch Up
sleep 10
#Open Nautilus Search
nautilus /home/tyler/Desktop/Test.savedSearch
#Unmount Drive
eject /media/disk/
```
The Open Nautilus Search is a saved search I did in Nautilus of .JPG in the /home/tyler/Test directory. Pretty nifty.

---

### Post by K.Mandla on 2007-11-23
> **ice60 said:**
> here's a welcome message for when i open my terminal. ...
```
clear

echo -ne "${LIGHTGREEN}" "Hello, $USER. today is, "; date
echo -e "${WHITE}"; cal ;  
echo -ne "${CYAN}";
echo -ne "${LIGHTPURPLE}Sysinfo:";uptime ;echo ""
```
Hold on a second. ... This is a one-time message when you open an emulator? I've been wanting to do that for a while; where do you put that? What triggers it?

---

### Post by spupy on 2007-11-25
I just wanted to make a thread like this! I have loads of aliases in bashrc, but they are nothing special. I like to write scripts that use zenity; here are some:
- change mouse from left to right handed
- a little textbox to set the names of windows
- another zenity script that one can use to post to his tumblr.
- a simple text editor only using zenity! It's called zen :D

---

### Post by picklesmagee on 2007-11-29
heres a playlist gen script for video files.. picked the 11 most used.. 
 add anything i missed.. creates .m3u in every directory it's executed in.. 
... useful an easy to have a videoplaylist jukebox folder
  then just "mplayer -playlist blabla.m3u"
----------------------------------------------------------

#!/bin/bash
# Generates .m3u for many Video Formats
#
#
IFS=$'\n' # Input Field Separator
#
M3Ulist="`pwd`/M3UfileList.txt"
#
rm -f $M3Ulist
#
indexCurrDir ()
{
FileList="" # initialize empty variable FileList
for FileTypes in "ogm" "mov" "mpeg" "mpg" "mp4" "m4v" "avi" "wmv" "flv" "swf" "vob"
#
do
FindFiles=$(find $(pwd) -type f -iname "*.$FileTypes" | sort)
#
FileList=$FileList$FindFiles
#
done
#
if [ "${#FileList}" != "0" ]
then
CurrDir=$(pwd)
echo "$CurrDir"
m3uName=$(basename $CurrDir)
#
echo "Writing m3u playlist."
echo "$FileList" > "${m3uName}.m3u"
echo "$CurrDir/${m3uName}.m3u" >> "$M3Ulist"
#
fi
}

AllDirs=$(find $(pwd) -type d | sort)
for Directory in $AllDirs
do
cd "$Directory"
indexCurrDir
done

exit 0
----------------------------------------------------------------
.......
an here move the playlist with ease...
------------------------------------------------------------------
#!/bin/bash

find /path/to/video/folders -name "*.m3u" -print0 | xargs -0 cp --target-directory /path/to/videoplaylist

done
--------------------------------------------------------------------
.. :)

---

### Post by victorbrca on 2007-11-29
Simple as the noob I'm .. ;)


```
########################
### personal aliases ###
########################

# Basics
alias cp='cp -v -i'
alias rm='rm -i'
alias mv='mv -i' 
alias utar='tar -xvf'
alias utarz='tar -xzvf'
alias tarz='tar -czvf'
alias lah='ls -lah'
alias fproces='ps x | grep '

# SSH
## bunch of ssh aliases with port binding

# Software Management
alias aptl='sudo apt-get update && sudo apt-get install'
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias inst='sudo apt-get install'
alias apts='sudo apt-cache search'
alias updupg='sudo apt-get update && sudo apt-get upgrade'

## Check IP ##
alias my-ip='wget http://checkip.dyndns.org/ -O - -o /dev/null | cut -f7 -d"<" | cut -f2 -d">" '
```


Vic.

---

### Post by arsenic23 on 2007-11-29
[COLOR="DarkRed"]**Aliases:**[/COLOR]
```
# System
alias thumbclean="find ~/.thumbnails -type f -atime +7 -exec rm {} \;"
alias sudoupdate="sudo apt-get update&&sudo apt-get upgrade"
alias sudoshutdown="sudo shutdown now -h"
alias acs="apt-cache search"
alias aci="apt-cache showpkg"
alias addalias="nano ~/.bash_aliases"
alias cl="clear&&ls"
alias cll="cd ~/&&clear&&ls"
alias clll="clear&&ls -la"

# Scripts
alias work="sh ~/Desktop/work.sh"
alias workpy="python ~/Desktop/work.py"
alias killzip="rename 's/\.rar/.cbr/' *.rar && rename 's/\.zip/.cbz/' *.zip"
alias comicgo="sh ~/userscripts/comicscript.sh"
alias goodnameonly="sh ~/userscripts/goodnameonly.sh"

# Misc
alias pxcpu="ps -e -o pcpu,cpu,nice,state,cputime,args --sort pcpu | sed '/^ 0.0 /d'"
alias pxmem='ps -e -o rss=,args= | sort -b -k1,1n | pr -TW$COLUMNS'
alias today='grep -h -d skip `date +%m/%d` /usr/share/calendar/*'

#Radio
alias radioparadise="vlc http://www.radioparadise.com/musiclinks/rp_128.m3u &"
alias radioparadise2="amarok http://www.radioparadise.com/musiclinks/rp_128.m3u &"
alias kohina="vlc http://stream.nute.net/kohina/fresh.ogg.m3u &"
alias kohina2="amarok http://stream.nute.net/kohina/fresh.ogg.m3u &"

# Apps
alias wgtmp="cd ~/Desktop && wget --ftp-user=****** --ftp-pass=****** --tries=0 --retry-connrefused -c  -r ftp://******.*****.***/tmp"
alias sshgo="ssh ****@****.*****.***"
alias pydump="python ~/userscripts/python/pydump.py"
alias megapydump="python ~/userscripts/python/megapydump.py"
```


[COLOR="#8b0000"]**Script to toggle uploading on my vsftp server:**[/COLOR]
```
#!/bin/bash
# Toggle vsftpd uploading on/off --
# Run as superuser

inform(){
i=`grep write_e /etc/vsftpd.conf | grep -v anon`;
sh /etc/init.d/vsftpd restart
if [ $i = "#write_enable=YES" ]; then
        echo " User write function has been turned OFF.";
elif [ $i = "write_enable=YES" ]; then
        echo " User write function has been turned ON.";
else
        echo " Error with vsftpd.conf."
fi
return
}


if [ $1 = "on" ]; then
        sed -e 's/^\#write_e/write_e/' /etc/vsftpd.conf > /etc/ftp.tmp ; 
        rm /etc/vsftpd.conf; 
        mv /etc/ftp.tmp /etc/vsftpd.conf;
        inform;
elif [ $1 = "off" ]; then
        sed -e 's/^write_e/\#write_e/' /etc/vsftpd.conf > /etc/ftp.tmp ;
        rm /etc/vsftpd.conf; 
        mv /etc/ftp.tmp /etc/vsftpd.conf;
        inform;
else
        echo "$1 is not a valid option."; echo "Please try again using 'on' or 'off'.";
fi
```


[COLOR="#8b0000"]**Script to rename comic files as I download them:**[/COLOR]
```
#!/bin/bash

rename 's/\ /\_/g' *.[zrc][iab][prz]
rename 's/(^[^\[]*)(\[[^]]*\])([^.]*)/$1$3$2/' *.[zrc][iab][prz]
rename 's/\.zip/\.cbz/' *.zip
rename 's/\.rar/\.cbr/' *.rar
rename 's/[_]\_*/\ /g' *.[zrc][iab][prz]
rename 's/\ \./\./' *.cb[rz]
rename 's/^[ ]*//' *.cb[rz]
```

---

### Post by picklesmagee on 2007-12-01
~/.bashrc on my macbook
-----------------------

#!bashrc

# path to bin
###########################################################

export PATH="$PATH:$HOME/bin"

# d. resizing
###########################################################

shopt -s checkwinsize

# c. prompt
###########################################################
export PS1="\n\$(/bin/date)\n\$(/usr/bin/tty | /bin/sed -e 's:/dev/::'): \$(/bin/ls -1 | /usr/bin/wc -l | /bin/sed 's: ::g') files \$(/bin/ls -lah | /bin/grep -m 1 total | /bin/sed 's/total //')b [\w] \n \u @ \h~:/ "

# Add color
eval `dircolors -b`

# colors
###########################################################

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
NC='\e[0m' 

# systeminfo
###########################################################

alias sinfo='~/scripts/sysinfo.sh '
alias ssinfo='~/scripts/ssinfo.sh '

# User defined aliases
###########################################################

alias ll='ls -l'
alias lsa='ls -A'
alias lsg='ls | grep'
alias lll='ls -al'
alias cls='clear'
alias clls='clear; ls'
alias na='nano'
alias web='lynx -g -download-dir ~/ [www.google.com](www.google.com)' 
alias ~='cd ~'
alias md=mkdir
alias ps='ps -ax'
alias home='cd ~'
alias un='tar -zxvf'
alias mountedinfo='df -hT'
alias ping='ping -c 10'
alias ns='netstat -alnp --protocol=inet | grep -v CLOSE_WAIT | cut -c-6,21-94 | tail +2'
alias da='date "+%Y-%m-%d %A    %T %Z"'
alias ebrc='nano ~/.bashrc'
alias c='cal'
alias up='uptime'
alias exi='exit'
alias shutdown='sudo shutdown -h now'

# figlet
#############################################

alias figlet='figlet -d ~/.figfonts/ '


# mntd info
##########################################################

alias mountedinfo='df -hT'

# c. hardware
##########################################################

alias dvdo='eject /dev/dvd'
alias dvdc='eject -t /dev/dvd'
alias scan='scanimage -L'
alias playw='for i in *.wav; do play $i; done'
alias playo='for i in *.ogg; do play $i; done'
alias playm='for i in *.mp3; do play $i; done'

# applications
##########################################################
alias tronad='/usr/local/bin/armagetronad'
alias copydisk='dd if=/dev/dvd of=/dev/dvdrecorder'
alias dvd_rip='vobcopy -i /dev/dvd/ -o /media/1/DVDs/ -l'

#alias to scripts
###########################################################
#audio
alias aac2mp3='~/scripts/audio/aac2mp3.sh '
alias cleanmp3='~/scripts/audio/cleanmp3.sh '
alias m4a2mp3='~/scripts/audio/m4a2mp3.sh '
alias m4a2wav='~/scripts/audio/m4a2wav.sh '
alias m4a2ogg='~/scripts/audio/m4a2ogg.sh '
alias mp32wav='~/scripts/audio/mp32wav.sh '
alias mp32ogg='~/scripts/audio/mp32ogg.sh '
alias ogg2mp3='~/scripts/audio/ogg2mp3.pl '
alias tagm4a2mp3='~/scripts/audio/tagm4a2mp3.sh '
alias wav2mp3='~/scripts/audio/wav2mp3.sh '
alias wav2ogg='~/scripts/audio/wav2ogg.sh '
alias wma2mp3='~/scripts/audio/wma2mp3.sh'
alias wma2wav='~/scripts/audio/wma2wav.sh '
alias rmm4a='~/scripts/audio/rmm4a.sh '
alias rmwav='~/scripts/audio/rmwav.sh '
alias rmogg='~/scripts/audio/rmogg.sh '
alias mvm3uplayfolder='~/scripts/audio/mvm3uplayfolder.sh '
#video
alias DvDencoder='~/scripts/DvD_encoder.sh '
alias snapscreen='~/scripts/scrotsnap.sh '
alias snapdelay='~/scripts/scrotdelay.sh '
alias dragscrot='~/scripts/dragscrot.sh 
alias sub2srt='~/.sub2srt/sub2srt 

#alias to ssh
###########################################################

alias mediatwr='ssh [email]username@lol.mydomain.com[/email] -p ######'
alias wrktwr='ssh [email]username@lol.mydomain.com[/email] -p ######'

#misc scripts
###########################################################

alias wooisip='~/scripts/whois_simple.sh'
alias passwordgen='~/scripts/passgen.sh'
alias treedirlist='~/scripts/tree.sh'
alias wgetter2='~/scripts/wgetter2.bash'

# WELCOME SCREEN
###########################################################

clear
echo "";
#sysinfo
uptime
echo "";
fortune
echo "";

#EOF
###########################################################

---

### Post by blithen on 2007-12-01
Wow! Lots of new information I never new of before in here.

---

### Post by Interestedinthepenguin on 2007-12-01
I've modified the ls2 script.  (Filenames that start with a number were being displayed with the folders.)


```

ls -F | grep "^\.*[[:digit:]]" | grep "\/"
ls -F | grep "^\.*[A-Z]" | grep "\/"
ls -F | grep "^\.*[a-z]" | grep "\/"
ls -F | grep "^\.*[[:digit:]]" | grep -v "\/"
ls -F | grep "^\.*[A-Z]" | grep -v "\/"
ls -F | grep "^\.*[a-z]" | grep -v "\/"

```

conky=$HOME/scripts/strt-conky
clr='clear'
cron='crontab -e'
awn='avant-window-navigator'
chmod='chmod -c'
grep='grep --colour'

I read that if you want to run a command (that alias has taken the name of), prefix the command with a backslash.:popcorn:

---

### Post by Interestedinthepenguin on 2007-12-17
echo='echo -e'
killfx='killall firefox-bin'
rm='rm -i'
c2desk='cd ~/Desktop'


fxproflist
```

#!/bin/bash

#Lists ("in-use") Firefox profiles
#An "in-use" profile is one that is "attached" to Firefox (not one whose files still exist even though it was deleted from Firefox's Profile Manager.
#Created by Interestedinthepenguin 12/13/2007

echo
echo -e "Firefox Profiles\n------------------"
echo

profnm=$(grep -i name /home/suna/.mozilla/firefox/profiles.ini | cut -b 6-)
for i in $profnm
do
	echo $i | sed 's/$/ == /' >> ~/.fx222
done

line=1
profpth=$(grep -i path /home/suna/.mozilla/firefox/profiles.ini | cut -b 6-)
for ii in $profpth
do
	sed -e "$line s/$/$ii/" ~/.fx222 -e "/ == $/d"
	line=$((line+1))
done

echo
rm ~/.fx222

```


exedump
```

#!/bin/bash
#dump executables in $PATH to file
#Created by Interestedinthepenguin 12/13/2007

echo  -e "\n\t\tExecutables in \$PATH\n-------------------------------------------------\n" > ~/.exedump1
echo -e > ~/.exedump2
paths=$(echo $PATH | sed "s/:/ /g")
for i in $paths
do
ls -F $i | sed -e '/[^@*]$/d' -e 's/\([@*]\)$//' >> ~/.exedump2
done
sort ~/.exedump2 | column -x > ~/.exedump2
cat ~/.exedump1 ~/.exedump2 > ~/.exedump
rm ~/.exedump2 ~/.exedump1
echo -e "\nFile, .exedump, containing all executables in \$PATH, has been added to your home directory.\n"
```

---

### Post by vishzilla on 2007-12-17
Is there any good guide to learn bash scripting. I am a noob, I know the basics of bash scripting, I would like to learn further.

---

### Post by Interestedinthepenguin on 2007-12-18
I'm a noob, too.:)  

I don't know what you mean by "the basics", but check out:  [http://tldp.org/LDP/Bash-Beginners-Guide/](http://tldp.org/LDP/Bash-Beginners-Guide/) and [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by blithen on 2007-12-31
Just made a new script that remove/installs all the crap I need when I reformat.
Bash scripts make my happy.

Contents of said script:
sudo apt-get remove gnome-btdownload evolution system-config-printer openoffice.org-core && sudo apt-get install cmus yakuake k3b amsn drpython virtualbox-ose finch ubuntu-restricted-extras ia32-libs deluge-torrent abiword-common glipper ffmpeg audacity && sudo dpkg -i ~/.debs/ubuntu-tweak.deb && cd /home/blithen/scripts && sudo ./GetFlash

---

### Post by picpak on 2007-12-31
> **K.Mandla said:**
> Hold on a second. ... This is a one-time message when you open an emulator? I've been wanting to do that for a while; where do you put that? What triggers it?

I assume by "emulator" you mean things like gnome-terminal. If so, put it in .bashrc.

---

### Post by olejorgen on 2008-01-14
Here goes :P

Scripts and functions:

pathdump # Modified exedump. exe is for windows :)
```

#!/bin/bash
#dump executables in $PATH to file
#Created by Interestedinthepenguin 12/13/2007, modified by Ole Jørgen

if [ "$1" = "-s" ]; then
	POST='sort';
elif [ "$1" = "-u" ]; then
	POST='cat';
elif [ "$1" = "-h" -o "$1" = "--help" ]; then
	echo 'Dumps all binaries in $PATH to stdout'
	echo '-s sorted output'
	echo '-u unsorted output (standard)';
	exit
else
	POST='cat'
fi

paths=$(echo $PATH | sed "s/:/ /g")
{
	for i in $paths; do
		ls -F $i | sed -e '/[^@*]$/d' -e 's/\([@*]\)$//';
	done;
} | $POST

```

change-wallpaper # changes your gnome wallpaper
```

#!/bin/bash

modes=" none wallpaper centered scaled stretched zoom "
mode="stretched"

if [ $2 ]; then
	if [ "${modes/[ ]$2[ ]/}" != "$modes" ]; then
				mode=$2; 
	else
		echo "Invalid mode. ($modes)"
		exit;
	fi
fi
echo $1
gconftool -t string -s "/desktop/gnome/background/picture_options" "none"
gconftool -t string -s "/desktop/gnome/background/picture_filename" "$(realpath "$1")"
gconftool -t string -s "/desktop/gnome/background/picture_options" "$mode"

# Determines how the image set by wallpaper_filename is rendered. Possible values are "none", "wallpaper", "centered", "scaled", "stretched", "zoom".

```

proc-toggle # toggles (stop/cont) all processes with name ARG
```

#!/bin/bash

STATUS=$(ps -C "$1" -o state=)
if [ "$STATUS" = T ]; then
	killall -s CONT -e "$1"
else
	killall -s STOP -e "$1"
fi

```

install-list # install all packages in FILE, ignoring lines starting with #
```

#!/bin/bash

echo "Installing" "$1", $(date) >> install.log
echo "" >> install.log
cat "$1" | while read LINE; do
	NAME=$(echo $LINE | sed -e "s/[ \t]*#.*//")
	if [ -n "$NAME" ]; then
		apt-get install "$NAME" >> install.log
		echo $LINE
	fi
done

```

append # (function) you want this after you've overwritten some important file using > instead of >> ^^
```

function append() {
        lastarg="${!#}"
        echo "${@:1:$(($#-1))}" >> "$lastarg"
}

```

trash # (function) move a file to nautilus trash folder (located on the same partition)
```

function trash() {
	MOUNT_POINT=$(df "$1" | tail -n 1 | awk '{ print $6 }')
	if [ "$MOUNT_POINT" == /home ]; then
		TRASH="$MOUNT_POINT/$(whoami)/.Trash";
	else
		TRASH="$MOUNT_POINT/.Trash-$(whoami)";
	fi
	mv -i $* "$TRASH"
}

```

Aliases:
```

alias gop='gnome-open' # stop worry about what the heck the open office binaries are called ^^

```

---

### Post by fedex1993 on 2008-01-14
what are aliases i cant figure out what they are also is there a guid for making scripts like shows what impooots and out poots and what not

---

### Post by brunovecchi on 2008-01-15
My modest contribution to the script pool...
A script that sorts downloaded files into subfolders according to their file type. It also mantains a list of books in the book folder. Simple, but very time-saving! I put it in my .bashrc file.
I also use a batch-resizer for pictures and a random wallpaper switcher, but I didn't write those.

my only alias:

alias rm='rm -v'
(this would be helpful for the "sudo rm -rf  *" problem)

```
#!/bin/bash
# Classify downloaded files.

ORIGIN=$HOME/.aMule/Incoming

# Video folder
VIDEO=$HOME/Videos
VIDEO_EXT="*.mpeg *.avi *.wmv *DVD*"

# Books folder
BOOKS=$HOME/Docs/Books
BOOK_EXT="*.pdf *.chm *.djvu"

# Music folder
MUSIC=$HOME/Music
MUSIC_EXT="*.mp3 *.wav *.ogg *album*"

for EXT in $ORIGIN/$MUSIC_EXT; do
    mv $ORIGIN/$EXT $MUSIC_EXT/Classify 2> /dev/null
done

for EXT in $ORIGIN/$BOOK_EXT; do
    mv $ORIGIN/$EXT $BOOK_EXT/Classify 2> /dev/null
done

for EXT in $ORIGIN/$VIDEO_EXT; do
    mv $ORIGIN/$EXT $VIDEO_EXT/Classify 2> /dev/null
done

ls -R $BOOKS > $BOOKS/list.BOOKS.txt
```

---

### Post by beercz on 2008-01-15
Here is a very, very simple script I wrote to update my debian servers every day.

I call the script 'dupdate' and have put it in my /usr/local/bin directory.

I have root's crontab calling the script at 22:00hrs daily:

> #!/bin/bash

#script to update a debain based server
#April/May/June 2006

#update repositories
apt-get -y update
apt-get -y dist-upgrade

#in case boot menu (lilo) is updated, may need to run lilo before reboot
###lilo

#finish
exit 0
~        I have been using it daily for about 18 months now.

Works in Ubuntu too.

---

### Post by Christmas on 2008-01-15
I use some Bash scripts to edit my audio collection. I put them into ~/bin which on Debian Lenny is included in the path by default (Or at least I think so, I don't remember to export my $PATH var).
vcrm.bash - remove all tags in OGG vorbis files
```
#!/bin/bash

echo "OGG Tag Remover"
echo "Creating empty file..."
touch file

echo "Starting to remove all tags in OGG files..."
for i in *.ogg; do
	echo "Executing command \"vorbiscomment -w $i -c file\"..."
	nice -n 15 vorbiscomment -w $i -c file
done

echo "Removing empty file..."
rm file

echo "Done! All tags removed."

```
vcl.bash - list all tags in OGG vorbis files
```
#!/bin/bash

for i in *.ogg; do
	nice -n 15 vorbiscomment -l $i
done

echo "Done!"

```
vctn.bash - edit the 'TRACKNUMBER' tag in OGG vorbis files
```
#!/bin/bash

echo "OGG TRACKNUMBER Edit"

n=1
for i in *.ogg; do
	echo "Executing command \"vorbiscomment -a $i -t \"TRACKNUMBER=$n\"\""...
	nice -n 15 vorbiscomment -a $i -t "TRACKNUMBER=$n"
	n=$((n + 1))
done

echo "Done. TRACKNUMBER tags completed."

```
After using vctn.bash I proceed to editing the other tags (Artist, Title, Album, Year and Genre) with Amarok.

vcmv.bash - rename OGG vorbis files in a directory to match my way
```
#!/bin/bash

k=1
for i in *.ogg; do
	if [[ $k -lt 10 ]]; then
		echo "Executing \"mv \"$i\" \"track0${k}.ogg\"\"..."
		mv "$i" "track0${k}.ogg"
	fi
	if [[ $k -ge 10 ]]; then
		echo "Executing \"mv \"$i\" \"track${k}.ogg\"\"..."
		mv "$i" "track${k}.ogg"
	fi
	k=$(($k + 1))
done
echo "Done! All files renamed."

```
And the last one, flaudio.bash (which I only use occasionally):
```
#!/bin/bash

echo "Encoding to OGG at 192 kbps..."
nice -n 15 oggenc -b 192 *.flac

echo -n "Enter band name: "
read band_name
echo -n "Enter year: "
read year

echo "Creating directory ${band_name}/${year}..."
mkdir -p ${band_name}/${year}

echo "Moving the OGG files into ${band_name}/${year}..."
mv *.ogg ${band_name}/${year}

echo "Done. The files are in the ${band_name}/${year} directory."

```
They are all simple scripts to automate easy tasks. But they come in handy when dealing with albums or compilations with, say, 100 songs or more.

---

### Post by olejorgen on 2008-02-27
nth-line
```

#!/bin/sh

if [ "$1" = "-h" -o "$1" = "--help" ]; then
        echo usage: $(basename $0) "[<line> <file|->] | [-n <# lines> <line> <file|->]"
        exit;
elif [ "$1" = "-n" ]; then
        LINE_FROM=$3
        LINE_TO=$(($LINE_FROM + $2 - 1));
        FILE="$4"
else
        LINE_FROM=$1
        LINE_TO=$LINE_FROM;
        FILE="$2"
fi

sed -n "$LINE_FROM,${LINE_TO}p;${LINE_TO}q;" "$FILE"

```

I sometimes need to examine lots of files and potentially move them to a common directory. eg. make a playlist for my crappy mp3 player. 
These are simple wrappers around cp and mv, that allows you to set a permanent target directory.
eg. ```

tmv -s /mnt/disk/5k
tmv eye-of-the-tiger.mp3 #  <-> mv eye-of-the-tiger.mp3 /mnt/disk/5k

```
```

function tmv () {
        if [ "$1" = "-s" -o "$1" = "--set-target" ]; then
                MOVE_TARGET="$(realpath $2)";
        elif [ "$1" = "-h" -o "$1" = "--help" ]; then
                echo "usage: tmv [-s|--set-target <dir>] | <mv args> <files>";
        else
                mv --target-directory "$MOVE_TARGET" "$@";
        fi
}

# TODO: fix so -s can be sent to cp
function tcp () {
        if [ "$1" = "-s" -o "$1" = "--set-target" ]; then
                COPY_TARGET="$(realpath $2)";
        elif [ "$1" = "-h" -o "$1" = "--help" ]; then
                echo "usage: tcp [-s|--set-target <dir>] | <mv args> <files>";
        else
                cp --target-directory "$COPY_TARGET" "$@";
        fi
}

```
Swaps two files
```

#!/bin/sh

if [ "$1" = "-h" -o "$1" = "--help" ]; then
	echo Swaps to files
	echo usage: $(basename $0) "<file 1> <file 2>"
	exit;
fi

ARG1="$1"
ARG2="$2"

TMP_ARG1="$ARG1".$(date "+%s%N")

if [ -e "$TMP_ARG1" ]; then
	echo "Ups.. unique file name not unique" > /dev/stderr;
	exit 1
fi

mv -i "$ARG1" "$TMP_ARG1"
mv -i "$ARG2" "$ARG1"
mv -i "$TMP_ARG1" "$ARG2"

```

---

### Post by kaiju on 2008-03-11
i just hacked together this silly little thing for connecting to irc with irssi inside a screen session. it either starts irssi with the given parameters or connects to an already running instance.

```
#!/bin/bash
############
# set channel, username, password and screen session name here:
############
CHAN=irc.freenode.net
USER=<setme>
PASS=<setme>
SESS=$CHAN
############         
ps -e | grep irssi
PRESENCE=$?;
if [ $PRESENCE -eq 1 ]; then
        screen -S $SESS irssi -c $CHAN -n $USER -w $PASS
else
        screen -rd $SESS
fi
```

---

### Post by Dr Small on 2008-03-11
I generally write alot of different scripts to make my life easier or for cronjobs, but most of my scripts are dependant upon other scripts I have made.

Example:

netload
```
#!/bin/bash
ifconfig ath0 | grep bytes
```

I place that in the /usr/bin on several different Ubuntu PCs (with SSH + Keybased Passwordless Login) and then run netloadall on my system to see the netload of every system and total usage.

Example:
netloadall
```
#!/bin/bash
#Shows an organized output from the netload command.
#The netload script must be on each host, and you must
#have access to each of the hosts via SSH with a passwordless login
#for everything to work properly.
#
# A Good Script for Network Admins to watch the bandwidth of
# each client, and shows total usage at the bottom.
#
# Written by Dr Small
# http://php.8ez.com/drsmall/blog/


#DEFINE A SET OF COLORS#
GREEN='\e[0;32m'
RED='\e[0;31m'
BLUE='\e[0;34m'
NC='\e[0m' # No Color


#DEFINE HOSTS#
#Either use hostnames (if defined in your hosts file)
# or IP Addresses to the host
host1="darkghost"
host2="mycroft"
host3="firefoxwiz-desktop"

#CALCULATE DOWNLOAD#
netd1=$( netload | awk '/RX/ {print $2}' | sed 's/bytes://' )
netd2=$( ssh -q $host2 netload | awk '/RX/ {print $2}' | sed 's/bytes://' )
netd3=$( ssh -q $host3 netload | awk '/RX/ {print $2}' | sed 's/bytes://' )

netdm1=$(($netd1 / 1048576))
netdm2=$(($netd2 / 1048576))
netdm3=$(($netd3 / 1048576))

netdt=$(($netdm1 + $netdm2 + $netdm3))



#CALCULATE UPLOAD#
netu1=$( netload | awk '/TX/ {print $6}' | sed 's/bytes://' )
netu2=$( ssh -q $host2 netload | awk '/TX/ {print $6}' | sed 's/bytes://' )
netu3=$( ssh -q $host3 netload | awk '/TX/ {print $6}' | sed 's/bytes://' )

netum1=$(($netu1 / 1048576))
netum2=$(($netu2 / 1048576))
netum3=$(($netu3 / 1048576))

netut=$(($netum1 + $netum2 + $netum3))



echo ''
echo -e $GREEN $host1: $NC `netload`
echo -e $RED $host2: $NC `ssh -q $host2 netload` 
echo -e $BLUE $host3: $NC `ssh -q $host3 netload`
echo ''
echo -e $RED 'Total Download:'$NC $netdt 'MiB'
echo -e $GREEN 'Total Upload:  '$NC $netut 'MiB'
echo ''

exit

```

A RUN Dialog for IceWM:
```
#!/bin/bash
#A Run Dialog Box for IceWM

cmd=$(zenity --title="Run" --entry --text "Enter Command:")
exec $cmd&
exit 0

```

The first simple script that I ever designed... with a little humor:
```
#!/bin/sh
# 
# Having fun with your cd tray!
# Including Dr Watson and Sherlock Holmes!


eject /dev/cdrom
eject -t /dev/cdrom
echo " "
echo "Dr Watson: 'My dear Holmes! What have you done?'"
eject /dev/cdrom
eject -t /dev/cdrom
echo " "
echo "Sherlock Holmes: 'It is nothing more than a simple mathematical problem...'"
echo " "
eject /dev/cdrom
eject -t /dev/cdrom
echo "Dr Watson: 'But, look! It won't stop!'"
eject /dev/cdrom
eject -t /dev/cdrom
echo " "
echo "Sherlock Holmes: 'My dear fellow, watch and learn..'"
echo " "
exit
```

The Westminster Chime (you will need beep to use this, and will need to run it as root due to /dev/console and other permission problems with beep... :|)
```

#!/bin/bash
#Westminster chime
#
#       .=THE NOTES=.
#C E D g C D E C E C D g g D E C


# C
beep -f 261 -l 600 -D 100

# E
beep -f 329 -l 600 -D 100

# D
beep -f 293 -l 600 -D 100

# g
beep -f 195 -l 800 -D 400

# C
beep -f 261 -l 600 -D 100

# D
beep -f 293 -l 600 -D 100

# E
beep -f 329 -l 600 -D 100

# C
beep -f 261 -l 800 -D 400

# E
beep -f 329 -l 600 -D 100

# C
beep -f 261 -l 600 -D 100

# D
beep -f 293 -l 600 -D 100

# g
beep -f 195 -l 800 -D 400

# g
beep -f 195 -l 600 -D 100

# D
beep -f 293 -l 600 -D 100

# E
beep -f 329 -l 600 -D 100

# C
beep -f 261 -l 800 -D 400


dongtime=$(date +%l)

#DONG
beep -f 130 -l 900 -D 400 -r $dongtime
```


My ./info script that I use for monthly screenshots:
```

#!/bin/bash

# A Simple Information Script
# which could be useful for screenshots.
# Simply edit the variables to change the values
# Any variable that is left blank will not show when executed.
#
# Usage: ./info
#
# Written by Dr Small
# http://php.8ez.com/drsmall/blog/

#Set your personal info here
#Anything that you leave unset will not display :)
email="drsmall@hackermail.com"
jabber="drsmall@cafelinux.com"
msn="drsmall@hackermail.com"
yahoo=""
icq="324-464-073"
gpg="26FD8AF9"
skype=""
aim=""
openid=""
launchpad="drsmall" #USERNAME ONLY
irc="DrSmall @ irc.freenode.net"
website="http://php.8ez.com/drsmall/blog/"

#Set your desktop config here
#Anything unset will not display.
desktop="IceWM"
theme="FauxGlass"
wallpaper="127.0.0.1"


#Some Additional Settings
#1 = true
#0 = false
show_user="1"
show_host="1"
prntscrn="0" #TAKE A SCREENSHOT
delay="5" #DELAY FOR SCREENSHOT, IN SECONDS



# There is nothing else to edit below here...


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
NC='\e[0m'


if [[ -z $* ]]; then

echo ''
	if [[ $show_user == "1" ]]; then

	echo -e $LIGHTCYAN 'User: '`whoami`

	fi

	if [[ $show_host == "1" ]]; then

	echo -e $YELLOW 'Host: '`hostname`

	fi

$0 --contact

echo  -e $NC ''
	if [[ -n $desktop ]]; then

	echo -e $LIGHTPURPLE 'Desktop: '$desktop

	fi

	if [[ -n $theme ]]; then

	echo -e $DARKGRAY 'Theme: '$theme

	fi

	if [[ -n $wallpaper ]]; then

	echo -e $GREEN 'Wallpaper: '$wallpaper $NC

	fi


echo ''

	if [[ $prntscrn == "1" ]]; then
	$0 --prntscrn
	fi
fi


if [[ $* == '--contact' || $* == '-c' ]]; then

echo ''

	if [[ -n $email ]]; then

	echo -e $BLUE 'Email:' $email
	
	fi

	if [[ -n $jabber ]]; then

	echo -e $GREEN 'Jabber:' $jabber

	fi

	if [[ -n $msn ]]; then

	echo -e $CYAN 'MSN:' $msn

	fi

	if [[ -n $yahoo ]]; then

	echo -e $RED 'Yahoo:' $yahoo
	
	fi

	if [[ -n $icq ]]; then

	echo -e $PURPLE 'ICQ #:' $icq

	fi

	if [[ -n $gpg ]]; then

	echo -e $LIGHTGRAY 'OpenPGP Key:' $gpg

	fi

	if [[ -n $skype ]]; then

	echo -e $DARKGREY 'Skype:' $skype

	fi

	if [[ -n $aim ]]; then

	echo -e $LIGHTBLUE 'AIM:' $aim

	fi

	if [[ -n $openid ]]; then

	echo -e $LIGHTGREEN 'OpenID:' $openid

	fi

	if [[ -n $launchpad ]]; then

	echo -e $LIGHTRED 'Launchpad: http://launchpad.net/~'$launchpad

	fi

	if [[ -n $irc ]]; then

	echo -e $LIGHTPURPLE 'IRC:' $irc

	fi

	if [[ -n $website ]]; then

	echo -e $BROWN 'Website:' $website

	fi
fi


if [[ $* == '--help' || $* == '-h' ]]; then
echo  -e $CYAN ''
echo -e 'Terminal Information... a useful tool for taking\nscreenshots'
echo ''
echo 'Help Contents:'
echo $0'  Executes the script.'
echo $0' -c'
echo $0' --contact  Only displays the contact information.'
echo $0' -p'
echo $0' --prntscrn  Only used if $prntscrn variable is set.'
echo $0' -h'
echo $0' --help  Displays this message.'
echo ''
echo -e 'For this script to function properly,\nPlease edit the variables in the file\nto show the correct information.\n\nIf you wish for a certain variable\nto not show up, just simply leave it empty.'
echo -e $NC ''

fi

if [[ $* == "--prntscrn" || $* == "-p" ]]; then
scrot -d $delay
fi

exit
```


And some aliases that I use on my server:
```
alias cksize="du -hs"
alias killuser="skill -KILL -u"
alias authlog="tail -f /var/log/auth.log"
alias sshlog="tail -f /var/log/auth.log | grep sshd"
alias ftplog="tail -f /var/log/xferlog"
alias httplog="tail -f /opt/lampp/logs/access_log"

alias stopxampp="sudo /opt/lampp/lampp stop"
alias startxampp="sudo /opt/lampp/lampp start"

alias stopmysql="sudo /opt/lampp/lampp stopmysql"
alias startmysql="sudo /opt/lampp/lampp startmysql"

alias stopftp="sudo /etc/init.d/proftpd stop"
alias startftp="sudo /etc/init.d/proftpd start"

```


Dr Small

---

### Post by phrostbyte on 2008-03-11
> **tdrusk said:**
> I'm making my grandfather a computer since we are getting him a digital camera for christmas. I got it so when he plugs in the camera it automatically syncs the pictures to a folder, deletes the pictures off the camera, opens a window of all of his pictures and unmounts the drive. ahh old people

```
#!/bin/bash
# Sync Files
rsync -av /media/disk/test /home/tyler/Test
#Delete Files From Camera
rm -r /media/disk/test
#Wait For Indexing To Catch Up
sleep 10
#Open Nautilus Search
nautilus /home/tyler/Desktop/Test.savedSearch
#Unmount Drive
eject /media/disk/
```
The Open Nautilus Search is a saved search I did in Nautilus of .JPG in the /home/tyler/Test directory. Pretty nifty.

+1 Such a small script, yet so useful

---

### Post by olejorgen on 2008-03-12
You really should check rsync's exit status and/or verifying that the files were transfered before deleting the images

---

### Post by chick on 2008-03-15
I found the following very useful

List files only, the advantage is that it works just like normal 'ls' so you could do 'lf -al | grep blah' etc.
```
lf () { ls -1p $@ | grep -v '\/$' }
```

Grep process by name and list the results nicely with the header.
```
pg () {
    if pgrep -f $@ > /dev/null;
    then
        pgrep -f $@ | xargs ps -o user,pid,stat,rss,vsz,pcpu,args \
                               --sort -pcpu,-rss;
    else 
        exit 1;
    fi
}
```

The following utilize curl and dict.org for powerful lookups.
```

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

```

For following strategies are avaiable (do 'curl dict://dict.org/show:strat')
```

exact "Match headwords exactly"
prefix "Match prefixes"
substring "Match substring occurring anywhere in a headword"
suffix "Match suffixes"
re "POSIX 1003.2 (modern) regular expressions"
regexp "Old (basic) regular expressions"
soundex "Match using SOUNDEX algorithm"
lev "Match headwords within Levenshtein distance one"
word "Match separate words within headwords

```

And some important dbs (do 'curl dict://dict.org/show:db')
```

gcide "The Collaborative International Dictionary of English v.0.48"
wn "WordNet (r) 2.0"
...
vera "Virtual Entity of Relevant Acronyms (Version 1.9, June 2002)"
jargon "Jargon File (4.3.1, 29 Jun 2001)"
foldoc "The Free On-line Dictionary of Computing (27 SEP 03)"
...
english "English Monolingual Dictionaries"
trans "Translating Dictionaries"
all "All Dictionaries (English-Only and Translating)"
web1913 "Webster's Revised Unabridged Dictionary (1913)"

```

---

### Post by spupy on 2008-03-15
This here is a script that when run with "&" runs like a daemon and checks the battery state every 5 minutes, and alerts you when the charge % is lower that you specified. (I haven't used it for months, so don't know if it still works):
```
#!/bin/bash
# Arg 1 - % when to give warning
# Arg 2 - Custom message

warnLvl=5
if test -n "$1"
	then
		warnLvl=$1
fi

msg="Your battery is almost discharged. Please plug in AC."
if test -n "$2"
	then
		msg=$2
fi

while true
	do
		dis=`acpi | grep -o discharging`
		if test -n $dis	#dis is not empty => the battery is discharging
			then
				batLvl=`acpi | grep -o '[0-9]\{1,3\}%' | grep -o '[0-9]\{1,3\}'`
				if test "$batLvl" -le "$warnLvl"
					then zenity --warning --title="Battery almost discharged" --text="$msg"
				fi						
		fi
		sleep 5m
done
```

Check how full is your /home partition:
```
df /home/user | grep -o -e '[0-9]\{1,2\}%'
```

Display an ASCII cow saying a fortune in a robotic voice:
```
#!/bin/bash
clear
fort=`fortune -a`
cowsay $fort
espeak "$fort"
```

Make a shortcut to this one for changing the titles of windows easily:
```
#!/bin/bash
# Set the title of the window thru a zenity entry dialog
export DISPLAY=:0.0
title=`zenity --entry --title='New name' --text='New window title:'`
wmctrl -r :SELECT: -T "$title"
```

Another script using zenity. With this one you can post stuff to your Tumblr:
```
#!/bin/bash

#This Script requires zenity and curl:
#sudo apt-get install zenity curl

#Here type your email and pass, no spaces after the '='
email=your_email_here
password=your_pass_here

#Don't touch anything below this line

function confirm(){
	zenity --question --title="Post?" --text="Are you sure you want to post?"
}
function sent(){
	zenity --info --title='Posted' --text='The post was completed'
}

action=`zenity --list --title='Post to Tumblr' --text='Choose post type' --column=Action Text Photo Quote Link Conversation Video Audio`

############### TEXT POST
if [ $action = "Text" ]
	then
		title=`zenity --entry --title='New Text Post' --text='Title'`
		body=`zenity --text-info --editable --title='New Text Post' --text='Text body'`
		confirm && curl -d "email=$email&password=$password&type=regular&title=$title&body=$body" http://www.tumblr.com/api/write && sent
fi
############### QUOTE POST
if [ $action = "Quote" ]
	then
		quote=`zenity --text-info --editable --title='New Quote' --text='Quote'`
		souce=`zenity --entry --title='New Quote Post' --text='Source'`
		confirm && curl -d "email=$email&password=$password&type=quote&source=$souce&quote=$quote" http://www.tumblr.com/api/write && sent
fi
############### LINK POST
if [ $action = "Link" ]
	then
		name=`zenity --entry --title='New Link' --text='Name'`
		url=`zenity --entry --title='URL' --text='URL'`
		description=`zenity --text-info --editable --title='New Link Post' --text='Description'`
		confirm && curl -d "email=$email&password=$password&type=link&name=$name&url=$url&description=$description" http://www.tumblr.com/api/write && sent
fi
############### CONVERSATION POST
if [ $action = "Conversation" ]
	then
		title=`zenity --entry --title='New Conversation Post' --text='title'`
		conversation=`zenity --text-info --editable --title='New Conversation' --text='Conversation'`
		confirm && curl -d "email=$email&password=$password&type=conversation&title=$title&conversation=$conversation" http://www.tumblr.com/api/write && sent
fi
############### TODO PICTURE, AUDIO and VIDEO UPLOAD
if [ $action = "Photo" ]
	then
		zenity --error --title='Missing feature' --text='Sorry! Photo posting is not implemented yet. Stay tuned at http://somlev.com'
fi
if [ $action = "Video" ]
	then
		zenity --error --title='Missing feature' --text='Sorry! Video posting is not implemented yet. Stay tuned at http://somlev.com'
fi
if [ $action = "Audio" ]
	then
		zenity --error --title='Missing feature' --text='Sorry! Audio posting is not implemented yet. Stay tuned at http://somlev.com'
fi
echo

```

I was so obsessed with zenity scripts, i wrote a bash+zenity text editor! Unfortunately, it doesn't save newline chars, so i'm not posting it.

---

### Post by blithen on 2008-06-11
All my useful aliases 
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias purge='sudo apt-get remove --purge'
alias update='sudo apt-get update && sudo apt-get upgrade'
alias upgrade='sudo apt-get upgrade'
alias clean='sudo apt-get autoclean && sudo apt-get autoremove'
alias d='cd ~/Desktop'
alias open='gnome-open'
alias connect='python /home/blithen/python/login.py'
alias installremove='cd /home/blithen/scripts && ./remove-install.sh'
alias nb='nano ~/.bashrc'
alias updatedb='sudo updatedb -v'
alias search='apt-cache search'
alias info='python ~/python/info.py'

---

### Post by DasCrushinator on 2008-06-11
Does anyone know how to make the 'install' aliases auto complete?  Say I want to install mplayer, and I type 'install mpl' and hit tab twice to auto complete it or see my options.  It won't do it the way it is now :(

---

### Post by KingTermite on 2008-06-11
> **ice60 said:**
> i got loads of stuff, most i got from the internet and maybe changed a bit.Nice collection, ice60. :)

---

### Post by KingTermite on 2008-06-12
Here are two of my new faves. These are both modified from scripts found in "Linux Desktop Hacks" by Nicholas Petreley & Jono Bacon (O'Reilly). I'll put them in separate posts to be more readable.


First my .bashrc script. It simplifies my prompt (and colors it) by removing the current directory (quite annoying if you are are 4 levels deep because your prompt takes up half the line). It puts the current directory up in the top right corner of the terminal window.

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


########## Custom Prompt (courtesy of "Linux Desktop Hacks") ##########
function prompt_command
{
	# Save current cursor position
	tput sc
	
	# backwash is where to set cursor (upper right side)
	# to write CWD [col=screen width - (CWD +2) for brackets]
	let backwash=$(tput cols)-$(echo $(pwd) | wc -m)-2
	
	#position cursor at Y=0, X=calculated columr (see above)
	tput cup 0 ${backwash}
	
	#set foreground color and bold
	tput setaf 4; tput bold
	
	#Wrap path in brackets
	echo -n "["
	
	# show path
	echo -n "$(pwd)"
	
	#show closing bracket
	echo -n "]"
	
	#return cursor to saved position
	tput rc
}
	
# Set prompt via function above	
PROMPT_COMMAND=prompt_command

PURPLE="\[$(tput setaf 5 ; tput bold)\]"
BLACK="\[$(tput setaf 0 ; tput bold)\]"
NO_COLUR="\[$tput sgr0)\]"

case "$TERM" in
	xterm*|rxvt*)
		TITLEBAR='\[\033]0;\u@\h \007\]'
		;;
	*)
		TITLEBAR=""
		;;
esac



PS1="$PURPLE\u \
$BLACK\$$NO_COLOUR "
PS2='>'
PS4='+'



########## Custom Prompt (courtesy of "Linux Desktop Hacks") ##########




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
    . /etc/bash_completion
fi

#################################################################
##### KT's login script mods
#################################################################

PATH=.:$PATH
source .bash_aliases

```


Here's a screenshot:

Note the current working directory in the upper right corner of screen. My prompt is now only my "kt $".

[[IMG]http://img168.imageshack.us/img168/357/sstermlj5.png[/IMG]](http://imageshack.us)

---

### Post by KingTermite on 2008-06-12
This one is totally sweet. It was also taken and only slightly modified from "Linux Desktop Hacks". It's a reminder script....but instead of popping up a window it uses on screen display. It comes up over top of windows or anything like that and figured out display so it doesn't matter what desktop you are in either.

Once set up, you can type something like 
***remindme 2:00pm "Walk the dog"***

and it just pops up in a nice colored font. Kind of like the volume bar on your TV looks. Note, it does require you to install the package "xosd" so the "osd_cat" command is available.

The script, remindme.sh

```
#!/bin/bash

#Figure out which display we're using

#
# Ubuntu version of osd_cat does not like "host name" in front of display
#

#HOST="$(xrdb -symbols | grep SERVERHOST | cut -d= -f2)"
DISPLAYNUM="$(xrdb -symbols | grep DISPLAY_NUM | cut -d= -f2)"
#THISDISPLAY=$HOST:$DISPLAYNUM.0
THISDISPLAY=:$DISPLAYNUM.0


#check to see if the reminders directory exists (create if not)
if [ ! -e ~/reminders ] ; then
  mkdir ~/reminders
fi

unique=`date +%F-%H-%M-%S`
reminder="reminders/reminder-"$unique

#Now output the reminder script
echo '#!/bin/bash' > ~/$reminder
echo -n 'export DISPLAY=' >> ~/$reminder
echo $THISDISPLAY >> ~/$reminder
echo "echo \"$2\" | osd_cat -s 2 -c green -p middle -A center \
-f -adobe-helvetica-bold-r-normal-*-*-240-*-*-p-*-*-* -d 30" >> ~/$reminder

#Make the reminder script executable
chmod +x ~/$reminder

#Schedule it to run
at $1 -f ~/$reminder

```

Here is a screenshot. The font uses could be bigger. I use the same font the author gave because he said it was a very common font that is probably in all Linux distos. I may change it at some point..you can use any font available on your system.

[[IMG]http://img176.imageshack.us/img176/7501/osdssej3.png[/IMG]](http://imageshack.us)

---

### Post by Trail on 2008-06-12
```

alias ll='ls -l -h'
alias la='ls -A'
alias l='ls -CF'
alias agu='sudo aptitude update'
alias agg='sudo aptitude safe-upgrade'
alias agi='sudo aptitude install'
alias ags='aptitude search'
alias agr='sudo aptitude remove'
alias k='kwrite'
alias vg='valgrind --leak-check=full --show-reachable=yes'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'
alias back='cd $OLDPWD'

# and some ssh login aliases

# following two scripts written by myself
# it's like ps ax | grep <x>, but improved a bit
# the second one prints some thread information as well

sps() {
    if [ $# -ne 1 ]; then
        echo Usage: sps PATTERN
        echo Lists running processes whose name matches PATTERN.
        return 1
    fi

    ps -eo pid,user,pcpu,nlwp=THREADS,nice=NICE,rss=MEM\(KB\),start,tty=TTY,args | grep -v grep > /tmp/spsfunction.tmp

    declare spstmp=`grep -c $1 /tmp/spsfunction.tmp`
    if [ $spstmp == 0 ]; then
        echo No processes found matching pattern \'$1\'.
        return 1
    fi

    head -n 1 /tmp/spsfunction.tmp
    grep --color=auto $1 /tmp/spsfunction.tmp
    echo $spstmp process\(ess\) found matching pattern \'$1\'.

}

stps() {
    if [ $# -ne 1 ]; then
        echo Usage: stps PATTERN
        echo Lists running processes whose name matches PATTERN, including thread information.
        return 1
    fi

    ps -eLo pid,tid,state=STATE,user,pcpu,nlwp=THREADS,nice=NICE,rss=MEM\(KB\),start,tty=TTY,args | grep -v grep > /tmp/spsfunction.tmp

    declare spstmp=`grep -c $1 /tmp/spsfunction.tmp`
    if [ $spstmp == 0 ]; then
        echo No processes found matching pattern \'$1\'.
        return 1
    fi

    head -n 1 /tmp/spsfunction.tmp
    grep --color=auto $1 /tmp/spsfunction.tmp
    echo $spstmp process\(ess\) found matching pattern \'$1\'.

}

# taken from these forums iirc

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

### Post by uncannybuzzard on 2008-06-12
ok, i hate it when i download a torrent of a season of a show i like and the files are all named something like "simpsons.season1.episode2.WaNKErsx.avi" and don't have the proper episode names. so i wrote a script to rename them with the episode number and proper title, i.e., "02 - USA Fun Society.avi"
there are a couple caveats though as this it pretty much a 0.1 version. you must rename the files to the episode number.extension (01.avi, 02.avi, etc.) and the titles must be in a file without an extension in a straight list, one title per line. you can grab season titles pretty easily at epguides.com, just copy them into a text editor and then vi or nano them into an extensionless file (you can copy the whole block for a season and do ```
cut -c40- *raw file* > *dump file*
``` like i said, this is still pretty alpha, i just whipped it up, so any suggestions are welcome.

Code:

```
#!/bin/bash

#VARIABLES#
read -p "Please enter the location of the file containing the episode names: " loc
eps=`ls *.* | sed 's/\(.*\)\..*$/\1/'`
num=`ls *.* | wc -l`
titlenum=`cat $loc | wc -l`
###########

if [ $num != $titlenum ]; then

	echo "The number of episodes and the number of titles do not match. Exiting."
	exit 0

fi

for X in $eps

do

        title=`head -n $X $loc | tail -n 1`
	ext=`ls $X* | sed 's/.*\(\..*$\)/\1/'`
        file=`ls $X*`
        echo "$X - $title$ext"
        mv $file "$X - $title$ext"
	ext=NULL

done

exit 0
```

the number of extensioned files in the directory must match the number of titles in the title file. you can rename most garbled torrent names to 01.avi, 02.avi format fairly easily with thunar bulk rename or any similar program.

---

### Post by 0lsxl0lphnqhubm on 2008-07-02
First, my bashrc file

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

set -o vi

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
#export HISTCONTROL=ignoredups
export EDITOR=vim
export BROWSER=firefox
unset COLUMNS
export SCRIPTS=$HOME/.scripts

# export settings for privoxy / tor use
## http_proxy=http://127.0.0.1:8118/
## HTTP_PROXY=$http_proxy
## export http_proxy HTTP_PROXY

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# check operating system
# and select process path

if [[ `uname -s` == "SunOS" ]]
then
    PS_CMD=/usr/ucb/ps
else
    PS_CMD=ps
fi

# enable color support of ls and also add handy aliases
# if [ "$TERM" != "dumb" ]; then
#     eval "`dircolors -b`"
#     alias ls='ls --color=auto'
#     #alias dir='ls --color=auto --format=vertical'
#     #alias vdir='ls --color=auto --format=long'
# fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

echo "setting aliases"

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    export LS_OPTIONS='--color=auto'
    [ -e "$HOME/.dircolors" ] && DIR_COLORS="$HOME/.dircolors"
    [ -e "$DIR_COLORS" ] || DIR_COLORS=""
    eval "`dircolors -b $DIR_COLORS`"
fi

alias ls='ls $LS_OPTIONS'
alias ll='ls $LS_OPTIONS -l'
alias l='ls $LS_OPTIONS -lF'
alias l.='ls -dF .[a-zA-Z0-9]* --color=tty' #only show dotfiles`
alias la='ls $LS_OPTIONS -alF'
alias lr='ls $LS_OPTIONS -lrtF'
alias lw='echo $1 | wc -w'
alias tf='tail -f $1'
alias t100='tail -100f $1'
alias vi='vim'
alias cls='clear'
alias gzip='gzip -9'
alias gz='gzip $1'
alias ='find . -name $1'
alias psf='$PS_CMD auxww|grep -v "grep"|grep -i $1'
#alias pid='$PS_CMD auxww|grep -v "grep"|grep -i $1|awk \'{ print \$2 }\' '
alias tf='tail -f $1'
alias hist='grep -i $1 $HOME/.bash_history'
alias rebash='. $HOME/.bashrc'
alias vibash='vi $HOME/.bashrc'
alias cd..='cd ..'

# A few ubuntu related aliases
alias mountiso='mount -t iso9660 $1 /media/iso -o loop'
alias hostedit='sudo vi /etc/hosts'
alias restartx='sudo /etc/init.d/gdm restart'
alias comprep='compiz --replace --only-current-screen &'
alias emrep='emerald --replace --only-current-screen &'

# Some more alias to avoid making mistakes:
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'

#Use human-readable filesizes
alias du="du -h"
alias df="df -h"

# Disk space used
alias diskspace='xdiskusage'

# Aptitude shortcuts for Ubuntu
alias aptsearch='sudo apt-cache search $1'
alias aptupdate='sudo apt-get update'
alias aptupgrade='sudo apt-get upgrade'
alias aptinstall='sudo apt-get install $1'
alias aptforce='sudo apt-get -f install'
alias aptremove='sudo apt-get remove $1'
alias aptauto='sudo apt-get autoremove'
alias aptclean='sudo apt-get clean'
alias aptpurge='sudo apt-get purge $1'

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

#Functions

function extract () {
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

function ziprm () {
	if [ -f $1 ] ; then
		unzip $1
		shred $1
	else
		echo "Need a valid zipfile"
	fi
}

function tonk2 {

local BLACK="\[\033[22;30m\]"
local BLUE="\[\033[22;34m\]"
local BROWN="\[\033[22;33m\]"
local CYAN="\[\033[22;36m\]"
local DARK_GRAY="\[\033[01;30m\]"
local GRAY="\[\033[22;37m\]"
local GREEN="\[\033[22;32m\]"
# local LIGHT_BLUE="\[\033[01;34m\]"
local DARK_BLUE="\[\033[01;34m\]"
# local LIGHT_CYAN="\[\033[01;36m\]"
local DARK_CYAN="\[\033[01;36m\]"
local LIGHT_GREEN="\[\033[01;32m\]"
local LIGHT_MAGENTA="\[\033[01;35m\]"
local LIGHT_RED="\[\033[01;31m\]"
local MAGENTA="\[\033[22;35m\]"
local NO_COLOUR="\[\033[0m\]"
local RED="\[\033[22;31m\]"
local WHITE="\[\033[01;37m\]"
local YELLOW="\[\033[01;33m\]"

# If this is an xterm set the title to user@host:dir
# case "$TERM" in
# xterm*|rxvt*)
#     PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#     TITLEBAR='\[\033]0;\u@\h:\w\007\]'
#     ;;
# *)
#     ;;
# esac

# set a fancy prompt (non-color, unless we know we "want" color)
 case "$TERM" in
 xterm-color*|rxvt*)
#     PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
     TITLEBAR="\[\033]0;\u@\h:\w\007\]"
     ;;
 *)
#     PS1="${debian_chroot:+($debian_chroot)}\u@\h:\w\$ "
     TITLEBAR=""
     ;;
 esac
# Comment in the above and uncomment this below for a color prompt
# PS1="${debian_chroot:+($debian_chroot)}\$LIGHT_GREEN\u@\h\$NO_COLOUR:$LIGHT_BLUE\w\$NO_COLOUR\n \$ "

     PS1="$DARK_GRAY :: ${debian_chroot:+($debian_chroot)}$BLUE\u@\h$DARK_GRAY :: $RED\$PWD$DARK_GRAY :: $LIGHT_BLUE$NO_COLOUR\n \$ "
     PS2="$LIGHT_BLUE-$YELLOW-$YELLOW"

}

tonk2

function ff() { find . -name ''$*'' -exec ls -al {} \; 2/dev/null ; }

echo "done"

```

Second - I want to have an alias for the following:

```
$ kill -9 `ps -eaf  | grep -i $1 | awk '{print $2}'`
```

How to I escape the "'" character and the $2 bit? Backslashed do not appear to work

---

### Post by kevdog on 2008-07-02
Script to get the current time from the internet naval installation (may need to modify if you don't want central daylight savings time: CDT):

$ wget -q -O - [http://tycho.usno.navy.mil/cgi-bin/timer.pl](http://tycho.usno.navy.mil/cgi-bin/timer.pl) - | grep -m 1 'CDT'
| sed -e :a -e 's/<[^>]*>//g;/</N;//ba' | awk '{print $3}'

The long sed statement -- although intimidating -- just filters out any html tags.

---

### Post by RATM_Owns on 2008-07-02
I'm not really good at this, so, could someone make an alias for this (me specifying the input video name and the output mp3 name) or a bash script to alias?
```
ffmpeg -i inputfile.flv -f mp3 -vn -acodec copy audio.mp3
```And
```
alias nds='wine $HOME/.wine/drive_c/nocashgba/NOGBA'
alias flv2mp4='/home/andy/Videos/flv2mp4'
alias wadpatch='$DEVKITPRO/wadpatch'
alias saga='/home/andy/.updatescriptandy'
alias crark='/home/andy/.crark-3.1/crark'
alias fahstart='/home/andy/foldingathome/folding start'
alias fahstop='/home/andy/foldingathome/folding stop'
alias ytdl='youtube-dl -t'
alias sagp='sudo apt-get remove --purge'
alias gbrc='gedit /home/andy/.bashrc && source .bashrc'
alias my-ip='wget http://checkip.dyndns.org/ -O - -o /dev/null | cut -f7 -d"<" | cut -f2 -d">" '
```

---

### Post by kevdog on 2008-07-02
Rather than an alias you could make it a function like this (put this in your .bashrc file:

function convert() { ffmpeg -i $1 -f mp3 -vn -acodec copy $2; }

This is assuming that $1 is the input file and $2 is the output file.  You could also call this something other than convert if you wanted.

---

### Post by kaiju on 2008-07-09
```
#!/bin/bash
## keyswitch (dmenu)
input=`echo -e "de\nen\nhu\nro" | $DMENU_VAR`
case $input in
  de)   numlockx off; setxkbmap de; numlockx on;;
  en)   numlockx off; setxkbmap us; numlockx on;;
  hu)   numlockx off; setxkbmap hu 101_qwerty_dot_nodead; numlockx on;;
  ro)   numlockx off; setxkbmap ro winkeys; numlockx on;;
  *)    exit 0
esac
```

xkbmap layout switcher with dmenu.

$DMENU_VAR is only used to not have to specify colors in every single script. (exported from .bashrc with "export DMENU_VAR='dmenu -nb #000000 -nf #7F7F7F -sb #000000 -sf #DAA520'" - to match the default colors of evilwm :evil:)
the numlockx commands are needed in my case because the numlock light usually switches off a few seconds after using setxkbmap.

these are the layouts im using, but you get the idea :)

---

### Post by Bruce M. on 2008-07-10
> **DasCrushinator said:**
> Does anyone know how to make the 'install' aliases auto complete?  Say I want to install mplayer, and I type 'install mpl' and hit tab twice to auto complete it or see my options.  It won't do it the way it is now :(

What do you mean by "auto complete"?

What does hitting tab twice do?

Thanks,
Bruce

---

### Post by chris4585 on 2008-07-12
**_You need youtube-dl and ffmpeg for this to work right_**

This bash script will download youtube videos then convert them to a mp3

Step 1

Paste this into gedit or nano or whatever your favorite editor is, save it as. yt2mp3

```
#!/bin/bash
echo Enter the youtube url to begin downloading the video.
read VIDEO
echo What is the artist of the song?
read ARTIST
echo What is the name of the song?
read NAME
youtube-dl $VIDEO -o "${ARTIST} - ${NAME}.flv"
ffmpeg -i "${ARTIST} - ${NAME}.flv" "${ARTIST} - ${NAME}.mp3"
rm -rf "${ARTIST} - ${NAME}.flv"
echo Your video is finally converted into a mp3!
```

Step 2

then run
```

chmod +x yt2mp3

sudo mv yt2mp3 /bin/
```

Now you can run yt2mp3 and download your video and convert it in no time :)

feed back, please, since this is my first bash script pretty much.

---

### Post by corney91 on 2008-07-13
> **Bruce M. said:**
> What do you mean by "auto complete"?

What does hitting tab twice do?

Thanks,
Bruce

Hitting tab while midway through a command will, if there is only one possibility of the next letters, type out the rest of the command. If there is more than one possibility then hitting it another time will show all of them and you can carry on typing. As you can imagine it's very handy ;)

chris4585, that looks good - once I fix my laptop I think I'll end up using it quite alot! :D

---

### Post by chris4585 on 2008-07-13
> **corney91 said:**
> 
chris4585, that looks good - once I fix my laptop I think I'll end up using it quite alot! :D

Thanks

---

### Post by JT9161 on 2008-07-13
My 2 scripts: One starts up Hamchi and the other out  puts a never ending stream of random numbers (I got the idea from [http://www.bleepingcomputer.com/forums/topic62965-30.html](http://www.bleepingcomputer.com/forums/topic62965-30.html) )

---

### Post by spupy on 2008-07-14
This will check if there are unread emails in a gmail account. If there are new emails, a notification will appear in the lower right corner, displaying the count. The notification automatically disappears after 3 seconds.
(I haven't tested it in Ubuntu, though.)

```
#!/bin/bash

icon="gtk-justify-left"
exp="3000"

gmail_login="username"  
gmail_password="password" 

hasMail="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://${gmail_login}:${gmail_password}@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"

if [ $hasMail -ne "0" ]; then
	notify-send --icon=$icon --urgency=low --expire-time=$exp "$hasMail new email(s) for $gmail_login"
else 
	notify-send --icon=gtk-info --urgency=low --expire-time=$exp "You have no new mail"
fi
```

---

### Post by KIAaze on 2008-07-30
This is a set of shellscripts I use to keep my system from becoming unresponsive when the RAM fills up.
I just add memwatch.sh in System->Preferences->Sessions.
It saved me quite a lot of times. :)

"Kills" are logged in ~/memwatch.log.

_memwatch.sh:_
```

#! /bin/bash
# daemon to kill the most memory intensive user process

# Check if all parameters are present
# If no, exit
echo
echo "usage :"
echo "$0"
echo "This shellscript will kill the most memory intensive user process if the free RAM goes beneath the value given in ~/bin/minmem.txt"
echo

#example output of free
#              total       used       free     shared    buffers     cached
# Mem:        450300     420636      29664          0      25172     234092
# -/+ buffers/cache:     161372     288928
# Swap:            0          0          0

while true
do
	sleep 1

# 	Mem:=free | grep 'Mem:' |  awk '{print $1 }'
# 	total=free | grep 'Mem:' |  awk '{print $2 }'
# 	used=free | grep 'Mem:' |  awk '{print $3 }'
	freemem_1=$(free | grep 'Mem:' |  awk '{print $4 }')
# 	shared=free | grep 'Mem:' |  awk '{print $5 }'
# 	buffers=free | grep 'Mem:' |  awk '{print $6 }'
# 	cached=free | grep 'Mem:' |  awk '{print $7 }'
	
# 	-/+=free | grep 'buffers/cache:' |  awk '{print $1 }'
# 	buffers/cache:=free | grep 'buffers/cache:' |  awk '{print $2 }'
# 	used=free | grep 'buffers/cache:' |  awk '{print $3 }'
	freemem_2=$(free | grep 'buffers/cache:' |  awk '{print $4 }')

#	freemem=$(cat /proc/meminfo | head -2 | tail -1 | awk '{print $2 }')
	freemem=$freemem_2;
# 	echo "$freemem_1" >>mem_1.log
# 	echo "$freemem_2" >>mem_2.log

	min_mem=$(cat ~/bin/minmem.txt)

	if test $freemem -lt $min_mem
	then
		echo "=========================" >>memwatch.log
		echo "freemem=$freemem < $min_mem" >>memwatch.log
		~/bin/killmaxmemprocess.sh 1
	fi
done

```

_killmaxmemprocess.sh:_
```

#! /bin/bash
# kill the most memory intensive user process

# Check if all parameters are present
# If no, exit
if [ $# -ne 1 ]
then
        echo
        echo "usage :"
        echo "$0 license_to_kill"
	echo "This shellscript will kill the most memory intensive user process if license_to_kill!=0."
	echo "Otherwise, it just locates it without killing it."
	echo "All missions will be logged in memwatch.log."
        echo
        exit 0
fi

USAGE=`ps -eo %mem,pid,user -o comm= | grep $USER | sort -k1 -n -r | head -1 | awk '{ print $1 } '`
PID=`ps -eo %mem,pid,user -o comm= | grep $USER | sort -k1 -n -r | head -1 | awk '{print $2 }'`
PNAME=`ps -eo %mem,pid,user -o comm= | grep $USER | sort -k1 -n -r | head -1 | awk '{print $4 }'`

echo $(date)
echo "Hostile process detected:"
echo "memory used: $USAGE%"
echo "PID: $PID"
echo "Name: $PNAME"

echo "=========================" >>memwatch.log
echo $(date) >>memwatch.log
echo "Hostile process detected:" >>memwatch.log
echo "memory used: $USAGE%" >>memwatch.log
echo "PID: $PID" >>memwatch.log
echo "Name: $PNAME" >>memwatch.log

if [ $1 -ne 0 ]
then
	echo "killing process..." >>memwatch.log

	kill_1=0
	kill_2=0

	#clean kill
	killall $PNAME
	if [ $? -eq 0 ]
	then
		kill_1=1
	fi

	#messy kill
	kill -9 $PID
	if [ $? -eq 0 ]
	then
		kill_2=1
	fi

	if [ $kill_1 -eq 1 ] || [ $kill_2 -eq 1 ]
	then
		echo "Target successfully eliminated." >>memwatch.log
		echo "kill_1=$kill_1" >>memwatch.log
		echo "kill_2=$kill_2" >>memwatch.log
		zenity --info --text "$PNAME was killed because of excessive RAM usage.\n kill_1=$kill_1 \n kill_2=$kill_2" ||
		kdialog --msgbox "$PNAME was killed because of excessive RAM usage.\n kill_1=$kill_1 \n kill_2=$kill_2" ||
		xmessage -buttons okay -default okay "$PNAME was killed because of excessive RAM usage.\n kill_1=$kill_1 \n kill_2=$kill_2" &
	else
		echo "Mission failed." >>memwatch.log
	fi
	
# 	#messy kill
# 	kill -9 $PID
# 	if [ $? -eq 0 ]
# 	then
# 		echo "Target successfully eliminated." >>memwatch.log
# 		zenity --info --text "$PNAME was killed because of excessive RAM usage." ||
# 		kdialog --msgbox "$PNAME was killed because of excessive RAM usage." ||
# 		xmessage -buttons okay -default okay "$PNAME was killed because of excessive RAM usage."
# 	else
# 		echo "kill -9 failed." >>memwatch.log
# 	fi

fi

```

My current settings:
_minmem.txt:_
```
90000

```

---

### Post by qazwsx on 2008-07-30
I made this for my NES gaming
```
#!/bin/bash

if [ -e /dev/input/js0 ]
then
        cp $HOME/.fceultra/joystick.cfg $HOME/.fceultra/fceu98.cfg
else
        cp $HOME/.fceultra/keyboard.cfg $HOME/.fceultra/fceu98.cfg
fi

#updates list of available games (nes -u)
if [ "$1" = "-u" ]
then
        cd $HOME/.nes
        rm $HOME/.nes/games
        rm $HOME/.nes/script
        echo "#!/bin/bash">$HOME/.nes/script
        echo "cd $HOME/.nes ">>$HOME/.nes/script
        echo case '$'1>>$HOME/.nes/script
        echo " in">>$HOME/.nes/script
        nmbr=1
        for i in *.nes
        do
                file=$(ls $i)
                echo ""$nmbr") game=$file ;;">>$HOME/.nes/script
                list=$(echo ${file%.nes}|sed 's/_/ /g')
                echo "$nmbr) $list">> $HOME/.nes/games
                nmbr=$(($nmbr +1))
        done
        echo "*) echo No such game && exit;;">>$HOME/.nes/script
        echo "esac">>$HOME/.nes/script
        echo aoss fceu '$'game>>$HOME/.nes/script
fi

cat $HOME/.nes/games
read -p "Game: " game
sh $HOME/.nes/script $game
```

---

### Post by Sarmacid on 2008-07-30
Here are my scripts, nothing too complex since I'm not that good at it :P

This one is to update the system and make my own log

```
#!/bin/bash

PATH="$PATH:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin"

echo "* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *" >> /root/logs/updatelog 
date >> /root/logs/updatelog 
echo "* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *" >> /root/logs/updatelog
echo "" >> /root/logs/updatelog
apt-get update #>> /root/logs/updatelog
apt-get -y upgrade >> /root/logs/updatelog 2>&1
echo "" >> /root/logs/updatelog

```

Since I'm running some tests with snort(logging to MySQL), I reset the DB every once in a while, so I made a script for it. I don't know how to make it ask for the password just once so it asks 3 times, I also know how to embed the pass in the script but not sure about doing that.

```
#!/bin/bash

#Drop the current snort database
/usr/bin/mysql -u root -p -e "drop database snort;"

#Create a new snort database
/usr/bin/mysql -u root -p -e "create database snort;"

#Run the script to create all the tables in the snort database(Note: this file is
#compressed, to uncompress run gunzip /usr/share/doc/snort-mysql/create_mysql.gz)
/usr/bin/mysql -u root -p < /usr/share/doc/snort-mysql/create_mysql snort

```

Remove the firewall.

```
#!/bin/sh

#
# Set the default policy
#
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT


#
# Delete all rules
#
iptables -F

# End message
echo " [End of flush]"

```

Update Snort rules with Oinkmaster also, logging on my own

```
#!/bin/bash

echo "* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *" >> /root/logs/snortrules
date >> /root/logs/snortrules
echo "* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *" >> /root/logs/snortrules
echo "" >> /root/logs/snortrules
/usr/sbin/oinkmaster -o /etc/snort/rules/ >> /root/logs/snortrules 2>&1
echo "" >> /root/logs/snortrules

```

Hope this helps someone.

---

### Post by KIAaze on 2008-07-30
What does the number sign (#) do in:
```
apt-get update #>> /root/logs/updatelog
```
?
edit: ... just a comment ... ^^'

---

### Post by Sarmacid on 2008-07-31
> **KIAaze said:**
> What does the number sign (#) do in:
```
apt-get update #>> /root/logs/updatelog
```
?
edit: ... just a comment ... ^^'

Yeah it's just a comment, figured I didn't need so much stuff in my logs :P

[COLOR="Red"]***Update***[/COLOR]

Got a new script since I couldn't find a command to tell me where the apache root directory was. Not sure if it'd work all the time for everyone, but works for me

```
#!/bin/bash

cat /etc/apache2/sites-available/default | while read line
do
        set -- $line
        if [ "$1" == "DocumentRoot" ] ; then
                echo $2
                exit
        fi
done

```

---

### Post by markp1989 on 2009-01-26
all these are nothing special, but they work fine for what i need:

toggles the mute status of mpd, have this tied to the mute key on my keyboard.
```
#!/bin/sh

if mpc | tail -n 1 | grep "volume:  0%" > /dev/null
then
 mpc volume +70  >/dev/null 2>&1
else
 mpc volume -100   >/dev/null 2>&1
 fi
```
checks if mpd is running, if it is not running then it runs it , and plays. if it is running it plays or pauses the music, i have this tied to the play/pause key on my pc.
```
#!/bin/sh
if pidof mpd | grep [0-9] > /dev/null
then
 mpc toggle  >/dev/null 2>&1
else
 mpd  >/dev/null 2>&1
 mpc play  >/dev/null 2>&1
 fi
```
this one displays the current stats of any torrent flux downloads, i use this through conky.
```
#!/bin/dash
dir=/media/downloads ## replace with torrentflux download dir
cutno=26 #Specifies the number of characters to show in the title name, usefull to stop
host=http://192.168.1.99/torrentflux
user=mark
pass=******


curl -c .tf_cookie -d username=$user -d iamhim=$pass $host/login.php >/dev/null 2>&1
curl -H "Expect:" -b .tf_cookie $host/index.php  >/dev/null 2>&1 > .torrentstats.tmp

echo RX Speed `cat .torrentstats.tmp | grep -i '<strong' | tail -n 4| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';` Kb/s
echo TX Speed `cat .torrentstats.tmp | grep -i '<strong' | tail -n 3| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';` Kb/s
echo Free Space `cat .torrentstats.tmp | grep -i '<strong' | tail -n 2| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';`

cd $dir/.torrents
echo Transfers: `ls *.stat  | wc -l` ##counts the amount transfers 
echo " "
for file in *.stat; do
size=`cat $file | tail -n 1;`
echo $file | cut -f1 -d'.' | cut -c 1-$cutno | tr '_' ' ' | tr -d '[{}(),\!]' | tr -d "\'" | tr '[a-z]' '[A-Z]'; ## displays torrent names, in upper case, without any puncuation 
echo `cat $file | head -n 3 | tail -n 1 | tr '[a-z]' '[A-Z]';`  : `cat $file | head -n 2 | tail -n 1;`% ## displays the status of the torrent
echo RX speed: `cat $file |  head -n 4 | tail -n 1;`  ##displays the current download speed per torrent 
echo TX speed: `cat $file |  head -n 5 | tail -n 1;` ##displays the current upload speed per torrent 
echo size: `expr $size / 1048576` MB ##displays the file size 
echo Seeds: `cat $file |  head -n 7 | tail -n 1 | cut -f1 -d'+';` ##displays the amount of seeds 
echo Peers: `cat $file |  head -n 8 | tail -n 1 ;` ##displays the amount of peers
echo " "
done
.torrentstats.tmp
```
this downloads the latest observation feed from bbc weather, then it prints out a bit of info. if you want to use this your self, you will have to change the link to the rss feed for your town, currently its set for london, also this is used with conky.
```
curl http://feeds.bbc.co.uk/weather/feeds/rss/obs/world/0008.xml  >/dev/null 2>&1 > .weatherfeedrs
echo Temperature:     `cat .weatherfeedrs | grep "Temperature"| cut -f2 -d' ' | tr '&#xB0' ' ' | cut -c 1-4`C
echo Wind Direction:  `cat .weatherfeedrs| grep "Temperature"| cut -f6 -d' ' | tr -d ','`
echo Wind Speed:      `cat .weatherfeedrs | grep "Temperature"| cut -f9 -d' '` mph
echo Humidity         `cat .weatherfeedrs | grep "Temperature"| cut -f13 -d' ' | tr '&#xB0' ' ' | cut -c 1-3`%
echo pressure `cat .weatherfeedrs | grep "Temperature"| cut -f15 -d' '` `cat .weatherfeedrs | grep "Temperature"| cut -f16 -d' '`
echo Visability:      `cat .weatherfeedrs | grep "Temperature"| cut -f7 -d':'| cut -c2-20`
rm .weatherfeedrs
```

---

### Post by adamlau on 2009-01-27
```
alias k='killall'
alias u='unrar e -r'
alias dsp='df -hl'
alias mem='free -mot'
alias root='sudo -i'
alias thx='gksu thunar & exit'
alias dsk='sudo fdisk -l'
alias dir='ls -aFlhX'
alias rdir='ls -aFlhRX | less'
alias svc='sudo sysv-rc-conf'
alias sp='du -chs --apparent-size'
alias src='. ${HOME}/.bashrc'
alias mnt='gksu mousepad /etc/fstab & exit'
alias clk='sudo ntpdate 207.200.81.113'
alias ht='htop -u user --sort-key PERCENT_MEM'
alias mem='free -mot; sync && echo -n 3 | sudo tee /proc/sys/vm/drop_caches; free -mot'
alias cln='sudo apt-get -f check; sudo apt-get clean; sudo apt-get autoremove'
alias sc='sudo nmap --script-updatedb; nmap -sV -d -v --script=discovery,malware,vuln localhost'
alias rsc='sudo nmap --script-updatedb; sudo nmap -A -d -v --script=discovery,malware,vuln 192.168.2.*'
alias trash='sudo chown root:admin -hR ${HOME}/.local/share/Trash; sudo rm -rf ${HOME}/.local/share/Trash'
alias cfg='./configure --help > /tmp/cfg; mousepad /tmp/cfg & exit'
alias idx='aria2c --no-conf --show-files'
alias bit='aria2c --conf-path=${HOME}/.aria2/aria2.bit'
alias ver='aria2c --conf-path=${HOME}/.aria2/aria2.bit -V'
alias chk='make && sudo checkinstall -D --fstrans=no --nodoc'
alias ins='sudo apt-get update && sudo apt-get install'
alias rem='sudo apt-get purge'
alias tcd='sync && truecrypt -d & exit'
alias po='netstat -aetpu'
alias mp='sudo mousepad'
alias dl='aria2c'
alias ll="ls -lh"
alias la="ls -a"
alias exit="clear; exit"

# Dar Backups
alias bkl='dar -Nl'
alias fbkc='dar -c CF-`date -I` -P Desktop -P Documents -P Templates && dar -Nt ${HOME}/CF-`date -I` && par2 create -n1 -u ${HOME}/CF-`date -I`.par2 ${HOME}/CF-`date -I`*.dar'
alias fbkd='dar -c DF-`date -I` -g Desktop -g Documents -g Templates && dar -Nt ${HOME}/DF-`date -I` && par2 create -n1 -u ${HOME}/DF-`date -I`.par2 ${HOME}/DF-`date -I`*.dar'
alias bkc='dar -c CD-`date -I` -P Desktop -P Documents -P Templates -A /files/Backups/CF-2009-01-27 && dar -Nt ${HOME}/CD-`date -I` && par2 create -n1 -u ${HOME}/CD-`date -I`.par2 ${HOME}/CD-`date -I`*.dar'
alias bkd='dar -c DD-`date -I` -g Desktop -g Documents -g Templates -A /files/Backups/DF-2009-01-27 && dar -Nt ${HOME}/DD-`date -I` && par2 create -n1 -u ${HOME}/DD-`date -I`.par2 ${HOME}/DD-`date -I`*.dar'
```

---

### Post by yabbadabbadont on 2009-01-27
```
/home/daffy $ cat bin/ob_wallpaper 
#!/bin/bash

# The trailing / is important to the find
# command whenever the value of
# BACKGROUND_DIR is actually a symbolic
# link to the real directory...

BACKGROUND_DIR="$HOME/backgrounds/"
WP_SETTER="hsetroot -solid '#000000' -full"
SAVED_WP="$HOME/.config/openbox/wallpaper"

if [ $# -eq 1 ]
then
        echo "$1" > $SAVED_WP
else
        echo  "<?xml version=\"1.0\" encoding=\"UTF-8\"?>"
        echo  "<openbox_pipe_menu>"

        find "$BACKGROUND_DIR" -type f -print | \
        sort | \
        while read curr_file
        do
                base_filename="$(echo $(basename "${curr_file%\.*}") | sed -s 's/_/ /g')"
                echo  "  <item label=\"$base_filename\">"
                echo  "    <action name=\"Execute\"><execute>$WP_SETTER \"$curr_file\"</execute></action>"
                echo  "    <action name=\"Execute\"><execute>$0 \"$curr_file\"</execute></action>"
                echo  "  </item>"
        done

        echo  "</openbox_pipe_menu>"
fi

```

---

### Post by KIAaze on 2009-01-27
For those who want to contribute to this "Community scripts" project: [https://launchpad.net/scripting](https://launchpad.net/scripting)

---

### Post by adamlau on 2009-02-02
My set of aliases modified for Arch Linux:

```
alias k='killall'
alias u='unrar e -r'
alias dsp='df -hl'
alias root='sudo -i'
alias thx='sudo thunar /; exit'
alias dsk='sudo fdisk -l'
alias dir='ls -aFlhX'
alias rdir='ls -aFlhRX | less'
alias sp='du -chs --apparent-size'
alias src='. ${HOME}/.bashrc'
alias mnt='sudo mousepad /etc/fstab; exit'
alias clk='sudo ntpd -s -d'
alias ht='htop -u user --sort-key PERCENT_MEM'
alias mem='free -mot; sync && echo -n 3 | sudo tee /proc/sys/vm/drop_caches; free -mot'
alias sc='sudo nmap --script-updatedb; nmap -sV -d -v --script=discovery,malware,vuln localhost'
alias rsc='sudo nmap --script-updatedb; sudo nmap -A -d -v --script=discovery,malware,vuln 192.168.2.*'
alias trash='sudo chown root -hR ${HOME}/.local/share/Trash; sudo rm -rf ${HOME}/.local/share/Trash'
alias cfg='./configure --help > /tmp/cfg; mousepad /tmp/cfg & exit'
alias upg='sudo pacman -Syu --ignore truecrypt && sudo abs'
alias upd='sudo pacman -Sy && sudo abs'
alias ins='sudo pacman -S'
alias insd='sudo pacman -S --asdeps'
alias inst='sudo pacman -Up'
alias rem='sudo pacman -Rns'
alias re='sudo pacman -R'
alias rep='pacman -Si'
alias loc='pacman -Qi'
alias locs='pacman -Qs'
alias what='pacman -Qo'
alias exp='pacman -Qe'
alias dep='pacman -Qd'
alias orp='pacman -Qdt'
alias plk='sudo rm -f /var/lib/pacman/db.lck'
alias cln='sudo pacman -Scc && sudo pacman-optimize && sync'
alias mir='sudo pacman -Syy'
alias tcd='sync && truecrypt -d && exit'
alias po='netstat -aetpu'
alias mp='sudo mousepad'
alias dl='aria2c'
alias idx='aria2c --no-conf --show-files'
alias bit='aria2c --conf-path=${HOME}/.aria2/aria2.bit'
alias ver='aria2c --conf-path=${HOME}/.aria2/aria2.bit -V'
alias reps="pacsearch"
pacsearch() {
   echo -e "$(pacman -Ss "$@" | sed \
     -e 's#^core/.*#\\033[1;34m&\\033[0;37m#g' \
     -e 's#^extra/.*#\\033[0;32m&\\033[0;37m#g' \
     -e 's#^community/.*#\\033[1;31m&\\033[0;37m#g' \
     -e 's#^.*/.* [0-9].*#\\033[0;34m&\\033[0;37m#g' ) \
     \033[0m"
}
alias mn='manout'
manout () {
   man $1 | col -b > /tmp/$1 && mousepad /tmp/$1
}
alias ll="ls -lh"
alias la="ls -a"
alias exit="clear; exit"
alias mkp='makepkg -c'
alias mkk='makepkg -g'
alias mks='makepkg -e -c'

# Dar Backups
alias bkl='dar -Nl'
alias fbkc='dar -c CF-`date -I` -P Desktop -P Documents -P Templates && dar -Nt ${HOME}/CF-`date -I` && par2 create -n1 -u ${HOME}/CF-`date -I`.par2 ${HOME}/CF-`date -I`*.dar'
alias fbkd='dar -c DF-`date -I` -g Desktop -g Documents -g Templates && dar -Nt ${HOME}/DF-`date -I` && par2 create -n1 -u ${HOME}/DF-`date -I`.par2 ${HOME}/DF-`date -I`*.dar'
alias bkc='dar -c CD-`date -I` -P Desktop -P Documents -P Templates -A /files/Backups/CF-2009-01-27 && dar -Nt ${HOME}/CD-`date -I` && par2 create -n1 -u ${HOME}/CD-`date -I`.par2 ${HOME}/CD-`date -I`*.dar'
alias bkd='dar -c DD-`date -I` -g Desktop -g Documents -g Templates -A /files/Backups/DF-2009-01-27 && dar -Nt ${HOME}/DD-`date -I` && par2 create -n1 -u ${HOME}/DD-`date -I`.par2 ${HOME}/DD-`date -I`*.dar'
```

---

### Post by N0_Named_Guy on 2009-02-07
I've made a simple script to ease my SMS sending... This is only valid if you have a VOIP Buster account...

```

VERSION="VoipBuster SMS Sender 0.1"

if [[ "$1" == "" ]]
then
	echo "No args supplied! Run $0 -h for more info"
	exit 1
fi

if [[ "$1" == "-V" ]]
then
	echo "$VERSION"
	exit 0
fi

if [[ "$1" == "-h" ]]
then
	echo $VERSION \- Usage
	echo 
	echo $0 recipient_number \"message\"
	echo
	echo \* recipient_number - The recipients phone number. Without the country number
	echo \* \"message\" - Defines the message to send. The \"\" are mandatory
	exit 0 
fi 

DEFINDIC=00351			# Defines the default country number 
SMSTO=$DEFINDIC$1		# To whom are we going to send the sms
MESSAGE=$2			# What's the message

# Thanks dear MrQuincle
if [ ${#MESSAGE} -gt 160 ] 
then
	echo "Message contains ${#MESSAGE} tokens, which is more than 160."
	exit(1)
fi

USERNAME=putYourUserName	# Define your VOIPBuster user name
PASSWORD=putYourPassword	# Define your VOIPBuster password
SMSFROM=00YOURCELLNUMBER	# Define your cellphone number

#FAILURE=\<result\>0\</result\>	# Returned string in the case of failure
SUCCESS=\<result\>1\</result\>	# Returned string in the case of success

# Defines the base site of VOIPBuster sms sending system URL
BASESITE="https://myaccount.voipbuster.com/clx/"

# Defines the params to send to site
DOCPARAMS="sendsms.php?username=$USERNAME&password=$PASSWORD&from=$SMSFROM&to=$SMSTO&text=$MESSAGE" 

TMPRET=/tmp/$SMSTO%$RANDOM.tmp	# The status of the sms sending process will be stored in this file

#echo $DOCPARAMS

# Sends the sms, by sending a request to the VOIPBuster site
wget -nv -o /dev/null -O - "$BASESITE$DOCPARAMS" > $TMPRET

#cat $TMPRET
#echo

grep "$SUCCESS" $TMPRET > /dev/null	# Searches for the success string

# If the string was found, a 0 status error was returned
if [[ "$?" == "0" ]]
then
#	echo "Message sent to $SMSTO!";
	# Cleanup
	rm $TMPRET
	exit 0
else
	# Advise what happened
	# Cleanup is not done, due to troubleshooting purposes
	echo "Message not sent to $SMSTO!" >> /lib/udev/devices/stderr
	exit 1
fi

```

If you feel this can be improved, please let me know ;)

Edit1: addition suggested by MrQuincles
Edit2: bug added by my laziness... thank you again MrQuincles.

---

### Post by dannytatom on 2009-02-07
```

##### DEFAULTS #####

PS1='\[\033[1;31m\]\w/\[\033[0m\] '

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

PROMPT_COLOR='35;1m'

export HISTCONTROL=ignoreboth
export EDITOR="nano"
export VISUAL="nano"

shopt -s histappend
shopt -s checkwinsize

# Make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# Set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# Color prompt
force_color_prompt=yes

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi



##### CUSTOM STARTS HERE #####

### FUNCTIONS

# Easy extract
extract () {
  if [ -f $1 ] ; then
      case $1 in
          *.tar.bz2)   tar xvjf $1    ;;
          *.tar.gz)    tar xvzf $1    ;;
          *.bz2)       bunzip2 $1     ;;
          *.rar)       rar x $1       ;;
          *.gz)        gunzip $1      ;;
          *.tar)       tar xvf $1     ;;
          *.tbz2)      tar xvjf $1    ;;
          *.tgz)       tar xvzf $1    ;;
          *.zip)       unzip $1       ;;
          *.Z)         uncompress $1  ;;
          *.7z)        7z x $1        ;;
          *)           echo "don't know how to extract '$1'..." ;;
      esac
  else
      echo "'$1' is not a valid file!"
  fi
}

# Makes directory then moves into it
function mkcdr {
	mkdir -p -v $1
	cd $1
}

# Creates an archive from given directory
mktar() { tar cvf  "${1%%/}.tar"     "${1%%/}/"; }
mktgz() { tar cvzf "${1%%/}.tar.gz"  "${1%%/}/"; }
mktbz() { tar cvjf "${1%%/}.tar.bz2" "${1%%/}/"; }

# Get weather
weather ()
{ 
declare -a WEATHERARRAY 
WEATHERARRAY=( `elinks -dump "http://www.google.com/search?hl=en&lr=&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=weather+71822&btnG=Search" | grep -A 5 -m 1 "Weather for" | grep -v "Add to "`) 
echo ${WEATHERARRAY[@]} 
}

# Get IP
function myip {
  myip=`elinks -dump http://checkip.dyndns.org:8245/`
  echo "${myip}"
}

### ALIASES

## Keeping things organized
alias ls='ls --color=auto'
alias ll='ls -l'
alias la='ls -A'
alias cp='cp -i'
alias mv='mv -i'
alias mkdir='mkdir -p -v'
alias df='df -h'
alias du='du -h -c'
alias reload='source ~/.bashrc'
alias biggest='BLOCKSIZE=1048576; du -x | sort -nr | head -10'
alias rmtxtbkup='find . -name "*~" -exec rm {} \;'

## Moving around & all that jazz
alias back='cd $OLDPWD'
alias ..="cd .."
alias ...="cd ../.."
alias ....="cd ../../.."
alias .....="cd ../../../.."
alias ......="cd ../../../../.."

## Dir shortcuts
alias home='cd ~/'
alias bin='cd ~/bin'
alias documents='cd ~/documents'
alias images='cd ~/images'
alias norbert='ssh 192.168.1.3'

## App-specific
alias nano='nano -W -m'
alias wget='wget -c'
alias scrot='scrot -c -d 7'

## Sudo ease
alias yogurt="yaourt"
alias pacs="pacsearch"
pacsearch () {
       echo -e "$(pacman -Ss $@ | sed \
       -e 's#core/.*#\\033[1;31m&\\033[0;37m#g' \
       -e 's#extra/.*#\\033[0;32m&\\033[0;37m#g' \
       -e 's#community/.*#\\033[1;35m&\\033[0;37m#g' \
       -e 's#^.*/.* [0-9].*#\\033[0;36m&\\033[0;37m#g' )"
}
alias install='yaourt -S'
alias update='yaourt -Syu --aur'
alias remove='yaourt -R'
alias search='yaourt -Ss'
alias pkg-info='yaourt -Si'
alias fetch='yaourt -G'
alias list-files='yaourt -Ql'
alias group-install='sudo pacman -S'
alias install-local='sudo pacman -U'

## Easy script callin'
alias show-info='~/bin/ssig.pl'

```

If any of that stuff under **Defaults** can be removed safely, someone should let me know. I hate seeing all that stuff. :s

---

### Post by KIAaze on 2009-02-07
> **dannytatom said:**
> 
If any of that stuff under **Defaults** can be removed safely, someone should let me know. I hate seeing all that stuff. :s

Nothing of it is necessary, but you might want to keep some of it.
bash will still work if you delete ~/.bashrc.
So you can try commenting different parts out to see if you can live without them and then remove them. ;)

Things you might want to keep:
```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```
It's what enables auto-completion when you press tab I believe.

---

### Post by dannytatom on 2009-02-07
Ah, thanks!  I got rid of all the defaults other than tab-completion and it works fine.  Guess I could've tried commenting out before asking. :P

---

### Post by phenest on 2009-03-01
In the interests of security, I wrote a PSK generator ...
```
#!/bin/bash

# Random PSK generator

if [ -z $1 ]; then echo -e "Usage: psk-generator type length [-o [filename]]\ntype\t-p psk\n\t-a alphanumeric\nlength\tbetween 8 and 63 (0 for random)"; exit 0; fi
case $1 in
-p)
# Characters - no space as it could be confusing if leading or trailing
# !"#$%&`()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\]^_'abcdefghijklmnopqrstuvwxyz{|}~
characters=('!' '"' '#' '$' '%' '&' '`' '(' ')' "*" '+' ',' '-' '.' '/' '0' '1' '2' '3' '4' '5' '6' '7' '8' '9' ':' ';' '<' '=' '>' '?' '@' 'A' 'B' 'C' 'D' 'E' 'F' 'G' 'H' 'I' 'J' 'K' 'L' 'M' 'N' 'O' 'P' 'Q' 'R' 'S' 'T' 'U' 'V' 'W' 'X' 'Y' 'Z' '[' '\' ']' '^' '_' "'" 'a' 'b' 'c' 'd' 'e' 'f' 'g' 'h' 'i' 'j' 'k' 'l' 'm' 'n' 'o' 'p' 'q' 'r' 's' 't' 'u' 'v' 'w' 'x' 'y' 'z' '{' '|' '}' '~');;
-a)
# Alpha-numeric
characters=('0' '1' '2' '3' '4' '5' '6' '7' '8' '9' 'A' 'B' 'C' 'D' 'E' 'F' 'G' 'H' 'I' 'J' 'K' 'L' 'M' 'N' 'O' 'P' 'Q' 'R' 'S' 'T' 'U' 'V' 'W' 'X' 'Y' 'Z' 'a' 'b' 'c' 'd' 'e' 'f' 'g' 'h' 'i' 'j' 'k' 'l' 'm' 'n' 'o' 'p' 'q' 'r' 's' 't' 'u' 'v' 'w' 'x' 'y' 'z');;
*)
echo "Invalid type"; exit 0;;
esac

if [ -z $2 ]; then echo "You must specify a length"; exit 0; fi
l=$2;
case $1 in
-p)
if [ $2 -eq 0 ]; then ((l=RANDOM%56+8)); fi
if [ $l -lt 8 ]; then echo "Less than 8 characters won't give very good security"; exit 0; fi
if [ $l -gt 63 ]; then echo "Maximum of 63 characters allowed"; exit 0; fi;;
-a)
if [ $2 -eq 0 ]; then ((l=RANDOM%59+6)); fi
if [ $l -lt 6 ]; then echo "Less than 6 characters won't give very good security"; exit 0; fi
if [ $l -gt 64 ]; then echo "Maximum of 64 characters allowed"; exit 0; fi;;
esac

# n equals the number of characters available
n=${#characters[@]}

i=0
s=""
until [ $i -eq $l ]; do
((r=RANDOM%n))
s=$s${characters[$r]}
i=$(($i+1))
done
echo -e "\033[1;32m"$s"\033[0m"

exit 0
```
... which can also generate alpha-numeric passwords.

---

### Post by KIAaze on 2009-03-01
Well, here are two programs for generating random passwords:
[LIST]
[*]pwgen
[*]makepasswd
[/LIST]
But it's certainly safer to use something you wrote yourself. ^^

---

### Post by paimon.soror on 2009-03-01
In all honesty, this has to be one of the best/most useful threads on the forum (not to demean anyone elses thread)

---

### Post by phenest on 2009-03-07
> **KIAaze said:**
> 
Things you might want to keep:
```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```
It's what enables auto-completion when you press tab I believe.

I haven't got that in my .bashrc file, but auto complete works anyway.

---

### Post by phenest on 2009-03-07
If I put a function in my .bashrc file, it works fine from a terminal prompt, but it won't work from another bash script.

Should this be possible? The bash script complains "command not found".

---

### Post by K7522 on 2009-03-07
I run a couple small personal websites, so I wanted a way to back up the files and databases.

This keeps the files and db for seven days, and runs daily with cron.daily.

```
#!/bin/bash
# This file is run daily because of a soft link in /etc/cron.daily

# DB_BACKUP is where you want the backups to go. Must have two subdirs.
# /files and /database
export DB_BACKUP="***"
export DB_USER="***"
export DB_PASSWD="***"

find $DB_BACKUP/database -type f -mtime +7 -exec rm {} \;
find $DB_BACKUP/files -type f -mtime +7 -exec rm {} \;

/opt/lampp/bin/mysqldump --user=$DB_USER --password=$DB_PASSWD --all-databases | bzip2 > $DB_BACKUP/database/mysql-`date +%Y-%m-%d`.bz2

tar -zcvf $DB_BACKUP/files/htdocs-`date +%Y-%m-%d`.tar.gz /opt/lampp/htdocs
exit 0
```

ALSO
Instead of putting a bunch of programs in the Startup Programs in Sessions, I put one script in there under ~/startup and I put my files I wanted to boot in there. That way, all of the programs that did not boot on startup originally with the OS can be modified in the home directory.

---

### Post by phenest on 2009-03-08
If you're like me and constantly improving your .bashrc file, I added this alias:
```
alias bashrc='clear; . $HOME/.bashrc'
```
Type bashrc and your terminal will refresh and reload the .bashrc file.

---

### Post by phenest on 2009-03-08
> **phenest said:**
> If I put a function in my .bashrc file, it works fine from a terminal prompt, but it won't work from another bash script.

Should this be possible? The bash script complains "command not found".

I figured it out partially. I exported the function, so now it works from another bash script, but if I create a launcher on the Gnome panel, nothing happens. Weird!

---

### Post by Eviltechie on 2009-03-08
I made sysstatus give me a bofh excuse from fortune.

---

### Post by kaiju on 2009-03-12
> **phenest said:**
> I figured it out partially. I exported the function, so now it works from another bash script, but if I create a launcher on the Gnome panel, nothing happens. Weird!

if you want the function to be available outside of bash, you should include it in a script placed into one of the directories contained in your $PATH

---

### Post by Firestem4 on 2009-03-12
I got annoyed that my Ubuntuzilla Firefox process wouldn't shut down so I wrote my first script because I was tired of running terminal or opening the process window to close it.

```
killall firefox-bin
firefox
```
So atleast everytime I wanted to run it again I would just hit this script to close the process and open it up for me. I'm so proud of myself :D

I'm trying to figure out a way to add the script as an object (i think my friend said it was something like that. I can't honestly remember). But to run a kill-process script whenever I close out of Firefox itself. But I have absolutely no programming knowledge so I wouldn't know where to begin when looking at the files.

---

### Post by linuxisevolution on 2009-03-12
Here is my aliases file, it's kind of funny:

```
 alias soud="sudo"

alias die="sudo halt"

alias kill="xkill"

alias server2="ssh -X root@192.168.1.125"

alias server="sudo mount 192.168.1.125:/home/guest ~/server"

alias backup="cp -v -R /home/winrid/server /home/winrid/serverbackup"

```

And my scripts:

#This telnets my router:
#!/bin/sh

xterm -e telnet 192.168.1.1

exit 0


I have around 15 bash scripts on my desktop, most of them are to rdesktop and vncviewer my other machines. Two are for ssh. :D

I feel smart :lolflag:

---

### Post by Primefalcon on 2009-03-12
Not much for me I'm afraid justa  couple of aliases to make working with apache and mysql a little quicker

```
### Apache 2 Aliases ###
alias apachestart="sudo /etc/init.d/apache2 start"
alias apachestop="sudo /etc/init.d/apache2 stop"
alias apacherestart="sudo /etc/init.d/apache2 restart"

### Mysql Aliases ###
alias mysqlstart="sudo /etc/init.d/mysql start"
alias mysqlstop="sudo /etc/init.d/mysql stop"
alias mysqlrestart="sudo /etc/init.d/mysql restart"
```

---

### Post by linuxisevolution on 2009-03-12
I should create a script or alias that restarts pulseaudio, since it crashes constantly on this system...

---

### Post by chris200x9 on 2009-03-12
simple but my fav :)
```
 function sudo {
  command="$@"
  if [ -z "$command" ]; then
    command sudo -s
  else
     command sudo "$@"
  fi
}

```

---

### Post by bc54 on 2009-07-15
nice works everyone.
heres my little contribution. i hate it when im in the middle of downloading a torrent or two, but i logoff/reboot, and forget to restart my torrent client. so i looked up some man pages and did some googling, and came up with this:
```
#!/bin/bash
sleep 15
set -- /home/<username>/.config/transmission/torrents/*.torrent
	if [ -e "$1" ]; then
		transmission -m
	fi
done & exit
```
i have it run on startup. basicly it checks /home/<username>/.config/transmission/torrent/ for .torrent files. but you have to change <username> to your username. then add it to the startup list.

also, this isnt really mine, some of it i found in a google search. it zip all files and directories in the current directory into an individual .zip file.
```
#!/bin/bash
ls -1 | while read i; do f="${i%.*}";zip "${f}".zip "$i"; done
echo "The selected files have been zipped. Would you like to delete the original files y/n? (No is default)"
read ans
case $ans in
     Y|y) ;;
[Yy][Ee][Ss]) ;;
     N|n) exit ;;
[Nn][Oo]) exit ;;
       *) echo "Files will not be deleted..." & exit
esac
find . -type f ! -name '*.zip' -execdir rm -f {} +

```
hope i could help, and please keep more coming.
edit: okay, the transmission script didnt work, but i found the fix. the above transmission script now works.

---

### Post by Tibuda on 2009-07-17
> **bc54 said:**
> but you have to change <username> to your username.
You can use the $USER and $HOME variables to find the user name or the user personal folder. Try this in a terminal:
```
echo $USER
echo $HOME
```

---

### Post by Tibuda on 2009-08-05
Anyone knows how to tell how many updates are available in apt from bash (without sudo)? I would like my bash welcome message to say "There are $X updates available".

EDIT: I found it at [http://ubuntuforums.org/showthread.php?t=1012974](http://ubuntuforums.org/showthread.php?t=1012974):
```
UPDATES=`aptitude search "~U" | wc -l`
if [ $UPDATES = 0 ]; then
  echo 'No updates available'
else
  echo "There are $UPDATES updates available"
fi
```

---

### Post by Hells_Dark on 2009-08-05
> **phenest said:**
> If you're like me and constantly improving your .bashrc file, I added this alias:
```
alias bashrc='clear; . $HOME/.bashrc'
```
Type bashrc and your terminal will refresh and reload the .bashrc file.
```

source $HOME/.bashrc
```

---

### Post by KIAaze on 2009-08-07
Just for the info: source = .
From man bash:
```
        .  filename [arguments]
       source filename [arguments]
              Read and execute commands from filename  in  the  current  shell
              environment  and return the exit status of the last command exe&#8208;
              cuted from filename.  If filename does not contain a slash, file
              names  in  PATH  are used to find the directory containing file&#8208;
              name.  The file searched for in PATH  need  not  be  executable.
              When  bash  is  not  in  posix  mode,  the  current directory is
              searched if no file is found in PATH.  If the sourcepath  option
              to  the  shopt  builtin  command  is turned off, the PATH is not
              searched.  If any arguments are supplied, they become the  posi&#8208;
              tional  parameters  when  filename  is  executed.  Otherwise the
              positional parameters are unchanged.  The return status  is  the
              status  of  the  last  command exited within the script (0 if no
              commands are executed), and false if filename is  not  found  or
              cannot be read.

```

---

### Post by mysoogal on 2009-09-12
automated video encoding to be used with cron :KS

i was going to use this, with bittorrent web ui, this script would've been watching the incoming folder, and cron would fire every 160 mints it would've encoded video to h264 and grab thumbnail jpg, then send completed encode to storage. later to be viewed through php with vlc plugin installed. this idea is still floating around my head. 

> #!/bin/bash
# ffmpeg and mencoder script
# Grab thumb from avi, start encoding to ITU h264 using mencoder, ffmpeg is doing thumb processing

# Bash script for operating system Ubuntu 8.10 
# packages used : FFMPEG, MENCODER ,MPLAYER ENCODING ENGINE
# VIDEO CODEC ITU H264 AUDIO MP3


# Written by FakeOutdoorsman and updated by mysoogal
# Attribution-Noncommercial 3.0 Unported
# [http://creativecommons.org/licenses/by-nc/3.0/deed.en](http://creativecommons.org/licenses/by-nc/3.0/deed.en)
# trackback [http://ubuntuforums.org/showthread.php?t=960627](http://ubuntuforums.org/showthread.php?t=960627)

# Location of source videos
sourcelocation="/home/yugo/Desktop/video/"
# Extension of source videos
sourceext="avi"

# grab thumbs hehehe ! yahhoo hope this works!
find ${sourcelocation} -iname "*${sourceext}" -exec ffmpeg -v 0 -y -i {} -vframes 1 -ss 90 -vcodec mjpeg -f rawvideo -s 286x160 -aspect 16:9 {}.jpg \;
# Check to see if videos were encoded, then delete source vids and shutdown
if [ -e "${sourcelocation}*.ogm" ] && [ -e "${sourcelocation}*.jpg" ]; then
	# Delete videos	
	rm ${sourcelocation}*.ogm
	# Sleep for 10 seconds before shutting down
	sleep 10
	# Shutdown computer
	# sudo shutdown -h now
else
	echo "Encoding FAILED"
fi


# Convert all video clips to ITU H264 OGM video container
find ${sourcelocation} -iname "*${sourceext}" -exec mencoder {} -o {}.ogm -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=300:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame \;



exit

---

### Post by reboot09 on 2009-12-07
#! /bin/bash
dialog --title 'Wgetsum.vs1.0' --msgbox 'Welcome to Wgetsum vs 1.0 beta!!!' 8 40
dialog --title "Info" --textbox /home/guest/wg.txt 22 70 
dialog  --title "Wgetsum.vs1.0" --inputbox "Enter Url:" 8 40 2>target.txt 
dialog  --title "Wgetsum.vs1.0" --inputbox "EnterMax Download Speed In K/s numbers only:" 8 40 2>speed.txt
ADDY=`cat target.txt`
SPEED=`cat speed.txt`
X='k'
rm target.txt speed.txt
 wget -c --limit-rate=$SPEED$X $ADDY
# created by me reboot09 my first script of any real use
#the dialog info line refers to a url of a local text file a info file about the script
#i suppose i could put it on the web and change the url but this is just a test script
#i made this so i could download movies without using to much bandwith and slowing down the network im using
#usually use setting of about 50-75 k/s and no one notices the tap.
#i had a hard time with the var x=k until i added the 'symbol' which fixed it 
#any advice comments critisisms etc.. are welcomed and appreciated 
#i am fairly new to bash i learned basic and pasqual in high school yrs ago but i have to say this is fun


done

---

### Post by KIAaze on 2009-12-08
```

#! /bin/bash
# mktemp creates a temporary file in /tmp . I prefer avoiding the use of rm as much as possible personally because it is dangerous if there's a bug in the script.
TMP=$(mktemp)
dialog --title 'Wgetsum.vs1.0' --msgbox 'Welcome to Wgetsum vs 1.0 beta!!!' 8 40
dialog --title "Info" --textbox wg.txt 22 70
dialog --title "Wgetsum.vs1.0" --inputbox "Enter Url:" 8 40 2>$TMP
# $(CMD) is another way to get the output from a command
ADDY=$(cat $TMP)
dialog --title "Wgetsum.vs1.0" --inputbox "EnterMax Download Speed In K/s numbers only:" 8 40 2>$TMP
SPEED=`cat $TMP`
# just for debugging
echo ${SPEED}k $ADDY
# using ${} makes it easier to add stuff after a variable. ;)
wget -c --limit-rate=${SPEED}k $ADDY
# using the escape character "\" also works.
echo $SPEED\k $ADDY

```

You might also be interested in the following dialog systems:
-zenity
```
zenity --info --text="foo"
```
```
zenity  --notification  --text "foo"
```
-kdialog
-xdialog
-whiptail

Notification solutions:
-knotify
```
dcop knotify default notify eventname appname "foo" '' '' 2 0
```
-notify-send
```
notify-send "foo"
```

Mail confirmation:
-mail
```
echo "hello" | mail -s "subject" foo@bar.com
```

For fun:
-festival
```
echo "Hello festival" | festival --tts
```
-cowsay
```
echo "foo" | cowsay
```

---

### Post by Bachstelze on 2009-12-08
```
#!/bin/sh

cd /home/firas/software/x264
git pull > git.txt

if ! grep -q "Already up-to-date." git.txt; then
        sh version.sh
        echo >> git.txt
        cat config.h >> git.txt
        mail -s "New x264 version" firas@fkraiem.org < git.txt
fi
```

Runs in cron, sends me an email when a new x264 version in available in the GIT repo.

---

### Post by passonno on 2010-03-31
please disregard this post!  Sorry!

---

### Post by afrodeity on 2010-07-25
Quite a collection, some bits found via this thread,some via google.

```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
HISTCONTROL=$HISTCONTROL${HISTCONTROL+:}ignoredups
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth
#HISTCONTROL=erasedups

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

HISTSIZE=1000

#Ignore duplicates and types
HISTIGNORE="&:[ ]*:exit"

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

###########################################################
#################### PROMPT SECTION #######################
###########################################################
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_color_prompt=yes

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

   # PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '


# Comment in the original above and uncomment this below for a color prompt
    #PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    PS1="\$\e[0;1;33;41m[\u@\h:\w]\$ \e[m "
    #PS1="\e[0;1;33;41m[\u@\h:\w]\$ \e[m "
    #PS1="${debian_chroot:+($debian_chroot)}\[\e[0;1;33;41m\][\#][\w]\$ \[\e[m\] "
    
    # set a fancy prompt
    #PS1="\e[0;31m[\u@\h \W]\$ \e[m "
    #PS1="\e[0;1;33;41m[\u@\h:\w]\$ \e[m "
    #PS1='\u@\h:\w\$ '

#PS1='\n\D{%Y-%m-%d_%H:%M:%S_%a}, \!\n${debian_chroot:+($debian_chroot)}\u@\H:\n\w/\n\w/'
#PS1='\n\D{%Y-%m-%d_%H:%M:%S_%a}, \!\n${debian_chroot:+($debian_chroot)}\u@\H:\n\w/\n'
#PS1='\n\D{%Y-%m-%d_%H:%M:%S_%a}, \!\n${debian_chroot:+($debian_chroot)}\u@\H:\n\w/'
#PS1='\n\[\033[01;33m\]\D{%Y-%m-%d_%H:%M:%S_%a}, \!\n${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\H:\n\[\033[01;34m\]\w\[\033[01;37m\]/'
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\#@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#PS1="\[\e[0;1;33;41m\]testing\[\e[00m\]"
#PS1="\[\e[0;1;33;41m[\w]\$ \e[00m\]"


else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

#XTERM support
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
    alias dir='dir --color=auto'
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

# make bash autocomplete with up arrow
bind '"\e[A":history-search-backward'
bind '"\e[B":history-search-forward'

# make tab cycle through commands instead of listing
bind '"\t":menu-complete'

#PATH=/usr/bin:$PATH
LD_LIBRARY_PATH=/usr/lib/:$LD_LIBRARY_PATH
PKG_CONFIG_PATH=/usr/lib/pkgconfig:$PKG_CONFIG_PATH
MONO_GAC_PREFIX=/usr/lib/mono:$MONO_GAC_PREFIX
PATH=/usr/local/flashcam/bin:/usr/lib/surfraw/:$PATH

#Disable Pango in Firefox
export MOZ_DISABLE_PANGO=1


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

# WELCOME SCREEN
#######################################################

clear

echo -ne "${LIGHTGREY}" "Hello, $USER. today is, "; date
echo -e "${BROWN}"; cal ;  
echo -ne "${CYAN}";
echo -ne "${LIGHTPURPLE}Sysinfo:";uptime ;echo ""

##COWSAY FORTUNE
COWDIR=/usr/share/cowsay/cows/; COWNUM=$(($RANDOM%$(ls $COWDIR | wc -l))); COWFILE=$(ls $COWDIR | sed -n ''$COWNUM'p'); fortune | cowsay -f $COWFILE

#Colour Manual Pages
export LESS_TERMCAP_mb=$'\E[01;31m' # begin blinking
export LESS_TERMCAP_md=$'\E[01;38;5;74m' # begin bold
export LESS_TERMCAP_me=$'\E[0m' # end mode
export LESS_TERMCAP_se=$'\E[0m' # end standout-mode
export LESS_TERMCAP_so=$'\E[38;5;246m' # begin standout-mode - info box export LESS_TERMCAP_ue=$'\E[0m' # end underline
export LESS_TERMCAP_us=$'\E[04;38;5;146m' # begin underline

#export LESS_TERMCAP_mb=$'\E[01;31m'
#export LESS_TERMCAP_md=$'\E[01;31m'
#export LESS_TERMCAP_me=$'\E[0m'
#export LESS_TERMCAP_se=$'\E[0m'
#export LESS_TERMCAP_so=$'\E[01;44;33m'
#export LESS_TERMCAP_ue=$'\E[0m'
#export LESS_TERMCAP_us=$'\E[01;32m'

#SNIPPETS_DIR=~/Code

##########################
########FUNCTIONS#########
##########################
function    ff               { find . -name $@ -print; }

function    rmd              { rm -fr $@; }

function    osr              { shutdown -r now; }
function    osh              { shutdown -h now; }

function    psa              { ps aux $@; }
function    psu              { ps  ux $@; }

function    dub              { du -sclb $@; }
function    duk              { du -sclk $@; }
function    dum              { du -sclm $@; }

function    dfk              { df -PTak $@; }
function    dfm              { df -PTam $@; }
function    dfh              { df -PTah $@; }
function    dfi              { df -PTai $@; }

##################################
########SPECIAL FUNCTIONS#########
##################################
#wiki
function wiki () {

COLUMNS=`tput cols`

dig +short txt "`echo $@`".wp.dg.cx | sed -e 's/" "//g' -e 's/^"//g' -e 's/"$//g' -e 's/ http:/\n\nhttp:/' | fmt -w $COLUMNS

}

function duf {
du -sk "$@" | sort -n | while read size fname; do for unit in k M G T P E Z Y; do if [ $size -lt 1024 ]; then echo -e "${size}${unit}\t${fname}"; break; fi; size=$((size/1024)); done; done
}

#dirsize - finds directory sizes and lists them for the current directory
dirsize () {
du -shx * .[a-zA-Z0-9_]* 2> /dev/null | \
egrep '^ *[0-9.]*[MG]' | sort -n > /tmp/list
egrep '^ *[0-9.]*M' /tmp/list
egrep '^ *[0-9.]*G' /tmp/list
rm -rf /tmp/list
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

# clock - A bash clock that can run in your terminal window. 
clock () 
{ 
while true;do clear;echo "===========";date +"%r";echo "===========";sleep 1;done 
}

#Powerprompt
function powerprompt()
 {
     _powerprompt()
     {
         LOAD=$(uptime|sed -e "s/.*: \([^,]*\).*/\1/" -e "s/ //g")
	#LOAD=$(mplayer /home/kiaaze/desktop_merge/Tank/opening.wav 1>/dev/null 2>&1)
     }

    PROMPT_COMMAND=_powerprompt
     case $TERM in
         *term | rxvt  )
             PS1="${HILIT}[\A \$LOAD]$NC\n[\h \#] \W > \[\033]0;\${TERM} [\u@\h] \w\007\]" ;;
         linux )
             PS1="${HILIT}[\A - \$LOAD]$NC\n[\h \#] \w > " ;;
         * )
             PS1="[\A - \$LOAD]\n[\h \#] \w > " ;;
     esac
 }
#
# powerprompt     # this is the default prompt - might be slow
#                 # If too slow, use fastprompt instead....


```


My aliases, which are now, finally where they should be, in my .bash_aliases file

```

#Edit bashrc
alias bashrc="sudo gedit ~/.bashrc" 

#open software sources
alias repos="sudo gedit /etc/apt/sources.list"

###Aptitude/Apt####
#update software sources index
alias update="sudo aptitude update"
alias upgrade="sudo aptitude safe-upgrade"
alias install="sudo aptitude install"
alias clean='sudo apt-get autoclean && sudo apt-get autoremove'
alias search='apt-cache search'
alias show='apt-cache show'
alias repocheck="apt-cache policy"
alias go='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean && sudo apt-get autoremove && exit'

#shutdown
alias shutdownnow="shutdown now -P"

#DNS
alias dns="sudo nano /etc/resolv.conf"

#Explore
alias explore="nautilus --browser ."

#Network Interfaces
alias network="sudo nano /etc/network/interfaces"

#Restart Network
alias netstart="sudo /etc/init.d/networking restart"

#Fix keys
alias fixkey="sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com"

alias fixkeyalt="sudo apt-key adv --recv-keys --keyserver keys.gnupg.net "

#Dont cache update
alias fonts="sudo fc-cache -f -v"

#Proxy
alias proxy="export http_proxy=http://manual:manual@super.opendns.co.za:3128"

#Change Java Alternatve
alias altjava="sudo update-alternatives --config java"

#Commands
alias commands="man -k list directory"

alias cd..="cd .."
alias cd...="cd ../.."
alias cd....="cd ../../.."
alias cd.....="cd ../../../.."
alias cd......="cd ../../../../.."

#Clean Firefox
alias vacuum="find ~/.mozilla/firefox/ -type f -name "*.sqlite" -exec sqlite3 {} VACUUM \;"

#Remove orphan packages
alias orphan="sudo deborphan | xargs sudo apt-get -y remove --purge"

#Restart sysctl
alias system="sudo sysctl -p /etc/sysctl.conf"

#Restartx
alias restartx="sudo service gdm start"

#SDL lonestar login
alias superdimension="ssh deity@sdf.lonestar.org"

#Logout
alias logout="gnome-session-save --force-logout"

#lynx web browser
alias bbc='lynx http://news.bbc.co.uk/text_only.stm'
alias nytimes='lynx http://nytimes.com'

#Google
#alias google="sr google"

#launch MoC command line music player using desired theme
#alias mocp='mocp -m ~/Music'

#Services
alias services="sudo sysv-rc-conf"

#on this day
alias today='grep -h -d skip `date +%m/%d` /usr/share/calendar/*'

#Thesaurus
#alias thesaurus="sr thesaurus"

#Update System DB
alias updatedb='sudo updatedb -v'

#Unpack
alias unpack="tar -xvf"

#What is my ip
alias whatismyip="wget -qO- whatismyip.org"

#Wineboot
alias winebooter="wineboot -r ~/.wine/drive_c/windows/WININIT.INI"

#Xwinwrap background
alias mobius="xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/moebiusgears -window-id WID"

```

---

