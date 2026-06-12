---
title: "Minimize KAlarm on startup"
date: 2012-05-12
forum: Tutorials
---

### Post by billstei on 2012-05-12
I use KAlarm, and I had it set to start using the Startup Applications list, but KAlarm does not minimize itself on startup (using the Close Window button, which does not do a Quit), so I use this little script to do the job, and then call the script from the Startup Applications list.  It requires the xdotool package to be installed:

#!/bin/bash

# Starts KAlarm and then closes the KAlarm window (but KAlarm does not Quit)

# Start KAlarm
kalarm

# Get Window ID, the last one in the list of KAlarm Window processes
WID=`xdotool search --name KAlarm | tail -n 1`

# Activate that window and send Alt F4 to that Window ID to close it
xdotool windowactivate $WID key alt+F4

---

