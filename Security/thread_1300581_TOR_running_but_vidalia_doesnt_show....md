---
title: "TOR running but vidalia doesnt show..."
date: 2009-10-25
forum: Security
---

### Post by emigrant on 2009-10-25
hi,
iv installed TOR and Vidalia.
i can see that tor is working and my ip is changed.
but when i start vidalia it says tor not running.

what is the problem?

helps are most appreciated.
thank you very much.

---

### Post by emigrant on 2009-10-25
or is it may be i installed polipo?
how to see which one is running and how to stop the idle one?

thank you very much.

---

### Post by skaramanger on 2010-02-04
> **emigrant said:**
> hi,
iv installed TOR and Vidalia.
i can see that tor is working and my ip is changed.
but when i start vidalia it says tor not running.

what is the problem?

helps are most appreciated.
thank you very much.

Greetings emigrant

Did you find a resolution to Vidalia not detecting tor running?  I have the same problem.  I just installed tor,vidalia and polipo and tor works fine.

skar

---

### Post by rifter on 2010-04-04
> **skaramanger said:**
> Greetings emigrant

Did you find a resolution to Vidalia not detecting tor running?  I have the same problem.  I just installed tor,vidalia and polipo and tor works fine.

skar

It seems that unless Vidalia starts TOR it won't find or talk to TOR.  So you have to stop TOR and set it up so it does not start on its own, and let Vidalia start TOR.

---

### Post by ApEkV2 on 2010-04-04
If you installed tor, and then installed vidalia, you have to go into sysv-rc-conf (the command line) scroll down and unselect all the tor startup levels.
Vidalia automatically starts tor, so if tor is already running, there will be problems. Solution.....first you need to turn off tor....

```
*Turn off tor...*

pidof tor
sudo kill <the pid of tor>

*Install sysv-rc-conf...*

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

*scroll down with the arrow keys (alphabetical order) should look like...*
[color=red]tor          [ ]        [X]         [X]         [X]        [X]        [ ]        [ ][/color]
*scroll over the X's for tor and "unselect" them with the spacebar*
```

If you want to use vidalia with tor, you need to make sure tor doesn't automatically start at computer's startup, sysv-rc-conf allows you to turn it off.

---

### Post by skaramanger on 2010-04-05
Thanks for your replies,

See below

> **ApEkV2 said:**
> If you installed tor, and then installed vidalia, you have to go into sysv-rc-conf (the command line) scroll down and unselect all the tor startup levels.
Vidalia automatically starts tor, so if tor is already running, there will be problems. Solution.....first you need to turn off tor....

```
*Turn off tor...*

pidof tor
sudo kill <the pid of tor>

*Install sysv-rc-conf...*

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

*scroll down with the arrow keys (alphabetical order) should look like...*
[color=red]tor          [ ]        [X]         [X]         [X]        [X]        [ ]        [ ][/color]
*scroll over the X's for tor and "unselect" them with the spacebar*
```

If you want to use vidalia with tor, you need to make sure tor doesn't automatically start at computer's startup, sysv-rc-conf allows you to turn it off.

I don't know about the OP, but I removed polipo and vidalia. I'm using privoxy with tor.  I'll try again when time permits though and the moment moves me :).

Thanks again
skaramanger

---

### Post by rifter on 2010-04-13
> **skaramanger said:**
> Thanks for your replies,

See below



I don't know about the OP, but I removed polipo and vidalia. I'm using privoxy with tor.  I'll try again when time permits though and the moment moves me :).

Thanks again
skaramanger

I got rid of Vidalia too.  It was hogging resources, going greyed out all the time, and in the end the only thing it was "controlling" about tor was starting and stopping it.  so I just got rid of Vidalia and set tor back to starting on startup; no problems anymore.

---

