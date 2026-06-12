---
title: "laptop shuts down"
date: 2012-04-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rtalcott on 2012-04-09
I have been running 12.04 on a new HP DM4 Intel machine...worked fine till this afternoon...I shut it down...came back turned it on and it will boot and I can get to the desktop then about 1-2 minutes later it shuts down....anyone else seeing this...I have no clue where to start...HELP!
rt

---

### Post by Gompa on 2012-04-09
you could see if its kernel related by checking /var/log/kern.log and /var/log/dmesg

you could do this by running : 
cat /var/log/kern.log
cat /var/log/dmesg

---

