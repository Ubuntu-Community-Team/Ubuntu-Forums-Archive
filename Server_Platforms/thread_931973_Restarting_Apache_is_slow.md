---
title: "Restarting Apache is slow"
date: 2008-09-27
forum: Server Platforms
---

### Post by LordKelvan on 2008-09-27
Hi:

I just recently installed LAMP on my Ubuntu 8.04.  This a fresh installation and it went smoothly.  My only issue is that whenever I tell Apache to restart by issuing the command:

```
/etc/init.d/apache2 restart
```

it takes about 10 seconds to complete (i.e., restart Apache).  However, if I enter in the following two commands (one after the other):

```

/etc/init.d/apache2 stop
/etc/init.d/apache2 start

```

Than its instantaneous.  Is this how its supposed to be?  Or is there some way to make the "restart" command as fast as the "stop" + "start" commands?

Cheers,
LK

---

### Post by lykwydchykyn on 2008-09-27
Interestingly, if you look at the apache2 init script (/etc/init.d/apache2), the restart command has right smack in the middle of it (line 173):
```

sleep 10

```

So that ten second pause is quite literally programmed into the restart command.  I suppose you could comment out this line or change the 10 to something smaller, but I would want to know why it was there to begin with before doing that.  It's probably just there to make sure the old process has completely cleared out before trying to start a new one.

---

### Post by LordKelvan on 2008-09-28
Rofl - I was afraid of something like that :D

Hmm.. can any Apache devs answer this?

Edit:  Just to be sure, restarting = stop + start for Apache right?  Or are they different?

---

### Post by TsTBo8U on 2008-09-28
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by LordKelvan on 2008-11-21
I just upgraded to Ubuntu 8.10, and I can no longer find the "sleep 10" in the init file.  Restarting is now as fast as stopping and then starting.  Problem solved I guess :)

---

### Post by Vegan on 2008-11-21
When I was using 8.04 restarting Apache2 was fast even on my old IBM. I wonder what would put a sleep into the file?

I have a standard LAMP stack with a few extras and everything runs fine and snappy.

:guitar:

---

### Post by JDiss on 2008-11-22
> **LordKelvan said:**
> I just upgraded to Ubuntu 8.10, and I can no longer find the "sleep 10" in the init file.  Restarting is now as fast as stopping and then starting.  Problem solved I guess :)

'graceful' is a gentler way of restarting that doesn't crash the threads.

---

