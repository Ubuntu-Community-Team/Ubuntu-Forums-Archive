---
title: "Ubuntu Studio freezed after start Qjackctl"
date: 2016-06-19
forum: Ubuntu Studio
---

### Post by lancaster2 on 2016-06-19
I found rosegarden is no sound so I googled that I need to start Jack server.
I tried to start [COLOR=#111111][FONT=Ubuntu]Qjackctl in startup menu, however, I got Permission Error. So I start a terminal and typied:
```
sudo qjackctl
```
But the desktop freezed as soon as the Enter key was pressed. I can only move my mouse, but nowhere response to click or drag.
I waited for minutes, I have to shutdown the computer by force.
I tried another time that:
```

sudo -s
qjackctl &

```
But same problem turns up.
Do you guys meet same problem before? Thanks[/FONT][/COLOR]

---

### Post by kazakore on 2016-06-22
Don't run it as superuser! There are many reasons against doing so and it shouldn't be needed.

You can also start jackd from the commandline but you would have to  check their website or wait for somebody else to respond to learn the  correct syntax to use.

I can't help you with your actual problem but you shouldn't have to shut down your computer "by force" if you mean with the power button. Switch to another TTY, eg TTY2 by pressing ALT+CTRL+F2, from here log in with your username and password. Once on the commandline use the command **sudo shutdown -r now[b] to restart or [b]sudo shutdown -h now** to power off. Should be better for your system than simply powering off.

---

### Post by jejeman on 2016-06-23
Run
```
qjackctl
```
and copy here output.
Are you running Ubuntu Studio? Which version?
Give here output from
```
groups
```

---

