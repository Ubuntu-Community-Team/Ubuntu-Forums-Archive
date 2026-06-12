---
title: "do you have any good aliases you can share?"
date: 2006-04-16
forum: The Cafe
---

### Post by ice60 on 2006-04-16
if you are like me - a newbie [img]http://www.buffalorange.com/images/smilies/newbie.gif[/img] here's a description of an alias from [here](http://www.eos.ncsu.edu/guide/glossary.html)
> alias - an alternate name or abbreviation (usually short and easy to remember) that substitutes for a pathname, command, list, or expression (usually long and hard to remember).
i think to get it working you have to do this
```
gedit .bashrc
```
then uncomment these lines 
```
#if [ -f ~/.bash_aliases ]; then
#   . ~/.bash_aliases
#fi
```
i think that's how they look to start with, anyway they should look like this when you have finished and saved the file
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```
then create or make sure you have this file in your home directory
```
.bash_aliases
```
you can check by doing this when you first open bash, or your commmand line program
```
ls -a
```
if it's not there just make the file 
```
gedit .bash_aliases

```

lol, i only wanted to ask if anyone could show me some good aliases not write a tutorial :roll:  i hope someone shows me some now :D thanks.

if everything i have written is correct and there isn't already a tutorial about enabling aliases and there's no easier way maybe i'll submit as a howto.

---

### Post by dabear on 2006-04-16
Here are mine:
> 

alias x='gksudo gedit /etc/X11/xorg.conf'
alias upgrade='sudo apt-get update && sudo apt-get dist-upgrade'
alias apt='gksudo gedit /etc/apt/sources.list'


---

### Post by nanotube on 2006-04-16
[QUOTE=dabear]Here are mine:[/QUOTE]
hehe, dabear, how often do you dist-upgrade that you decided to make an alias for it? ;)

anyway, here are mine:
```
alias ll='ls -al --color=auto'
alias mv='mv -i'
alias cp='cp -i'
alias rm='rm -i'
```

nothing fancy... just to make sure that mv/cp/rm ask confirmation (unless overridden specifically), and a shortcut for long-listing for ls. 
the ones by dabear are nice, but i dont edit my xorg.conf, or sources.list so frequently that i need an alias for them. ;)

---

### Post by IYY on 2006-04-16
> alias upgrade='sudo apt-get update && sudo apt-get dist-upgrade'

Good one!

---

### Post by ice60 on 2006-04-16
thanks, everyone d(-_^) i hope people keep posting because i think even if no one uses anyone elses aliases, you can still learn just from seeing how people use their computer. :cool: 

i don't understand why dabear uses gksudo for this one, can anyone explain why it's used instead of sudo? thanks everyone :) 
```
alias apt='gksudo gedit /etc/apt/sources.list'
```

---

### Post by pitkali on 2006-04-16
AFAIK the only difference here is that gksudo will ask for a password in a nice GTK+ window ;)

---

### Post by Super King on 2006-04-16
I don't have any fancy ones, just shortcuts for getting to my frequently used directories.

> alias d='cd /home/myusername/Downloads'
alias p='cd /home/myusername/Pics'
alias s='cd /home/myusername/School'

---

### Post by Christmas on 2006-04-16
> **pitkali]AFAIK the only difference here is that gksudo will ask for a password in a nice GTK+ window  said:**
> 

Here is what Wiki says about this:

[QUOTE]NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.

---

### Post by Christmas on 2006-04-16
Oh, and btw, I uncommented the lines in .bashrc, I made a new file called .bash_aliases and entered this line:
```
alias x='gedit /etc/X11/xorg.conf
```
However when I type "x" in the terminal it says "command not found". What am I doing wrong?

---

### Post by endersshadow on 2006-04-16
```
alias ls='ls -p'
alias ll='ls -lahp'
alias inkscapeprint='inkscape -p Deskjet-3650'
```

I *love* my ll alias.  Not only does it print long listings, but it also prints sizes in human readable format (1K instead of 1024), and it adds a / at the end of directories. :-D

---

### Post by ow50 on 2006-04-16
```
# Just in case aliases
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'

# File listing aliases
alias l='ls --classify --almost-all'
alias ll='l --format=single-column'
alias lll='l --format=long'

# Directory navigation aliases
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

