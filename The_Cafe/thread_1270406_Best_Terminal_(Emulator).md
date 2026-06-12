---
title: "Best Terminal (Emulator)?"
date: 2009-09-19
forum: The Cafe
---

### Post by rob86 on 2009-09-19
What's the best terminal out there for a linux user? As a new Ubuntu user, I find myself loving the functionality of a command line, but the terminal is so unappealing to look at. Aren't there any with, I don't know, a bit of colour? Not just for aesthetic purposes, but it'd make the information a bit easier to sort through if it wasn't so monochrome , kind of like a programming code editor. Even a background and default font change would be nice, something other than black and grey all the time!

---

### Post by SuperSonic4 on 2009-09-19
I've always just used konsole

---

### Post by hessiess on 2009-09-19
All Linux terminals _can_ display colour, howeaver few CLI programs are written to use it.

---

### Post by kevCast on 2009-09-19
Xfce terminal, using xfce4.

Konsole is good.

For an environment independent terminal, you can't beat urxvt.

If you're a cool guy, twm and xterm.

---

### Post by RiceMonster on 2009-09-19
In KDE, I use Konsole. In GNOME I use GNOME-Terminal. In Xfce and everything else, I use Xfce terminal. There isn't really any advantage to any of them, except xfce terminal doesn't have a lot of dependencies, so it's good for use in lightweight wms, I find.

---

### Post by Bachstelze on 2009-09-19
> **RiceMonster said:**
> There isn't really any advantage to any of them,

I like being able to switch windows in irssi without it switching tabs because some developer thought he would be a smart boy and hardcoded the Alt+n shortcut to "Switch to tab n".

No, I won't give names, you can easily find out which one I'm talking about if you're interested.

---

### Post by dragos240 on 2009-09-19
> **rob86 said:**
> What's the best terminal out there for a linux user? As a new Ubuntu user, I find myself loving the functionality of a command line, but the terminal is so unappealing to look at. Aren't there any with, I don't know, a bit of colour? Not just for aesthetic purposes, but it'd make the information a bit easier to sort through if it wasn't so monochrome , kind of like a programming code editor. Even a background and default font change would be nice, something other than black and grey all the time!

I just use gnome-terminal.

---

### Post by Xbehave on 2009-09-19
What you really want to ask is best shell + profile, IMO bash is a very good shell and with bash-completion and coloring (set it up in your .bashrc or at system level in /etc/bash_profile or something like that) it looks pretty too (and color can help usability too).

AS for the question you asked, i find console marginally better than the gnome terminal because it can be customised quite well (menubars/tab bars).

---

### Post by tjwoosta on 2009-09-19
> **rob86 said:**
> What's the best terminal out there for a linux user? As a new Ubuntu user, I find myself loving the functionality of a command line, but the terminal is so unappealing to look at. Aren't there any with, I don't know, a bit of colour? Not just for aesthetic purposes, but it'd make the information a bit easier to sort through if it wasn't so monochrome , kind of like a programming code editor. Even a background and default font change would be nice, something other than black and grey all the time!

Any terminal emulator can use color. Actually I think default gnome-terminal is probably one of the most customizable and easy to use terminals available. Just right click anywhere inside the terminal and choose profiles then profile preferences and you can change colors transparency fonts and much more with just a few clicks.

As mentioned above some other good easy to use and highly customizable terminals are xfce's terminal and konsole. I personally use xterm, simply because its the lightest weight terminal Ive ever tried, but with xterm you have to edit the ~/.Xdefaults file to change colors and other preferences making it a little less user friendly.

Everything being monochrome like you describe is probably more the programs that you're running then anything. Some programs use color while others dont, thats not the terminal emulators fault.

---

### Post by doorknob60 on 2009-09-19
Just use what comes with your DE (gnome-terminal for Gnome, Konsole for KDE, xfce4-terminal for Xfce, etc.), they all are good. If you use Openbox or something, I also recommend using the xfce-terminal, it's just as good as the big boys (Konsole and gnome-terminal) but it doesn't have many dependencies.

---

### Post by littlemog on 2009-09-19
gnome terminal works for me. tried another one called guake but didn't like it cos some text weren't rendered properly.

---

### Post by PurposeOfReason on 2009-09-19
urxvt + zsh 

Because real tab completion is cool.

---

### Post by RiceMonster on 2009-09-19
> **Bachstelze said:**
> I like being able to switch windows in irssi without it switching tabs because some developer thought he would be a smart boy and hardcoded the Alt+n shortcut to "Switch to tab n".

No, I won't give names, you can easily find out which one I'm talking about if you're interested.

Yeah, that's annoying. I forgot about that. If you don't have any tabs open, you still have to type /window 1 to get to it.

---

