---
title: "Why was ctrl-alt-backspace disabled by default in lucid?"
date: 2010-06-30
forum: The Cafe
---

### Post by Dustin2128 on 2010-06-30
At the moment I'm working on further configuring my new triple-monitor setup; each monitor has its own computer (thank you windows performance decay!) anyway, my main system runs slackware, the one on the left runs arch, and the one on the right runs ubuntu 10.04. Arch was... different (only one of the three I'd never used before) but it setup alright. Ubuntu was wonderfully easy as usual. However, I got into the habit of using ctrl-alt-backspace to logout in slackware and did the same in arch (knew it was a supposedly universal linux shortcut) but it wouldn't work in lucid. The most recent version of ubuntu I'd used until that point was intrepid I believe, and it worked with that. Of course it was quite easy to enable but it just made me wonder why it was disabled. Also, if anyone wants them, I'll have pics up after I've got everything configured, the arch system is giving me some trouble with the graphics card...

---

### Post by chessnerd on 2010-06-30
It was replaced by Alt-SysRq-K. Don't ask me why...

---

### Post by Dustin2128 on 2010-06-30
huh, that's strange. I still think that there are some inviolable key combos there must be to unite distros/OSes. Like ctrl-z for undo. Worth petitioning canonical to swap back in 10.10/11.04?

---

### Post by FuturePilot on 2010-06-30
It has been disabled for a few releases now.

---

### Post by chessnerd on 2010-06-30
I wouldn't mind having it back. It was removed originally back in Jaunty. You used to be able to re-enable it by installing a program called dontzap (which was designed to stop people from being able to use Ctrl-Alt-Backspace) and then disabling that program. However, dontzap is no longer in the repositories and I think the current version of X doesn't work with it.

---

### Post by cariboo on 2010-06-30
It was done in X-server, it had nothing to do with Ubuntu. If you check the [Release Notes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes"), you'll find instructions on how to re-enable Ctrl-Alt-Backspace.

---

### Post by Dustin2128 on 2010-06-30
nah, reinitializing it was no problem, you don't even need to install software. just go system-pref-keyboard-layouts-options-key sequence to kill x server (or something similar). I'm not complaining that it's hard to fix, I'm just saying that there should be a few key combos universal to all distros/OSes. And slackware 13.1- which accepts the key combo- is far more recent than jaunty, released only a month or two ago.

---

### Post by r_avital on 2010-12-10
> **cariboo907 said:**
> It was done in X-server, it had nothing to do with Ubuntu. If you check the [Release Notes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes"), you'll find instructions on how to re-enable Ctrl-Alt-Backspace.
Well, Thanks!  Because the other sequence of alt+sysrq+k was crazy - on my end sysrq (alone or with any sequence) was triggering screenshots.  I know it shouldn't but it does.  I'd like to solve THAT problem...

Thanks again :)

---

### Post by Mmmbopdowedop on 2010-12-10
I kinda like the change. :)
Not knowing the new combo has led me to atleast attempt to save my stuffs and try and recover whatever on a freeze before doing "/etc/init.d/gdm3 stop" on a new TTY, seems like i'm losing less data. :) 

Main reason I really ever used it was because I open about 100 different windows and get lost in them and i'm like; pfft, refresh. ;) Now i've learned to close them. :)

---