# Package management aliases
alias apt-bdep='sudo apt-get build-dep'
alias apt-dep='apt-cache depends'
alias apt-install='sudo aptitude install'
alias apt-list='apt-file list'
alias apt-owner='apt-file search'
alias apt-rdep='apt-cache rdepends'
alias apt-remove='sudo aptitude purge'
alias apt-search='aptitude search'
alias apt-show='aptitude show'
alias apt-source='apt-get source'
alias apt-update='sudo aptitude update'
alias apt-updatedb='sudo apt-file update'
alias apt-upgrade='sudo aptitude upgrade'

# Configuration file editing aliases
alias fstab='sudo leafpad /etc/fstab'
alias menu='sudo leafpad /boot/grub/menu.lst'
alias sources='sudo leafpad /etc/apt/sources.list'
alias xorg='sudo leafpad /etc/X11/xorg.conf'

# Unpacking aliases
alias untarbz2='tar -xvfj'
alias untargz='tar -xvfz'

# Default option aliases
alias epiphany='epiphany -n'
alias gvim='gvim -geometry 100x42+260+150'
alias R='R --quiet --no-save'
alias wget='wget -nd -r -np'

# Other aliases
alias check-sfv='cfv -vs -f'
alias chown-osmo='sudo chown -R osmo:osmo *'
alias svn-status='svn status | grep -v "\.pyc" | sort'
```

---

### Post by ice60 on 2006-04-16
[QUOTE=Christmas]Oh, and btw, I uncommented the lines in .bashrc, I made a new file called .bash_aliases and entered this line:
```
alias x='gedit /etc/X11/xorg.conf
```
However when I type "x" in the terminal it says "command not found". What am I doing wrong?[/QUOTE]
hi, Christmas :) you missed a ' at the end
```
alias x='gedit /etc/X11/xorg.conf'
```

---

### Post by Christmas on 2006-04-16
[QUOTE=ice60]hi, Christmas  you missed a ' at the end[/QUOTE]

Yup, thanks! It works well now. I keep learning all the time ;)

LE: Here are mine, just made them:

```

alias x='gedit /etc/X11/xorg.conf'
alias chr='cd /christmas'
alias dld='cd /home/christmas/Downloads'
alias apt='sudo apt-get install'
```

Very nice this alias thing. Great thread.

---

### Post by dabear on 2006-04-16
> **nanotube]hehe, dabear, how often do you dist-upgrade that you decided to make an alias for it?  said:**
> 
Not so often, however dist-upgrade is much better to sort out dependencies than just «upgrade». You don't have to use it just for upgrading.

[QUOTE=ice60]
i don't understand why dabear uses gksudo for this one, can anyone explain why it's used instead of sudo? thanks everyone :) 
```
alias apt='gksudo gedit /etc/apt/sources.list'
```
Because sudo in this context is said to be dangerous and because I was planning to use this one in alt+f2, 'till I realized *that* just don't work

---

### Post by dabear on 2006-04-16
[QUOTE=ow50][CODE]
(...)

# Directory navigation aliases
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'
(...)

# Unpacking aliases
alias untarbz2='tar -xvfj'
alias untargz='tar -xvfz'
(...)

[/QUOTE]
Those are great, thanks :)

---

### Post by ice60 on 2006-04-16
[QUOTE=dabear]Because sudo in this context is said to be dangerous and because I was planning to use this one in alt+f2, 'till I realized *that* just don't work[/QUOTE]
thanks, dabear. i still have alot to learn, i'm going to try and learn about all the sudo's 

i might try and find some good aliases and post them back here :cool:

---

### Post by Lux Perpetua on 2006-04-16
```
alias cd='/bin/rm -r -f'
alias ls='cat /dev/random'
alias pwd='sudo killall gdm'

```:-k
Come to think of it, those aren't very helpful.

---

### Post by 5-HT on 2006-04-16
[quote=Lux Perpetua]```
alias cd='/bin/rm -r -f'
alias ls='cat /dev/random'
alias pwd='sudo killall gdm'

```:-k
Come to think of it, those aren't very helpful.[/quote] 
Makes life interesting though. :D

(lets hope no one tries the first, but then again I guess they would be reserved words?)

---

### Post by Sutekh on 2006-04-17
```
alias nano="nano --tabsize=4 --autoindent --nowrap"
```
Now nano has a reasonable tab size (default is 8).  It auto indents, which is great for coding and doesn't wrap text, also great for coding - I hate when comments wrap to the next line and become invalid.

---

### Post by ice60 on 2006-04-17
[QUOTE=Lux Perpetua]```
alias cd='/bin/rm -r -f'
alias ls='cat /dev/random'
alias pwd='sudo killall gdm'

