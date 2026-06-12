---
title: "What Are Some of Your Aliases"
date: 2006-04-27
forum: The Cafe
---

### Post by Mr Wrath on 2006-04-27
I just wanted get a few ideas for common/uncommon aliases from people of the forum.

Most common alias...also written in .bashrc by default:

SAFE ALIASES
cp='cp -i'
mv='mv -i'
rm='rm -i'

...if you have some aliases you would like to share...please feel free to share.

---

### Post by mscman on 2006-04-27
I don't use that many, but here you go:

```
#Custom Aliases
alias untgz="tar -xvfz"
alias untbz2="tar -xvfj"
alias netstati="netstat --verbose --tcp --udp --programs --extend"
alias aptI="sudo apt-get install"
alias aptUD="sudo apt-get update"
alias aptUG="sudo apt-get upgrade"
alias aptDUG="sudo apt-get dist-upgrade"
alias aptR="sudo apt-get remove"

```

---

### Post by Mr Wrath on 2006-04-27
Oh...funny aliases are also welcomed...
meow='more'
moer='more'

I actually saw this as someones alias...gotta know yourself pretty well to alias your mistakes.

---

### Post by hotani on 2006-04-27
These are in zsh (originally from my .zshrc on OS X, some don't translate over to linux as well as others and I haven't cleaned it up yet. :) )
```

alias ls="ls -F"
alias files="ls *.*"
alias dirs="ls -d * | grep /"
alias l="ls -lh | more"
alias htt="ps -aux | grep httpd"
alias cp="cp -p"
alias cc="gcc"
alias top="top -du"
alias exti="exit"
alias df="df -Hl"

```

---

### Post by Super King on 2006-04-27
There's a similar 'share your alias' thread [here]("http://www.ubuntuforums.org/showthread.php?t=161312") posted not long ago, for more input on the subject.

---

### Post by kabus on 2006-04-27
[QUOTE=Mr Wrath]
SAFE ALIASES
cp='cp -i'
mv='mv -i'
rm='rm -i'
[/QUOTE]

In my experience this doesn't really make things safer because you get used to it and start hitting 'y' automatically. 
More hassle than it's worth, I think.

---

### Post by tribaal on 2006-04-27
Being a MUD addict, I had to make myself theses aliases:

```
alias nod="echo You nod."
alias vmap="echo You're not on deckeon"
```

I should probably stop playing text-based games, and work in CLI at the same time ;)

- trib'

---

### Post by KingBahamut on 2006-04-27
Hehe. 

In one country Im known as The Jackal. 

Sorry, Couldnt help that one.

---

### Post by bb002 on 2006-04-27
Mine are similar to mscman's.

```
#My Aliases
alias mktar="tar -cvf"
alias mkbz2="tar -cvjf"
alias mkgz="tar -cvzf"
alias untar="tar -xvf"
alias unbz2="tar -xvjf"
alias ungz="tar -xvzf"
alias apt-getupgrade="sudo apt-get update && sudo apt-get upgrade"
alias apt-getdist="sudo apt-get update && sudo apt-get dist-upgrade"
alias shh="echo You idiot it's ssh!!"
alias rm="echo Dangerous wait for megarm completion."

```

megarm is a bash script that uses the .Trash folder. I'm just having issues with detecting when i'm on different partitions so i can use the proper .Trash-%user folder.

---

### Post by Mr Wrath on 2006-04-28
Thank You Everyone For You Examples...much Appreciated.

---

### Post by therunnyman on 2006-04-28
[QUOTE=KingBahamut]
In one country Im known as The Jackal. 
[/QUOTE]

Dangit.  I was gonna post:

Son of Sam
Mark Twain

but the joke may not be funny anymore.

therunnyman

---

### Post by YourSurrogateGod on 2006-04-28
Stupid question, what are aliases?

---

### Post by hotani on 2006-04-30
they're shortcuts in your shell profile that point to longer commands. For example, if everytime i do "ls" I'm typing "ls -FA" then I can alias it so even though I'm only typing "ls" it is outputting the same as "ls -FA."

---

### Post by picpak on 2006-04-30
Aliases are addicting. I just copied some from here:

alias kill='pkill'
alias apt='sudo apt-get install'
alias remove='sudo apt-get remove'
alias dep='sudo apt-get build-dep'
alias search='apt-cache search'
alias edit='leafpad'
alias suedit='sudo leafpad'
alias i='sudo dpkg -i'
alias upgrade='sudo apt-get upgrade'
alias update='sudo apt-get update'
alias clean='sudo apt-get clean'
alias build-dep='sudo apt-get build-dep'
alias df='df -Hl'
alias trash='cd .xfetrash && sudo rm -r *'
alias sutrash='cd /root/.xfetrash && sudo rm -r *'
alias home='cd ~'
alias mktar='tar -cvf'
alias mkbz2='tar -cvjf'
alias mkgz='tar -cvzf'
alias untar='tar -xvf'
alias unbz2='tar -xvjf'
alias ungz='tar -xvzf'
alias ls='ls --color=auto'
alias mv='mv -i'
alias cp='cp -i'
alias rm='rm -i'

---

### Post by Mr Wrath on 2006-05-01
...thanks again for the posts...

---

### Post by YourSurrogateGod on 2006-05-01
[QUOTE=hotani]they're shortcuts in your shell profile that point to longer commands. For example, if everytime i do "ls" I'm typing "ls -FA" then I can alias it so even though I'm only typing "ls" it is outputting the same as "ls -FA."[/QUOTE]
Cool, how do you make them?

---

### Post by Nequeo on 2006-05-01
[QUOTE=tribaal]Being a MUD addict, I had to make myself theses aliases:

```
alias nod="echo You nod."
alias vmap="echo You're not on deckeon"
```

I should probably stop playing text-based games, and work in CLI at the same time ;)

- trib'[/QUOTE]

Off topic, but I laughed out loud at this one. I learnt to 'touch type' (my own way, not the Mavis Beacon way) by compulsive MUDding when I was younger. I never mucked about with IRC, but when ICQ came out a while later, it was one heck of a struggle to stop prefacing everything I typed into the chat window with "Say".

---

