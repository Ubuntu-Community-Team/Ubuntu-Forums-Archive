---
title: "Just installed and setup The UNICORN"
date: 2014-07-04
forum: Ubuntu Development Version
---

### Post by Cliff_Simonds on 2014-07-04
Hi everyone, I became sooo bored with how clean an perfect TRUSTY worked (I have a win 7 - ubuntu dualboot system, so room to play), so I downloaded and setup the UNICORN. I made sure I checked off send system information and error reports so Canonical can know how their OS is working on my particular laptop ( ASUS X54C with 8 gig memory and 256 GB Samsung 840 Pro SSD). Then turned off the advertising in the DASH. After trying it out, I then uninstalled that piece of malware called RHYTHMBOX (you can't turn it off or pause it from the desktop, you have to do it from the panel) and installed Audacious like always. I was able to use my last backup from TRUSTY for all my media and Thunderbird and Lightning settings, UBUNTU BACKUP is great for this. I'm sorry to see people always looking for 3rd party tools to do this, I never had a problem with it (i guess one just has know how to use it, like windows own backup in win 7). Right now UNICORN is running like a dream and the installation is the fastest I've ever seen it. Only the programs without ppa's have to wait.( I can work around that later). For example UBUNTU TWEAK had to be download instead... I'll mess with conky tomorrow. All in all installation and setup took only a little less than an hour ( BOOM take that microdollars!!!). Has is gone as easy with anyone else? Or am I the exception?

---

### Post by Cliff_Simonds on 2014-07-05
Also this morning I worked on conky. For UNICORN, conky-all and conky manager are not yet available (installable), but conky-std is. After updating ttf-mscorefonts-installer and installing conky and conky-std, I later rebooted and because I had restored my files from from my previous TAHR setup, to my suprise: my previous conky setup was on my desktop!!! I looked in my files after clicking "show hidden files" and my old conky manager files where there (no sign of manager though). I haven´t been able to change anything (color, position, etc...), but at least I have my Gotham and Seamod on my desktop. Like I said yesterday, ubuntu backup rocks.  I now have the same desktop and setup that I always have. For now instead of using ppa's I've had to download and install to local or obsolete in Synaptic, but I'm a happy camper now. I hope this helps anyone.

---

### Post by craig10x on 2014-07-05
Does it seem to be reliable? (utopic)...i mean, like good enough for regular daily primary use?
I am running 14.04 currently...and have been in development before but usually got in around the mid point (about 3 months in) and it worked well...but never got into development this early in the game...so i was curious ;)

---

### Post by Cliff_Simonds on 2014-07-06
To craig:
Only one "problem" so far, the mobile broadband indicator dissapeared from the panel, but a logout-login fixed that. I'm not sure why that happend, could be because I'm using  ** the latest Ambiance & Radiance Colors 14.04.5  **and it's for 14.04, or maybe utopic just needs time to "settel in". Today is the third day and it's working great now, but if you don't dual boot and for primary use, I would wait; you don't know what the future updates can change. I jump in early because I like suprises.:eek:

---

### Post by craig10x on 2014-07-06
Thank You, Cliff for the report...I'll just be using it "stock" and in the past, for me, development versions ran generally smooth as i do have intel on the computer and of course with intel it's open source drivers, so usually less chance of major problems...i am doing it mostly because i really like the newer kernels (3.15 and 3.16 which is coming soon to 14.10) and want the ubuntu "patched" versions because they run cooler then the mainline ones i have installed...and it's a bit of a hassle getting patched versions installed...

So, i am going to chance it....with luck i will be able to run it to release...worse case, i will just have to re-install 14.04 and wait for the final on 14.10....
I'll be using the upgrade, so at least that will save some work switching over...;)  and i always have my important data (like photos, music, videos, various files) backed up on a usb flash drive...just in case...

Certainly, development is never boring :mrgreen:  Utopic Unicorn...here i come...

---

### Post by Cliff_Simonds on 2014-07-06
Craig, I usually find if I have problems using ubuntu (development or release) or even windows, it's usually my fault... using something 3rd party, forcing a program on the os or sometines simply changing a setting...somewhat like mixing milk with lemon aid...it curdles:p. Remember to make a backup from 14.04 files then when 14.10 is installed restore from it, then your Firefox, Thunderbird, and Conky manager (no conky all yet in the repository, just basic and standard) settings and addons will be carried over (saves looots of setup time).

---

### Post by Cavsfan on 2014-07-08
I just took the partition (and I have a few on this 500GB drive) that I had trusty developmental release on and changed the trusty to utopic in the sources list and it seems to work very good.
Especially if you boot using systemd instead of upstart.

Having said that, myself I would be very hesitant to put 14.10 on the only partition I had. I have Precise 12.04 as my "main Ubuntu OS" but you can see from my signature I have others. :p
That makes it much easier to recover in case of a complete system collapse where you need to re-install. I can copy/backup all of my relevant files fairly easy from another install if needed.

I especially like the way to preserve my firefox, chromium, thunderbird  and opera settings by backing up ~/.mozilla, ~/.config/chromium, ~/.thunderbird and ~/.opera folders.
I thank **cariboo907** for showing me that handy way to preserve all of your email and browser settings: bookmarks, addons, etc. 
When you re-install you don't lose anything.

Well that's my 2 cents.

---

### Post by Cliff_Simonds on 2014-07-08
> **Cavsfan said:**
> 
Having said that, myself I would be very hesitant to put 14.10 on the only partition I had. I have Precise 12.04 as my "main Ubuntu OS" but you can see from my signature I have others. :p
That makes it much easier to recover in case of a complete system collapse where you need to re-install. I can copy/backup all of my relevant files fairly easy from another install if needed.