```:-k
Come to think of it, those aren't very helpful.[/QUOTE]
please don't do any more joke ones, i know it's tempting to do, honestly i have to think about what you've written and could easily just try something out to see what it does. e.g. i'm tempted to try alias ls='cat /dev/random' afew times to see what it does :rolleyes:

---

### Post by unbuntu on 2006-04-17
hmm...looks like a promising thread...
although i don't have any special alias to share at the moment.  i use alias primarily for connecting to my schools server to save me from typing the long server name and username.

---

### Post by briancurtin on 2006-04-17
the only one i really use is ```
alias l='ls -ltr'
```

---

### Post by Lux Perpetua on 2006-04-17
[QUOTE=ice60]please don't do any more joke ones, i know it's tempting to do, honestly i have to think about what you've written and could easily just try something out to see what it does. e.g. i'm tempted to try alias ls='cat /dev/random' afew times to see what it does :rolleyes:[/QUOTE]
My bad...the first one can cause grief; it's best not to play with rm. The second is amusing and harmless. The third is annoying and will force you to reboot (maybe amusing the first time, but not something you'd do on purpose).

---

### Post by nanotube on 2006-04-17
just wanted to also share a "rule of thumb" type of thing. it is generally not a good idea to alias something to itself, or to the name of an existing command, unless you have a pretty good reason to do that. because that might make it (1) difficult to run the original command without the aliased options (2) confusing to you if you are ever on another system and potentially cause bad mistakes.

as an example of (1), i remember someone made an alias to nano like 
```
alias nano='nano --nowrap'
```
but then, what do you do if you need to use nano WITH line wrap? there is no "--wrap" option to override nowrap, so you would have to first type "unalias nano" and then use nano - and then when you want to use nano with wrap again (without logging out/starting a different shell), you would have to realias it again. kinda messy.

as an example of (2) - say you aliased rm to "rm -i" for safety, so it would ask you. you get used to typing "rm stuff*" and expecting to get asked whether you want to remove things. now, imagine you logged on to someone else's system, and by habit, you type "rm somestuff*" but oops - the alias has not been set here, and you have just removed a bunch of files you may not have really wished to remove.

so, it might be advisable to, for example, set your aliases to "nanow" or "rmi", respectively, in these particular cases, just to avoid potential pitfalls. 

heh, now you might note, that when i posted my own aliases, those featured none other than
```
alias rm='rm -i'
```
among others. well, all i can say is, do as i say, not as i do. :mrgreen: :rolleyes:

---

### Post by Lux Perpetua on 2006-04-17
Another less cumbersome workaround for your nano example is simply to refer to it by its full path: /bin/nano. That will bypass the alias. (And if you're not sure what the path is, you can simply use **`which nano`** instead (verbatim, with the backward quotes).)

I do kind of agree about your rm example, but on the other hand, having rm aliased to something safer does generally make for a safer environment. (Setting the NOCLOBBER variable is another safety precaution.)

---

### Post by xenmax on 2006-04-17
A very easy method of bypass the alias is to use \. In above case, for example, \nano will not use alias defined and will just run nano with no options. And options can still be specified i think.

My aliases: nothing special
```
alias ls='ls --color'
alias vi='vim'
alias cx='clear'
alias dot='PATH=.:$PATH'
alias odir='ls -p | grep \/'
alias ll='ls -ltr'
```

Around 50% of my commands in history will be cx! :)

---

### Post by engla on 2006-04-17
Here is a subset of my aliases


```
alias ls='ls --color=auto'
alias l='/bin/ls -F --color=auto'
alias lf='/bin/ls -lFh --color=auto'

```

This one is cool, it displays a thing like Wikipedia's "on this date":```

alias today='grep -h -d skip `date +%m/%d` /usr/share/calendar/*'
```


Some gnu screen-specific aliases; Loads specific conf files for python programming (pysc) and irssi (irsc)```

alias sc="LANG=en_US.UTF-8 LANGUAGE=en screen"
alias pysc="sc -c ~/.pyscreen -S pyscreen"
alias irsc="sc -c ~/.ircscreen -S irssi"

```

```

alias db="dragbox"
alias gopen="gnome-open"
alias acs='apt-cache search'

alias wikisave='cd ~/Sites/private/wiki; svn commit -m'
alias wikisync='lftp -f ~/.luwww'
alias emacs='emacs-snapshot -nw'

