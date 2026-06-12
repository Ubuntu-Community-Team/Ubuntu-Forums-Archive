---
title: "service lightdm restart, from terminal-window = bla{ck,nk} VT (aka BSOD)"
date: 2011-12-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-12-23
I used to restart lightdm with sudo service lightdm restart directly from gnome-terminal. 
Doing so now just puts me back in console with no error or any better explanations.
At this point, the only option is to switch to another VT, login and sudo service lightdm start.

Anyone else seeing it or did I just broke something?

---

### Post by thedarkdonut on 2011-12-23
I tried it and saw the same thing as you almost.  My screen displayed the same text you see when you've shutdown linux.

---

### Post by |{urse on 2011-12-23
I'm guessing 'right alt' + sysrq + k doesn't help you?

---

### Post by Ibidem on 2011-12-23
What happens if you login to the console, and run sudo service lightdm restart from there (in the first place, not after getting a black screen)?

---

### Post by thedarkdonut on 2011-12-23
> **|{urse said:**
> I'm guessing 'right alt' + sysrq + k doesn't help you?

I tried that combination and got the following that's with holding the Fn key since I'm on a netbook.
```

SysRq  :  Changing Loglevel
Loglevel set to 2

```

The following is without holding the Fn key.
```

SysRq  :  SAK

```

> **Ibidem said:**
> What happens if you login to the console, and run sudo service lightdm restart from there (in the first place, not after getting a black screen)?

It stops and starts lightdm like a normal service restart, but here's question.  Should stopping and starting lightdm usually stop and restart the graphics session?

---

### Post by effenberg0x0 on 2011-12-23
> **thedarkdonut said:**
> I tried that combination and got the following that's with holding the Fn key since I'm on a netbook.
```

SysRq  :  Changing Loglevel
Loglevel set to 2

```The following is without holding the Fn key.
```

SysRq  :  SAK

```

It stops and starts lightdm like a normal service restart, but here's question.  Should stopping and starting lightdm usually stop and restart the graphics session?

That's how it used to work. I always restarted lightdm from within a console inside the session. There has never been this need to drop to a VT to start it after restarting it. It makes no sense: If I wanted to drop to stop it and drop to a VT I'd issue a sudo service lightdm stop.

---

### Post by Ibidem on 2011-12-23
It should restart X on VT7.
The interesting part is that if you use a terminal, service is a child of sudo, which is a child of your shell, which is a child of your terminal, which is a child of unity and a client of X, which is started by the service lightdm.  When lightdm restarts, it kills X, and all X clients thus die, killing most/all children.  Depending on whether sudo/service detaches from the shell, they might die at the same time.
Which suggests something: if you activate sudo, then run sudo service lightdm restart & , would it do the job?  Not a realistic solution, just an idea that came up.

The thing to do would be to look at changes for lightdm, probably.

---

### Post by thedarkdonut on 2011-12-23
> **Ibidem said:**
> It should restart X on VT7.
The interesting part is that if you use a terminal, service is a child of sudo, which is a child of your shell, which is a child of your terminal, which is a child of unity and a client of X, which is started by the service lightdm.  When lightdm restarts, it kills X, and all X clients thus die, killing most/all children.  Depending on whether sudo/service detaches from the shell, they might die at the same time.
Which suggests something: if you activate sudo, then run sudo service lightdm restart & , would it do the job?  Not a realistic solution, just an idea that came up.

The thing to do would be to look at changes for lightdm, probably.

Wow...just wow.  I know that you meant child processes, but that just kind of seemed a bit morbid to me.  Oh I'm not running unity.  I'm actually running gnome shell for my session, but I get the idea.

---

### Post by effenberg0x0 on 2011-12-23
> **Ibidem said:**
> It should restart X on VT7.
The interesting part is that if you use a terminal, service is a child of sudo, which is a child of your shell, which is a child of your terminal, which is a child of unity and a client of X, which is started by the service lightdm.  When lightdm restarts, it kills X, and all X clients thus die, killing most/all children.  Depending on whether sudo/service detaches from the shell, they might die at the same time.
Which suggests something: if you activate sudo, then run sudo service lightdm restart & , would it do the job?  Not a realistic solution, just an idea that came up.

The thing to do would be to look at changes for lightdm, probably.

Hi, interesting line of thought. But I had no luck forking lightdm service restart to a subshell - yet another child to kill :) I'm guessing on a race condition: Either pidof lightdm still exists when lightdm is invoked, or some other dependence is still up. Later today I realised that the current state of my install is flaky mainly due to some problem with dbus, which seems to "mute" (not crash though) randomly, making calls to it timeout. I'll try to get a log of the whole situation.

