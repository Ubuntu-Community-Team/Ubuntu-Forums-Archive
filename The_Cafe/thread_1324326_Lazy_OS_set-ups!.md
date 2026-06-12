---
title: "Lazy OS set-ups!"
date: 2009-11-12
forum: The Cafe
---

### Post by hoppipolla on 2009-11-12
Do you have any?

My personal favourite is one I made last night. It's a link on my desktop that fires off the command:

*kdesu xterm updateme*

updateme being a script I wrote that reads this:

*apt-get update && apt-get dist-upgrade && apt-get upgrade*


So basically in one go without any GUI tools (which can be long-winded) or prompt commands (which can be lengthy) it updates! It can be quite cool!

I also made a script which fires up Pidgin, Amarok, gufw and kmail in one click (which also now sits on the desktop) which saves me a bit of time on start-up without FORCING me to wait for them to start if I just popped on to do something quickly!


So do you guys have any? I think that these kinds of hacks and workarounds and flexibility is part of the beauty of such an open system! ^_^

Hoppi!

---

### Post by NoaHall on 2009-11-12
If you use alias, you set that up to run on something like "u" ;)

---

### Post by FuturePilot on 2009-11-12
I wouldn't call that lazy, I would call that being efficient.

I have a launcher on my panel that does
```
gnome-terminal --window-with-profile=IRC --geometry=135x35 --command='ssh blah blah blah'
```

which opens a terminal window with a special profile I made specifically for this and runs an ssh command which connects me to my server and automatically reattaches to my screen session running Irssi.

---

### Post by ajgreeny on 2009-11-12
My most used alias is a very simple one, **q='exit'** for closing the terminal which I must use 10s of times a day.

 When I first started using Ubuntu, I never dreamed I would use the terminal as much as I do, but it is such a fantastically powerful  tool that to go back to the miserable command prompt of windows would seem like absolute hell to me now.

---

### Post by -grubby on 2009-11-12
Hacks and workarounds aren't beautiful, but shell scripts can be convenient.

---

### Post by knepig91 on 2009-11-12
alias ..='cd..'

Now, that is lazy

---

### Post by hoppipolla on 2009-11-12
> **-grubby said:**
> Hacks and workarounds aren't beautiful, but shell scripts can be convenient.

haha yes I guess I used the wrong terminology there :)

---

### Post by Sporkman on 2009-11-12
[http://www.turnkeylinux.org/](http://www.turnkeylinux.org/)

---

### Post by earthpigg on 2009-11-12
```
alias l='ls --color=auto'
alias dfg='df -Th -x tmpfs'
alias f='free -m'
alias t='htop'
alias e='exit'

alias ..='cd .. && fortune'
alias ...='cd ../.. && fortune'
alias ....='cd ../../.. && fortune'
alias .....='cd ../../../.. && fortune'

```

---

### Post by RiceMonster on 2009-11-12
not lazy, but I think this one shows true boredom:

```
alias gtfo=exit
```

---

### Post by sisco311 on 2009-11-12
> **knepig91 said:**
> alias ..='cd..'

Now, that is lazy

```
shopt -s autocd
```

```
man bash | less --pattern\="autocd"
```

---

### Post by uberdonkey5 on 2009-11-12
I have a cool script that shutsdown in set number of minutes (user input).. could be done from command line (with sudo) but I made it possible without using sudo, and just from launcher...

great when I want computer to shut down after radio program (e.g. at night) or after a torrent

at work (windows.. huff) so can't list it at mo'

---

### Post by Tibuda on 2009-11-12
snip

---

### Post by hoppipolla on 2009-11-12
> **earthpigg said:**
> ```
alias l='ls --color=auto'
alias dfg='df -Th -x tmpfs'
alias f='free -m'
alias t='htop'
alias e='exit'

alias ..='cd .. && fortune'
alias ...='cd ../.. && fortune'
alias ....='cd ../../.. && fortune'
alias .....='cd ../../../.. && fortune'

```

these are cool - I never even knew about alias. Does it set the alternate command permanently or just for that session?

---

### Post by sisco311 on 2009-11-12
> **hoppipolla said:**
> these are cool - I never even knew about alias. Does it set the alternate command permanently or just for that session?

for a session.


to make them permanent you can add them to the [~/.bashrc]("http://www.faqs.org/docs/abs/HTML/files.html") file.

---