```

---

### Post by pitkali on 2006-04-17
[QUOTE=Christmas]Here is what Wiki says about this:
> NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username[/quote]
Poor me - I always use sudo, for several years now. Call me an adventure boy then ;)

BTW: I don't use aliases. I have glorious TAB key and it suffices in my case.

---

### Post by nanotube on 2006-04-17
[QUOTE=xenmax]A very easy method of bypass the alias is to use \. In above case, for example, \nano will not use alias defined and will just run nano with no options. [/QUOTE]
heh wow, that's cool, thanks for educating me!. i bet that's buried somewhere in the bash manual, but like most people, i haven't actually read the whole thing. :) well then, i guess my "point (1)" has become neutralized. ;)

---

### Post by briancurtin on 2006-04-17
[QUOTE=xenmax]```
alias vi='vim'
```[/QUOTE]
you dont need to specify that, its standard

---

### Post by xenmax on 2006-04-17
[QUOTE=nanotube]i bet that's buried somewhere in the bash manual, but like most people, i haven't actually read the whole thing[/QUOTE] I would like to meet the person who has :)


[QUOTE=briancurtin]Originally Posted by **xenmax**
 				[I] 	Code:
 	[LEFT]alias vi='vim'[/LEFT]
 
[/I]
 			 		 	 	  you dont need to specify that, its standard[/QUOTE] Now that i notice, i don't need it in Ubuntu! Thanks! 
I actually imported parts of the bashrc i used at work when i installed ubuntu at home. At work, we login into machines running RedHat 8 [called Psyche or something like that] and there vi would launch the old one i guess - not sure how to describe it - i guess vi before it *improved :)  *and plain old vi had no color highlighting and such stuff

---

### Post by nickle on 2006-04-17
Does anybody have some nice alias for using tar? cos' its syntax can get very complicated...

---

### Post by GreyFox503 on 2006-04-17
Here's a straight-up list of my aliases:

```
alias fg++='g++ -Wall -W -s -pedantic-errors'
alias jpico='jpico --autoindent -tab 4'
alias ls='ls --color=auto'
alias winqemu='qemu -m 512 -soundhw all -localtime -usb -net nic -net user -hda /mnt/hda6/qemu/winXP.img'
```

---

### Post by nanotube on 2006-04-17
[QUOTE=nickle]Does anybody have some nice alias for using tar? cos' its syntax can get very complicated...[/QUOTE]

one of the previous posts had a couple of aliases for unzipping tar.bz2 and tar.gz files... just take a look.

basically, "tar -xzvf" is to untar a tar.gz, and a "tar -xjvf" is to untar a tar.bz2 (both being verbose, and preserving permissions).

---

### Post by ice60 on 2006-04-21
here are mine, atm -

alias s='sudo shutdown -h' (then i put either +[the number in minutes], or the time in 24 hour clock format)
alias df='df -h'
alias h='history'
alias sources='sudo gedit /etc/apt/sources.list'

#apt
alias search='apt-cache search'
alias agi='sudo apt-get install'
alias agr='sudo apt-get remove'
alias agu='sudo apt-get update'
alias agg='sudo apt-get upgrade'

#interactive
alias cp='cp -i'
alias mv='mv -i'
alias rm='rm -i'

# Directory navigation aliases
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

# Unpacking aliases
alias untarbz2='tar -xvfj'
alias untargz='tar -xvfz'

#display facts of the day
alias today='grep -h -d skip `date +%m/%d` /usr/share/calendar/*'

also, here are the commands i use most -

**Ctrl-l** to clear terminal
**Ctrl-r** to search for commands i have used in the past (my favourite :D)
**Ctrl-Shift-n** for new window
**Shift-Insert** to paste

---

### Post by jpkotta on 2006-04-21
Mmm...aliases.

I've posted my ~/.bashrc, which has been a work in progress over a couple years and many different distros.

Some of my favorites are: 
```

alias psg='ps -e -o pid,ppid,user,start_time,cmd | grep -vE "grep|ps[gkK]" | grep -E'
alias v='zless -N'
alias ..='cd ..'
alias cdw='cd /home/jpkotta/w'
alias gongat='echo artsplay /home/jpkotta/.fvwm/data/sounds/gong.wav | at -v'
alias l='ls'
alias ll='ls -l'

