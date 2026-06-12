---
title: "Strange problem: terminal opened in wrong directory when using CTRL+ALT+T"
date: 2019-11-20
forum: Ubuntu/Debian BASED
---

### Post by puffcorn on 2019-11-20
I have a weird issue that's probably not a big deal, but I'm hoping someone can me let know if anything is wrong.

I opened a terminal a little while back, using CTRL+ALT+T, and it opened up showing the wrong directory.

Instead of the usual **[COLOR="#008000"]name@computer[/COLOR] [COLOR="#0000FF"]~$[/COLOR]_** prompt, it showed **[COLOR="#008000"]name@computer[/COLOR] [COLOR="#0000FF"]usr/share/peppermint-settings-panel $[/COLOR]_**

I tried CTRL+ALT+T several more times, and it would open with the wrong folder showing. Earlier in the session, though, there were no problems. 

If I clicked on terminal on the panel, it would open normally.

Once I logged out and logged back in, the problem disappeared.

Even though it seems to be fine now, I can get a bit OCD and am wondering why it happened and if there might be something wrong here.

Thanks for any help.

---

### Post by #&amp;thj^% on 2019-11-20
Can you also include:
```
lsb_release -a && echo $DESKTOP_SESSION
```
Also have you changed or added any new terminals to your install?

---

### Post by puffcorn on 2019-11-20
output from lsb_release -a && echo $DESKTOP_SESSION

No LSB modules are available.
Distributor ID:	Peppermint
Description:	Peppermint 10 Ten
Release:	10
Codename:	bionic
Peppermint

No, I haven't added (or changed) any terminals.

---

### Post by #&amp;thj^% on 2019-11-20
Sorry I fixed the code box for SESSION in my above post. (I had a space where it shouldn'tbe :))
Have a look at:
```
sudo update-alternatives --config x-terminal-emulator
```
See if anything strange shows up.
I run a couple of DE's so mine shows as:
```
There are 6 choices for the alternative x-terminal-emulator (providing /usr/bin/x-terminal-emulator).

  Selection    Path                             Priority   Status
------------------------------------------------------------
* 0            /usr/bin/xfce4-terminal.wrapper   40        auto mode
  1            /usr/bin/koi8rxterm               20        manual mode
  2            /usr/bin/lxterm                   30        manual mode
  3            /usr/bin/mate-terminal.wrapper    30        manual mode
  4            /usr/bin/uxterm                   20        manual mode
  5            /usr/bin/xfce4-terminal.wrapper   40        manual mode
  6            /usr/bin/xterm                    20        manual mode

Press <enter> to keep the current choice[*], or type selection number: 

```
You can see any choices would be made there, so choose wisely. :)

---

### Post by puffcorn on 2019-11-20
I edited the output (only slight difference) in post #3 without the space

here's the output from sudo update-alternatives --config -x-terminal-emulator :

```
There are 5 choices for the alternative x-terminal-emulator (providing /usr/bin/x-terminal-emulator).

  Selection    Path                 Priority   Status
------------------------------------------------------------
* 0            /usr/bin/sakura       40        auto mode
  1            /usr/bin/koi8rxterm   20        manual mode
  2            /usr/bin/lxterm       30        manual mode
  3            /usr/bin/sakura       40        manual mode
  4            /usr/bin/uxterm       20        manual mode
  5            /usr/bin/xterm        20        manual mode

Press <enter> to keep the current choice[*], or type selection number: 
```

---

### Post by #&amp;thj^% on 2019-11-20
Depending on where or how you launch the terminal, it might of got caught up in race condition. (Just my Guess here)
Try changing to option 2 "lxterm" then logout, and see if that helps, if this is the only time you have seen this behavior I wouldn't fret much about it though. ;)

---

### Post by puffcorn on 2019-11-20
It was just the one time/session, so probably not something to be too concerned about. I probably do worry a little too much :) but in any event, I truly appreciate your help. Thank you very much. You are surely more proficient than me with Linux, but if you ever need some help with something, let me know.

---

### Post by #&amp;thj^% on 2019-11-20
That's very kind, and the gesture is also appreciated.
Kind Regards

---

### Post by TheFu on 2019-11-20
Only a guess, but perhaps some terminals remember the last CWD where they were?

I've never seen this and can't think of any normal way for an inherited CWD/PWD to be modified before the WM+DE get started, unless there's a **cd /usr/share/peppermint-settings-panel** in the ~/.profile  Even then, I'd have to look through the login steps carefully to see what happens in which order from the login.

Or perhaps systemd broke something.  That's always a concern these days, unfortunately, since that project seems to put their fingers in new places all the time.

If this is SOLVED, it would really help the community to use the "thread tools" button and mark it that too.

---

### Post by puffcorn on 2019-11-20
I had never switched to that directory, so it shouldn't have been remembered by the terminal. I also checked out my ~/.profile, and no **/usr/share/peppermint-settings-panel** in there. Since I don't really know what actually caused it, I'm not sure if I should mark it solved.

I don't really know much about systemd, but that's an interesting thought.

Thanks for your response.

> **TheFu said:**
> Only a guess, but perhaps some terminals remember the last CWD where they were?

I've never seen this and can't think of any normal way for an inherited CWD/PWD to be modified before the WM+DE get started, unless there's a **cd /usr/share/peppermint-settings-panel** in the ~/.profile  Even then, I'd have to look through the login steps carefully to see what happens in which order from the login.

Or perhaps systemd broke something.  That's always a concern these days, unfortunately, since that project seems to put their fingers in new places all the time.

If this is SOLVED, it would really help the community to use the "thread tools" button and mark it that too.

---