> **thedarkdonut said:**
> Wow...just wow.  I know that you meant  child processes, but that just kind of seemed a bit morbid to me.  Oh  I'm not running unity.  I'm actually running gnome shell for my session,  but I get the idea.

Christmas brings out the best of us :) Another way to think about it is that there's no better/"more VIP" level than that in which you are alone and mostly every other PID is dead: You root and become God-like, you're #1. But then, if you want more than being number one, you die (halt - level0). Linux is clearly targeted at sociopaths.

---

### Post by mc4man on 2011-12-23
There's quite a bit of flaky behavior atm. As far as this you'd likely see as intended if you used gksu instead of sudo if using the command from any  terminal
(from a run dialog sudo would probably work

---

### Post by effenberg0x0 on 2011-12-24
> **mc4man said:**
> There's quite a bit of flaky behavior atm. As far as this you'd likely see as intended if you used gksu instead of sudo if using the command from any  terminal
(from a run dialog sudo would probably work

Hey mc4man, good idea, I tested it, but got the same results: Went to VT6, verified that neither X nor lightdm were running/stalled and I could start lightdm normally. It's weird cause I can't find a reason why the session is not restarted in any of my logs. I'm seeing some random lightdm and libc segfaults too, but in logs from earlier today, and during session usage, not session restart. Things are not looking good right now. Considering it may be a while till new updates start to come in, with X-mas and New Year's, I better check backups before things get uglier... 

As a side note: The gnome-shell session seems more stable right now: I can work long hours running many apps on it without any weird behaviours or crashes. Too bad I really feel lost inside of it.

EDIT: I think my major recent update was kernel 3.2.0-6... Maybe if I go back to previous RC.

---

### Post by mc4man on 2011-12-24
Just gave it a try, (gksu service lightdm restart) & it works here fine as does Alt+f2 > 'sudo service lightdm restart' or  'service lightdm restart' from the 'old' gksu gui run box.

If I run your 'sudo ..' command from _any_ terminal it seems to hang at the console at about the same spot (a few times I've then hit ctrl+alt+delete but that just causes a full restart

( I do use the 1.7.2 sudo though don't think that's a factor here & don't particularly advise others to do so though for me it makes life easier during dev. 

Then again I see some things that occurring in other area's - out of the blue ccsm can open 'greyed out', no errors, just can't use, fixed itself somehow?

I'll probably do a new install next week though not much has come thru lately.

(Ot - one of the odd things I've seen lately is doing a log out/in with an audio cd in the drive. Pegs a cpu with dbus-daemon till the disc is manually 'mounted'

---

### Post by effenberg0x0 on 2011-12-24
> **mc4man said:**
> Just gave it a try, (gksu service lightdm restart) & it works here fine as does Alt+f2 > 'sudo service lightdm restart' or  'service lightdm restart' from the 'old' gksu gui run box.

If I run your 'sudo ..' command from _any_ terminal it seems to hang at the console at about the same spot (a few times I've then hit ctrl+alt+delete but that just causes a full restart

( I do use the 1.7.2 sudo though don't think that's a factor here & don't particularly advise others to do so though for me it makes life easier during dev. 

Then again I see some things that occurring in other area's - out of the blue ccsm can open 'greyed out', no errors, just can't use, fixed itself somehow?

I'll probably do a new install next week though not much has come thru lately.

(Ot - one of the odd things I've seen lately is doing a log out/in with an audio cd in the drive. Pegs a cpu with dbus-daemon till the disc is manually 'mounted'
Dude... I DID had an audio CD in the drive. This is rare for me, but I was trying to recover something from an old disk and totally forgot it was there. I'll kill myself if that was the cause for the dbus annoyances. If so you're officially a genius :)

---

### Post by mc4man on 2012-01-02
The issue with a log out/in, audio cd's & dbus-daemon seems be the fault of zeitgeist-datahub. Whether z-d  causes any other issues don't know, I may remove it for a short bit.
open bug on, added zeitgeist today
[https://bugs.launchpad.net/zeitgeist/+bug/905898](https://bugs.launchpad.net/zeitgeist/+bug/905898)

edit: or it may be zeitgeist-core/(rhythmbox), had removed z-c & not noticed...

---

