---
title: "System logging out during updates"
date: 2015-09-10
forum: Ubuntu Development Version
---

### Post by cariboo on 2015-09-10
While doing updates especially on my laptop, the screen will go black for a couple of seconds the when it comes back on again it's at the login screen. I've had it happen once or twice on my desktop as well. Is anyone else seeing this type of behavior? Running Ubuntu on both systems.

---

### Post by QIII on 2015-09-10
Now that you mention it, yes.

---

### Post by mc4man on 2015-09-10
I've noticed it going black for a split second or so  during a number of updates over the course of  Wily dev. Diff is here it just returns back to current state.
(thought it was odd though, reminded me of nvidia install/updates on Windows where screen will go off for a moment.

Here using Intel drivers if that's a factor??

---

### Post by Rustan on 2015-09-10
after logoff check for errors in Xorg.0.log.old

---

### Post by ventrical on 2015-09-10
@cariboo

Yes .. once or twice... but not as of recent (on desktop). 

regards..

---

### Post by QIII on 2015-09-10
> **Rustan said:**
> after logoff check for errors in Xorg.0.log.old

If it's not an "error", looking for an error won't likely help.  This is just a discussion about an observation to see if it's worth reporting -- or even a thing.  It's a dev version.  These things happen.

---

### Post by QIII on 2015-09-10
I didn't get the blackout to login this time, but I did just get 


```
dpkg: cycle found while processing triggers:
 chain of packages whose triggers are or may be responsible:
  software-center -> software-center
 packages' pending triggers which are or may be unresolvable:
  software-center: /usr/share/app-install/desktop
dpkg: error processing package software-center (--configure):
 triggers looping, abandoned
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


--- Hmmm.  Already reported.  I'm never Mr Johnny-on-the-Spot!

---

### Post by zika on 2015-09-11
> **QIII said:**
> I didn't get the blackout to login this time, but I did just get 


```
dpkg: cycle found while processing triggers:
 chain of packages whose triggers are or may be responsible:
  software-center -> software-center
 packages' pending triggers which are or may be unresolvable:
  software-center: /usr/share/app-install/desktop
dpkg: error processing package software-center (--configure):
 triggers looping, abandoned
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


--- Hmmm.  Already reported.  I'm never Mr Johnny-on-the-Spot!Just rerun apt, for example with```
sudo apt-get install -f
```and You're OK and done...

---

### Post by tokyobadger on 2015-09-11
I've also had the temporary black-out maybe 2 or 3 times (desktop, GTX680 nvidia 355.06). I've noticed it usually happens when apt is processing an update to systemd.

Re: the software-centre thing - had that last night and did as zika is suggesting - all fixed

---

### Post by cariboo on 2015-09-11
I had the software-center loop problem too, with todays updates on my desktop system:

[LIST]
[*]AMD FX8350
[*]16 GiB Ram
[*]Nvidia Geforce 210
[/LIST]

It didn't black out this time, I'll update my laptop a little later today, to see if it happens again.

---

### Post by slickymaster on 2015-09-11
See [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1494184](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1494184)

---

### Post by QIII on 2015-09-11
Saw that, slickymaster.  That's the one that had already been reported when I tried to report it.  I guess  I didn't update my post here, but I did mention it on Launchpad.

I never have any fun.  By the time I notice something it has either been mentioned here or reported already.  :(

---

### Post by slickymaster on 2015-09-11
> **QIII said:**
> Saw that, slickymaster.  That's the one that had already been reported when I tried to report it.  I guess  I didn't update, but I did mention it on Launchpad.

I never have any fun.  By the time I notice something it has either been mentioned here or reported already.  :(

:lolflag:
Don't give up QIII. Keep trying ;)

---