### Post by Namtabmai on 2009-09-19
> **Bachstelze said:**
> I like being able to switch windows in irssi without it switching tabs because some developer thought he would be a smart boy and hardcoded the Alt+n shortcut to "Switch to tab n".

On a similar note I only ask for 2 things from a terminal program,
1) Transparency
2) Always show tab bar.

Every GTK terminal apps seemed to fall on the second requirement.

I just found this [bug report](https://bugzilla.gnome.org/show_bug.cgi?id=78776) for Gnome Terminal regarding implementing a "Always show tabs" option. It's still open and was originally submitted 7 years ago. :(

When I was using Gnome Terminal I maintained my own patch to hard code this functionality.

---

### Post by PurposeOfReason on 2009-09-19
> **Namtabmai said:**
> On a similar note I only ask for 2 things from a terminal program,
1) Transparency
2) Always show tab bar.

Every GTK terminal apps seemed to fall on the second requirement.

I just found this [bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=78776") for Gnome Terminal regarding implementing a "Always show tabs" option. It's still open and was originally submitted 7 years ago. :(

When I was using Gnome Terminal I maintained my own patch to hard code this functionality.
Why not just use screen?

---

### Post by Namtabmai on 2009-09-19
> **PurposeOfReason said:**
> Why not just use screen?

Valid question, but to be honest switching between different screens isn't as fluid as switching tabs.

---

### Post by calrogman on 2009-09-19
Terminator, it's based on GNOME Terminal, but it allows you to split the window into multiple terminals, very useful for [multitasking]("http://www.aircrack-ng.org/").

---

### Post by lovinglinux on 2009-09-19
I use gnome-terminal for regular stuff, tilda (better than guake) or the awn terminal applet for easy access and the screenlet terminal in a widget layer for monitoring logs.

---

### Post by RATM_Owns on 2009-09-19
> **PurposeOfReason said:**
> urxvt + zsh 

Because real tab completion is cool.
Exactly what I would've said.

---

### Post by Barrucadu on 2009-09-19
urxvtd/urxvtc - why run many terminals when you can have one daemon? :p

---

### Post by schauerlich on 2009-09-19
> **Bachstelze said:**
> I like being able to switch windows in irssi without it switching tabs because some developer thought he would be a smart boy and hardcoded the Alt+n shortcut to "Switch to tab n".

No, I won't give names, you can easily find out which one I'm talking about if you're interested.

wmii does that. You can change it in wmiirc if I recall correctly. I just use esc-n because on OS X, alt+char is how you do special characters.

---

### Post by MikeTheC on 2009-09-19
I use this one and it serves my (fairly minimal) needs just fine:

[img]http://img43.imageshack.us/img43/893/terminaldotapp.png[/img]

---

### Post by schauerlich on 2009-09-19
> **MikeTheC said:**
> I use this one and it serves my (fairly minimal) needs just fine:

[http://img43.imageshack.us/img43/893/terminaldotapp.png](http://img43.imageshack.us/img43/893/terminaldotapp.png)

+1. Although there are some minor things that get annoying, such as not handling colors the same as most other terminals. It seems like they've changed that in 10.6, but only when run in 64-bit mode.

---

### Post by Bachstelze on 2009-09-19
It really doesn't play nice with irssi either, though.

BTW, this is one of the reasons why, of the 3 OSes installed on my MBP, OSX is by far the one I boot less often.

---

### Post by red_Marvin on 2009-09-19
Usually I keep to what the de provides, however if I, as I am now, do non trun a de (in the traditional sense at least) I stay with xterm, .Xdefaults is easy enough to set up.

---

### Post by kk0sse54 on 2009-09-19
> **PurposeOfReason said:**
> urxvt + zsh 

Because real tab completion is cool.

+1, although the xfce4 terminal is pretty nice

---

### Post by tcoffeep on 2009-09-19
urxvt is what i use.

---

### Post by rob86 on 2009-09-19
Lots of replies! 

So I was looking in the wrong place by wanting to change terminals, I should be customizing the bash shell? I saw this screenshot of someones terminal and it was a bit colorized, this part:

user@computername:$ 

was in different colours. This is part of the shell and can be edited to be different colours? How do I do that? Edit .bashrc ? bash_profile? 

How do I put colours in, anyway? You know, something like, $ echo this is RED , how would I colourize the RED.

---

### Post by tcoffeep on 2009-09-19
Well, here's my line (in my .bashrc):

```

[ -z "$PS1" ] && return
PS1='\[\033[0;31m\][\@]\[\033[0;m\][\[\033[0;34m\]\u@\[\033[0;33m\]\h\[\033[0;m\] \w]\[\033[0;32m\]\$ '

```

Here's a link to see what it looks like : [http://i35.tinypic.com/358rzh1.png](http://i35.tinypic.com/358rzh1.png)

---

### Post by rob86 on 2009-09-19
> **tcoffeep said:**
> Well, here's my line (in my .bashrc):

```

[ -z "$PS1" ] && return
PS1='\[\033[0;31m\][\@]\[\033[0;m\][\[\033[0;34m\]\u@\[\033[0;33m\]\h\[\033[0;m\] \w]\[\033[0;32m\]\$ '

```

Here's a link to see what it looks like : [http://i35.tinypic.com/358rzh1.png](http://i35.tinypic.com/358rzh1.png)

That's what I was talking about, I didn't know you had to edit .bashrc for that. How are you doing the colours? The codes a bunch of brackets and slashes, it's kind of hard to decypher!

---

### Post by tcoffeep on 2009-09-19
> **rob86 said:**
> That's what I was talking about, I didn't know you had to edit .bashrc for that. How are you doing the colours? The codes a bunch of brackets and slashes, it's kind of hard to decypher!

the 0;34 and stuff :

[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html)

---

### Post by Xbehave on 2009-09-19
The above link covers what you want to know, but for another link try [arch-wiki]("http://wiki.archlinux.org/index.php/Color_Bash_Prompt") (has a bit more info) or [this]("http://maketecheasier.com/8-useful-and-interesting-bash-prompts/2009/09/04") (has a few other tricks)
Apart from the prompt, several utilities can be made colorful, e.g you can add this to ~/.bashrc
```
alias ls="ls --color=auto"
```
On my fedora install this is done by /etc/profile.d/colorls.sh (attached)
[colorize grep]("http://www.debian-administration.org/article/grep_highlighting_matches_in_color")
```
GREP_OPTIONS='--color=auto'
```
allow color through less
```
LESS=-R
```
I remember setting up quite an impressive .bashrc when i used gentoo/arch for a day so there is much more you can do,

---

### Post by Exodist on 2009-09-19
In Gnome I use Gnome Term, in everything else I use Eterm.

---

### Post by tcoffeep on 2009-09-20
if you're interested, here's my .bashrc :

```

[ -z "$PS1" ] && return
PS1='\[\033[0;31m\][\@]\[\033[0;m\][\[\033[0;34m\]\u@\[\033[0;33m\]\h\[\033[0;m\] \w]\[\033[0;32m\]\$ '


# alias ############################################

alias ls='ls --color=auto'
eval `dircolors -b`
alias sd='sudo shutdown -h now'
alias c='clear'
alias e='exit'
alias ht='htop'
alias rt='rtorrent'
alias ex='extract'
alias screensaver='yes "$(seq 1 255)" | while read i; do printf "\x1b[48;5;${i}m\n"; sleep .01; done'

# extract ##########################################

extract () {
if [ -f $1 ]; then
	case $1 in
             *.tar.bz2)   tar xjf $1	;;
             *.tar.gz)    tar xzf $1	;;
             *.bz2)       bunzip2 $1	;;
             *.rar)       unrar e $1	;;
             *.gz)        gunzip $1		;;
             *.tar)       tar xf $1		;;
             *.tbz2)      tar xjf $1	;;
             *.tgz)       tar xzf $1	;;
             *.zip)       unzip $1		;;
             *.Z)         uncompress $1	;;
             *.7z)        7z x $1		;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
	esac
else
	echo "'$1' is not a valid file"
fi
}

# bash completion ##################################

if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# other ############################################

alias update='sudo eix-sync && sudo emerge -fuDNv @system @world && sudo emerge -uDNv @system @world && sudo emerge @preserved-rebuild && sudo env-update && source /etc/profile && sudo revdep-rebuild'

```

Note : You can ignore the update alias, as that's quite non-ubuntu :D

---

### Post by Renée Jade on 2009-09-20
I'm on GNOME and I use three different ones. Tilda starts on startup and stays open the whole time - it's cool coz you can show/hide it with one keystroke. I use terminator for writing code coz you can split up for vim + compiling + debugger, or whatever you need. And I use gnome-terminal if I need a little temporary terminal window. All of them are mapped to an Alt + <letter> command and I use a few simple aliases to make life a bit easier:
  
 ```
 
  alias adal='vim ~/.bash_aliases'
  
  alias mygcc='gcc -std=c99 -Wall -Werror -pedantic'
   
  alias c='clear'
  alias la='ls -a'
  alias lal='ls -a -l -h'
  
 alias gt='gnome-terminal'
 alias go='gnome-open'
  
 alias ff='firefox'
 alias sw='swiftweasel3'
 alias tb='thunderbird' 
 alias goo='gnome-open http://www.google.com/'
  
 alias p='PS1="\[\033[1;34m\]\w \$ \[\033[0m\]";clear'
 alias up='PS1="\[\033[1;34m\][\d \t] \[\033[0;36m\]\# \[\033[1;34m\]Renée: \w \$ \[\033[0m\]";clear'  

```:)

---

