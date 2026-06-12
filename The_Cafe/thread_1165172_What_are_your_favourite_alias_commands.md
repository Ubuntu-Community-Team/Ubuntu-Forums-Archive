---
title: "What are your favourite alias commands?"
date: 2009-05-20
forum: The Cafe
---

### Post by Rytron on 2009-05-20
Hi.
What are your favourite alias commands that you always put in the ~/.bashrc file?
Thanks.

---

### Post by ukripper on 2009-05-20
I like to type instead. It makes me remember commands if I need to access on different system quickly.

I am not a supporter of alias to be honest.

---

### Post by m_duck on 2009-05-20
[B]alias x='startx'
[/B]
Because I'm *that* lazy.

---

### Post by RiceMonster on 2009-05-20
I did this recently, because I was getting annoyed at Xorg output on the terminal.

alias startx='startx >& ~/.Xoutput'

probably not a good idea :p.

---

### Post by billgoldberg on 2009-05-20
rm is aliased with the -I option, that's about it.

I guess it could be useful to replace sudo apt-get install with just install, but meh, I'm too lazy.

---

### Post by chucky chuckaluck on 2009-05-20
> **m_duck said:**
> [B]alias x='startx'
[/B]
Because I'm *that* lazy.

haha! that's great.

---

### Post by Keith Hedger on 2009-05-20
I've still only got dial-up so I use this:```
alias downloadrobust='wget --continue --read-timeout=10 --random-wait --retry-connrefused --tries=inf'
```
to download everything and anything, and I use this```
alias goto='nautilus'
``` to open a nautilus window in a specific directory.

---

### Post by Bodsda on 2009-05-20
alias _p='sudo shutdown -P'
alias _r='sudo shutdown -r'

alias session='firefox [http://ubuntuforums.org&;](http://ubuntuforums.org&;) xchat&; rhythmbox&;'

alias restart_wicd='sudo killall wicd-client; sudo /etc/init.d/wicd stop; sudo /etc/init.d/wicd start; sudo wicd-client &'

---

### Post by ibuclaw on 2009-05-20
```

alias canhaz='sudo apt-get install'
alias nowantz='sudo apt-get --purge remove'
alias ninjaz='sudo vim'

```

---

### Post by init1 on 2009-05-20
> **tinivole said:**
> ```

alias canhaz='sudo apt-get install'
alias nowantz='sudo apt-get --purge remove'
alias ninjaz='sudo vim'

```
LOL that's great :D

---

### Post by spupy on 2009-05-20
```
alias +='clear'
alias +l='clear && ls'
alias suq='su && exit'
alias telnethack='telnet nethack.alt.org'
alias tnh='telnet nethack.alt.org'
```

---

### Post by SuperSonic4 on 2009-05-20
```
alias ping1='ping -c 4 www.google.com'
alias ping2='ping -c 4 192.168.0.1'
alias y='yaourt'
```

---

### Post by Tibuda on 2009-05-20
My problem with aliases are that some tab completion does not work with them. If I type install pack<TAB><TAB> it will not display the packages starting with pack, as sudo aptitude install pack<TAB><TAB> will.

---

### Post by Rytron on 2009-05-22
alias c64=x64
alias chrome=chromium-browser
alias ipconfig=ifconfig

---

### Post by alberto ferreira on 2009-05-22
```
current_ip(){
ifconfig eth0 | grep inet\ addr | awk -F" " '{print $2}'
}

netest(){
tmp=`mktemp`
echo -n -e "Network Status...\t"
2>/dev/null ping -w 1  -c 1 www.google.com|grep packets|awk -F" " '{print $4}' > $tmp
[ "`cat $tmp`" = "1" ] && echo "[   OK   ]" || echo "[OFF/FAIL]"
rm $tmp
}

alias i='sudo apt-get install -y'
alias r='sudo apt-get remove -y --purge'
alias cip="current_ip"

```Notice that **netest** is also an "alias"
I made it to know if my connection is working or has some issues. It's super useful for me and it works in a very user friendly way.

---

### Post by bostonaholic on 2009-05-22
```
# ls aliases
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'

