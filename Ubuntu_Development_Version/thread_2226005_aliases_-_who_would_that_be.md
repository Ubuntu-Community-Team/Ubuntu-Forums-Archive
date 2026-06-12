---
title: "aliases - who would that be?"
date: 2014-05-24
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2014-05-24
This thread is in deference to Zika who recommends using aliases. I have no idea what he is talking about but I found this

[http://www.howtogeek.com/73768/how-to-use-aliases-to-customize-ubuntu-commands/](http://www.howtogeek.com/73768/how-to-use-aliases-to-customize-ubuntu-commands/)

A tutorial even I can understand. I created the file .bash_aliases, ticked it to allow executing and put this, courtesy of Zika, in it.
```
alias pkx='pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY $i'
```

now pkx gedit will do the work of pkexec gedit. Of course, we first need to have a Polkit policy as well for this to work.

Regards.

---

### Post by Elfy on 2014-05-24
Amazing what you just assume people use. I use a few aliases - a few for apt-get and I've 3, 32l,64l,64u to zsync the 3 images I'm worried about in general.

---

### Post by Cavsfan on 2014-05-24
I guess I just assumed that you put aliases in the ~/.bashrc file. But since it doesn't exist on new installs (at least I don't think it does) I copy it into the new install. 
Then I logoff and back on and they work. I use several aliases myself:

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'