I'm pretty extreme when it comes to backups. On my laptop for every day use I use a 840 pro SSD, I have Ubuntu(usually a developement version) which I use almost always use, on the extended partiton; and windows 7 kept updated on the other, in case some I kill ubuntu, for bios updates, and ssd firmware update. Then I have a 1.5 GB  ext. hdd for all backups and system images. Also I have the original sloooow hdd that came with the laptop with windows 7 and the latest LTS version of ubuntu (now TRUSTY) kept updated every couple of months so if my primary disk dies I can still get working right away. The hdd may be slow but its a good back up for an emergency.
 I just like to use dev versions as a normal user does so I can see what's new and if something crashes often I send launchpad the reports  so they know about it. the more people that test and send error reports the quicker everything can get ironed out. That's why I use the dev version daily.

---

### Post by craig10x on 2014-07-08
I've only been running it a few days, but so far have to say that my experience with 14.10 has been great...seems to be very reliable and stable for an alpha 1 ;)
And that ubuntu-ized (patched) version of kernel 3.15 is working much better then the mainline one did on my 14.04 install in that it offers the same advantages (solves my multimedia problem i had with kernel 3.13) as well as being fast, snappy and even slightly better audio too...but in addition, has lower temps then that mainline version did, so i am a very happy camper :D

Lots of updates, of course but other wise everything appears to be running as it should...so, hopefully will be able to run with it until release...I have all my data backed up and an iso of 14.04 in reserve of course (just in case...lol)....

I used the upgrade in the terminal method and it was great...did not lose a thing!   just a few broken packages which package manger fixed in less then 30 seconds...funny thing was that in the past i used the upgrade option on the iso and though it worked well, i always lost a few apps...but not using this method...so, i made it...now running utopic unicorn as my PRIMARY (and only) system...

---

### Post by Cavsfan on 2014-07-08
> **Cliff_Simonds said:**
> I'm pretty extreme when it comes to backups. On my laptop for every day use I use a 840 pro SSD, I have Ubuntu(usually a developement version) which I use almost always use, on the extended partiton; and windows 7 kept updated on the other, in case some I kill ubuntu, for bios updates, and ssd firmware update. Then I have a 1.5 GB  ext. hdd for all backups and system images. Also I have the original sloooow hdd that came with the laptop with windows 7 and the latest LTS version of ubuntu (now TRUSTY) kept updated every couple of months so if my primary disk dies I can still get working right away. The hdd may be slow but its a good back up for an emergency.
 I just like to use dev versions as a normal user does so I can see what's new and if something crashes often I send launchpad the reports  so they know about it. the more people that test and send error reports the quicker everything can get ironed out. That's why I use the dev version daily.

My point exactly. I am in the development system all day pretty much. I have a 1TB USB drive that I backup windows 7 to on a weekly basis.
As far as my 5 Linux installs I can back the important stuff from another install if I cannot login to that OS to do it.
My point was mainly that if I had one partition on my hard drive and it had one version of Ubuntu I would not upgrade to or install a developmental version; I would put an LTS on it for sure.
Then I'd wait until the subsequent LTS comes out and when the first point release comes out I would then upgrade if the LTS I was using was nearing EOL.

Maybe I should look into that backup that comes with Ubuntu a little farther. But my USB drive is NTFS so I doubt that would work.

---

### Post by Cliff_Simonds on 2014-07-09
> **Cavsfan said:**
> 
Maybe I should look into that backup that comes with Ubuntu a little farther. But my USB drive is NTFS so I doubt that would work.
My external hdd is formated ntfs and ubuntus backup works just fine.

---

### Post by Cavsfan on 2014-07-09
> **Cliff_Simonds said:**
> My external hdd is formated ntfs and ubuntus backup works just fine.

Thanks for the info.

---

### Post by Cavsfan on 2014-07-09
At least in my case I don't see the point of backing anything in Ubuntu or Mint up as I have ready access to anything on that partition.
And if I cannot login to that system, I can login to another system and copy what I need from the other partition.
I have all the partitions labelled for easy identification and this is what I see from Utopic:

[ATTACH=CONFIG]254595[/ATTACH]

I copy stuff to my USB drive as needed and generally it is just stuff in my home directory: Documents, Music, Pictures, etc.

---

### Post by Cliff_Simonds on 2014-07-13
A little information for conky fans and users...
  I have two Conky's (Gotham & Seamod) and because conky-all isn't in the repositories yet I can't install conky manager. Like I said before in posting #2 my conky files from my Trusty backup carried over well. Without conky manager sometimes my conky's failed to load or only one loaded. To or reload them I was going to their gedit setup files and resaving to start them.
  After doing this a while I noticed two conky start icons, on with a lock on it and one without. The one without was from my Trusty start up (/home/cliff/.config/autostart) with the command: sh "/home/cliff/.conky/conky-startup.sh". I clicked it and noticed it restarted my conky's. I then right clicked it and **copied **it to Desktop folder and got the icon on my desktop:idea:. So now until I can install Conky Manager, if I need to restart conky, I don't have to go searching every time, I just double click the desktop icon ha!

---

### Post by Cavsfan on 2014-07-14
To restart multiple conkys just use this command **killall -SIGUSR1 conky**. Although an icon does seem pretty sweet.

I made an alias:
```
#Conky restart
alias crestart='killall -SIGUSR1 conky'
```

in ~/.bashrc then after logging out and back in to get the alias to take effect I just enter crestart in terminal to restart them.
I've never had the need to use conky manager before.

---

### Post by Cliff_Simonds on 2014-07-15
> **Cavsfan said:**
> in ~/.bashrc then after logging out and back in to get the alias to take effect I just enter crestart in terminal to restart them.
I've never had the need to use conky manager before.

Cool! That keeps the destop clean too. Thanks' for the idea Cavsfan. I'll try it.

---

### Post by Cavsfan on 2014-07-15
> **Cliff_Simonds said:**
> Cool! That keeps the destop clean too. Thanks' for the idea Cavsfan. I'll try it.