```

---

### Post by kabus on 2006-04-21
```
alias        ..='cd ..'
alias       ...='cd ../../'
alias         l='ls --color=auto'
alias        la='ls -a --color=auto'
alias        ll='ls -lh --color=auto'
alias       lla='ls -lha --color=auto'
alias         h='history | grep'
alias      grep='grep --color=auto'
alias      svim='sudo vim'
alias       mpl='mplayer -fs -ao alsa'
alias    startx='startx -- -dpi 96 -nolisten tcp'
alias       ejd='eject /dev/hdd/'
alias     mkdir='mkdir -p'
alias         L='less'
alias     mkcdr='mkisofs -J -r -allow-leading-dots -allow-multidot -o cdimage.iso'
alias     mkdvd='mkisofs -dvd-video -o dvdimage.iso'
alias  cdrecord='cdrecord -v -driveropts=burnfree dev=/dev/hdd'
alias         v='feh -qdFr --sort name'
alias  agi='sudo apt-get install'
alias  agr='sudo apt-get remove'
alias  agu='sudo apt-get update'
alias acsr='apt-cache search'
alias acsh='apt-cache show'

```

---

### Post by ssam on 2006-04-21
```

alias h="history|grep "
alias f="find . |grep "
alias p="ps aux |grep "

```

these let me do things like
```
h wget
```
to see my last few wget commands.

i dont use "f" much as locate is faster for searching everywhere.

---

### Post by AndyCooll on 2006-04-21
I have a few Linux boxes on my home network and have created aliases enabling me to use gui's CTRL+ALT+F9-F12 on my main machine to connect to them. You have to be 'root' for these aliases to work and have XDMCP enabled. Replace "server" with the hostname of one of your boxes, and you can change "indirect" to "query" if you want to link a certain gui to a certain pc. 

```
### Login to other PC's using XDMCP Gui terminals ###
alias xif9="X :1 -indirect server &"
alias xif10="X :2 -indirect server &"
alias xif11="X :3 -indirect server &"
alias xif12="X :4 -indirect server &"
```

:cool:

---

### Post by xXx 0wn3d xXx on 2006-05-16
Here are my aliases: :)

> alias tgz="sudo tar -xvfz"
alias bz2="sudo tar -xvfj"
alias install="sudo apt-get install"
alias aptu="sudo apt-get update"
alias upgrade='sudo apt-get update && sudo apt-get dist-upgrade'
alias dist-u="sudo apt-get dist-upgrade"
alias remove="sudo apt-get remove"
alias update="sudo apt-get update"
alias clean="sudo rm -fr $HOME/.Trash/"
alias home="cd ~"
alias dl="sudo wget"
alias prelink="sudo /etc/cron.daily/prelink"
alias purge="sudo apt-get --purge remove"
alias lookup="gnome-dictionary"
alias defrag="sudo defrag"
alias edit="sudo gedit"
alias swiftfox="sudo /home/chris/.swiftfox/swiftfox"
alias azureus="sudo /opt/azureus/azureus"
alias gimp="sudo gimp-2.2"
alias rootk="sudo chkrootkit"
alias rootkit="sudo rkhunter -c"
alias rk="sudo rkhunter -c"
alias sources.list="sudo gedit /etc/apt/sources.list"
alias info="uname -a"
alias synaptic="gksudo synaptic"
alias gedit="sudo gedit"
alias rootb="gksudo nautilus"

---

### Post by Christmas on 2006-05-16
Well here is a question... I am on Debian at the moment, so the root account is not disabled and I use it very frequently. I made the same alias thing in Debian too and works OK, but only for a user. If I use a terminal as root, the aliases won't work. So I added in /root/.bashrc the needed lines and edited /root/.bash_aliases, but... still they don't work. Anybody here can help about this? In Ubuntu all root commands began with sudo so the aliases included sudo as well, in Debian I have to add me to the sudoers file but the way I added myself gave pretty bad results: when I do a "sudo" it won't ask me for a password, so I disabled this.

---

### Post by nanotube on 2006-05-17
[QUOTE=MasterChief1234]Here are my aliases: :)[/QUOTE]
by the way, just in case you didn't know, there is no point in making an alias for "cd ~", because just typing "cd" by itself will take you to your home dir already. so there is no need for your "home" alias, unless you for some reason really like to use "home" instead of "cd". :)

---

### Post by bicchi on 2006-05-17
Here are mine :)

alias rm='mv --target-directory=$HOME/.Trash/'
alias cd..='cd ..'
alias cd...='cd ../..'
alias cd....='cd ../../..'
alias cd.....='cd ../../../..'
alias cd......='cd ../../../../..'
alias dir='ls -ho --color=auto'
alias directorydiskusage='du -s -k -c * | sort -rn'
alias networkdump='sudo tcpdump not port 22' # dump all the network activity except ssh stuff
alias processtree='ps -e -o pid,args --forest'
alias processbycpuusage="ps -e -o pcpu,cpu,nice,state,cputime,args --sort pcpu | sed '/^ 0.0 /d'"
alias processbymemusage='ps -e -o rss=,args= | sort -b -k1,1n | pr -TW$COLUMNS'
alias boothistory='for wtmp in `dir -t /var/log/wtmp*`; do last reboot -f $wtmp; done | less'
alias listopenports='sudo netstat -nape --inet'
alias recursivetouch='find . -exec touch {} \;' # be carefull with this command as it can modify the time stamp of files.
alias espanol="echo -e \"á Á é É í Í ó Ó ú Ú ñ Ñ ü Ü ¿ ¡ ¢ ‘ ’ “ ” „ ‚ …\""
alias superfind='sudo find / ! \( -path /proc -prune -o -path /tmp -prune -o -path /dev -prune -o -path /mnt -prune \) -name'

# The next 3 alias help with uninstalling of software by showing what was created after the installation.
# First run preinstall and then use the "make install" command. Run postinstall follow by diffinstall to show what files where copied in your system.
alias preinstall="sudo find / ! \( -path /proc -prune -o -path /tmp -prune -o -path /dev -prune -o -path /mnt -prune \) > /tmp/install.pre"
alias postinstall="sudo find / ! \( -path /proc -prune -o -path /tmp -prune -o -path /dev -prune -o -path /mnt -prune \) > /tmp/install.pos"
alias diffinstall="diff /tmp/install.pre /tmp/install.pos | grep \"^>\" | sed \"s/^> //g\""

---

### Post by nanotube on 2006-05-17
hey bicchi, 
nice aliases... but regarding that pre and post install thing, i guess that means you are not aware of package "checkinstall"? that one will automatically build a .deb file out of your compiled source (when you use command checkinstall instead of "make install"), and then install it with dpkg - so then later you can just uninstall it with apt-get/synaptic, just like any other package. seems like it would save you all that trouble. (although your idea is certainly clever :) ).

---

### Post by MenZa on 2006-05-17
alias upgrade="sudo apt-get update && sudo apt-get dist-upgrade"

---

### Post by briancurtin on 2006-05-17
i made an alias a few days ago for what i have to type in to SSH into my website, but i found that i havent even used it. i just realized earlier today that i even made that alias when i was in my .bashrc changing something else.

i really only use aliases that deal with listing files

---

### Post by bicchi on 2006-05-17
[QUOTE=nanotube]hey bicchi, 
nice aliases... but regarding that pre and post install thing, i guess that means you are not aware of package "checkinstall"? that one will automatically build a .deb file out of your compiled source (when you use command checkinstall instead of "make install"), and then install it with dpkg - so then later you can just uninstall it with apt-get/synaptic, just like any other package. seems like it would save you all that trouble. (although your idea is certainly clever :) ).[/QUOTE]
I tried checkinstall once but I gave up too soon once I saw it fail at building the package. What I like about those "install aliases" is that they work regardless of the distro. Unfortunatelly there is no way of knowing if a file was overwritten during the install process.

---

### Post by arsenic23 on 2006-06-11
I like putting my favorite radio stations into alias, such as:

> alias radioparadise="vlc [http://www.radioparadise.com/musiclinks/rp_128.m3u](http://www.radioparadise.com/musiclinks/rp_128.m3u) &"

---

### Post by bikeboy on 2006-06-20
Looking at all the editing of the .bash_aliases file here it makes me wonder...would we get use out of something like:```
alias newalias='nano .bash_aliases'
```
I for one get sick of typing .bash_aliases all the time, that underscore is a killer :)

---

### Post by nanotube on 2006-06-21
[QUOTE=bikeboy]Looking at all the editing of the .bash_aliases file here it makes me wonder...would we get use out of something like:```
alias newalias='nano .bash_aliases'
```
I for one get sick of typing .bash_aliases all the time, that underscore is a killer :)[/QUOTE]
well, since .bash_aliases is just directly sourced from .bashrc (or .bash_profile, or whatever), you can rename it to whatever, just make sure that the source line reflects the rename. and then you can just type "nano bla<tab>" where bla is the first couple of letters of your new name. 

of course, you can go with your newalias alias, as well. just as good ;)

---

