---
title: "Is student monitoring programs available for Ubuntu?"
date: 2009-06-25
forum: Security
---

### Post by hashbrowns on 2009-06-25
The school that I work at uses Ubuntu on some machines in a lab, and we would like to put a monitoring software on them that will display what the students are doing - make sure it's nothing inappropriate.

Plenty of solutions for this exist in Windows, but is there anything like this for ubuntu? Free or paid; it doesn't matter - I will consider and be willing to work with either one.

Thanks for your help!

---

### Post by Divider on 2009-06-25
Lookup vnc or vino. That might provide a few links.

Good luck!

-Divider

---

### Post by wojox on 2009-06-25
You could try this for free

SQUID proxy server and any free software for making reports from SQUID logs e.g. Webalizer

[http://www.squid-cache.org](http://www.squid-cache.org)
[http://www.mrunix.net/webalizer](http://www.mrunix.net/webalizer)

---

### Post by prshah on 2009-06-25
> **hashbrowns said:**
> like to put a monitoring software on them that will display what the students are doing

System-Preferences-Remote Desktop[indent]
Check (tick) Allow other users to view your desktop
Then Uncheck (untick) "Allow other users to control your desktop"
Then uncheck (untick) "You must confirm each access to this machine"
Then select "Never display an icon"
[/indent]

And set up a suitable password (Single password? Location based password? System based password?)

---

### Post by hashbrowns on 2009-07-01
> **prshah said:**
> System-Preferences-Remote Desktop[indent]
Check (tick) Allow other users to view your desktop
Then Uncheck (untick) "Allow other users to control your desktop"
Then uncheck (untick) "You must confirm each access to this machine"
Then select "Never display an icon"
[/indent]

And set up a suitable password (Single password? Location based password? System based password?)

Thanks, Prshah, that one seems to be the simplest and the most effective to just use the software that's already integrated into Ubuntu without adding extras. There's only 4-5 at most lab machines running at once and I can see them all at the same time, nice! :)

---

