---
title: "TOR Browser - keyboard malfunction / Keyboard issue - Ubuntu 13.10"
date: 2014-03-08
forum: Security
---

### Post by g999b on 2014-03-08
Hi,

I have been using TOR for a while on my Ubuntu 12.04 -> no problem

I recently upgraded to Ubuntu 13.10. The "start-tor-browser" script would not launch (in 12.04, Ubuntu would ask me "Do you want to run this script in the Terminal?", I click on yes -> done)... So to work around this, I made the script executable and launched it from the terminal -> problem solved, TOR starts successfully.

But now something strange happens: I can use TOR all right, except that I cannot input anything from the keyboard : no URL, no search, etc. Keyboard is not responding. Meanwhile, in my terminal window (from which I launched TOR) this message appears:

*(firefox:3834): IBUS-WARNING **: Events queue growing too big, will start to drop.*

If anyone can help to solve this problem that'd be great. 

Good day to all

---

### Post by bashiergui on 2014-03-09
Download the latest Tor browser bundle and launch it from the terminal. Cd to your Downloads folder and then type ```
./start-tor-browser
```

---

### Post by g999b on 2014-03-11
Hey Bashiergui, thanks for the contribution... Unfortunately it does not change anything. When I launch Tor using 13.10 (from the Terminal - I dont know how else to launch it anyway) I cannot input anything (URL, search string etc.) This is just plain weird...

If anyone knows another one to launch Tor NOT from the terminal, I'd be curious to give it a shot.

Thanks

---

### Post by raja.genupula on 2014-03-11
you getting anything else rather than only that single message ?

---

### Post by untrustytahr on 2014-03-11
These may help:

[http://askubuntu.com/questions/375826/keyboard-doesnt-work-with-tor-browser/377321#377321](http://askubuntu.com/questions/375826/keyboard-doesnt-work-with-tor-browser/377321#377321)

[https://trac.torproject.org/projects/tor/ticket/9353#comment:40](https://trac.torproject.org/projects/tor/ticket/9353#comment:40)

---

### Post by bashiergui on 2014-03-11
Looks like untrustytahr has the solution. 

An alternate way to achieve the same thing is here [http://ubuntuforums.org/showthread.php?t=2183308](http://ubuntuforums.org/showthread.php?t=2183308)

---

### Post by g999b on 2014-03-15
Hi all,

Problem solved... the issue was with ibus... 

Thanks to all for your replies. Special kudos to [ 						 							]("http://ubuntuforums.org/member.php?u=1895014")[**[COLOR=#000000]untrustytahr[/COLOR]**]("http://ubuntuforums.org/member.php?u=1895014") and [URL="http://ubuntuforums.org/member.php?u=1879546"]**[COLOR=#000000]bashiergui[/COLOR]**[COLOR=#000000]
[/COLOR]

[/URL]

---

### Post by untrustytahr on 2014-03-15
Glad to hear it g999b.  
If you could, just give a quick blurb describing what you did to fix it for future viewers of this thread if those links ever go dead. thx

---

### Post by g999b on 2014-03-15
OK!

So what I did to solve this problem, since the problem is with ibus... 

The idea is to neutralize Ibus since it is the cause of the problem. 

Completely removing Ibus from the system is definitely one option, and you can do it like this:

```
sudo apt-get remove ibus
```

Tor would then operate normally... but I am gainst death penalty and I dont want to find myself in a situation where I have to re-install Ibus for whatever reason in the future. So the idea becomes to **temporarily** halt Ibus when I need Tor... Ibus can be halted on any terminal just by typing:

```
Ibus exit
```

If I launch Tor after doing this it would operate normally, for this session, while I dont have to delete/remove Ibus.

But I want to make this automatic, I dont want to have to think "Oh I should exit Ibus, bc. I have to start Tor... right?" ... It should be seamless...

So I have added one line in .bash_aliases in order to ask my system to 1. exit Ibus and then only 2. launch Tor. I have done this by adding this line to my ,bash_aliases:

```
alias start_tor='ibus exit; /path/to/folder/tor-browser_en-US/start-tor-browser &'
```

Of course you need to replace /path/to/folder/ with your own destination depending where you installed the Tor browser on your system

Hope the above is clear!

---

