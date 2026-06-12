---
title: "Temp Sensors Update Page"
date: 2008-09-05
forum: Server Platforms
---

### Post by cantdrive55 on 2008-09-05
I've got a server running at home while I'm at school and want to keep an eye on it. I've got lm-sensors installed and configured just fine. What I want to do is make some sort of webpage that will let me monitor the temps without having to open up an ssh connection. 

So if I go to [http://MYIP/temps.html](http://MYIP/temps.html) I can view what the current temps are. I don't care if its html or php. How can I accomplish this or is it impossible?

Thanks,
Jeff

**EDIT**
What I've come up with so far is this script:
> #!/bin/bash

sensors > echo >> /var/www/temp.txt

exit 0


---

### Post by schettj on 2008-09-06
Look at munin. There are great howtos for ubuntu, it's in the repos, and it makes really pretty graphs like these:

[http://www.schettino.us/monitor/us/schettino.us.html#Sensors](http://www.schettino.us/monitor/us/schettino.us.html#Sensors)

---

### Post by zeevikn on 2009-02-03
The easiest way:
1) change your script to put the output in temps.html
(the browser will display the text even if it does not have the full HTML tags)
2) using cron.d, run the script every 1,5,10 minutes

```
*/5 * * * * <your script-path-and-name>
```

---