#Conky restart
alias crestart='killall -SIGUSR1 conky'
```

I got the first 2 from someone in this forum and I can't remember who. #-o

---

### Post by vasa1 on 2014-05-24
> **Cavsfan said:**
> ...
Then I logoff and back on and they work. ...
Why don't you use
```
source .bashrc
```or```
. ~/.bashrc
``` assuming you don't have several terminals open? Won't either be more simple? In which case would a log off, log on be preferable?

---

### Post by zika on 2014-05-25
> **grahammechanical said:**
> This thread is in deference to Zika who recommends using aliases. I have no idea what he is talking about but I found this

[http://www.howtogeek.com/73768/how-to-use-aliases-to-customize-ubuntu-commands/](http://www.howtogeek.com/73768/how-to-use-aliases-to-customize-ubuntu-commands/)

A tutorial even I can understand. I created the file .bash_aliases, ticked it to allow executing and put this, courtesy of Zika, in it.
```
alias pkx='pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY $i'
```

now pkx gedit will do the work of pkexec gedit. Of course, [B]we first need to have a Polkit policy as well for this to work.
[/B]
Regards.Well, I think: **no**. When trying this I did not change anything from vanilla default for Polikit so... I'm pretty sure, as I wrote in thread from which You've taken this alias, that simple proper usage op pkexec is enough... I might be wrong, but...
I should apologize for assuming that so powerfull tool such as aliases is not widely known... I've been using it for 35 years or even more and do always have a bunch (200+) of those, just carrying them from one OS to another, from 4DOS to...

---

### Post by sudodus on 2014-05-25
Do you recommend ***pkx***
```
alias pkx='pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY $i'
```
instead of gksu or gksudo?

---

### Post by zika on 2014-05-25
> **sudodus said:**
> Do you recommend ***pkx***
```
alias pkx='pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY $i'
```
instead of gksu or gksudo?```
$ ll gks*
-rwxr-xr-x 1 root root 28176 Oct  2  2012 gksu*
lrwxrwxrwx 1 root root     4 Nov 12  2012 gksudo -> gksu*
```

---

### Post by sudodus on 2014-05-25
I should have asked 'Do you recommend ***pkx*** instead of gksu ***and*** gksudo?'

- Is it generally better or only in some cases in Utopic?
- Do you think pkexec will completely replace gksu in the future?

---

### Post by Cavsfan on 2014-05-25
> **vasa1 said:**
> Why don't you use
```
source .bashrc
```or```
. ~/.bashrc
``` assuming you don't have several terminals open? Won't either be more simple? In which case would a log off, log on be preferable?

I just drop the .bashrc file from a backup into my home directory. What could be simpler?

I also don't have the problem with gksu, it just gives the same warning I get in Trusty. So I have no need for pkexec.

This is the same developmental install as Trusty was on just with the sources switched to Utopic.
Is that cheating? :p

---

### Post by grahammechanical on 2014-05-25
gksudo is not installed by default anymore as it is considered depreciated by the devs and a few days ago some of us found gksu/gksudo to be broken in Utopic.

[http://ubuntuforums.org/showthread.php?t=2225514](http://ubuntuforums.org/showthread.php?t=2225514)

So, my attention came back to pkexec. And then someone mention aliases. And here we are. Not wishing to go off topic and just so we are clear about the future of gksu/gksudo in Ubuntu

[https://answers.launchpad.net/ubuntu/+source/gksu/+question/227275](https://answers.launchpad.net/ubuntu/+source/gksu/+question/227275)

> Patches dropped:
    - debian/patches/21_strip_blank_space.patch: No longer needed since we
      don't build nautilus-gksu anymore.

> Drop the nautilus-gksu package. It won't be ported to GNOME 3 and is
    blocking the nautilus 3 transition. Closes: #637325

[http://changelogs.ubuntu.com/changelogs/pool/main/g/gksu/gksu_2.0.2-6ubuntu2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/g/gksu/gksu_2.0.2-6ubuntu2/changelog)

Regards.

---

### Post by sudodus on 2014-05-25
I see. So ***pkexec*** is replacing ***gksu***, but it cannot be run as is, it needs the parameters provided by the alias ***pkx***.

It's not that I'm afraid of aliases, I have 51 of them according to ```
grep ^alias ~/.bashrc|wc -l
``` but it is not convenient for the average user. What should we tell those who intend to use ***gparted*** to prepare for a dual boot system? And how is it implemented via the menu or dash?

Is sudo -H OK?

```
sudo -H gparted
```

---

### Post by zika on 2014-05-25
> **sudodus said:**
> What should we tell those who intend to use ***gparted*** to prepare for a dual boot system? And how is it implemented via the menu or dash?Valid question, this early in development I would not be bothered... Those who embark in testing should be able to figure that themselves...> **sudodus said:**
> Is sudo -H OK?
```
sudo -H gparted
```It should be... See (among others, also) my previous posts about that "issue"... I'll never give up CLI so...
> **Cavsfan said:**
> Is that cheating? [IMG]http://ubuntuforums.org/images/smilies/icon_razz.gif[/IMG]There is no cheating in this game... Everything is legal if it is according to syntax, Debian hierarchy and sanity... This is, as I've asked already at the end of TT testing... My current TT is generated from beated SS the same way, with some adjustments to accomodate syntax and Debian hierarchy... ;)

---

### Post by cariboo on 2014-05-25
Using gparted, isn't a very good example, because if a user starts it from the dash, or Alt-F2, it asks for authentication, at least on Ubuntu and Gnome-Shell, I didn't try the other three derivatives, but I assume they work the same. As for aliases, to stay on topic, I'm not lazy enough to set them up, but I think I found a bug in the aliases section of ~/.bashrc.:

> # Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

on my system there isn't a /usr/share/doc/bash-doc directory.

---

### Post by mc4man on 2014-05-25
gparted currently uses pkexec without issue so no need to use an env or alias. It currently suffers from the GLib-CRITICAL **: Source ID issue but that has been fixed in git
[https://bugzilla.gnome.org/show_bug.cgi?id=729800](https://bugzilla.gnome.org/show_bug.cgi?id=729800)

As far as gksu it is still useful & as long as something uses will be available
(- gdebi has no current intention to use pkexec last I checked

---

### Post by zika on 2014-05-25
> **cariboo907 said:**
> on my system there isn't a /usr/share/doc/bash-doc directory.As far as I know no-one lives on that address for some time... ;) Even that file-name is not taken anymore... ;)
You vere just one line away from the solution... ;)
As I am lazy guy these days to write too much, time is in a kind of shortage, let me just point You to a nice and short recipe: [http://www.stchman.com/alias.html](http://www.stchman.com/alias.html) ... ;) First of many search engine just produced...

---

### Post by sudodus on 2014-05-25
> **zika said:**
> [QUOTE=sudodus;13032889]What should we tell those who intend to use ***gparted***  to prepare for a dual boot system? And how is it implemented via the  menu or dash?Valid question, this early in development I would  not be bothered... Those who embark in testing should be able to figure  that themselves...> **sudodus said:**
> Is sudo -H OK?
```
sudo -H gparted
```It should be... Ses (among others,  also) my previous posts about that "issue"... I'll never give up CLI  so...
> **Cavsfan said:**
> Is that cheating? :razz:There  is no cheating in this game... Everything is legal if it is according  to syntax, Debian hierarchy and sanity... This is, as I've asked already  at the end of TT testing... Ma TT is generated fro SS the same way,  with some adjustments to accomodate syntax and Debian hierarchy... :wink:[/QUOTE]

Thanks for making this clear :-)

---

### Post by Cavsfan on 2014-05-26
> **grahammechanical said:**
> gksudo is not installed by default anymore as it is considered depreciated by the devs and a few days ago some of us found gksu/gksudo to be broken in Utopic.

[http://ubuntuforums.org/showthread.php?t=2225514](http://ubuntuforums.org/showthread.php?t=2225514)

So, my attention came back to pkexec. And then someone mention aliases. And here we are. Not wishing to go off topic and just so we are clear about the future of gksu/gksudo in Ubuntu

[https://answers.launchpad.net/ubuntu/+source/gksu/+question/227275](https://answers.launchpad.net/ubuntu/+source/gksu/+question/227275)





[http://changelogs.ubuntu.com/changelogs/pool/main/g/gksu/gksu_2.0.2-6ubuntu2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/g/gksu/gksu_2.0.2-6ubuntu2/changelog)

Regards.

So you are saying pkexec is going to become the new gksu/gksudo? That is what the second two links appeared to be saying.

I added the policies from the other thread you created for pkexec gedit and nautilus. I rebooted and still got warnings:

```
cavsfan@cavsfan-MS-7529:~$ pkx gedit /etc/fstab

