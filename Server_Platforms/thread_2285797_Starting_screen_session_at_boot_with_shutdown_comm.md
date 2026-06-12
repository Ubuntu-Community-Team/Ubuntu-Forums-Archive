---
title: "Starting screen session at boot with shutdown command"
date: 2015-07-08
forum: Server Platforms
---

### Post by jlinkkai on 2015-07-08
So this is something I've not been able to quite nail down despite a lot of searching. Have been using Linux for a little over a year, but haven't really gotten the hang of scripting or managing things at boot. So I suppose I'll get right to what my goal is and how I'd prefer things fit together. I'd like to rig headless Ubuntu to start a Minecraft server in a screen session at boot. Also I'd like that screen session to run at the user level and have a stop command to be thrown at it on shutdown so things have a chance to save. Currently have a working manual script to achieve half of this, but can't seem to gather the required info on how to achieve the boot and shutdown portions of this little project.

Stuff I need to know:
-What boot management system should I be using
-How to configure that system to call for a screen daemon at boot and gracefully kill it on shutdown
-Anything that might need to be set to delay the shutdown process until that screen has terminated

Current launcher is as follows: 
```

#!/bin/bash


screen -dmS minecraft java -jar -Xms6G -Xmx6G -XX:MaxPermSize=256m -XX:UseSSE=3 FTBServer-1.7.10-1408.jar nogui
```


I greatly appreciate any help that can be offered. Really interested in learning these things so I can offer help of my own. (Also I hope this is the right category to post this.)

---

