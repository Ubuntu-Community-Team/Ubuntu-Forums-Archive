---
title: "Lucid, Tor and Polipo (plus Vidalia?) problem"
date: 2010-05-03
forum: Security
---

### Post by nicknefarious on 2010-05-03
Hi all,

I have just started building my new Lucid (64bit) install. Previously I had Karmic 64 bit running with Tor and Polipo installed, using Torbutton in Firefox and Proxy Switchy with Chrome - absolutely no problem.

In Lucid I can't get either Firefox or Chrome to work through Tor.

Or perhaps, more as I believe, Tor is not working properly. I installed Vidalia to see if I could see a bit more about what was going on. In Vidalia's logs it seems Tor is not connecting properly. (I have included a copy of the log's attached below).

Secondly the package in the Tor Community repos is still Karmic... There is not yet a Lucid package. My assumption is that the Karmic package is not playing nice in Lucid but I don't know why or how to fix it. Can anyone light the way for me here?

And finally there seems to be some confusion around about the necessity for Vidalia... but I believed that you don't need Vidalia to run Tor with Polipo and Firefox or Chrome. Am I right here?

Thanks to anyone who can give me back the past couple of hours of my life...

Nick

---

### Post by olive.ewe on 2010-05-03
not sure if its the same or similar problem I was having with Tor, when I started Vidalia it couldn't start Tor, which I later discovered was actually running from startup. I found this thread very useful basically check if tor is running, stop tor. Then I ran vidalia again and my problem was gone (although I have to do this anytime I have rebooted my machine and wish to use Tor again with the vidalia GUI). 
[http://ubuntuforums.org/showthread.php?p=4236484](http://ubuntuforums.org/showthread.php?p=4236484)

---

### Post by ApEkV2 on 2010-05-03
@ op, i've never seen that in the logs before, so I don't know what that problem is.


@ olive.ewe, If you installed tor, and then installed vidalia, you have to go into sysv-rc-conf (the command line) scroll down and unselect all the tor startup levels.

```
*Turn off tor...*

pidof tor
sudo kill <the pid of tor>

*Install sysv-rc-conf...*

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

*scroll down with the arrow keys (alphabetical order) should look like...*
[color=red]tor          [ ]        [X]         [X]         [X]        [X]        [ ]        [ ][/color]
*scroll over the X's for tor and "unselect" them with the spacebar*
```

If you want to use vidalia with tor, you need to make sure tor doesn't automatically start at computer's startup, sysv-rc-conf allows you to turn it off.  This is the third thread I posted this in.  Searching will help

---

### Post by olive.ewe on 2010-05-03
> **ApEkV2 said:**
>   This is the third thread I posted this in.  Searching will help


Thanks but I wasn't actually searching for help on this :P I just saw the post and thought it may have been similar to what I had come across myself months ago. i don't use tor/vidalia much for it to be an issue but I will try out what you suggest anyway

---

### Post by simon_w on 2010-05-04
@ApEkV2:

> **ApEkV2 said:**
> If you want to use vidalia with tor, you need to make sure tor doesn't automatically start at computer's startup, sysv-rc-conf allows you to turn it off.

Will using sysv-rc-conf cause the disabling to persist when services are upgraded?  I've always used ```
sudo update-rc.d -f <service> remove
``` but the rc.d links are recreated whenever a package is upgraded.  See my post [here]("http://ubuntuforums.org/showthread.php?t=1464183").  Most annoying.  I don't want polipo and tor to start by default every time I boot my machine!  Do you know a way around?

Furthermore, Vidalia will automatically start polipo (or another proxy) when tor starts, which is great, but I wish it would *stop* it again when it closes!  At the moment I'm starting Vidalia with a quick bash wrapper I wrote, but it's a pretty ugly solution.

---

### Post by simon_w on 2010-05-04
it might also be worth mentioning that you can do runlevel administration with the GUI BUM (Boot-Up-Manager) too, which might be easier for some folks.

```
sudo apt-get install bum
```

still can't make it persist across upgrades though :(

---

### Post by cadaverousmob on 2010-06-02
> **simon_w said:**
> it might also be worth mentioning that you can do runlevel administration with the GUI BUM (Boot-Up-Manager) too, which might be easier for some folks.

```
sudo apt-get install bum
```

still can't make it persist across upgrades though :(

Thanks, Simon!

---

### Post by Trollbeater on 2010-06-02
I use the Tor browser bundle for linux.  It seems to work fine for me.  Try that.

---

### Post by windeguy on 2011-08-18
> **ApEkV2 said:**
> @ op, i've never seen that in the logs before, so I don't know what that problem is.


@ olive.ewe, If you installed tor, and then installed vidalia, you have to go into sysv-rc-conf (the command line) scroll down and unselect all the tor startup levels.

```
*Turn off tor...*

pidof tor
sudo kill <the pid of tor>

*Install sysv-rc-conf...*

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

*scroll down with the arrow keys (alphabetical order) should look like...*
[color=red]tor          [ ]        [X]         [X]         [X]        [X]        [ ]        [ ][/color]
*scroll over the X's for tor and "unselect" them with the spacebar*
```

If you want to use vidalia with tor, you need to make sure tor doesn't automatically start at computer's startup, sysv-rc-conf allows you to turn it off.  This is the third thread I posted this in.  Searching will help

In my case, TOR was not running so I could not kill it.  There were X's that I turned to blanks using sysv-rc-conf as you suggested, but I am still having the same problem. Thanks for trying to help.

---

