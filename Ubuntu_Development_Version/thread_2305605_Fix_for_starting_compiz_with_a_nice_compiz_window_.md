---
title: "Fix for starting compiz with a nice compiz window decorator"
date: 2015-12-07
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2015-12-07
Booted up Xubuntu today and compiz would not start no matter what I did. I fiddled with it an hour or so and decided to put in a delay and that worked.

```
cavsfan@cavsfan-le-beast:~$ cat /etc/*release && uname -r
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu Xenial Xerus (development branch)"
NAME="Ubuntu"
VERSION="16.04 (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
UBUNTU_CODENAME=xenial
4.3.0-2-generic

```

I also found out something yesterday. Everywhere you look it says to put **/usr/bin/compiz** in CCSM Window Decoration.
That did not work. But found something that did for a change. Putting **/usr/bin/compiz-decorator** in CCSM Window Decoration provides a nice window decorator.

[ATTACH=CONFIG]266025[/ATTACH]

But Compiz would not simply startup with the old **compiz --replace** in startup commands.
I had to create a script with a 5 second delay for it to work properly.

I added this to a file I named compiz-startup in the /bin folder of my home directory and made it executable.
```
#!/bin/bash
# pause before starting compiz
sleep 5
compiz --replace
```

Then instead of **compiz --replace** in startup command I put **./bin/compiz-startup** instead and it works like a charm every time.

Hopefully this will help someone else. I never knew compiz had such a nice window decorator before.

---

### Post by QDR06VV9 on 2015-12-07
> [COLOR=#000000]I also found out something yesterday. Everywhere you look it says to put [/COLOR][B]/usr/bin/compiz in CCSM Window Decoration.
That did not work. But found something that did for a change. Putting [B]/usr/bin/compiz-decorator in CCSM Window Decoration provides a nice window decorator.
[/B][/B]
That means I would have to give up on Emerald:p

---

### Post by ventrical on 2015-12-07
@cavsfanThanks for the info. I do not usually use compiz(ccsm) on xubuntu. I usually end up busting it completely.

Regards..

---

### Post by QDR06VV9 on 2015-12-07
> **ventrical said:**
> @cavsfanThanks for the info. I do not usually use compiz(ccsm) on xubuntu. I usually end up busting it completely.

Regards..
Only if you are interested in a little Eye candy for XFCE.
Some of our users in the general area of the forum are using Kwin with XFCE
[http://www.thelinuxrain.com/articles/tutorial-how-to-use-kwin-window-manager-with-xfce](http://www.thelinuxrain.com/articles/tutorial-how-to-use-kwin-window-manager-with-xfce)
Kind Regards

---

### Post by Cavsfan on 2015-12-07
> **runrickus said:**
> That means I would have to give up on Emerald:p

I've always used Emerald too, still am in Arch but while I was purging things trying to fix the problem I had; it purged emerald and it's associated lib.

While putting it back together I stumbled upon, well really just noticed :P in /usr/bin/ there was the compiz file as well as compiz-decorator and put that in there and viola a nice window manager similar to Emerald.
Since Emerald is not readily available in Xenial... I'll just use this new found treasure. :P


> **ventrical said:**
> @cavsfanThanks for the info. I do not usually use compiz(ccsm) on xubuntu. I usually end up busting it completely.

Regards..

You're most welcome! :) I know that compiz is hard to get setup and easily breaks your system but it's just something I have to have. 

[ATTACH=CONFIG]266035[/ATTACH]

> **runrickus said:**
> Only if you are interested in a little Eye candy for XFCE.
Some of our users in the general area of the forum are using Kwin with XFCE
[http://www.thelinuxrain.com/articles/tutorial-how-to-use-kwin-window-manager-with-xfce](http://www.thelinuxrain.com/articles/tutorial-how-to-use-kwin-window-manager-with-xfce)
Kind Regards

Got to have eye candy! I wish they'd get the fusion-icon fixed in Ubuntu! It makes it so easy to switch and control your WM.
I have kept my Arch system very clean about not mixing any other DE apps in with Xcfe and I'm feeling it in Ubuntu too.
 I generally use  Xfwm4 in Arch and Xfwm in Xubuntu for the alternate WM. Instead of gedit I use mousepad instead. :P

I play like one game Super Tux2 and it doesn't work right with a compiz WM, I set it to Xfwm while playing it.
Of course I've got a couple of gnome games like mahjong lol but that is about it.

Cheers

---

### Post by Cavsfan on 2015-12-08
BTW, if you are using compiz WM you cannot get to window manager settings.

So, I switch to Xfwm, then go to window manager settings and change the Window Operations Menu shortcut from space+Alt to something else.
Becuse in Super Tux2 I have space set to jump and alt set to "take action" like shoot, etc.

Without doing that the Window Operations Menu pops up and I get killed all the time. :lol:

But after fininshing the game I change it back to compiz. :p

---

