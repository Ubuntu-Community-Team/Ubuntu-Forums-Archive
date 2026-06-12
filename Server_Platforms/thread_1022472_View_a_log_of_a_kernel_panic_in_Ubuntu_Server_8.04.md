---
title: "View a log of a kernel panic in Ubuntu Server 8.04?"
date: 2008-12-26
forum: Server Platforms
---

### Post by djbon2112 on 2008-12-26
I'm getting a kernel panic in my Ubuntu server. This just started a couple days ago after a nasty bout of fighting with Xen. Now I get these kernel panics whenever my bittorrent server consistently writes to my RAID array. However, my problem is I can't view any logs as they don't exist! There's nothing in any of the /var/logs files. I have a major suspicion that it's a software issue with Xen, but I don't want to start over to find out it's actually a hardware issue. And since everything flashes so quickly on screen I don't have a chance to read it or take a picture.

Any suggestions as to what I should to do begin debugging this?

---

### Post by cariboo on 2008-12-27
You can slow down the output of cat by using the less or more command, for example to view /var/log/messages, at the prompt type:

```
cat /var/log/messages | less
```

This will make the log file nice and readable as you have to hit the space bar to continue on to the next page.

You can also use Shift-PageUp to scroll back up the log output.

Jim

---