(gedit:1838): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:1838): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

I got the first warning when I made a change and the 2nd one when I saved the file.

```
cavsfan@cavsfan-MS-7529:~$ gksudo gedit /etc/fstab

(gedit:2796): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```

I just got this one warning when I saved the file.

> **zika said:**
> [QUOTE=Cavsfan;13032825]Is that cheating? :razz:
There is no cheating in this game... Everything is legal if it is according to syntax, Debian hierarchy and sanity... This is, as I've asked already at the end of TT testing... My current TT is generated from beated SS the same way, with some adjustments to accomodate syntax and Debian hierarchy... ;)[/QUOTE]

Good to know zika! ;)

---

### Post by zika on 2014-05-26
> **Cavsfan said:**
> Good to know zika! ;)Part You've answered to had (at least) 4 subparts so I do not know which one of those was &#8222;good to know&#8220;... ;)
> **Cavsfan said:**
> I added the policies from the other thread you created for pkexec gedit and nautilus. I rebooted and still got warnings:I think that You should get these warnings, reading documentation...

---

### Post by cariboo on 2014-05-26
> **zika said:**
> As far as I know no-one lives on that address for some time... ;) Even that file-name is not taken anymore... ;)
You vere just one line away from the solution... ;)
As I am lazy guy these days to write too much, time is in a kind of shortage, let me just point You to a nice and short recipe: [http://www.stchman.com/alias.html](http://www.stchman.com/alias.html) ... ;) First of many search engine just produced...

What I was suggesting is that path shouldn't even be there, if it doesn't exist. I know editing ~/.bashrc is not something the targeted user is going to do, but if they try looking for the examples they won't find them, and from what I've seen from many their Google skills seem to not be the best.

Bug *[lpbug]1323455[/lpbug] created.

---

### Post by mc4man on 2014-05-27
It (usr/share/doc/bash-doc/whatever) exists when installed, maybe better to request it (bash-doc) be made a recommend of bash
(size of iso isn't that much of an issue anymore, maybe 2 Mb matters?

---

### Post by Alan F on 2014-05-27
Just to be clear what are the real objections to using, in terminal, for all programs that you wish to run with admin rights .....

sudo -H xxxx

---

### Post by zika on 2014-05-27
> **Alan F said:**
> Just to be clear what are the real objections to using, in terminal, for all programs that you wish to run with admin rights .....

sudo **-H** xxxxTo whom is this question addressed? Did You read (among others, mine too) posts about this (in various threads) in last week or so?
To make things faster: I do not have any objection at all... ;) (Note that H is bolded, just in case... ;))

