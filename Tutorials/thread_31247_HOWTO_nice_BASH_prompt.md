---
title: "HOWTO: nice BASH prompt"
date: 2005-05-02
forum: Tutorials
---

### Post by seven on 2005-05-02
1)first of all - backup your .bashrc file
> 
cp .bashrc .bashrc-backup

2)now edit .bashrc with your editor:
> 
gedit .bashrc


search for lines that contain the string: PS1
and comment them (with # before them).

in the end of the file add:
> 
PROMPT_HOSTNAME='SET_HERE'
PROMPT_COLOR='1;37m'
PROMPT_COLOR2='1;32m'

PS1='\e[${PROMPT_COLOR}[\e[${PROMPT_COLOR2}\u@${PROMPT_HOSTNAME}\e[${PROMPT_COLOR}] $ '


the first color is for the normal font and barckets, and the second one is for the user name and host



I choosed green and white. you can change the first number to any of the following:

> 
30: Black/Dark grey
31: Red
32: Green
33: Yellow
34: Blue
35: Magenta
36: Fuscia
37: White/light grey
38: "Default" foreground color

in the exmaple "1;37m" you will have to change the 37 to another number.
the 1 before it can be set into zero, it is for light \ dark colors 

rename the PROMPT_HOSTNAME to your hostname (or anything you want) 
and save the file.
pray for your god and open bash, it should work.

it should be like this:
[http://www.base17.hostorm.biz/Bash.png](http://www.base17.hostorm.biz/Bash.png)

EDIT: I have updated the pic. I used a new PS1
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\e[${PROMPT_COLOR2}\u@\h\[\033[00m\]:\[\033[1;37m\]\w\[\033[00m\]\$ '

it is not perfect yet, play with the colors and stuff as much as you want.

another one:
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\e[${PROMPT_COLOR2}\u@\h\[\033[00m\]:\[\033[1;37m\]\w\[\033[00m\]\$ '

i think this is the nicest until now

for more info:
[http://www.neowin.net/forum/lofiversion/index.php/t148706.html](http://www.neowin.net/forum/lofiversion/index.php/t148706.html)
[http://networking.ringofsaturn.com/Unix/Bash-prompts.php](http://networking.ringofsaturn.com/Unix/Bash-prompts.php)

good luck

---

### Post by ow50 on 2005-05-02
Good HOWTO. Here's another good prompt:
```
PS1='\n\[\033[1;34m\]\342\226\210\342\226\210 \u @ \w\n\[\033[0;36m\]\342\226\210\342\226\210 \t $ \[\033[0;39m\]'
```

The colorblocks and the newline before the prompt should make it easy to quickly visualize the prompts at a longer console output. For root, I have the same with red and violet and $ replaced with #.

[[IMG]http://img125.echo.cx/img125/4766/ss3sg.th.png[/IMG]](http://img125.echo.cx/my.php?image=ss3sg.png)

**Edit:**
Using those colorblock characters seems to cause weird behaviour for backspace and delete. Not good after all.

---

### Post by JonahRowley on 2005-05-02
Here's a helper file I use for this, I can't remember where I got it, or if it's complete, but it has mnemonics for a bunch of colors, which will make this easier.  I put it in ~/bin/ansicolor, so I can **source ~/bin/ansicolor** in scripts I want to add color to.

```
C_RED="\[\033[0;31m\]"
C_GREEN="\[\033[0;32m\]"
C_LIGHT_GRAY="\[\033[0;37m\]"
C_RESET="\[\033[0m\]"

C_BROWN="\[\033[0;33m\]"
C_BLUE="\[\033[0;34m\]"
C_PURPLE="\[\033[0;35m\]"
C_CYAN="\[\033[0;36m\] "
C_GRAY="\[\033[1;30m\]"
C_WHITE="\[\033[1;37m\]"
C_YELLOW="\[\033[1;33m\]"

C_LIGHT_BLUE="\[\033[1;34m\]"
C_LIGHT_CYAN="\[\033[1;36m\]"
C_LIGHT_PURPLE="\[\033[1;35m\]"
C_LIGHT_RED="\[\033[1; 31m\]"
C_LIGHT_GREEN="\[\033[1;32m\]"
```

Edit:  BTW, my prompt is this:
```
PS1="$C_BLUE[$C_RED\$?$C_BLUE][$C_RED\u@\h:\w$C_BLUE]\$ $C_RESET"
```

---

### Post by Juippisi on 2005-05-14
Thanks for the HOWTO.

Mine bash: [http://www.roskakori.org/juippis/pictures/screenshots/bash.png](http://www.roskakori.org/juippis/pictures/screenshots/bash.png)

And the line:
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w\[\033[01;34m\] \$\[\033[00m\] '

Heh, tried to make it "Gentoo-like" :)

---

### Post by stubby on 2005-05-15
brilliant stuff. it's so pretty now =). Many thanks for the HOWTO

---

### Post by henriquemaia on 2005-05-15
I was just thinking, after using bash, that I should search on how to change the prompt - so here it is!

Thanks a lot to you all here. All your suggestions are useful.

---

### Post by Heliode on 2005-05-15
I'm using this line:
```

PROMPT_COLOR='1;32m'
PROMPT_COLOR2='1;32m'
PROMPT_COLOR3='1;34m'

PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\e[${PROMPT_COLOR2}\u\033[01;32m\e[${PROMPT_COLOR3}@\033[01;32m\e[${PROMPT_COLOR}\h\[\033[1;31m\]:\[\033[1;34m\]\w\[\033[1;31m\]\$\033[00m'

```

See attachment for what it does ;)

---

### Post by stubby on 2005-05-16
> 
**Edit:**
Using those colorblock characters seems to cause weird behaviour for backspace and delete. Not good after all.

Here's something that works. The font colour and style is the same, just not the colour thing at the beginning.

PS1='\n\[\033[01;34m\]\u @ \w\n\[\033[0;36m\]\t $ \[\033[0;39m\]'

---

### Post by techmonkey on 2005-09-21
Here's what I use:

```

function jobcount {
   jobs | wc -l | tr -d " "
}

cur_tty=$(tty | sed -e "s/.*tty\(.*\)/\1/")

loadavg=$(uptime | sed -e "s/.*load average: \(.*\...\), \(.*\...\), \(.*\...\)/\1/" -e "s/ //g")

# PROMPT

PS1='\[\033[1;44m\]\[\033[1;34m\]  \[\033[1;40m\] [\u@\h:\w]\n\[\033[1;44m\]\[\033[1;34m\]  \[\033[1;40m\] [j:`jobcount`, t:$cur_tty, l:$loadavg]\n\[\033[1;46m\]\[\033[1;36m\]  \[\033[1;40m\] [`date +%D` \t] $> \[\033[0;39m\]'

```

Three-line hack of the colorblocks prompt. It displays:
1st line: the usual. user@host:directory
2nd line: suspended jobs, tty name and most recent load average.
3rd line: The actual prompt. Just the date and time, and a different kind of prompt character.

Wow, this terminal OWNS now. Shove **that** in your "C:\>" and smoke it, Win nuts! :razz:

---

### Post by liljencrantz on 2005-09-22
> **Heliode]I'm using this line:
```

PROMPT_COLOR='1 said:**
> :\[\033[1;34m\]\w\[\033[1;31m\]\$\033[00m'

```

See attachment for what it does ;)

Heh. This thread is such a perfect example of what is wrong with bash. Just look at that PS1 line. It is a completely needless second language within bash, and a 100% unreadable, unmaintanable mess of a language at that. What is wrong with simply specifying a function whose output becomes the prompt? That is what fish does.

 ```
function fish_prompt
	whoami
	echo ' '
	set_color green
	echo \n\ 
	pwd
	set_color normal
	echo \n\>\ 
end

``` 

The only caveats is that all terminal escape codes, such as those written by the set_color command to set the text color, must en with a newline in order to tell fish how long the escape code sequence is, and that newlines are ignored.

Now tell me that this isn't an order of magnitude more readable and easy to use...

---

### Post by techmonkey on 2005-09-22
Meh, I can understand both. Maybe your post will make a convert out of somebody else though. :)

---

### Post by skoal on 2005-09-22
I haven't see it mentioned yet here, but you can always get a really good idea of all the possible color combinations you can use by doing this:

dircolors -p

or capture it to a file (for better viewing):

dircolors -p > colors.txt

Then scroll around to the middle where you see:
```
# Below are the color init strings for the basic file types. A color init
# string consists of one or more of the following numeric codes:
# Attribute codes:
# 00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed

# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white

```
and look below it to see how your directory colors are managed this way...

Just for shiznitt's and grins, I modified my prompt just to show you how you can make the current path (PWD) you are in blink! Trust me, I don't torture myself with blinkage, and have changed it back after I posted this...

 PS1='${debian_chroot:+($debian_chroot)}\[\033[00;36m\]\u\[\033[00m\]@\h://\[\033[05;33m\]\w\[\033[00m\] \$ '

\\//_

---

### Post by techmonkey on 2005-09-22
Mine doesn't appear to blink. I tried making the dots in `date "+%H:%M"` blink, but it just gave it background colour and ignored the blink.

On the other hand, I think it's a good thing my terminal won't allow ANSI stuff to blink. :)

---

### Post by duminas on 2005-11-28
Any idea why this isn't working in Breezy? I realize this is for Hoary tips, but I'm wondering what package makes it work.
This comes up as my prompt:

```
\[\033[1;34m\]$?   \[\033[1;34m\]~ \[\033[1;32m\]$ \[\033[00m\]
```None of the names or anything.

The actual code I'm using is:
```
PS1='$C_LIGHT_BLUE\$? $C_LIGHT_RED\u $C_LIGHT_CYAN\h $C_LIGHT_BLUE\w $C_LIGHT_GREEN\$ $C_RESET'
```

With the same ansicolor file sourced as [is here](http://ubuntuforums.org/showpost.php?p=156019&postcount=3) (except for the extra unneeded space in the middle of one of the colors).

---

### Post by refrishx on 2010-05-04
PROMPT_HOSTNAME='LOVE'
PROMPT_COLOR='1;30m'
PROMPT_COLOR2='1;31m'

PS1='\e[${PROMPT_COLOR}[\e[${PROMPT_COLOR2}\u@${PROMPT_HOSTNAME}\e[${PROMPT_COLOR}] \e[${PROMPT_COLOR2}&#9825; '

---

### Post by coolkid on 2010-08-21
> **refrishx said:**
> PROMPT_HOSTNAME='LOVE'
PROMPT_COLOR='1;30m'
PROMPT_COLOR2='1;31m'

PS1='\e[${PROMPT_COLOR}[\e[${PROMPT_COLOR2}\u@${PROMPT_HOSTNAME}\e[${PROMPT_COLOR}] \e[${PROMPT_COLOR2}&#9825; '

it's really interesting :D . Thanks for sharing

---

### Post by piyushpandey on 2011-02-17
Hello Guys 

I have Ubuntu 10.04 lucid installed on my system and I want to give the color to the bash terminal of my Desktop, but I am not able to do so as recommended in the following topic of this forum.

Actually I have searched for the .bashrc  file in the /etc folder but there I have got no scuh file and instead of that I have the bash.bashrc file in my /etc file and in that I have got the line stating that :

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

and I have edited this file as follows :

PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\e[$1;32m\u@\h\[\033[00m\]:\[\033[1;37m\]\w\[\033[00m\]\$ '

but still I am not able to get the colorful PS1 .


So Please help me you guys because I am unable to color the PS!.

Also I want to ask that do I have to make the .bashrc file or all the editing have to be done in the bash.bashrc file .


Thank you

Piyush Pandey

---

### Post by The Abominable Snowman on 2012-09-26
Since it won't be the first time bringing back the thread - I'd rather put my plea here and not make a new one. Here's hwat: 
**How do you change the titlebar / tab title?** I've got it as far as it saying just *Terminal #n* (guess I deleted something), 
which is better than before (displaying the path to $PWD and I use sakura, so it's sucky), 
but I'd rather it just say the name of the one directory (instead of the full path). Any clues?

---