# apt-get aliases
alias sagup='sudo apt-get update'
alias sagug='sudo apt-get upgrade'
alias sagin='sudo apt-get install'

# other aliases
alias vi='vim'
```

---

### Post by Rytron on 2009-05-22
> **alberto ferreira said:**
> ```
current_ip(){
ifconfig eth0 | grep inet\ addr | awk -F" " '{print $2}'
}

netest(){
tmp=`mktemp`
echo -n -e "Network Status...\t"
2>/dev/null ping -w 1  -c 1 www.google.com|grep packets|awk -F" " '{print $4}' > $tmp
[ "`cat $tmp`" = "1" ] && echo "[   OK   ]" || echo "[OFF/FAIL]"
rm $tmp
}

alias i='sudo apt-get install -y'
alias r='sudo apt-get remove -y --purge'
alias cip="current_ip"

```Notice that **netest** is also an "alias"
I made it to know if my connection is working or has some issues. It's super useful for me and it works in a very user friendly way.

What does this do exactly?

```
current_ip(){
ifconfig eth0 | grep inet\ addr | awk -F" " '{print $2}'
}

netest(){
tmp=`mktemp`
echo -n -e "Network Status...\t"
2>/dev/null ping -w 1  -c 1 www.google.com|grep packets|awk -F" " '{print $4}' > $tmp
[ "`cat $tmp`" = "1" ] && echo "[   OK   ]" || echo "[OFF/FAIL]"
rm $tmp
}

```

---

### Post by benj1 on 2009-05-22
probably 
either
```
function cdl () { cd $1;ls;} 
```
or
```

function pythonhelp()
{
pydoc -p 7464&
sleep 0.5
if (( "$#" == 0))
then
        w3m http://localhost:7464
else 
        $1 http://localhost:7464
fi
kill $!
echo process $! ended
}
```
for viewing python documentation

not aliases i know but hey

---

### Post by sujoy on 2009-05-22
```
alias ls='ls --color=auto'
alias grep='grep --color=auto'
alias vi="vim"
alias rm="rm -v"
alias cp="cp -v"
alias mv="mv -v"
alias pacman="sudo pacman"
alias powerpill="sudo powerpill"
alias mocp="mocp -T darkdot_theme"
alias torlist='grep -ao -HP "http://[^/]*/"'
```

---

### Post by alberto ferreira on 2009-05-22
To _**Rytron**_:

current_ip(){....CODE.....}
and
netest(){...CODE....}

are functions, they execute the portion of code inside the {}.

**current_ip** that is linked to the cip alias ( i'm too lazy to write commands with more than 3 letters ;) ) is used to know what your current pc's ip is ( because I have quite a big number of computers connected in lan in my house )
If you wish to use it ensure that your internet interface is eth0 or change it's name in the function.

**netest** tells me if my internet connection is working at 100% - if you can browse the internet -  not only if your network interface is on ( if it is off the command takes several seconds to run instead of running instantly ).

---

### Post by swoll1980 on 2009-05-22
alias search='apt-cache search'
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias kill='sudo killall'
alias rootilus='gksu nautilus /'
alias grootit='gksu gedit'

---

### Post by RiceMonster on 2009-05-22
Added these today:

```
alias nano='vim'
alias emacs='vim'
```

:p

---

### Post by bostonaholic on 2009-05-22
I'm politically correct, equal opportunity
```
alias woman='man'
```

---

### Post by tomcheng76 on 2009-05-22
```
alias rd='rm -fr'
```

---

### Post by alberto ferreira on 2009-05-22
> alias woman='man'

Lol, that's great :)

---

### Post by RiceMonster on 2009-05-22
> **bostonaholic said:**
> I'm politically correct, equal opportunity
```
alias woman='man'
```

Wouldn't it be alias person='man'?

---

### Post by monsterstack on 2009-05-22
```
alias beep='echo -en "\007"'
```

---

### Post by automaton26 on 2009-05-22
```
alias sn='sudo nano'
alias aps='apt-cache search'
alias api='sudo apt-get install'
alias apr='sudo apt-get remove'
alias apa='sudo apt-get autoremove'
alias l='ls -ls'
alias ..='cd ..'
alias renet='sudo /etc/init.d/networking restart'
alias ccc='DISPLAY=:0 amdcccle'
```

---

### Post by bostonaholic on 2009-05-22
> **RiceMonster said:**
> Wouldn't it be alias person='man'?

I see what you mean.  I guess what I mean is...

politically correct:
```
alias person='man'
```
equal opportunity:
```
alias woman='man'
```

---

### Post by Rytron on 2009-05-22
> **alberto ferreira said:**
> To _**Rytron**_:

current_ip(){....CODE.....}
and
netest(){...CODE....}

are functions, they execute the portion of code inside the {}.

**current_ip** that is linked to the cip alias ( i'm too lazy to write commands with more than 3 letters ;) ) is used to know what your current pc's ip is ( because I have quite a big number of computers connected in lan in my house )
If you wish to use it ensure that your internet interface is eth0 or change it's name in the function.

**netest** tells me if my internet connection is working at 100% - if you can browse the internet -  not only if your network interface is on ( if it is off the command takes several seconds to run instead of running instantly ).

Thank you alberto ferreira.

---

### Post by Rytron on 2009-05-22
> **RiceMonster said:**
> Wouldn't it be alias person='man'?

Hi.
What is ```
yes RiceMonster
```

---

### Post by Tibuda on 2009-05-22
> **Rytron said:**
> Hi.
What is ```
yes RiceMonster
```

[QUOTE="man yes"]yes - output a string repeatedly until killed[/QUOTE]

```
$ yes RiceMonster | head
RiceMonster
RiceMonster
RiceMonster
RiceMonster
RiceMonster
RiceMonster
RiceMonster
RiceMonster
RiceMonster
RiceMonster

