---
title: "problem with ardour and backgroun applications"
date: 2015-05-24
forum: Ubuntu Studio
---

### Post by rik_drum on 2015-05-24
hi everyone,
i'm just new in ubuntu studio,
i have a problem, when i use ARDOUR and then i go on youtube i can't hear nothink, there is somethink that i have to set in Qjactctl?
Many thanks,
Riccardo

---

### Post by jejeman on 2015-05-24
Same question already asked and answered (many times). Search the forum.

---

### Post by burro on 2015-05-28
The easiest way I know is to install pulseaudio-module-jack:

sudo apt-get install pulseaudio-module-jack

Then create a scripts folder such as /home/yourusername/scripts and save the 4 attached files into this folder. You need to make them executable with:

chmod u+x pulse-jack-post-start.sh
chmod u+x pulse-jack-post-stop.sh
chmod u+x pulse-jack-pre-start.sh
chmod u+x pulse-jack-pre-stop.sh

Then open qjackctl and open "setup" and then the "options" tab. Tick each of the first 4 items and enter the following paths (adapting this to your actual username/path) in this order:

/home/yourusername/scripts/pulse-jack-pre-start.sh
/home/yourusername/scripts/pulse-jack-post-start.sh
/home/yourusername/scripts/pulse-jack-pre-stop.sh
/home/yourusername/scripts/pulse-jack-post-stop.sh

You will then need to stop jack and restart it and check the message window of qjackctl for any errors (perhaps a path error for example). 
It should then be working (you can try a restart of the computer as a last resort), but you will need to always to launch and initiate qjackctl before you launch other audio programs that use pulse audio (eg. a browser running Youtube). 

hope this helps - good luck

---

