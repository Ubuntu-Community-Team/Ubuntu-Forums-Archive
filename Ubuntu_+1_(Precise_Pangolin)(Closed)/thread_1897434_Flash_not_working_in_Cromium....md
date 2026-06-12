---
title: "Flash not working in Cromium..."
date: 2011-12-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2011-12-19
For several days now...
64-bit
Flash:```
You have version 11,2,202,96 installed
```
```
18.0.975.0 (Developer Build 114930 Linux) Built on Ubuntu 11.10, running on Ubuntu 12.04
```
Flash works nicely in all other browsers...

---

### Post by paul_in_london on 2011-12-19
> **zika said:**
> For several days now...
64-bit
Flash:```
You have version 11,2,202,96 installed
```
```
18.0.975.0 (Developer Build 114930 Linux) Built on Ubuntu 11.10, running on Ubuntu 12.04
```
Flash works nicely in all other browsers...

Can't test this right now, but will check later and let you know. I mainly use FF nightly (64 bit), but I'm sure Flash was working ok for me very recently in Chromium daily 64 bit. (There was a period when Flash wasn't working for me in Chromium 64 bit on one particular site, but it's been fine for a while now).

---

### Post by zika on 2011-12-19
> **paul_in_london said:**
> I mainly use FF nightly (64 bit)Ditto...

Update: It does not wirk with Flash 10, also, so it is not related to version of plugin... Of course, Google-Chrome works...

---

### Post by paul_in_london on 2011-12-19
> **zika said:**
> Ditto...

Update: It does not wirk with Flash 10, also, so it is not related to version of plugin... Of course, Google-Chrome works...

Ok, will check Chromium daily/Chrome 64 bit on my system later. 

Btw, one of the FF add-ons I use is [fxchrome](https://addons.mozilla.org/en-US/firefox/addon/fxchrome/) :lolflag:

---

### Post by zika on 2011-12-19
> **paul_in_london said:**
> Ok, will check Chromium daily/Chrome 64 bit on my system later. 

Btw, one of the FF add-ons I use is [fxchrome](https://addons.mozilla.org/en-US/firefox/addon/fxchrome/) :lolflag:Hey! That is solution!
[img]http://www.sherv.net/cm/emo/laughing/roflmao.gif[/img]

---

### Post by paul_in_london on 2011-12-19
> **zika said:**
> Hey! That is solution!
[img]http://www.sherv.net/cm/emo/laughing/roflmao.gif[/img]

I quite like it. :)

---

### Post by paul_in_london on 2011-12-19
Apparently I'm experiencing the same as you. Chrome 64 bit works ok, but chromium-daily thinks no plugins are installed.

```
paul@precise-64:~$ chromium-browser --version
Chromium 18.0.975.0 Built on Ubuntu 11.10, running on Ubuntu 12.04
```

Found this bug report:

[http://code.google.com/p/chromium/issues/detail?id=107955](http://code.google.com/p/chromium/issues/detail?id=107955)

EDIT:

```
paul@precise-64:~$ google-chrome --version
Google Chrome 17.0.963.12 dev
```

---

### Post by jerrylamos on 2011-12-20
Well I've tried chromium as comes with lubuntu and don't like it.  Very poor handling of my myriad bookmarks.

Easy solution, go to synaptic, "complete removal" of chromium automatically installs firefox which runs flash quite well thanks....

Jerry

---

### Post by zika on 2011-12-20
> **jerrylamos said:**
> Well I've tried chromium as comes with lubuntu and don't like it.  Very poor handling of my myriad bookmarks.

Easy solution, go to synaptic, "complete removal" of chromium automatically installs firefox which runs flash quite well thanks....

JerryThat is not a solution. I have (last time I've counted) 3 versions of FF installed...
Not to count Opera-next, Chromium, Google-Chrome...
We are here in testing sub-Forum, so I hope we are testing... ;)

---

### Post by zika on 2011-12-20
```
18.0.976.0 (Developer Build 115086 Linux) Built on Ubuntu 11.10, running on Ubuntu 12.04
```It came not long time ago. Flash works, again...

---

### Post by paul_in_london on 2011-12-21
> **zika said:**
> ```
18.0.976.0 (Developer Build 115086 Linux) Built on Ubuntu 11.10, running on Ubuntu 12.04
```

It came not long time. Flash works, again...

Didn't get around to trying it yesterday, but it's (still) ok with today's update:

```
paul@precise-64:~$ chromium-browser --version
Chromium 18.0.978.0 Built on Ubuntu 11.10, running on Ubuntu 12.04
paul@precise-64:~$
```

:)

---