---

### Post by Alan F on 2014-05-27
> **zika said:**
> To whom is this question addressed? Did You read (among others, mine too) posts about this (in various threads) in last week or so?
To make things faster: I do not have any objection at all... ;) (Note that H is bolded, just in case... ;))

The reason for asking is quite simple. I have always used gksu when required.

There are, currently, issues around using gksu, gksudo, pkexec with Utopic. There seems to be no consistancy in operation of these in Unity Alt+F2, Unity launcher or terminal. Some work, some do not, various error messages are given or not. 

The only consistancy I have found is to use, as you posted, sudo -H in terminal. This works in all cases that I have tried. Yes, there are some error messages but it appears that they can be ignored. I am aware that the use of sudo with graphical apps is deprecated but my understanding is that the use of the -H switch overcomes the main objection by ensuring that it does not overwrite the normal users .config file.

Thus using sudo -H is simple and it works. Is there any other reason NOT to use it?

---

### Post by Cavsfan on 2014-05-27
> **zika said:**
> [QUOTE=Cavsfan;13032825]Is that cheating? :razz:
There is no cheating in this game... Everything is legal if it is  according to syntax, Debian hierarchy and sanity... This is, as I've  asked already at the end of TT testing... My current TT is generated  from beated SS the same way, with some adjustments to accomodate syntax  and Debian hierarchy... :wink:[/QUOTE]

Good to know zika! :wink:

> **zika said:**
> Part You've answered to had (at least) 4 subparts so I do not know which one of those was „good to know“... ;)

Not sure how I could have made it any simpler that that: :wink: However I'll spell it out for you: I meant your response to my question "Is that cheating :p", which also just happens to be the only part you answered. :p

---

### Post by zika on 2014-05-27
> **Cavsfan said:**
> Good to know zika! :wink:



Not sure how I could have made it any simpler that that: :wink: However I'll spell it out for you: I meant your response to my question "Is that cheating :p", which also just happens to be the only part you answered. :pHa,Ha,Ha... ;)

---

### Post by Cavsfan on 2014-05-31
Doesn't everyone have a ~/.bashrc file? Mine is not even marked executable and it works like it should.

Here is the contents of my file: You have to scroll down for the aliases. Not sure you even have to logoff and back on but maybe you do can't remember. 

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

# pkexec alias
alias pkx='pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY $i'

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

### Post by zika on 2014-06-01
> **Cavsfan said:**
> Doesn't everyone have a ~/.bashrc file? Mine is not even marked executable and it works like it should.Why should it be marked as executable?

---

### Post by Cavsfan on 2014-06-01
> **grahammechanical said:**
> This thread is in deference to Zika who recommends using aliases. I have no idea what he is talking about but I found this

