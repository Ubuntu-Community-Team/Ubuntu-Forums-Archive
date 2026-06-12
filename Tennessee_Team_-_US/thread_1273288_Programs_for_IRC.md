---
title: "Programs for IRC?"
date: 2009-09-23
forum: Tennessee Team - US
---

### Post by secristrc on 2009-09-23
What are the recommended program(s) for using IRC under Ubuntu?  Most of the IRC FAQ material talks about what to do once you're already "in," and barely anything about software.

Thanks,
rcs

---

### Post by mac9416 on 2009-09-23
Hey, secristrc,

I personally use [**XChat**]("http://www.xchat.org/"). It's sort of a hackerish-looking program. To install it, run:
```
sudo apt-get install xchat
```

A lot of people use [**Pidgin**]("http://www.pidgin.im/"), which is more beginner-friendly, but not as powerful (as far as IRC goes). It also supports many other protocols besides IRC. It comes with Ubuntu by default.

Then there's [**irssi**]("http://irssi.org/"). It is command-line, therefore not really beginner-friendly, but I must admit it's kinda cool. You can install it with:
```
sudo apt-get install irssi
```

There are many others, but those are the ones I'm familiar with.

I hope that helps!
-mac

---

### Post by andrew.46 on 2009-09-23
Hi mac,

> **mac9416 said:**
> Then there's [**irssi**]("http://irssi.org/"). It is command-line, therefore not really beginner-friendly, but I must admit it's kinda cool.


I believe there is also an irssi guide on these forums:

[Howto] Setup irssi and join #ubuntu on Freenode
[http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

Andrew

---

### Post by mac9416 on 2009-09-23
Thanks, andrew.46 :)

I also found some howtos for XChat and Pidgin:
[https://help.ubuntu.com/community/XChatHowto](https://help.ubuntu.com/community/XChatHowto)
[https://help.ubuntu.com/community/Pidgin](https://help.ubuntu.com/community/Pidgin)

---

### Post by EricG on 2009-09-24
If you're using Kubuntu or KDE, Quassel is another IRC client that you could use. I think it comes installed by default in kubuntu and can be accessed under Applications -> Internet.

---

### Post by w4ett on 2009-09-25
Assuming you use Firefox, there is an IRC add on called ChatZilla too..simple to use and worth mentioning.

[https://addons.mozilla.org/en-US/firefox/addon/16](https://addons.mozilla.org/en-US/firefox/addon/16)

---

### Post by mystdragon on 2009-09-25
I recommend irssi.  They've got great documentation for getting setup and started in their [documentation section]("http://irssi.org/documentation").

---

### Post by infocop411 on 2009-10-08
well, I split my time with irssi & finch, finch is a command line (ncurses) based instant messenger/chat client, if you already setup pidgin, then you've also setup finch (as soon as you install it, "sudo apt-get -y install finch" without the quotes)

---

### Post by wstout on 2009-10-11
I would have to post my vote for Quassel its pretty user friendly and has a nice gui when you get it set up. I personally use irssi if you are interested in being online all the time, it makes a great client you can ssh into it from anyway when you use it combined with screen.

EDIT: I have now discovered using quassel in a core-client setup, set up the core on your server and the quassel-client on your desktop and have the always on of irssi and a nice gui to boot.

---

