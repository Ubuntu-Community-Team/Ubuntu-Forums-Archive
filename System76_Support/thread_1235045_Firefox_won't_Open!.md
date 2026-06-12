---
title: "Firefox won't Open!"
date: 2009-08-08
forum: System76 Support
---

### Post by brittany.meek on 2009-08-08
I am TOTALLY new to Linux and have had the Starling for about a month. I've been very pleased (except for the distance of wireless, which I will be updating the driver shortly to see if that will help) with the netbook. Today I have been trying to get on the internet. It shows I have a connection, and I'm sitting in the room where I can always get a connection, but Firefox Web Browser will not open. I went into add/remove programs and was going to try a different web browser. As I attempt to install a new browser, this error comes up:

[FONT=Calibri][SIZE=3]e: dpkg was interrupted, you must manually run ‘sudo dpkg –configure – a’ to correct the problem.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]e:_cache->open() failed, please report.[/SIZE][/FONT]
 
I have no idea what this means or what I need to do. Any help would be greatly appreciated. I would rather continue using Firefox Web Browser than to use a different one, but it won't open. I have attempted shutting down the computer and restarting, but that did not help the situation. 
 
Thank you!

---

### Post by HotShotDJ on 2009-08-08
> **brittany.meek said:**
> e: dpkg was interrupted, you must manually run ‘sudo dpkg –configure – a’ to correct the problem.
e:_cache->open() failed, please report.What you need to do is run```
sudo dpkg --configure -a
```to correct the problem.

Open up a terminal (I'm not sure what menu it is under in the Netbook Remix that comes installed on the Starling) and either type or copy/paste the command.

---

### Post by gila_monster on 2009-08-08
brittany,

first off, what new browser are you trying to install?

Second, if you would be so kind, open a terminal and type ```
firefox
``` and post the results of that. It should give us more information on why it is not starting.

---

### Post by thomasaaron on 2009-08-10
Brittany, 


It would be best if you could plug into your router for a WIRED internet connection. Then, after you open a terminal (Applications > Terminal) and run...

sudo dpkg --configure -a

...like HotShotDJ suggested, you need go straight to Administration > Update Manager, click the "Check" button and then the "Apply" button to download all updates. Then REBOOT your comptuer. This should fix your wireless problem (and possibly some other problems as well).

Once you've done that, run "firefox" from a terminal as gila_monster suggested. Let us know the output.

---

