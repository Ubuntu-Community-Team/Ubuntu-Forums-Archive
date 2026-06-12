---
title: "Logging to a console"
date: 2009-12-20
forum: Server Platforms
---

### Post by ccf on 2009-12-20
Currently, when my server (karmic/upstart) starts up, I get six ttys with login prompts.  I would like to replace one of these with some useful log output.  I figure this means changing something in /etc/init/ttyX.conf, thought it might just be a matter of sticking 'tail -f /var/log/syslog' in there, but I'm not sure if the getty's needed and don't have the luxury of being able to bring the server down to test this.

I'm looking to have useful inforamation there, so dmesg alone ("was 1581403 before or after last Thursday?") isn't really suitable.

---

### Post by KiLaHuRtZ on 2009-12-20
Try this...

```
echo -e "*.*;auth,authpriv.none\t\t/dev/console" | sudo tee -a /etc/syslog.conf > /dev/null 2>&1 && sudo /etc/init.d/sysklogd restart
```

Note, '/dev/console' is '/dev/tty1'.  So, you're logging to display will be on 'tty1' aka 'F1'.

---

### Post by ccf on 2009-12-20
> **KiLaHuRtZ said:**
> Try this...

```
echo -e "*.*;auth,authpriv.none\t\t/dev/console" | sudo tee -a /etc/syslog.conf > /dev/null 2>&1 && sudo /etc/init.d/sysklogd restart
```

Note, '/dev/console' is '/dev/tty1'.  So, you're logging to display will be on 'tty1' aka 'F1'.

I changed /dev/console to /dev/tty2 (mainly because I don't want it on tty1, which is where the main login prompt needs to be), and all I've got so far is a line out of dmesg, with the useless timestamp.  I've also uncommented the example line in syslog.conf which supposedly gets lots of other messages there, but (as yet) hasn't, even though syslog is filling nicely.

---

### Post by ccf on 2009-12-20
Turns out the file I was after was /etc/rsyslog.d/50-default.conf (Or Something[TM]).  Now works nicely.

---

