---
title: "Microphone doesn't wok"
date: 2013-04-15
forum: Ubuntu Development Version
---

### Post by nmg49 on 2013-04-15
Hey. I just installed Ubuntu 13.04 on my system76 Gazelle Profetional laptop. I've had bad luck with beta versions of Ubuntu in the past, but I heard this one was exteremly stable so I thought I'd give it a go. Well, turns out almost everything has worked, but I've still run into a few problems.

For some reason, I can't figure out how to get my microphone to work in 13.04. I should note that it worked for awhile and now it just stoped. Anyone have any ideas for this. If it helps, I think it may have stoped working after I tried to install the System76 drivers, which failed, I'm assuming becasue they haven't been updated to support 13.04 yet. Thanks.

---

### Post by keyxmakerx on 2013-04-27
I am having the same problem, just installed the full version of ubuntu 13.04. GazPro7 laptop

---

### Post by cariboo on 2013-04-27
Have either of you checked to seem if the microphone input in alsamixer is turned up? To run alsamixer open a terminal and type:

```
alsamixer
```

See the screenshot.

---

### Post by Marc v G on 2013-05-23
I had the same issues, but the microphone worked after I changed settings to pulseaudio as mentioned in [http://askubuntu.com/questions/157891/skype-and-vlc-sounds-sizzle-distorted-bad](http://askubuntu.com/questions/157891/skype-and-vlc-sounds-sizzle-distorted-bad)

In short, the solution for me is:
[LIST]
[*]edit /etc/pulse/default.pa
[*]search for the following line:
[LIST]
[*]load-module module-udev-detect
[/LIST]

[*]append "tsched=0" to the end:
[LIST]
[*]load-module module-udev-detect tsched=0
[/LIST]

[*]kill pulseaudio, it will respawn automaticaly
[LIST]
[*]sudo killall pulseaudio
[/LIST]
[/LIST]

---