You're welcome!

---

### Post by zika on 2014-07-15
> **Cavsfan said:**
> To restart multiple conkys just use this command **killall -SIGUSR1 conky**. Although an icon does seem pretty sweet.

I made an alias:
```
#Conky restart
alias crestart='killall -SIGUSR1 conky'
```

in ~/.bashrc then after logging out and back in to get the alias to take effect I just enter crestart in terminal to restart them.
I've never had the need to use conky manager before.No need to restart CLI.```
. ~/.bashrc
```will do the trick keeping everything intact.
Even better: turn ~/.bash_aliases in ~/.bashrc on and put all aliases there so it will safe and separate. Also ```
. ~/.bash_aliases
```works and reread _just_ aliases.

---

### Post by Cavsfan on 2014-07-15
It does the trick for which it was intended. ;)

Not sure if I copied the ~/.bashrc file from an older install but it does not need to be executable to work and here is the contents of my file:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
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

# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'

#Conky restart
alias crestart='killall -SIGUSR1 conky'

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
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
```

---

### Post by zika on 2014-07-15
> **Cavsfan said:**
> It does the trick for which it was intended. ;)

Not sure if I copied the ~/.bashrc file from an older install but it does not need to be executable to work and here is the contents of my file:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
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

# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'

#Conky restart
alias crestart='killall -SIGUSR1 conky'

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
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
```Interesting: You've enabled ~/.bash_aliases and, yet, You have aliases in ~/.bashrc... Any reason for that?

---

### Post by Cavsfan on 2014-07-16
> **zika said:**
> Interesting: You've enabled ~/.bash_aliases and, yet, You have aliases in ~/.bashrc... Any reason for that?

I didn't enable ~/.bash_aliases. No file exists with that name.

---

### Post by zika on 2014-07-16
> **Cavsfan said:**
> I didn't enable ~/.bash_aliases. No file exists with that name.You gave (I presumed) Your ~/.bashrc with```

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```when default is (or decades now) that these lines are commented-out. By un-commentig those lines You've enabled it. So, every time You start CLI, file ~/.bash_aliases is being looked for ...
So...
I do remove even that part of looking for ~/.bash_aliases and I have (having ~/.bash_aliases and using it)```

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
#fi
```while default, for those that do not have ~/.bash_aliases enabled and no such file in home folder, should be```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```Small but noticable difference on (older) machines... Especially for those of us that use CLI so many times during a very short working and playing day... ;)

---

### Post by Cavsfan on 2014-07-16
> **zika said:**
> while default, for those that do not have ~/.bash_aliases enabled and no such file in home folder, should be```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

