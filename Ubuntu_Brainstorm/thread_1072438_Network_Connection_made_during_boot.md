---
title: "Network Connection made during boot"
date: 2009-02-17
forum: Ubuntu Brainstorm
---

### Post by BCurtisWX on 2009-02-17
Hey all,

I would like your help getting the following brainstorm idea popular.

[http://brainstorm.ubuntu.com/idea/18091/](http://brainstorm.ubuntu.com/idea/18091/)

Here is the info I posted about it, please comment and give your ideas, on here and in the brainstorm.

Rationale:
All of the programs in ubuntu that require an internet connection that load up at the beginning have to wait for a connection before loading. Some often fail due to the time it takes my computer to get a wireless signal (this is especially important on netbooks). Even with my desktop computer, it will notify me that a connection is successful around the time that my desktop has completely loaded, which seems almost too long for such a direct connection.

Solution #1: get the internet connection to start up earlier...
If ubuntu can be made to get this internet connection set-up before the desktop is completely loaded, then programs like pidgin, evolution, etc.. (any internet program that runs on startup, either by default or user selection), can all connect on the first try allowing the user to get their blog reading/IM sending/youtube watching started that much sooner.
I would imagine theres other ways to tweak this idea to make it even better. please comment on this and how to make it an even better idea!

Thanks a ton!
~BCurtisWX

---

### Post by smartboyathome on 2009-02-17
WICD already does this, as it runs as a daemon. Just set it to automatically connect, and it does. Network Manager runs at gnome login, so it doesn't do this.

---

### Post by BCurtisWX on 2009-02-17
> **smartboyathome said:**
> WICD already does this, as it runs as a daemon. Just set it to automatically connect, and it does. Network Manager runs at gnome login, so it doesn't do this.

is this WICD a part of the default ubuntu installation?

---

### Post by smartboyathome on 2009-02-17
> **BCurtisWX said:**
> is this WICD a part of the default ubuntu installation?

No, because it works for some people and not for others, like Network Manager (Network Manager is the default). You can get WICD from [here]("http://wicd.sourceforge.net/download.php"), though. :)

---

### Post by BCurtisWX on 2009-02-17
> **smartboyathome said:**
> No, because it works for some people and not for others, like Network Manager (Network Manager is the default). You can get WICD from [here]("http://wicd.sourceforge.net/download.php"), though. :)

Ah, ok.. Maybe you can comment on my brainstorm, or make another solution to help it out.  Make WICD a part of NM or get it part of ubuntu and working on everything.

Any help on getting my brainstorm with the right ideas and direction will help devs out if they want to persue it.

---

### Post by 2scott on 2009-02-17
Just FYI - here is the actual link to WICD -   [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

the other link does not take you to a place where you can actually download code - but gives you troubleshooting advice for installation (good to have)

---