```

---

### Post by RiceMonster on 2009-05-22
> **Rytron said:**
> Hi.
What is ```
yes RiceMonster
```

Type it into a terminal. it just repeatadly prints RiceMonster, as danielrmt said.

Hit Ctrl-C to stop it.

---

### Post by benj1 on 2009-05-22
> **swoll1980 said:**
> 
alias rootilus='gksu nautilus /'
alias grootit='gksu gedit'

ha ha like it :)

---

### Post by Rytron on 2009-05-22
> **RiceMonster said:**
> Type it into a terminal. it just repeatadly prints RiceMonster, as danielrmt said.

Hit Ctrl-C to stop it.

Cool. A little Easter Egg/Linux quirk.

:)

---

### Post by Tibuda on 2009-05-22
> **Rytron said:**
> Cool. A little Easter Egg/Linux quirk.

:)

It's not a easter egg, it can be useful. You can pipe it to any command that needs a [y/n] confirmation, so you don't have to confirm it.

---

### Post by Kareeser on 2009-05-23
I aliased "sysupd" to "sudo apt-get update ; sudo apt-get upgrade"

I like the command line for the update process... :)

---

### Post by SuperSonic4 on 2009-05-23
Since I can never remember the command for "refreshing" the plasmoid list:

```
alias plasmoid='kbuildsycoca4'
```

---

### Post by bostonaholic on 2009-06-25
since I'm always switching between JDK's...

```
alias jv='java -version'
```

---

### Post by Sporkman on 2009-06-25
```
alias ls='ls --color=none'
alias l='echo ; echo $PWD; echo; ls -F; echo '
alias clean='rm *~'
alias stat='acpi -V'
alias mktar='tar -cvf'
alias mkbz2='tar -cvjf'
alias mkgz='tar -cvzf'
alias untar='tar -xvf'
alias unbz2='tar -xvjf'
alias ungz='tar -xvzf'
alias cdc='cd $CF3_HOME'
alias indrv='sudo cryptsetup luksOpen /dev/sdc1 mydata ; sudo mount -t ext3 /dev/mapper/mydata /media/usbdrv/'
alias outdrv='sudo umount /media/usbdrv/ ; sudo cryptsetup luksClose mydata'

```

---

