---
title: "HOWTO: Customizing bash prompt"
date: 2007-11-16
forum: Tutorials
---

### Post by MiCovran on 2007-11-16
The information in this thread has been moved to [https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2012407](http://ubuntuforums.org/showthread.php?t=2012407)

Thread closed.


If you have difficulties using the terminal because the prompt isn't visible enough or you would simply like it to look nicer, this howto is for you. It should work on any distribution if you use bash shell, just don't expect your existing .bashrc file to look like Ubuntu's. I've attached a before and after picture of my terminal as an example of what you could do.

So let's get started. Fire up your terminal and stay in your home directory.


[SIZE="3"]**1. Backup**[/SIZE]

First, let's backup our .bashrc file since we're about to make some changes to it:```
cp .bashrc .bashrc-backup
```
The .bashrc file tells bash what to do when terminal is started, including how to show prompt.


[SIZE="3"]**2. Preparing the .bashrc**[/SIZE]

Use your favorite text editor to edit the original .bashrc file, eg.:```
gedit .bashrc
```

Find this part:```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
```

Bash reads PS1 variable to see how to show primary prompt and PS2 for a secondary prompt (used when writing multi-line commands). In this "if" block, the first PS1 is a prompt which will be shown when color is turned on, and the second one (after "else") is being used when no color is desired. As you can see, color codes are quite tiring to use. Imagine you have to write things like \[\033[01;32m\] all over again. It's horrible. Fortunetly, bash lets us define variables that make our life easier. So paste this code above that "if" block:
```
# ANSI color codes
RS="\[\033[0m\]"    # reset
HC="\[\033[1m\]"    # hicolor
UL="\[\033[4m\]"    # underline
INV="\[\033[7m\]"   # inverse background and foreground
FBLK="\[\033[30m\]" # foreground black
FRED="\[\033[31m\]" # foreground red
FGRN="\[\033[32m\]" # foreground green
FYEL="\[\033[33m\]" # foreground yellow
FBLE="\[\033[34m\]" # foreground blue
FMAG="\[\033[35m\]" # foreground magenta
FCYN="\[\033[36m\]" # foreground cyan
FWHT="\[\033[37m\]" # foreground white
BBLK="\[\033[40m\]" # background black
BRED="\[\033[41m\]" # background red
BGRN="\[\033[42m\]" # background green
BYEL="\[\033[43m\]" # background yellow
BBLE="\[\033[44m\]" # background blue
BMAG="\[\033[45m\]" # background magenta
BCYN="\[\033[46m\]" # background cyan
BWHT="\[\033[47m\]" # background white
```
Now you don't have to write all that ANSI code over and over again. For instance, you can just use $FBLE to set foreground (text) to blue, instead of \[\033[34m\].


[SIZE="3"]**3. Setting the prompt without color**[/SIZE]

Now that you have this prepared, you can design your own prompt. Let's start with the one without color for simplicity (it's the one **just below the "else" line**). First, comment in the default PS1 that's already there to ignore it (**put a #** in front of the line), and then define your own PS1 and PS2 just below it.

I'll explain how I did mine. This is how they are defined:
```
PS1="[ ${debian_chroot:+($debian_chroot)}\u: \w ]\\$ "
PS2="> "
```
Secondary prompt is simple. It shows just ***>***.
However, the primary one is a little bit more complicated. It contains some special characters for additional info about a session. You can find a list of those special characters in bash's man page under section PROMPTING:```
man bash
```
I used ***\u*** (username), ***\w*** (current working directory) and, of course, ***\\$*** (the $ or # symbol, depending on your privileges). You don't need to worry about what "${debian_chroot:+($debian_chroot)}" means, just always copy-paste it in front of "/u". So my primary prompt will be shown like this (when I'm in my home directory): **[ penguin: ~ ]$**


[SIZE="3"]**4. Setting the prompt with color**[/SIZE]

If you want to use a colored prompt, you must find the line in your .bashrc that says **#force_color_prompt=yes** and **remove #** from it. This means that bash will from now on prefer what is defined **above the "else" line**. **Comment in** the old PS1 that's located there just like you did before, and then **copy-paste your PS1 and PS2** from below "else" (colorless versions). You now have the base layout and you just need to add some color to it.

The simplest way to deal with it is by inserting variables from that big chunk of code you pasted before. First put a ***$RS*** at the end of both PS1 and PS2 so you don't change formating of other text in the terminal. All ANSI color codes change only the text behind them, and you can only turn off ***$HC***, ***$UL*** and ***$INV*** codes by using ***$RS***. Here's how I added color to my prompt:
```
PS1="$HC$FYEL[ $FBLE${debian_chroot:+($debian_chroot)}\u$FYEL: $FBLE\w $FYEL]\\$ $RS"
PS2="$HC$FYEL> $RS"
```

I used hicolor at the beginning and left it on until that last ***$RS***. Then I just switched between colors I wanted (blue and yellow). So I got this prompt: **[COLOR="Yellow"][ [COLOR="RoyalBlue"]penguin[/COLOR]: [COLOR="RoyalBlue"]~[/COLOR] ]$[/COLOR]**

When you want to see what you've done, just save changes to .bashrc file, start another terminal and enjoy your new prompt. If you want to see how your secondary prompt looks like, enter just ***\*** as a command in the terminal.

_Tip:_ If you're using gnome-terminal and want to fine tune your color selection, right click the terminal, choose ***Edit Current Profile...*** and go to ***Colors*** tab. Note that these changes effect the complete terminal, not just prompt. I don't know how to do this for any other terminal emulators, I'm a GNOME man.


[SIZE="3"]**5. Reverting to old settings**[/SIZE]

If for some reason you wish to return the old prompt or if you broke your .bashrc, the easiest way is to just recover old .bashrc file you backed up. Run a terminal and use:```
cp .bashrc-backup .bashrc
```
Voila! Everything is back to normal.


[SIZE="3"]**For the end**[/SIZE]

I tried to make this howto as simple to understand as I could. If you don't understand or don't know how to do something, if you have a suggestion or think I made a mistake somewhere, feel free to contact me. This is the first howto I wrote so any feedback is appreciated.
This is just my small way to say thanks to people in this forum who helped me a lot, so ... thanks. :)

---

### Post by tzulberti on 2007-11-16
Great How-to.... I will try to customize it...

Thanks.

---

### Post by mfolnovic on 2007-11-17
this is great, when I get home, I'll try it :D

---

### Post by MiCovran on 2007-11-17
[QUOTE='tzulberti']I will try to customize it...[/QUOTE]
[QUOTE='mfolnovic']when I get home, I'll try it[/QUOTE]
Let me know how it worked. :popcorn:

BTW, I felt like section 3 - setting the prompt - wasn't clear enough for people with no scripting or programming experience, so I rewrote it in a more "step-by-step" approach.

---

### Post by Trezker on 2008-04-15
Good stuff, now I can finally see where my latest compile results start.

---

### Post by MiCovran on 2008-04-20
> **Trezker said:**
> Good stuff, now I can finally see where my latest compile results start.

That's the primary reason why I got into it too. ;)

---

### Post by uvdevnull on 2009-01-12
Thanks for that MiCovran, very helpful!

Just a small correction... The ANSI color variables must be defined prior to the prompts that use them, otherwise it doesn't work, at least for me.  So they can't be pasted at the end of file, but anywhere before the first attempted usage.

Thanks again,
uvdevnull

---

### Post by h711 on 2009-01-18
:P wat a great tutorial..do u have any customization??..plz share..

---

### Post by binbash on 2009-01-18
Great howto, thanks!

---

### Post by MiCovran on 2009-01-21
> **uvdevnull said:**
> The ANSI color variables must be defined prior to the prompts that use them

I did write what you told in the howto. I've put it in bold now so it will be easier to spot.

> **h711 said:**
> :P wat a great tutorial..do u have any customization??..plz share..

It's actually quite simple to customize it, you just have to play a little bit.

For changing the colour of the prompt just play with all the different variables you pasted into your .bashrc file (it's that big chunk of code from the howto). For instance, if you want to change colour of text in some part of the prompt to green, first find the "foreground green" line. There you'll see that the variable name is "FGRN" (on the beginning of the line). Then just add "$FGRN" before the text you want to change (in the "PS1" variable).

However, if you want to change contents of the prompt, then take a look at the bash man file (also available [*at this page*]("http://manpages.ubuntu.com/manpages/intrepid/en/man1/bash.1.html")):```
man bash
```
Find the "PROMPTING" section and there you'll see all the features that your prompt can have. When you find what you like, just put it in the "PS1" variable in your .bashrc file. So if you would like your prompt to show time, you could just add "\t" to the beginning of the "PS1" variable. And if you want to add some text or some brackets (or basically anything), you can just type it as it is.

As an example, **PS1="$FGRN(My first bash prompt) \t $RS"** would simply show "(My first bash prompt)" and current time after it. All in green, of course. ;)

---

### Post by uvdevnull on 2009-01-21
> **MiCovran said:**
> I did write what you told in the howto. I've put it in bold now so it will be easier to spot.


I think what perhaps confused me was the line:

```
(preferably below the text you just commented in or at the end of file)
```

But anyway, thanks for the tut!

---

### Post by MiCovran on 2009-01-22
Yeah, I see... Well, I guess you can put it at the end of file, as long as you put the PS1 at the end of file too. :D

---

### Post by Dirjel on 2009-05-11
Is it possible to have a different prompt while you're in a certain directory?

I want it to not show the ~ while I'm in my home directory, and only show the \w when I'm in a non-default directory.

Here's what I have:
```
if [ \w = /home/dirjel/ ]; then
    PS1="\[\033[1m\][Hello, world.] >\[\033[0m\] "
else
    PS1="\[\033[1m\][Hello, world.]\[\033[0m\] \w \[\033[1m\]>\[\033[0m\] "
fi
```

Is this impossible, or am I merely *doing it wrong?*

---

### Post by MiCovran on 2009-05-11
You could use```
if [ `pwd` = ~ ]; then
```but this will not solve your idea. The .bashrc file is executed only once when starting a new bash shell. So you'll always have a prompt without \w, since you always start in your home directory.

---

### Post by Dirjel on 2009-05-11
If I put the if/then expression inside the prompt using these:
```
\[     begin a sequence of non-printing characters, which could be used to embed a terminal control sequence into the prompt
\]     end a sequence of non-printing characters

```
Would that work?

---

### Post by monsterstack on 2009-05-11
> **Dirjel said:**
> Is it possible to have a different prompt while you're in a certain directory?

I want it to not show the ~ while I'm in my home directory, and only show the \w when I'm in a non-default directory.

Here's what I have:
```
if [ \w = /home/dirjel/ ]; then
    PS1="\[\033[1m\][Hello, world.] >\[\033[0m\] "
else
    PS1="\[\033[1m\][Hello, world.]\[\033[0m\] \w \[\033[1m\]>\[\033[0m\] "
fi
```

Is this impossible, or am I merely *doing it wrong?*

I don't know if it's the best way to go about doing it, but you *could* set up an alias function for the "cd" command, which would check to see if the folder you pass to "cd" is in your home or not and edit the prompt accordingly. Only trouble is you'd have to name it something other than "cd" in order to work properly. Here's a quick and dirty hash job I just tried (albeit with echo commands),

```

function cb()
    { 
    cd $@; 
    if [[ $(pwd) =~ "/home/dirjel" ]]; then
       PS1="\[\033[1m\][Hello, world.] >\[\033[0m\] "
    else
       PS1="\[\033[1m\][Hello, world.]\[\033[0m\] \w \[\033[1m\]>\[\033[0m\] ";
       fi;
    }
```

Put that bit of code in your .basrc or just paste it into the terminal and then try and use the "cb" command. Does that work for you?

EDIT: works for me (colours won't as my bashrc is set-up differently). I really should add some more colour.

[IMG]http://i717.photobucket.com/albums/ww177/stuffandstuffand/screenie1.png[/IMG]

I put a link to this thread on my own bash howto. :)

---

### Post by Dirjel on 2009-05-11
It works... kind of.  If I'm in my home directory, it doesn't print the ~.  However, if I'm in any subdirectory of my home folder, it *still* doesn't show the \w bit.

---

### Post by monsterstack on 2009-05-11
Oh sorry, I must have misread you.

```
if [[ $(pwd) =~ "/home/dirjel" ]];
```

will match your home directory and *all* sub-directories. I think you need to change it to something more like,
```

function cb()
    { 
    cd $@; 
    if [[ $(pwd) = "/home/dirjel" ]]; then
       PS1="\[\033[1m\][Hello, world.] >\[\033[0m\] "
    else
       PS1="\[\033[1m\][Hello, world.]\[\033[0m\] \w \[\033[1m\]>\[\033[0m\] ";
       fi;
    }
```

Any better?

---

### Post by Dirjel on 2009-05-12
Hm.  This is interesting.  Thanks, I think I'll use the command "go," as it makes more sense than "cb," and isn't being used for anything else.

So, there's no way to make the cd command do that?  I was trying to use the bash aliases "cd" that I type in different from the "cd" that is used in the bash function.

I don't really know the difference between a function and an alias, though, apart from an alias is only recognized if it's the first term in a command.  I think.

It *seems* like if the alias had a higher priority than the function, it should work, right?

---

### Post by monsterstack on 2009-05-12
If that bit of script was simple enough to be an alias, you could rename it "cd" no problem. As a function, however, you most certainly cannot name it "cd", because it already has "cd" inside itself!! Let me try and explain what I mean:

Aliases just replace strings. As such, they can't cope with super long, tangled up commands with ifs and loops and such. You're right in saying they can only cope with a couple of arguments. They're only meant for simple things. But the fact that all they do is replace strings is the reason why you can have aliases such as "ls='ls -l'". It takes the "ls" and just replaces it with "ls -l' with no further action taken.

Functions work just the same as shell scripts, really. I guess they're just a little more convenient in that you can bash them out right there in the shell. Functions can be as long and as complicated as you like. That's the way you should think about that little script there. It's an application in its own right that just so happens to use "cd". Naming your application "cd" is bad, because the "cd" inside your application will try to execute your application all over again. Infinite recursion!

Here's an example:
```
function ever_ever () { echo hello; ever_ever; }
```
If you tried to run this, all it would do is "echo hello" forever and ever. Even ctrl+c wouldn't be able to stop it.

I guess having the function in front of the alias might just work.
```
function cb () { cd $@; *and so on*; }
alias cd='cb'
```
In that order. Seems to work okay for me.

---

### Post by Dirjel on 2009-05-12
> **monsterstack said:**
> I guess having the function in front of the alias might just work.
```
function cb () { cd $@; *and so on*; }
alias cd='cb'
```
In that order. Seems to work okay for me.

Ah ha.  I understood the infinite recursion bit, but I didn't see any reason that alias cd='cb didn't work after the function was in place.

I had the alias in .bash_aliases, though, and not directly in the .bashrc file.

This is perfect.  Thanks a ton.

---

### Post by MiCovran on 2009-05-13
Sorry for being absent for a little while.

I must say I really love monsterstack's solution:
```
function cb () { cd $@; and so on; }
alias cd='cb'
```

It could practically be used to customize any command. It's just great!

---

### Post by netimen on 2009-05-16
I'm not sure what lines should I comment for deleting old prompt. Here is my .bashrc &#8212; sorry for large post.

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples
LANG="en_US.utf8"
LANGUAGE="en_US.utf8"
LC_ALL="en_US.utf8"

export LANG
export LANGUAGE
export LC_ALL
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

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

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

```

---

### Post by MiCovran on 2009-05-16
I don't actually use Ubuntu anymore, so I'll have to ask: Is this a .bashrc from a new Ubuntu release? If it is, then it seems like it has been modified and I'll have to update the howto.

For now let's just say that you can uncomment the **#force_colored_prompt=yes** line (remove the **#**) and paste the colour codes from the howto under that line. Now you can simply modify PS1 defined just under **if [ "$color_prompt" = yes ]; then** to suit your needs.

---

### Post by netimen on 2009-05-16
> **MiCovran said:**
> I don't actually use Ubuntu anymore, so I'll have to ask: Is this a .bashrc from a new Ubuntu release? If it is, then it seems like it has been modified and I'll have to update the howto.

For now let's just say that you can uncomment the **#force_colored_prompt=yes** line (remove the **#**) and paste the colour codes from the howto under that line. Now you can simply modify PS1 defined just under **if [ "$color_prompt" = yes ]; then** to suit your needs.
Thanks! This is .bashrc from 8.10 release

---

### Post by MiCovran on 2009-05-16
Since it changes with releases, could someone please post the one from 9.04 so I can update the howto?

---

### Post by monsterstack on 2009-05-17
> **netimen said:**
> I'm not sure what lines should I comment for deleting old prompt. Here is my .bashrc — sorry for large post.

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples
LANG="en_US.utf8"
LANGUAGE="en_US.utf8"
LC_ALL="en_US.utf8"

export LANG
export LANGUAGE
export LC_ALL
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
    [COLOR="Red"]PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '[/COLOR]
else
    [COLOR="Red"]PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '[/COLOR]
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

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

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

```

The first one is the prompt when you are using a colour terminal. The second one is for when you don't have access to a colour terminal, for whatever reason. Comment out the first one and replace it with whatever your heart desires. Hope this helps. :)

---

### Post by Dirjel on 2009-05-17
> **MiCovran said:**
> Since it changes with releases, could someone please post the one from 9.04 so I can update the howto?

The part that you need to comment is the same in the 8.10 and 9.04, but here's the new .bashrc file.
```
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
if [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
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
```

---

### Post by kthxbai2u on 2009-05-18
kthx <3 you for make his terminal sexy :D

---

### Post by MiCovran on 2009-05-18
Thanks Dirjel. I updated the howto. I'm just worried that maybe I over complicated it a bit. Did I?

---

### Post by Dirjel on 2009-05-18
Uh, yeah, it looks kinda' over-complicated.  Of course, it's almost 6AM, and I haven't gone to bed yet XD

I'll look it over when I wake up, and see if I can maybe help edit a bit...?

---

### Post by Dirjel on 2009-05-20
It actually looks pretty good, IMO.  I dunno' if you edited it again, or if I was just tired when I read through it last time.  You did a really good job explaining everything.

Thanks a lot for this how-to.  And thanks a lot to Monsterstack for coming up with a solution for my variable command line problem ^_^

---

### Post by Dirjel on 2009-07-24
I've done some more work on my bash prompt.  Now, in addition to hiding the current working directory when it is merely "~", my bash prompt also changes to reflect whether or not my screensaver is enabled (and thus whether or not it will lock if I leave it unattended).  I've attached a screenshot to show what I mean.

Here is the code for it:
```
function gsc {
if pidof "gnome-screensaver-command"; then
     killall gnome-screensaver-command > /dev/null ;
	if pidof "gnome-screensaver-command"; then
		if [[ $(pwd) = "/home/dirjel" ]]; then
   		   PS1="\[\033[31m\]\[\033[1m\][The screensaver is inactive!] >\[\033[0m\] "
   		else
   		   PS1="\[\033[31m\]\[\033[1m\][The screensaver is inactive!]\[\033[0m\] (\w) \[\033[1m\]>\[\033[0m\] ";
   		   fi;
   	else
   		if [[ $(pwd) = "/home/dirjel" ]]; then
   		   PS1="\[\033[1m\][Hello, world.] >\[\033[0m\] "
   		else
   		   PS1="\[\033[1m\][You are here:\[\033[0m\] (\w) \[\033[1m\]] >\[\033[0m\] ";
   		   fi;
	fi;
else
     gnome-screensaver-command -i & > /dev/null
   	if pidof "gnome-screensaver-command"; then
		if [[ $(pwd) = "/home/dirjel" ]]; then
   		   PS1="\[\033[31m\]\[\033[1m\][The screensaver is inactive!] >\[\033[0m\] "
   		else
   		   PS1="\[\033[31m\]\[\033[1m\][The screensaver is inactive!]\[\033[0m\] (\w) \[\033[1m\]>\[\033[0m\] ";
   		   fi;
   	else
   		if [[ $(pwd) = "/home/dirjel" ]]; then
   		   PS1="\[\033[1m\][Hello, world.] >\[\033[0m\] "
   		else
   		   PS1="\[\033[1m\][You are here:\[\033[0m\] (\w) \[\033[1m\]] >\[\033[0m\] ";
   		   fi;
   	fi;
fi; }

function asdfjklzzz()
   {
   cd $@;
   if pidof "gnome-screensaver-command"; then
	if [[ $(pwd) = "/home/dirjel" ]]; then
   	   PS1="\[\033[31m\]\[\033[1m\][The screensaver is inactive!] >\[\033[0m\] "
   	else
   	   PS1="\[\033[31m\]\[\033[1m\][The screensaver is inactive!]\[\033[0m\] (\w) \[\033[1m\]>\[\033[0m\] ";
   	   fi;
   else
   	if [[ $(pwd) = "/home/dirjel" ]]; then
   	   PS1="\[\033[1m\][Hello, world.] >\[\033[0m\] "
   	else
   	   PS1="\[\033[1m\][You are here:\[\033[0m\] (\w) \[\033[1m\]] >\[\033[0m\] ";
   	   fi;
   fi;
   }
alias cd='asdfjklzzz'
```
I'm sure there is a cleaner way to write this code, but I'm still a novice at any kind of scripting, so I'm quite proud that it works at all.

---

### Post by ferrisxb9r on 2009-09-02
Here's one to stump you then, how do you alter the colours for the root prompt?  Where is the .bashrc (or .bash_profile) for root kept?

So if I log in as root, I'll have (for example) all text in RED.

Because as it stands, this howto only works for the user (~/.bashrc), not root.  I'd really like a very visual deterrent for any root logins.

(I don't need help with the colourations or customization, just the location of root@ .bashrc/PS1 line.  ;)  )

Thanks in advance!

---

### Post by Dirjel on 2009-09-03
It looks like the file you want is /etc/bash.bashrc

That's what it says, anyway:
```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

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
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
		else
		   return 127
		fi
	}
fi
```
You'll probably want to do something like if $USER = root, then [insert red prompt here].

It's been a while since I've messed with this, but it should work.

---

### Post by Dirjel on 2009-09-03
This is the proper code.
```
if [ "$USER" == "root" ]; then
   PS1="\[\033[31m\]\[\033[1m\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$\[\033[0m\]"
else
   PS1="${debian_chroot:+($debian_chroot)}\u@\h:\w\$"
fi

```
I tried it a few times with my ~/.bashrc.  Also, I think the file is /etc/profile.  I'MMA' TRY IT.

---

### Post by Dirjel on 2009-09-03
Alright, it's done.  This is my /etc/profile file.  I'd recommend backing up the original one, as, in all honesty, I have no idea what I'm doing, and I'm essentially playing with fire.  Do it at your own risk.

...It looks pretty safe to me, though.
```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
     if [ "$USER" == "root" ]; then
       PS1="\[\033[31m\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$\[\033[0m\] "
     else
       PS1="${debian_chroot:+($debian_chroot)}\u@\h:\w\$ "
     fi
#    if [ -f /etc/bash.bashrc ]; then
#	. /etc/bash.bashrc
#    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022
```

---

### Post by MiCovran on 2009-09-03
Looks like Dirjel saves the day. Though I would use that code in my user's .bashrc and in /root/.bashrc (in case you actually log in as root at startup or use "su -").

But it's just me. I prefer to avoid system-wide configurations. Still, it is perfectly safe to edit /etc/profile or /etc/bash.bashrc like that, I don't see anything wrong with it.

Great idea and great solution.

---

### Post by slakkie on 2009-09-03
```

set_ps1() {
  local NONE="\[\033[0m\]"    # unsets color to term's fg color
                                                               
  # regular colors                                             
  local K="\[\033[0;30m\]"    # black                          
  local R="\[\033[0;31m\]"    # red                            
  local G="\[\033[0;32m\]"    # green                          
  local Y="\[\033[0;33m\]"    # yellow                         
  local B="\[\033[0;34m\]"    # blue                           
  local M="\[\033[0;35m\]"    # magenta                        
  local C="\[\033[0;36m\]"    # cyan                           
  local W="\[\033[0;37m\]"    # white                          
                                                               
  # empahsized (bolded) colors
  local EMK="\[\033[1;30m\]"
  local EMR="\[\033[1;31m\]"
  local EMG="\[\033[1;32m\]"
  local EMY="\[\033[1;33m\]"
  local EMB="\[\033[1;34m\]"
  local EMM="\[\033[1;35m\]"
  local EMC="\[\033[1;36m\]"
  local EMW="\[\033[1;37m\]"

  # background colors
  local BGK="\[\033[40m\]"
  local BGR="\[\033[41m\]"
  local BGG="\[\033[42m\]"
  local BGY="\[\033[43m\]"
  local BGB="\[\033[44m\]"
  local BGM="\[\033[45m\]"
  local BGC="\[\033[46m\]"
  local BGW="\[\033[47m\]"

  # without colors: PS1="[\u@\h \${NEW_PWD}]\\$ "
  # extra backslash in front of \$ to make bash colorize the prompt
  cur_tty="$(tty)" ; cur_tty="${cur_tty:5}"   # The tty we are working on
  last_exit="\$?"          # Exit code of the command executed from the prompt..
  if [ $UID -eq 0 ] ; then # Check for root
    UBC=$BGB
    UC=$EMR
    TERM_STRING='#'
  else # Otherwise..
    UBC=$BGB
    UC=$EMG
    TERM_STRING='$'
  fi
  export PS1="${UBC}${EMW}\t $cur_tty $last_exit${NONE} ${UC}\u@\h:\w${NONE}${TERM_STRING} "
}

```

Hi, maybe add it to the howto, this is my simple PS1 for bash. Changes colors when I am root, normal is green, root is red.. 
See the image [here](http://opperschaap.net/~wesleys/bash_ps1_colors.png)

---

### Post by marako on 2009-09-03
Thanks for the tutorial!

This seems like one of those things that you wouldt be able to keep in your head to well... needing it written down somewhere :D

---

### Post by thatvistunna on 2009-09-13
I must say, this is my fave bash prompt tutorial since I can copy paste the color definitions.  How do you bookmark these things in your account?  I always have trouble finding it.

---

### Post by skriv on 2010-07-14
Just wanted to say thanks.  This post was really helpful and easy to follow.:popcorn:

---

### Post by makos124 on 2010-12-28
Thanks a lot, this tutorial helped. I didn't read the thread, but I have a little info for you: I needed to change the color codes to something like this "\[033[0;32m\]" - I needed to add the "0;" part, otherwise the colors wouldn't work. Still, it's a great tutorial and it helped me.

---

### Post by Vermind on 2010-12-30
Hi,
I wanted to share my very convoluted PROMPT_COMMAND for anyone interested:
```
# change color on unsuccessful execution,
# show bash history line number (for !num exec) and color prompt

# dark red and green
export _dred="\[\033[31m\]"
export _dgre="\[\033[32m\]"

export PROMPT_COMMAND='
if [[ $? = "0" ]]; then _color=$_dgre; else _color=$_dred; fi;
if [ ${#PWD} -gt 30 ]; then _wd=\\W; else _wd=\\w; fi;
if [[ `whoami` = \"root\" ]]; then _prompt=\"${_dred}\\#\"; else _prompt=\$; fi;
PS1="\[\033[0;33m\][\!] ${_color}\u@\h ${_wd} ${_prompt}\[\033[00m\] "'

```
PROMPT_COMMAND gets executed just before PS1 is displayed, so this in effect changes the value of PS1 so it reflects the output status of the last command by the colour of the prompt (red for failure, green for success). It also changes the working directory display to just the last part of the path is the path is longer than 30 chars. And if you are root, it shows a red hash sign (#) instead of the regular (red or green) dollar sign ($).

---

### Post by Ertepeller on 2011-01-03
```

export PS1=

[[ $TERM = xterm* ]] && PS1+='\[\e]0;\u@\h:\w\a\]'   # Put user@host:path in titlebar

PS1+='\[\e[$((EUID?35:31));1m\]\u'        # user (bright magenta for normal users, red for root)
PS1+='\[\e[30;1m\]@'                      # literal "@" (bright black)
PS1+='\[\e[34;1m\]\h'                     # hostname (bright blue)
PS1+='\[\e[30;1m\]:'                      # literal ":"
PS1+='\[\e[0;1m\]\w'                      # path (default foreground color, but bold (#f93 in my terminal profile))
PS1+='\[\e[$((PIPESTATUS?31:32));1m\]\$'  # literal "$" for normal users, "#" for root (green or red, depending on exit status of last command)
PS1+='\[\e[m\] '                          # reset colors to normal

```

---

### Post by WarrenSH on 2011-01-05
I < color bash thx

---

### Post by oaxacamatt1 on 2011-01-06
Hi All,
One of my fav's is this little ditty.  It produces a color change in the prompt when the command I enter is completed or not.  

In other words, when the command is completed with no prob's it comes back with a **[COLOR="SeaGreen"][COLOR="Lime"]Green[/COLOR][/COLOR]** command line.  When the command is not completed it comes back **[COLOR="Red"]Red[/COLOR]**!

I change all my cli's to utilize this...

Cheers,
M

```
# Prompt changes color when depending on completion
PROMPT_COMMAND='PS1="\[\033[0;33m\][\!]\`if [[ \$? = "0" ]]; then echo "\\[\\033[32m\\]"; else echo "\\[\\033[31m\\]"; fi\`[\u.\h: \`if [[ `pwd|wc -c|tr -d " "` > 18 ]]; then echo "\\W"; else echo "\\w"; fi\`]\$\[\033[0m\] "; echo -ne "\033]0;`hostname -s`:`pwd`\007"'
```

---

### Post by novatax on 2011-02-05
need help here...

I can't get it work for normal user. Only root prompt changed..

here's my default Maverick
 
.bashrc
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
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$\ '
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
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
# . /etc/bash_completion
#fi

```/etc/profile :

```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
    . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022
```Found another tutorial which I prefer to use for my normal and root prompt```
PS1='\[\e[1;31m\]\h:\w \u\$\[\e[m\] ' or PS1='\[\e[1m\]\h:\w \u\$\[\e[m\] '
```

Is there any way to change it?

---

### Post by chk1123 on 2011-09-11
Thanks!
Informative and easy to implement.:P

---

### Post by wh1zz0 on 2011-10-21
Ohh great tutorial.. Awesome and easy to understand.. Thanks a bunch!

> **MiCovran said:**
> If you have difficulties using the terminal because the prompt isn't visible enough or you would simply like it to look nicer, this howto is for you. It should work on any distribution if you use bash shell, just don't expect your existing .bashrc file to look like Ubuntu's. I've attached a before and after picture of my terminal as an example of what you could do.

So let's get started. Fire up your terminal and stay in your home directory.


[SIZE="3"]**1. Backup**[/SIZE]

First, let's backup our .bashrc file since we're about to make some changes to it:```
cp .bashrc .bashrc-backup
```
The .bashrc file tells bash what to do when terminal is started, including how to show prompt.


[SIZE="3"]**2. Preparing the .bashrc**[/SIZE]

Use your favorite text editor to edit the original .bashrc file, eg.:```
gedit .bashrc
```

Find this part:```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
```

Bash reads PS1 variable to see how to show primary prompt and PS2 for a secondary prompt (used when writing multi-line commands). In this "if" block, the first PS1 is a prompt which will be shown when color is turned on, and the second one (after "else") is being used when no color is desired. As you can see, color codes are quite tiring to use. Imagine you have to write things like \[\033[01;32m\] all over again. It's horrible. Fortunetly, bash lets us define variables that make our life easier. So paste this code above that "if" block:
```
# ANSI color codes
RS="\[\033[0m\]"    # reset
HC="\[\033[1m\]"    # hicolor
UL="\[\033[4m\]"    # underline
INV="\[\033[7m\]"   # inverse background and foreground
FBLK="\[\033[30m\]" # foreground black
FRED="\[\033[31m\]" # foreground red
FGRN="\[\033[32m\]" # foreground green
FYEL="\[\033[33m\]" # foreground yellow
FBLE="\[\033[34m\]" # foreground blue
FMAG="\[\033[35m\]" # foreground magenta
FCYN="\[\033[36m\]" # foreground cyan
FWHT="\[\033[37m\]" # foreground white
BBLK="\[\033[40m\]" # background black
BRED="\[\033[41m\]" # background red
BGRN="\[\033[42m\]" # background green
BYEL="\[\033[43m\]" # background yellow
BBLE="\[\033[44m\]" # background blue
BMAG="\[\033[45m\]" # background magenta
BCYN="\[\033[46m\]" # background cyan
BWHT="\[\033[47m\]" # background white
```
Now you don't have to write all that ANSI code over and over again. For instance, you can just use $FBLE to set foreground (text) to blue, instead of \[\033[34m\].


[SIZE="3"]**3. Setting the prompt without color**[/SIZE]

Now that you have this prepared, you can design your own prompt. Let's start with the one without color for simplicity (it's the one **just below the "else" line**). First, comment in the default PS1 that's already there to ignore it (**put a #** in front of the line), and then define your own PS1 and PS2 just below it.

I'll explain how I did mine. This is how they are defined:
```
PS1="[ ${debian_chroot:+($debian_chroot)}\u: \w ]\\$ "
PS2="> "
```
Secondary prompt is simple. It shows just ***>***.
However, the primary one is a little bit more complicated. It contains some special characters for additional info about a session. You can find a list of those special characters in bash's man page under section PROMPTING:```
man bash
```
I used ***\u*** (username), ***\w*** (current working directory) and, of course, ***\\$*** (the $ or # symbol, depending on your privileges). You don't need to worry about what "${debian_chroot:+($debian_chroot)}" means, just always copy-paste it in front of "/u". So my primary prompt will be shown like this (when I'm in my home directory): **[ penguin: ~ ]$**


[SIZE="3"]**4. Setting the prompt with color**[/SIZE]

If you want to use a colored prompt, you must find the line in your .bashrc that says **#force_color_prompt=yes** and **remove #** from it. This means that bash will from now on prefer what is defined **above the "else" line**. **Comment in** the old PS1 that's located there just like you did before, and then **copy-paste your PS1 and PS2** from below "else" (colorless versions). You now have the base layout and you just need to add some color to it.

The simplest way to deal with it is by inserting variables from that big chunk of code you pasted before. First put a ***$RS*** at the end of both PS1 and PS2 so you don't change formating of other text in the terminal. All ANSI color codes change only the text behind them, and you can only turn off ***$HC***, ***$UL*** and ***$INV*** codes by using ***$RS***. Here's how I added color to my prompt:
```
PS1="$HC$FYEL[ $FBLE${debian_chroot:+($debian_chroot)}\u$FYEL: $FBLE\w $FYEL]\\$ $RS"
PS2="$HC$FYEL> $RS"
```

I used hicolor at the beginning and left it on until that last ***$RS***. Then I just switched between colors I wanted (blue and yellow). So I got this prompt: **[COLOR="Yellow"][ [COLOR="RoyalBlue"]penguin[/COLOR]: [COLOR="RoyalBlue"]~[/COLOR] ]$[/COLOR]**

When you want to see what you've done, just save changes to .bashrc file, start another terminal and enjoy your new prompt. If you want to see how your secondary prompt looks like, enter just ***\*** as a command in the terminal.

_Tip:_ If you're using gnome-terminal and want to fine tune your color selection, right click the terminal, choose ***Edit Current Profile...*** and go to ***Colors*** tab. Note that these changes effect the complete terminal, not just prompt. I don't know how to do this for any other terminal emulators, I'm a GNOME man.


[SIZE="3"]**5. Reverting to old settings**[/SIZE]

If for some reason you wish to return the old prompt or if you broke your .bashrc, the easiest way is to just recover old .bashrc file you backed up. Run a terminal and use:```
cp .bashrc-backup .bashrc
```
Voila! Everything is back to normal.


[SIZE="3"]**For the end**[/SIZE]

I tried to make this howto as simple to understand as I could. If you don't understand or don't know how to do something, if you have a suggestion or think I made a mistake somewhere, feel free to contact me. This is the first howto I wrote so any feedback is appreciated.
This is just my small way to say thanks to people in this forum who helped me a lot, so ... thanks. :)

---

### Post by powersaver on 2011-10-22
Re:  Problem with symbolic-linked home directory

My Gnome-terminal in Ubuntu 11.10 shows at the time of invocation the prompt shown below.
 usr_name@host_name:/mnt/main/home/usr_name$

although  my $HOME is /home/usr_name.  According to the ubuntu11.10's  /etc/bash.bashrc setting of PS1, the prompt must come out     "usr_name@host_name:~$" , if my home directory is not symbolic linked to  a mounted file system.

The reason gnome-terminal shows /mnt/main/home/usr_name   as the initial working directory is that
/home  is a symbolic link to /mnt/main/home.  /mnt/main is a mount point at  which another partition is mounted.  The mounted partition has the  "home" directory at its top level.

I want to make gnome-terminal  show the symbolic-linked path (~ or /home/usr_name,  i.e. $HOME value)  in the prompt instead of the real physical path  (/mnt/main/home/usr_name).  Could someone let me know how I can achieve  this?
(NOTE: When I type "cd", the prompt becomes "usr_name@host_name:~$" which is what I want.)

---

### Post by 14quartz on 2012-02-25
It worked. Thank you. finally I got colored my terminal. good one

---

### Post by rbaleksandar on 2012-04-26
Thank you so much. :p A college of mine told me about this because he saw me struggling with the terminal (a huge project for my uni involving plenty of (needed) output when entering the "make" command. I was sitting in front of my notebook and every time I remade my project, I had to search for the "user_name@host_name:~$" to see where the output starts from. It was just terrible. He wasn't using bash but told me that I should look for info. All I needed was to look inside the .bashrc and see the line "forced_color = yes", remove the comment and there it was - bright green (on black transparent background) visible from miles. :D

---

### Post by Pants Masterson on 2012-04-28
I've tried this a couple of times, modifying the .bashrc in my home directory, and still don't get any changes to my Terminal prompt. Am I doing something wrong? Has something changed in Ubuntu 12.04 that I should be aware of? 

Here's my current .bashrc, post-mods: 

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

# ANSI color codes
RS="\[\033[0m\]"    # reset
HC="\[\033[1m\]"    # hicolor
UL="\[\033[4m\]"    # underline
INV="\[\033[7m\]"   # inverse background and foreground
FBLK="\[\033[30m\]" # foreground black
FRED="\[\033[31m\]" # foreground red
FGRN="\[\033[32m\]" # foreground green
FYEL="\[\033[33m\]" # foreground yellow
FBLE="\[\033[34m\]" # foreground blue
FMAG="\[\033[35m\]" # foreground magenta
FCYN="\[\033[36m\]" # foreground cyan
FWHT="\[\033[37m\]" # foreground white
BBLK="\[\033[40m\]" # background black
BRED="\[\033[41m\]" # background red
BGRN="\[\033[42m\]" # background green
BYEL="\[\033[43m\]" # background yellow
BBLE="\[\033[44m\]" # background blue
BMAG="\[\033[45m\]" # background magenta
BCYN="\[\033[46m\]" # background cyan
BWHT="\[\033[47m\]" # background white

if [ "$color_prompt" = yes ]; then
    #PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    PS1="$HC$FYEL[ ${debian_chroot:+($debian_chroot)}\u$FYEL: $FBLE\w $FYEL]\\$ $RS"
    PS2="$HC$FYEL> $RS"
else
    #PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    PS1="[ ${debian_chroot:+($debian_chroot)}\u: \w ]\\$ "
    PS2="> "
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

export PS1="> "
export PS1="[\u@\h \W]\$"
```I've commented the old code out, so you can see the original bash stuff in there as well.

Newbie, in case you hadn't noticed. :)

EDIT: FIGURED IT OUT! You have to modify the "Export P1" settings at the VERY BOTTOM of the file to set up your prompt.

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012407](http://ubuntuforums.org/showthread.php?t=2012407)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

