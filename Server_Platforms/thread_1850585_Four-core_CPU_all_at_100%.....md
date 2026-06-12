---
title: "Four-core CPU all at 100%.... ???"
date: 2011-09-26
forum: Server Platforms
---

### Post by n8af on 2011-09-26
Hey all,

I've got my Ubuntu server box running on a Quad-core Intel CPU.  I suspected some network sluggishness and decided to remote in and see what the system monitor was reporting.  To my suprise, it is showing all four CPU cores being maxed out.  I ran the 'ps' command in the terminal and there is nothing showing up.

So, my questions is, anyone have an idea what is going on?  Is there a better resource monitor daemon out there than can show some more detail and give me a clue as to why all my cores are maxed?

Attached is a screen shot of my resource monitor.

---

### Post by arrrghhh on 2011-09-26
> **n8af said:**
> Hey all,

I've got my Ubuntu server box running on a Quad-core Intel CPU.  I suspected some network sluggishness and decided to remote in and see what the system monitor was reporting.  To my suprise, it is showing all four CPU cores being maxed out.  I ran the 'ps' command in the terminal and there is nothing showing up.

So, my questions is, anyone have an idea what is going on?  Is there a better resource monitor daemon out there than can show some more detail and give me a clue as to why all my cores are maxed?

Attached is a screen shot of my resource monitor.

This is not Ubuntu Server, this appears to be Ubuntu Desktop.

At any rate, did you look at the "processes" tab?  Sort by processor utilization and see what is pegging those cores...

Otherwise you can look at top or htop.

---

### Post by n8af on 2011-09-26
Actually, it is Ubuntu server running the Gnome GUI.  The process tab shows nothing is running - nothing is showing it is using any CPU %.

EDIT: I rebooted the server and it seems to have fixed this issue for now.  Not sure why nothing was showing up on the process list.

Anywho - i'll post back if it starts up again.

Thanks "arrrghhh" for your time.

---

### Post by arrrghhh on 2011-09-26
> **n8af said:**
> Actually, it is Ubuntu server running the Gnome GUI.  The process tab shows nothing is running - nothing is showing it is using any CPU %.

top/htop..?  Running as root/sudo?

Obviously *something* is pegging out those cores.  Just not something being run by your user account.

Hrm, just saw your edit.  A reboot will of course resolve the issue, but it could happen again.  Watch it closely, especially if it's a production server.

---

### Post by Kelketek on 2011-09-27
You can install the GUI on the server edition, even if it isn't recommended. :)

Anyway, run these commands and give us the output:

```
uptime
ps faux
vmstat -S M 10 10
```

That last one will take a little while. With these three we should be able to get a pretty good idea of what's going on.

---

### Post by arrrghhh on 2011-09-27
> **Kelketek said:**
> You can install the GUI on the server edition, even if it isn't recommended. :)

Anyway, run these commands and give us the output:

```
uptime
ps faux
vmstat -S M 10 10
```

That last one will take a little while. With these three we should be able to get a pretty good idea of what's going on.

vmstat is a good one!  Learn something new every day.  Thanks!

No comment on the GUI on a server.... *shudders*

---

