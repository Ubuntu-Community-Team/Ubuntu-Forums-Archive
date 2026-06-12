---
title: "An idea for a musical alarm"
date: 2012-10-31
forum: The Cafe
---

### Post by kwrogers on 2012-10-31
After much searching and researching what others have done for musical alarms on Ubuntu - be it new programs or just scheduling a playlist to run - I came up with my own setup and I thought I'd share.

I first created two shell scripts in my home directory using
```
~$ sudo gedit scriptname.sh
```
where one file was "pandora_alarm.sh" and the other was "cancel_alarm.sh"

the content of the scripts are,
pandora_alarm.sh:
```
#!/bin/bash

#launch pandora and start music
gnome-open http://www.pandora.com

#lock screen
gnome-screensaver-command --lock

#set start volume
amixer sset 'Master' 40%

#wait 90 seconds
sleep 90s

#increase volume 10%
amixer -q sset 'Master' 10%+

#wait 90 seconds
sleep 90s

#increase volume 10%
amixer -q sset 'Master' 10%+

#wait 90 seconds
sleep 90s

#increase volume 10%
amixer -q sset 'Master' 10%+

#wait 90 seconds
sleep 2m

#set volume very loud
amixer sset 'Master' 90%


```

and cancel_alarm.sh:
```
#!/bin/bash

#This requires any input and [enter]
echo "Are you  up?"
read -p "If so, press [enter]"

pkill -x pandora_alarm
```

I used **chown** to make myself the owner of each (probably could have avoided this if I didn't use **sudo**.) and then enabled executing the scripts as programs.

Then I added these to **cron** as follows:
```
0 6 * * 1-5 ~/pandora_alarm.sh
1 6 * * 1-5 -f ~/cancel_alarm.sh
```

So every weekday:
[LIST]
[*]my browser launches with Pandora
[*]the screen locks requiring me to log in
[*]every 90 seconds the volume increases
[/LIST]
[INDENT]and I must log in to stop it. The cancel_alarm.sh script allows me to kill the increases in volume, if I get to it before it reaches 90%.[/INDENT]

I chose to launch Pandora rather than use my music from my computer because it provides a different song set each time and it was easier (I think) to just launch the browser than to setup a playlist/media player.

---