[COLOR=#ff0000]#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi[/COLOR]
```Small but noticable difference on (older) machines... Especially for those of us that use CLI so many times during a very short working and playing day... ;)

Ok I commented those 3 lines out but the first statement looks for the file (which doesn't exist) and then enables it? 
I do not see how that could enable something that is not there. It fails to meet the criteria of the if statement, therefore it will never be executed. Yeah we use CLI a lot. ;)

---

### Post by zika on 2014-07-16
> **Cavsfan said:**
> Ok I commented those 3 lines out but the first statement looks for the file (which doesn't exist) and then enables it? 
I do not see how that could enable something that is not there. It fails to meet the criteria of the if statement, therefore it will never be executed. Yeah we use CLI a lot. ;)Easy and simple. If You do not enable looking for that file and do not enable line which executes that file, file will not be read and aliases will not be read and enabled. We are, obviously, having some noise in communication. There is no point in looking for a file that You know that does not exist by default, and in real life at Your machine. Not wanting to write whole message I've already have written I am going just to point to my previous message that have all three cases clearly explained with appropriate content(s) of ~/.bashrc.

---

### Post by Cavsfan on 2014-07-16
@Cliff_Simonds
If you need to install conky-all there is a deb for it under Downloadable files on the right of this page:
[https://launchpad.net/ubuntu/utopic/amd64/conky-all/1.9.0-4](https://launchpad.net/ubuntu/utopic/amd64/conky-all/1.9.0-4)

I had to purge mine and since conky-all is not available on Utopic I installed it from that deb.
It fixed one problem I had.

My screen in Utopic:

[[img]http://en.zimagez.com/miniature/screenshotfrom2014-07-16160751.png[/img]](http://en.zimagez.com/zimage/screenshotfrom2014-07-16160751.php)

---

### Post by Cliff_Simonds on 2014-07-17
Thanks for the info Cavsfan, once I uninstalled conky-std, the deb worked like a charm. I was then able to install conky manager after with absolutly no problems. I prefer a simple conky myself: Gotham and seamod.

---

### Post by Cavsfan on 2014-07-17
> **Cliff_Simonds said:**
> Thanks for the info Cavsfan, once I uninstalled conky-std, the deb worked like a charm. I was then able to install conky manager after with absolutly no problems. I prefer a simple conky myself: Gotham and seamod.

Glad it worked out for you as well! I have to have conky-all as that looks at nvidia settings etc. I like to see my GPU temp and other system info.

---

### Post by Cliff_Simonds on 2014-07-17
> **Cavsfan said:**
>  I have to have conky-all as that looks at nvidia settings etc. I like to see my GPU temp and other system info.
Ya I can see that. I like to know what's using RAM or watch my cpu, especially because I only have an ASUS X54C laptop with intel pentium B960 HD2000 intergrated graphics, but still get decent enough 3D when surfing or just mucking around when using ubuntu. Windows 7 though is another (sad) story.
 The last couple of days utopic has been pretty stable for me, as long as I watch out for what I change when playing around. Even the system testing program (to be used when you have time to kill) worked pretty well for me.

---

### Post by Cavsfan on 2014-07-17
> **Cliff_Simonds said:**
> Ya I can see that. I like to know what's using RAM or watch my cpu, especially because I only have an ASUS X54C laptop with intel pentium B960 HD2000 intergrated graphics, but still get decent enough 3D when surfing or just mucking around when using ubuntu. Windows 7 though is another (sad) story.
 The last couple of days utopic has been pretty stable for me, as long as I watch out for what I change when playing around. Even the system testing program (to be used when you have time to kill) worked pretty well for me.

This is VidnDSL's conky on the right side of the screen. It's handy as I have FireFox sized so I can always see what's going on. This is on Precise 12.04.
As you can tell I have a "few" installs on this 500GB drive. :) If you want something like this I can point you in the right direction. There's a huge learning curve and conky will drive you nuts but it's all good.

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-07-17112256.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-07-17112256.php")

---

### Post by Cliff_Simonds on 2014-07-17
@Cavsfan thanks for the offer, I like to read the VinDSL thread, but I personally don't need all that info on my desktop all the time. I've been there in windows using Rainmeter and had a really cool desktop, but it got to a point where I had to ask myself, do I really need ALL of this? And decided no. For my weather I check Bing weather in the morning and it's pretty accurate for me here in Germany. And I have System Load Indicator on my panel if I need a quick glimps of basic resources. But thanks any way. But in case there are others out there thinking of it: DON'T be affraid of the learning curve, just like linux in general, when you finally master something new or hard to comprehend at first and finally do, it's as good as the first coffee rush in the morning.

---

### Post by Cliff_Simonds on 2014-07-20
So it's been another week using utopic alpha 1:

  After installing conky-all (kudos to Cavsfan) then installing Conky Manager, I've had no more problems with my conkys loading on boot.
  Also after setting the firewall back to original settings, I've had no more problems with my mobile broadband usb.
  _The whole week through, I haven't had any crashes or freezes and everything is running as stable for me as it did in Trusty._ I chose to jump in early this time in the alpha 1 phase instead of waiting for the late beta testing or even the final release candidate, and it's very interesting to see through the fixes and updates, just how much work goes into my OS of choice. 
 Microdollars could learn alot from Canonical in this sense: Let the users who want to test and run alpha or beta do so, so they can test more systems(no two are equal) and not have the problems like they're updating from 8 to 8.1 for alot of their customers. When I had a crash and apport aske me to send a report to Launchpad I did. I even got a personal thank you email from them and alittle more info on how to go about reporting better. That's what I call "True interest in the user".
 I'm just a typical user, and not a coder or programmer, so I don't understand what all the parts(packages) of ubuntu are, but thanks to synaptic I can read what "ingredients" my flavor of choice has, and thanks to ubuntu forums can read how it all interacts.
 To all alpha testers: Have a fun week!

---

### Post by Cliff_Simonds on 2014-07-27
So another week gone by using utopic ubuntu and no crashes or freezes what so ever, if anything it's faster and snappier. All this weeks updates went without a hitch and the new kernel (Linux 3.16.0-5-gerneric) is working great. 
  One really great thing I noticed is that utopic now boots to_ the last used brightness setting_ and not 100% like all the earlier versions. That means: in the evening when I shut down for bed and have the screen dimmed, then boot early in the morning before work(04:00 a.m.) to read my mails and RSS feeds it's still dimmed and my eyes don't get flashed burned:shock:!!!

---

### Post by Cliff_Simonds on 2014-08-01
After the last updates, for memory sanitizer et all.. It some how reactivated that dreaded hibernate, and seeing that I use an ssd I had to manualy deactivate it using:
 
Type (or copy/paste): 
[COLOR=#0000FF]sudo apt-get install gksu leafpad[/COLOR]

Press Enter and submit your password. Please note that the password will  remain invisible, not even asterisks will show, which is normal.

Leave the terminal window open for the actual hack.

b. Copy/paste the following line into the terminal (use copy/paste to prevent typo's):

[COLOR=#0000FF]sudo touch /etc/polkit-1/localauthority/90-mandatory.d/disable-hibernate.pkla[/COLOR]

Press Enter.

c. Copy/paste the following line into the terminal (use copy/paste to prevent typo's):

[COLOR=#0000FF]gksudo leafpad /etc/polkit-1/localauthority/90-mandatory.d/disable-hibernate.pkla[/COLOR]

Press Enter.

d. Copy and paste the following blue text into that empty text file:

[COLOR=#0000FF][Disable hibernate (upower)]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=no
ResultInactive=no
ResultAny=no

[Disable hibernate (logind)]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=no

[Disable hibernate for all sessions (logind)]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate-multiple-sessions
ResultActive=no[/COLOR]

Save the text file and close the text editor.

e. Reboot your computer (full reboot). Hibernation should now no longer be one of the options in the shutdown menu.

---

### Post by Cliff_Simonds on 2014-08-04
I just did a partial upgrade that was offered from the software updater, and it reinstalled that piece of** [COLOR=#ff0000]_MALWARE _[/COLOR]**Rhythmbox. I gave it a chance and tested it and as usual, after starting a song I couldn't stop it(no stop button) and when using the pause it stops the music only for a second then resumes from the beginning of the song. 
I had to uninstall it while a song was playing, and the song kept playing till I did a reboot.  This is the reason I  use Audacious(good sound, good control).
So far everything else is ok.

---

### Post by Cavsfan on 2014-08-05
> **Cliff_Simonds said:**
> I just did a partial upgrade that was offered from the software updater, and it reinstalled that piece of** [COLOR=#ff0000]_MALWARE _[/COLOR]**Rhythmbox. I gave it a chance and tested it and as usual, after starting a song I couldn't stop it(no stop button) and when using the pause it stops the music only for a second then resumes from the beginning of the song. 
I had to uninstall it while a song was playing, and the song kept playing till I did a reboot.  This is the reason I  use Audacious(good sound, good control).
So far everything else is ok.

If you pause Rhythmbox and then click the x to exit it that should work. It did for me just now. But when I just clicked the x to close it it kept playing so I understand. I prefer Audacious myself too.
I've got the music player in Cairo Dock set to use Audacious. So, I'd have to explicitly click on Rhythmbox to run it. Which I don't.
I suspect it will come back again as I believe it is part of the release.

Best way to avoid partial upgrades is to use the CLI method - **sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean** and it something is held back **sudo apt-get dist-upgrade**.
Then instead of typing that into the terminal each time you can set up aliases. I think I've already posted how to do that and don't want to repeat myself again.
But, if didn't see it and want to know how I'll be happy to let you know.

I just type **ud** for the first one and **ud2** for the second one. Cuts out much typing in terminal.

Ranch hand called update manager update mangler :p He showed me it's best to use CLI for updating. You never get a partial upgrade.

---

### Post by Cliff_Simonds on 2014-08-05
@Cavsfan thanks for the info. For CLI, I keep a file on my desk top with different commands that I need and just copy and paste. Pretty lazy I know and after a while you forget them especially when helping someone else at their house. Kinda like what speed dial has done to me: except for my own phone number I can't remember anyone elses. 
Back to Rythmbox: even after I uninstalled it the darn thing kept playing the song till I rebooted. Later it came to me probably a log out/in would of been enough. I called it malware because it took over my computer and I couldn't stop it. If they're going to keep giving us this with our distro, they really should work on the basic functions like: on, off, pause...etc and not just pulseaudio. I mean if I had control of it I'd use it even with out the EQ it sounds ok...I only use the media players when I'm on my laptop.
And like my signiture say's I [FONT=fixedsys]avoid 3rd party programs & apps where I can. [/FONT]

---

### Post by craig10x on 2014-08-05
Rhythmbox works fine on my 14.04 install...could be buggy because you are in Development and are no doubt running a newer version that might not yet be completely smoothed out...
In development you almost have to expect glitches with certains apps and stuff at times...it's still in Alpha...

---

### Post by Cliff_Simonds on 2014-08-06
> **craig10x said:**
> Rhythmbox works fine on my 14.04 install...could be buggy because you are in Development and are no doubt running a newer version that might not yet be completely smoothed out...
In development you almost have to expect glitches with certains apps and stuff at times...it's still in Alpha...
That's not necessarily true, I've always had problems with Rhythmbox be it alpha, beta, stable or even LTS. It's the only program that I uninstall and substitute for another in ubuntu. But that's just me. Plus I really don't like the idea that one has to search for an equalizer to install. Even WMA in Windollars comes with an EQ and sound processor.

---

### Post by Cavsfan on 2014-08-25
Just an FYI: I installed Ubuntu 14.10 Mate and it did come with the alias file **~/.bashrc** I thought I may have copied it from another install but that was not true it comes default.

---

### Post by Cliff_Simonds on 2014-09-06
I haven't posted in this thread in the last 4 weeks and just wanted to say that Utopic is running smoothly the whole time. But I must say I probably got luckly when I bought my ASUS X54C 4 years ago. It works perfectly with Ubuntu, plus I don't have a graphics card that seems to cause others alot of trouble be it linux or windows. I use default "system settings", and only make the changes necessary for ssd's. I even opened up 12 programs and 3 instances of Libreoffice(writer,calc and impress) and had 8 pages opened in firefox, at the same time running software center and synaptic and used only a little more than 3GB from my 8GB RAM...now that rocks! Talk about low on system resources. I mean I tried to thrash and crash the system and didn't even come close.

---

### Post by jerrylamos on 2014-09-06
> **Cavsfan said:**
> 
Ranch hand called update manager update mangler :p He showed me it's best to use CLI for updating. You never get a partial upgrade.

I miss Ranch Hand.  I forget where he went?

On install first thing I do is run a setup exec that among other things does
sudo software-properties-gtk
so I can turn update to "never".
I don't want update crashing in to what I'm doing, and 
anytime partial update is indicated likelyhood of killing the install is high.

Then practically daily during development I run

#! /bin/bash
sudo apt-get update
sudo apt-get dist-upgrade
exit 0

Updates clutter up the disk so I run

#! /bin/bash
df
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
df
#exit 0

and when the added disi space gets up over 1G more than it was when originally installed, 
to get rid of the un-used linux-images in /boot, 
start synaptic, search on linux-image-3. whatever, and remove including configuration files
Of course with unstable development releases have good backups.

---

### Post by zika on 2014-09-06
Updates do not &#8222;clutter up the disk&#8220; if set properly. OK, cleaning what is already clean does not do any harm... ;)
When cleaning &#8222;unused linux-images&#8220; (why did not they got cleaned with autoremove, if they were not installed manually?) try cleaning unused linux-headers and other stuff that comes with image...
About partial upgrades I thought almost all was said, but, alas... ;)
Last time I've looked (actually couple of seconds ago... ;)) RanchHand is on CodeRanch and [https://openlinuxforums.org/index.php?action=profile;u=193](https://openlinuxforums.org/index.php?action=profile;u=193)

---

### Post by jerrylamos on 2014-09-06
Thanks, zika.  I took a look at openlinuxforums.org didn't see much activity in the few topics I viewed.

From time to time there have been a lot of people posting on the ubuntu development forums.  Activity seems to be much reduced of late.  I wonder where all the people went?

---

### Post by Cavsfan on 2014-09-07
> **jerrylamos said:**
> I miss Ranch Hand.  I forget where he went?

On install first thing I do is run a setup exec that among other things does
sudo software-properties-gtk
so I can turn update to "never".
I don't want update crashing in to what I'm doing, and 
anytime partial update is indicated likelyhood of killing the install is high.

Then practically daily during development I run

#! /bin/bash
sudo apt-get update
sudo apt-get dist-upgrade
exit 0

Updates clutter up the disk so I run

#! /bin/bash
df
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
df
#exit 0

and when the added disi space gets up over 1G more than it was when originally installed, 
to get rid of the un-used linux-images in /boot, 
start synaptic, search on linux-image-3. whatever, and remove including configuration files
Of course with unstable development releases have good backups.

I had heard Ranch Hand was busy farming but that's been a while ago. I also heard he was doing Debian testing.
Setting the updates to never seems like a good idea. I occasionally get that error:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
I usually just open update manager and then close it and that solves the problem but since I don't use update mangler your idea is better. :)

I always check for updates first **ud** and then dist-upgrade second **ud2** to see if there is anything held back like a new kernel.
I'm sure autoremove has gotten better over the years and I have that as alias **ud3** but even on Precise it doesn't always remove all the parts of the kernel so I keep a text file with the kernels on them and remove any manually leaving the latest two.

i.e. ```
sudo apt-get purge linux-headers-3.16.0-12 linux-headers-3.16.0-12-generic linux-image-3.16.0-12-generic linux-image-extra-3.16.0-12-generic
```

> **zika said:**
> Updates do not &#8222;clutter up the disk&#8220; if set properly. OK, cleaning what is already clean does not do any harm... ;)
When cleaning &#8222;unused linux-images&#8220; (why did not they got cleaned with autoremove, if they were not installed manually?) try cleaning unused linux-headers and other stuff that comes with image...
About partial upgrades I thought almost all was said, but, alas... ;)
Last time I've looked (actually couple of seconds ago... ;)) RanchHand is on CodeRanch and [https://openlinuxforums.org/index.php?action=profile;u=193](https://openlinuxforums.org/index.php?action=profile;u=193)

Cool, glad to see Ranch Hand is still at it. :)

I see this on his profile so he is still involved with Debian and his sense of humor hasn't changed one bit. :D
Debian Testing for normal use, Stable for secure use, Sid for FUN.
Not one shred of evidence supports the notion that life is serious.

Edit: Ranch Hand is also the one that showed me how to make the custom grub menu that is the Wiki in my signature. After a while I asked him if he'd mind if I made a HowTo out of it and he just said go for it.
He also helped me a lot on it. Then Drs305 helped a lot later on.

---

### Post by zika on 2014-09-07
> **Cavsfan said:**
> I occasionally get that error:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
I usually just open update manager and then close it and that solves the problem but since I don't use update mangler your idea is better. :)Did You take time any time to just look who is keeping hands on lock file and did You simply try to erase that file?
This „idea“ made me remember jokes about programmer's way of „solving“ things...

---

### Post by creosote on 2014-09-07
> **zika said:**
> Did You take time any time to just look who is keeping hands on lock file and did You simply try to erase that file?
This „idea“ made me remember jokes about programmer's way of „solving“ things...
@zika
did you take the time, any time, to consider offering a helpful method to " look who is keeping hands on lock file"?:p:p
@cavsfan
sometimes i'll use the "Processes" tab in System Monitor to find and kill those types of things but sometimes i find your approach more efficient and somehow more satisfying.

---

### Post by zika on 2014-09-08
> **creosote said:**
> @zika
did you take the time, any time, to consider offering a helpful method to " look who is keeping hands on lock file"?:p:pYes. But I do not like to impose my solutions before being asked...
```
sudo fuser -vvv /var/lib/dpkg/lock
USER PID ACCESS COMMAND
/var/lib/dpkg/lock:  root      12006 F.... apt-get
```

---

### Post by creosote on 2014-09-08
> **zika said:**
> Yes. But I do not like to impose my solutions before being asked...
```
sudo fuser -vvv /var/lib/dpkg/lock
USER PID ACCESS COMMAND
/var/lib/dpkg/lock:  root      12006 F.... apt-get
```
I shouldn't think you would want to impose them at all. :p:p

Be that as it may, how would you go about finding"[COLOR=#000000]who is keeping hands on lock file"?[/COLOR]

---

### Post by Elfy on 2014-09-08
> **creosote said:**
> I shouldn't think you would want to impose them at all. :p:p

Be that as it may, how would you go about finding"[COLOR=#000000]who is keeping hands on lock file"?[/COLOR]

Did you try the command ;)

or man fuser

---

### Post by creosote on 2014-09-08
> **Elfy said:**
> Did you try the command ;)

or man fuser
I just hit the man page . ..thank you both, that was helpful

---

### Post by Cavsfan on 2014-09-08
Lol :lol: All I did was open up Synaptic and then in terminal **sudo apt-get update && sudo apt-get upgrade** to produce that error. :p

So yeah I knew precisely where the error was coming from. :p

Sometimes I'll have Synaptic open and forget that I do and others update mangler is either about to pop up or is on it's way to popping up.

I like [COLOR=#000000]jerrylamos' approach and set Automatically check for updates to never.

[ATTACH=CONFIG]256261[/ATTACH]

Since I only get my updates via terminal. [/COLOR];)

---

### Post by zika on 2014-09-08
Bad news: As far as I know, that un-checking for automatical checking for updates does not prevent system from checking for updates... ;)
I'm yet to find 100% sure way of preventing system from automatically checking for updates... ;)
Just watch system messages closely while booting/check logs and You will be sure to see what I'm writing about... ;)

---

### Post by Cavsfan on 2014-09-08
> **zika said:**
> Bad news: As far as I know, that un-checking for automatical checking for updates does not prevent system from checking for updates... ;)
I'm yet to find 100% sure way of preventing system from automatically checking for updates... ;)
Just watch system messages closely while booting/check logs and You will be sure to see what I'm writing about... ;)

LoL That would be very ironic wouldn't it?

I'll keep an eye on it but it doesn't much matter to me. If Update Mangler opens up I simply close it. Then I click on terminal. ;)

---

### Post by zika on 2014-09-09
> **zika said:**
> Bad news: As far as I know, that un-checking for automatical checking for updates does not prevent system from checking for updates... ;)
I'm yet to find 100% sure way of preventing system from automatically checking for updates... ;)
Just watch system messages closely while booting/check logs and You will be sure to see what I'm writing about... ;)
> **Cavsfan said:**
> LoL That would be very ironic wouldn't it?
I'll keep an eye on it but it doesn't much matter to me. If Update Mangler opens up I simply close it. Then I click on terminal. ;)Why "ironic"? What I've wrote is just sincere. I'd wish I found way to turn off all automatic updates for good but... alas...
One that I would mostly like to turn off is one that happens on first boot of the day...

---

### Post by Elfy on 2014-09-09
> **zika said:**
> Why "ironic"? What I've wrote is just sincere. I'd wish I found way to turn off all automatic updates for good but... alas...
One that I would mostly like to turn off is one that happens on first boot of the day...

Not got the inclination to play with it but perhaps /etc/apt/apt.conf.d/10periodic setting APT::Periodic::Update-Package-Lists "1" to 0 instead

---

### Post by zika on 2014-09-09
```
:~$ cat  /etc/apt/apt.conf.d/10periodic
APT::Periodic::Update-Package-Lists "0";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
```;)
```
:~$ cat /etc/apt/apt.conf.d/50unattended-upgrades 
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
//    "${distro_id}:${distro_codename}-security";
//    "${distro_id}:${distro_codename}-updates";
//    "${distro_id}:${distro_codename}-proposed";
//    "${distro_id}:${distro_codename}-backports";
};
...
```;)

---

### Post by Elfy on 2014-09-09
not that then :D

---

### Post by zika on 2014-09-09
> **elfy said:**
> not that then [IMG]http://ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG][IMG]http://ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG]

---

### Post by Elfy on 2014-09-09
of course if that's NOT doing it then perhaps it's a bug :)

---

### Post by zika on 2014-09-09
> **Elfy said:**
> of course if that's NOT doing it then perhaps it's a bug :)Once I get some more spare time on my hands I'll investigate. That is what I've been promising myself for quite some time... ;) A bit tricky to file that kind of bug properly...
There is a valid possibility that I'm wrongly diagnosing some other stuff happening... We'll see...  :p

---

### Post by Elfy on 2014-09-09
if nothing else - you're not alone - plenty of other people set it to 0 and confusion reigns when it still does it :p

Edit - I've set that to 0 in my other install, after 30 minutes I've not been informed of any updates - I'll boot it tomorrow morning again.

---

### Post by zika on 2014-09-09
> **Elfy said:**
> if nothing else - you're not alone - plenty of other people set it to 0 and confusion reigns when it still does it :p

Edit - I've set that to 0 in my other install, after 30 minutes I've not been informed of any updates - I'll boot it tomorrow morning again.I'm not getting information about new updates, I just resent waiting on first boot of the day while it checks for updates... In background and silently... I'll check if that has stopped...

---

### Post by Cavsfan on 2014-09-09
I'm not worried about it. I never have before so why start now. :p
The first thing I do when I boot up is bring a terminal up and check for updates. Sometimes Update Mangler :p will pop up in between updates with something held back like a kernel.
I just close it then do a dist-upgrade to get the held updates.

So, non fa niente.

---

### Post by jimmy-frydkaer on 2014-09-10
Been on the Unicorn GNOME since A1 and what a "race-horse"

HW-spec:
Intel Core i7 @ 3.200 Mhz
4 GB DDR3 RAM
1.5 GB GeForce 440
1 TB SATA hdd

The horse knows its way round the field I'd say - Stable, easy to use and FAST.

Boot is done faster than in any other *ntu I've tried since October 2006. 

I'm using the horse for every day use as the only system on my Pc. All my "important" stuff is stored on my 3 TB NAS server so in case of a crash I only need to fetch things from that drive.

Since A1 the Unicorn has been rock solid on my system. Only problem has been with the install of icedtea-plugin-7 which WILL NOT install - Well some day it will, I know that.

Audio and video on the Unicorn is beautiful. Much better than it was in 14.04 GNOME. The proprietary graphics driver runs smoother than ever before and has so far not had a single glitch. 

I'm used to the testing/dev editions and has been on every single one of them since 2007 - 

The probs with the icedtea-plugin is reported to Launchpad, so no worries. 

I love playing around with the "next" editions. To me it's a great way of getting to know your system.

/Have FUN

---

### Post by Cavsfan on 2014-09-10
> **jimmy-frydkaer said:**
> Only problem has been with the install of icedtea-plugin-7 which WILL NOT install - Well some day it will, I know that.

Perhaps instead of icedtea-plugin-7 you'd be interested in a later version that automagically updates itself.

[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

```
cavsfan@cavsfan-MS-7529:~$ java -version
java version "1.8.0_20"
Java(TM) SE Runtime Environment (build 1.8.0_20-b26)
Java HotSpot(TM) 64-Bit Server VM (build 25.20-b23, mixed mode)
```

You have the option of Java 7 or Java 8 and there's directions for changing back and forth on that page. It's the same link as the blue link in my signature.

cheers

---

### Post by slickymaster on 2014-09-10
> **Cavsfan said:**
> Perhaps instead of icedtea-plugin-7 you'd be interested in a later version that automagically updates itself.

[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

```
cavsfan@cavsfan-MS-7529:~$ java -version
java version "1.8.0_20"
Java(TM) SE Runtime Environment (build 1.8.0_20-b26)
Java HotSpot(TM) 64-Bit Server VM (build 25.20-b23, mixed mode)
```

You have the option of Java 7 or Java 8 and there's directions for changing back and forth on that page. It's the same link as the blue link in my signature.

cheers

I can't +1 enough Cavsfan's advise.

---

### Post by craig10x on 2014-09-10
agree ;) I've used that ppa in the past (from their site) works fantastically and you get all the updates too :D

---

### Post by zika on 2014-09-11
Why depend on PPA when You can do it Yourself?
DL Java{7,8,9} jdk tar, untar it in ~/Java/JDK (for example, for JDK, similar for JRE archive, little different paths)```
sudo update-alternatives --install "/usr/bin/java" "java" "/home/&#1080;&#1084;&#1077;/Java/JDK/bin/java" 1sudo update-alternatives --install "/usr/bin/javac" "javac" "/home/&#1080;&#1084;&#1077;/Java/JDK/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/home/&#1080;&#1084;&#1077;/Java/JDK/bin/javaws" 1
sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/home/&#1080;&#1084;&#1077;/Java/JDK/jre/lib/amd64/libnpjp2.so" 1
```[COLOR=#000000][FONT=Monaco]
[/FONT][/COLOR]Check jdk9.java.net/download/ regularly and just DL and untar and...

---

### Post by jimmy-frydkaer on 2014-09-11
Thanx guys - I've installed Oracle Java 8 first time I saw that icedtea-plugin7 wouldn't install. Forgot to mention that, sorry.

I've tried Icedtea-plugin on different systems of mine running the horse and each and every one of them fails to install icedtea-plugin. Only exception is my older MSI laptop which cannot run the Unicorn. It freezes every time no matter which install, with or without nomodeset. On Trusty icedtea-plugin just run and it does a great job doing that. The freeze on Unicorn isn't the first alpha/beta I've seen do that.

Truth to tell I do not trust Oracle that much (NSA), but I do need my Home Banking up and running.

---

### Post by Cavsfan on 2014-09-11
> **slickymaster said:**
> I can't +1 enough Cavsfan's advise.

Thank you. :)

> **craig10x said:**
> agree ;) I've used that ppa in the past (from their site) works fantastically and you get all the updates too :D

Kool! ;)

> **zika said:**
> Why depend on PPA when You can do it Yourself?
DL Java{7,8,9} jdk tar, untar it in ~/Java/JDK (for example, for JDK, similar for JRE archive, little different paths)```
sudo update-alternatives --install "/usr/bin/java" "java" "/home/&#1080;&#1084;&#1077;/Java/JDK/bin/java" 1sudo update-alternatives --install "/usr/bin/javac" "javac" "/home/&#1080;&#1084;&#1077;/Java/JDK/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/home/&#1080;&#1084;&#1077;/Java/JDK/bin/javaws" 1
sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/home/&#1080;&#1084;&#1077;/Java/JDK/jre/lib/amd64/libnpjp2.so" 1
```[COLOR=#000000][FONT=Monaco]
[/FONT][/COLOR]Check jdk9.java.net/download/ regularly and just DL and untar and...

I used to do it manually too and posted about 15 threads. One for every time a new version came out but why do it the hard way when you can have a ppa update it automagically for you which is so much easier. ;)

> **jimmy-frydkaer said:**
> Thanx guys - I've installed Oracle Java 8 first time I saw that icedtea-plugin7 wouldn't install. Forgot to mention that, sorry.

I've tried Icedtea-plugin on different systems of mine running the horse and each and every one of them fails to install icedtea-plugin. Only exception is my older MSI laptop which cannot run the Unicorn. It freezes every time no matter which install, with or without nomodeset. On Trusty icedtea-plugin just run and it does a great job doing that. The freeze on Unicorn isn't the first alpha/beta I've seen do that.

Truth to tell I do not trust Oracle that much (NSA), but I do need my Home Banking up and running.

I know what you mean but there are those times when you need it and you **do** want the *absolute latest version*. This will give you exactly that.

---

### Post by zika on 2014-09-11
> **Cavsfan said:**
> I used to do it manually too and posted about 15 threads. One for every time a new version came out but why do it the hard way when you can have a ppa update it automagically for you which is so much easier. ;)I've started in 2008. and old habbits in my case die hard... ;)
> **Cavsfan said:**
> I know what you mean but there are those times when you need it and you **do** want the *absolute latest version*. This will give you exactly that.Well, not the latest... ;) Absolute latest (pre)version is one I've mentioned... ;)

Have all a good time with UU it is worth it as it looks. Today I've made first official (i.e. on my workplace) upgrade from TT to UU (just by change of sources lists...)... It's upgrade time... ;)

---

### Post by Cavsfan on 2014-09-11
> **zika said:**
> I've started in 2008. and old habits in my case die hard... ;)
Well, not the latest... ;) Absolute latest (pre)version is one I've mentioned... ;)

Have all a good time with UU it is worth it as it looks. Today I've made first official (i.e. on my workplace) upgrade from TT to UU (just by change of sources lists...)... It's upgrade time... ;)

I understand about old habits! Welcome to the Unicorn with systemd built in. It's pretty cool! ;)

I also have Unicorn Mate which uses a fork of the GNOME 2-era desktop and its associated applications on top of an Ubuntu 14.10 base.

[http://www.omgubuntu.co.uk/2014/09/ubuntu-mate-remix-14-10-beta-1-released](http://www.omgubuntu.co.uk/2014/09/ubuntu-mate-remix-14-10-beta-1-released)

---

### Post by zika on 2014-09-12
> **Cavsfan said:**
> I understand about old habits! **Welcome **to the Unicorn with systemd built in. It's pretty cool! ;)I'm there all the time, just You did not notice/read me... ;)

---

### Post by Cavsfan on 2014-09-12
> **zika said:**
> I'm there all the time, just You did not notice/read me... ;)

I guess not. I took that as you were just now "officially" joining the developmental version which is what you said. I guess you had been dabbling with it before eh?

Got a TON of updates today and everything still appears smooth as silk.

---