[http://www.howtogeek.com/73768/how-to-use-aliases-to-customize-ubuntu-commands/](http://www.howtogeek.com/73768/how-to-use-aliases-to-customize-ubuntu-commands/)

A tutorial even I can understand. I created the file .bash_aliases, [COLOR=#ff0000]ticked it to allow executing[/COLOR] and put this, courtesy of Zika, in it.
```
alias pkx='pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY $i'
```

now pkx gedit will do the work of pkexec gedit. Of course, we first need to have a Polkit policy as well for this to work.

Regards.

> **zika said:**
> Why should it be marked as executable?

It doesn't but see the red in the OP's first post?

---

### Post by matt_symes on 2014-06-01
> **grahammechanical said:**
> This thread is in deference to Zika who recommends using aliases.

I'm a big fan of both aliases and functions myself. Even wrote a simple function (fa below) to search them.

```
matthew-S206:/home/matthew:1 % fa | wc -l
180
matthew-S206:/home/matthew:1 % 

```

---

### Post by zika on 2014-06-01
> **Cavsfan said:**
> It doesn't but see the red in the OP's first post?Mea culpa, and OP's mistake=two mistakes... ;)

---

### Post by Cavsfan on 2014-06-01
> **matt_symes said:**
> I'm a big fan of both aliases and functions myself. Even wrote a simple function (fa below) to search them.

```
matthew-S206:/home/matthew:1 % fa | wc -l
180
matthew-S206:/home/matthew:1 % 

```

I couldn't live without them myself! Especailly for CLI updates, upgrades, dist-upgrades and anything else that is too long to type over and over.

> **zika said:**
> Mea culpa, and OP's mistake=two mistakes... ;)

I made no mistake ;) I didn't make it executable; never have and never will. I know how it works.

---

### Post by zika on 2014-06-01
> **Cavsfan said:**
> I made no mistake ;) I didn't make it executable; never have and never will. I know how it works.O, yes You did, my friend: now You did not read my post well... ;)
I wrote:> **zika said:**
> Mea culpa, and [COLOR=#ff0000]OP's[/COLOR] mistake=two mistakes... :wink:Now we have (at least) three mistakes... ;)

---

### Post by Cavsfan on 2014-06-02
Deleted

---

### Post by Elfy on 2014-06-02
can we please get this thread back ontopic

thank you

---

### Post by zika on 2014-06-02
> **Cavsfan said:**
> Whatever. Why do you always have to be so bellicose zika? If there's anything you can read into something to make it disagreeable you get that job done well. :rolleyes:
Is your life that miserable? :pI'm very sorry but You've totally misunderstood me... I was trying to make a joke on a simple mistake (what I've missed in my reading)...
> **zika said:**
> [COLOR=#ee82ee]Mea culpa[/COLOR], and OP's mistake=two mistakes... [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG] Thank You for all the compliments but, believe me, they are totally undeserved... It might be my bad English that got me into this trouble... I do wish You all the best in Your life from a miserable one (by Your judgement which would be considered very rude (to be very conservative) as much here where I do live now and in many parts of the world that I've had opportunity to live) I have... At least I've learned a new word today and I'm very thankful to You for that... I hope that You'll read my messages above once again and do see that You've made a wrong judgement... All the best...
> **Elfy said:**
> can we please get this thread back ontopic
thank youThis is the first time I've felt need to answer on post like this even after such note from moderator... I'm not sorry because all previous times (being in position of moderator on several places myself) I've picked my tail and stopped when told... This time it was too much... Repetitive ad hominem attacks are not something I will resist to fight back any more... Over&out.

---

### Post by Cavsfan on 2014-06-02
> **Elfy said:**
> can we please get this thread back on topic

thank you

Yes, sorry about that.

Aliases are mucho useful in a CLI. Once someone showed me how to do one they are irreplaceable. Time savers they are. :)

Pardon me zika if I misunderstood your intentions. I didn't know English wasn't your native language. 
My apologies.

---

