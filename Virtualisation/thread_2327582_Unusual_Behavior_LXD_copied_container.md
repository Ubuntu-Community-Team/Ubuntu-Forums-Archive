---
title: "Unusual Behavior? LXD copied container"
date: 2016-06-12
forum: Virtualisation
---

### Post by jay116 on 2016-06-12
So I created a container and make some configurations to it and wanted to duplicate it so I could make two separate ones. One for Crashplan and one for Plex. So I copied my first container ubuntu-crash and named the copy ubuntu-plex. The new container (plex) has an ip and i can ping it from another computer on the LAN. it appears to be functioning. Odd thing is when i try and open a shell to configure it i don't get the container I asked for, I get the old container. What am I missing? 

But if I do ifconfig I see the IP is correct for plex (.110). So am I in the right container but the name on the command line is wrong?

[ATTACH=CONFIG]269544[/ATTACH]

---

### Post by jay116 on 2016-06-14
I guess I'll keep answering my own questions. This one was pretty simple. When I copied the other container it copied every aspect to include the hostname. So I logged into the Plex container and changed the hostname file located at /etc/hostname and that fixed it. Total newbie issue, but it confused me at first. I do appreciate all the helpful comments. 


Ever feel alone in a room full of people?

---

### Post by MAFoElffen on 2016-06-15
That happens all the time... It's so easy to clone a vm guest... In the clone process you give it anotther unique machine name. But the first thing I do after the clone it to change the static IP (so ip is unique), and the host name.

One thing I noticed, it with the Ubuntu Install process, all the different Ubuntu branch flavors, still use the same default hostname (ubuntu)... which will cause a conflict if not changed, and if you try to run multiples at the same time.

Glad you found your answer. If you could please revisit this thread, to mark it as solved. Upper right top of page, link amrked as "Thread Tools" > "Mark as Solved". That heps others looking for similar problems of there own, to find a solution.

---

