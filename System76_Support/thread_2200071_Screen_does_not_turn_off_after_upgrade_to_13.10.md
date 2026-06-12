---
title: "Screen does not turn off after upgrade to 13.10"
date: 2014-01-17
forum: System76 Support
---

### Post by gnu2 on 2014-01-17
I have brightness and lock set to turn the screen off after 10 minutes on a "Sable Complete." It worked as expected with 13.04 but now just blanks the screen instead of turning it off.

Is this a bug with 13.10, or is there a solution?

Thanks

---

### Post by joe4ska on 2014-01-18
It's possible you screen is set to "Sleep" and "Switch off" is set to Never.

Granted I'm running XFCE on a Lemur Ultra and have my screen set to sleep (go blank) at 10 minutes then turn off completely at 15.

[IMG]http://www.linuxbookpro.com/wp-content/uploads/2014/01/Screenshot-01182014-010317-PM.png[/IMG]

---

### Post by gnu2 on 2014-01-18
Thanks for replying. No, the only option in "brightness and lock" in Unity is to "Turn screen off when inactive for ..." then 10 minutes is selected on the drop down menu.

---

### Post by joe4ska on 2014-01-18
I'm stumped,

I'm asuming there isn't a seperate setting in the System Settings > Power for the display.

However you can [try the following solution]("http://askubuntu.com/questions/253818/manually-turn-off-monitor") in terminal to see if it the Sable can still turn off the screen correctly. 

If that worked try running it off a live CD or USB for Ubuntu or perhaps another Ubuntu variant and see if the problem persists. (don't install just run it and set the settings as you normally would.)

If the Ubuntu CD works as you expect It could be an update glitch.

---

### Post by gnu2 on 2014-01-19
Well, its my mother's computer and I'm not around to do any of that stuff for her. She's not particularly technologically savy so I don't really trust her with the command line, simple as xset is... Has anyone else had the same problem, or do any Sys76 reps know what's going on?

Thanks

---

