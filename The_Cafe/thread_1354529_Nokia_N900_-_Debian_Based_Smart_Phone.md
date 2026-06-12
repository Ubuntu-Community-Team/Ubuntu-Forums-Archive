---
title: "Nokia N900 - Debian Based Smart Phone"
date: 2009-12-14
forum: The Cafe
---

### Post by beastrace91 on 2009-12-14
Hey All,

So I just ordered one of these bad boys and I was wondering if anyone had taken a peek at them yet - [http://maemo.nokia.com/n900/](http://maemo.nokia.com/n900/)

They just released last month, it runs a full Linux operating system (that gives the user full control unlike Android or the OS the G1 runs) based on debian (thats right all the 18k+ debian packages that have all have an arm compiled package for them will install on it)

It also has some awesome tech specs - bar far one of the strongest phones on the market currently :D

~Jeff

---

### Post by Firepower-EX on 2009-12-14
Gimme Snapdragon and we'll talk. :l

Yeah, the specs are very good for a mobile device, and Maemo is extremely promising. I would seriously gladly flash WinMo on my phone for that is they make an installer

---

### Post by beastrace91 on 2009-12-14
Hmm, Snapdragon looks interesting. Too bad there isn't a release date on it any time soon ;)

~Jeff

---

### Post by Icehuck on 2009-12-14
Typing commands out on a phone gets really old really quick. Just an FYI

---

### Post by earthpigg on 2009-12-14
> **Icehuck said:**
> Typing commands out on a phone gets really old really quick. Just an FYI

so create a GUI frontend, or a simple .desktop file.

or even an alias in .bashrc. for example, i haven't typed "free -m" or "htop" in ages. i type "f" or "h" and press enter. have you typed those full commands out lately?????! if so, ***why***?!

anywho, im mostly posting here so i can find this thread and the discussion later :D

---

### Post by beastrace91 on 2009-12-14
Thehehe how exactly to I create an alias command in termina? (I've wondered about this for awhile now)

And Dell just delayed my order so it looks like I won't be getting my new toy till after the first of the year :-/ Which sucks because my black berry is super crappy.

~Jeff

---

### Post by earthpigg on 2009-12-14
> **beastrace91 said:**
> Thehehe how exactly to I create an alias command in termina? (I've wondered about this for awhile now)

```
gedit .bashrc
```

(or leafpad .bashrc or nano .bashrc, etc)

pick a spot in that file, make it your little alias area.

```
alias = whatitype='echo "Yay, the alias worked!"'
```

save, close. ***close the terminal window***. open a new one, so the modified .bashrc can take effect.

```
[chris: ~]$ whatitype
Yay, the alias worked!
[chris: ~]$ 

```

i maintain a 'master' .bashrc that i use on new installs, and when i create a new user i usually copy my .bashrc to their home folder so they can use it.

there is an outstanding thread around where people post their .bashrc. there are also such threads on pretty much every distro's forum. steal ideas from a bunch of them to put your own together. any distro that uses bash (ubuntu, arch, opensuse, etc) can use the exact same .bashrc stuff.

until you feel like diving into one of those threads, ill post a few .bashrc items that i consider 'must have'...

```
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'
```

^ so you can just type .. to go up a directory. ... to go up 2, .... to go up 3, etc.

```
alias la='ls -a --color=auto'
alias l='ls --color=auto'
alias dfg='df -Th -x tmpfs'
alias f='free -m'
alias t='htop'
alias e='exit'
```

```
alias myip='echo My IP is && curl http://www.whatismyip.com/automation/n09230945.asp && echo'
```

at the end of .bashrc, a lot of folks put personal welcome messages.

```
export GREP_OPTIONS='--color=auto'
echo -en "\033[1;36m"
echo "                        Chris' Desktop"
echo -en "\033[0m\n"
fortune -o
```

^ also useful if you use ssh a lot, so you get a friendly reminder of what system you are on... yes, ive run commands on the wrong computer because i had ssh'd into the wrong computer and didn't realize it lol.

---

### Post by beastrace91 on 2009-12-14
Neat - thanks for the tips :)

Aliasing commands like that will be super helpful when hacking out bash on a cell phone keypad :)

~Jeff

---

### Post by Duncan J Murray on 2009-12-29
Anyone else got hold of this phone?

I'm quite tempted to get one.  I would use it for:

+ internet
+ email
+ calendar/diary
+ word processing
+ note taking
+ non-artistic photographs
+ GPS and navigation
+ texting
+ playing MP3s in-car
+ maybe playing video if it's good enough

I have a Nokia E90, which is, in theory, capable of almost all of the above.  It fails though in some way in almost all areas:

+ internet - not bad, but very fiddly using 'web'
+ email - pretty good, actually
+ calendar/diary - doesn't make good use of screen space.  I installed aqua calendar instead
+ word processing - for some reason slow and sluggish, sometimes the delay between typing and seeing what you've written is ridiculous
+ note taking - pretty good - active notes is excellent
+ non-artistic photographs - also pretty good.  Though can be out-of-focus when doing close ups.
+ GPS and navigation - ovimaps and googlemaps are ok.  I used to be able to install TomTom on it, and it was amazing, but the firmware update put an end to that.
+ texting - excellent
+ playing MP3s in-car - nope.
+ maybe playing video if it's good enough - I tried on the E90, and gave up.


Any comment on the above.  Is it time to replace my E90?

All best,

Duncan.

---

### Post by dragos240 on 2009-12-29
Can it use apt? (Since it's based on debian)

---

### Post by beastrace91 on 2009-12-29
> **dragos240 said:**
> Can it use apt? (Since it's based on debian)

Yep it runs apt-get OOTB from what I have read and you can add the debian repositories to it (which are suppose to work just fine on it) simply by adding the url to your /etc/apt/sources.list on the phone.

I have not gotten mine yet but it is suppose to be here some time this week (Darn backorder making it take forever!)

~Jeff

---

