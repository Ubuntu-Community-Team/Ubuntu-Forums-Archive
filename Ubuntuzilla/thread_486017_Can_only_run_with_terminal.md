---
title: "Can only run with terminal"
date: 2007-06-27
forum: Ubuntuzilla
---

### Post by tolremeno on 2007-06-27
Sorry, I'm an extreme n00b here.

I can only get TB to run through the terminal. I installed through ubuntuzilla (at least I think I did - I've done so much with Linux in the last week that I think I'm going nuts) and am sharing the mail fine with the windows partition, but I can only start TB with the terminal.

If I try not starting with the terminal, I get the error that another instance of TB is running. 

Any help?

---

### Post by mig5 on 2007-06-27
I take it that you are talking about Mozilla ThunderBird?  Check if its running at startup.  Have you tried using the version in Synaptic, maybe you will get a different result with that.

---

### Post by tolremeno on 2007-06-27
Oops, sorry. Yeah, Thunderbird. I'm so used to the mozilla forums that I always abbreviate it.

But no, the synaptic version is 1.5. I don't want to run 1.5. I want 2.0.4. 

:-)

---

### Post by mig5 on 2007-06-27
When you run thunderbird without the terminal, from an icon i assume, do you know which command it is using?  Maybe it isn't using the command thunderbird on its own, instead maybe thunderbird %F or something?
To test it make a new icon on the desktop and just type thunderbird as the command (or whatever the command that you are using in the terminal is).

---

### Post by Rui Pais on 2007-06-27
> **tolremeno said:**
> Oops, sorry. Yeah, Thunderbird. I'm so used to the mozilla forums that I always abbreviate it.

But no, the synaptic version is 1.5. I don't want to run 1.5. I want 2.0.4. 

:-)

I use this repo. 
[http://ubuntu.iuculano.it/dists/feisty/](http://ubuntu.iuculano.it/dists/feisty/)

Works 100% and with minimum effort :)

---

### Post by tolremeno on 2007-06-27
> **mig5 said:**
> When you run thunderbird without the terminal, from an icon i assume, do you know which command it is using?  Maybe it isn't using the command thunderbird on its own, instead maybe thunderbird %F or something?
To test it make a new icon on the desktop and just type thunderbird as the command (or whatever the command that you are using in the terminal is).
Naw, it's just thunderbird. or mozilla-thunderbird. Both give me the error.

---

### Post by tolremeno on 2007-06-27
> **Rui Pais said:**
> I use this repo. 
[http://ubuntu.iuculano.it/dists/feisty/](http://ubuntu.iuculano.it/dists/feisty/)

Works 100% and with minimum effort :)
I think it's too late for that now. I'd have to uninstall what I've got, then reinstall through apt-get, then run that build.

---

### Post by nanotube on 2007-06-27
ok... well, post the output of the following commands:

quit thunderbird completely, and see if you get anything from:
```
ps ax |grep thunder
```

see what version your thunderbird shortcut points to:
```
thunderbird --version
```

see if your thunderbird shortcut links to /opt, as it would if it was installed with ubuntuzilla.
```
ls -al /usr/bin/thunderbird
```

ok, we'll go from there. :)

---

### Post by tolremeno on 2007-06-27
ok:

```
ps ax |grep thunder
``` I get:
```
ps ax |grep thunder
```
dunno what that means.

```
thunderbird --version
```
2.0.0.4, as it should.

see if your thunderbird shortcut links to /opt, as it would if it was installed with ubuntuzilla.
```
ls -al /usr/bin/thunderbird
```
I get:
```
lrwxrwxrwx 1 root root 28 2007-06-23 22:35 /usr/bin/thunderbird -> /opt/thunderbird/thunderbird
```

---

### Post by nanotube on 2007-06-27
well, ok, so the first one means, no other tbird instance is running...
second one, as it should be
as is the third one...

hmm... now... go to system -> preferences -> main menu -> internet -> thunderbird, right click, properties, and see what it says in there.

---

### Post by tolremeno on 2007-06-27
```
mozilla-thunderbird
```

---

### Post by nanotube on 2007-06-27
hm, so what is the exact message that it gives when you try to

and i suppose
```
ls -al /usr/bin/mozilla-thunderbird
```
also shows that it's linked to /opt/thunderbird/thunderbird ?

what is the exact message you get when you try to start it from the menu?

also, what's the output of
```
ps aux |grep 'thunder\|mozilla'
```

---

### Post by tolremeno on 2007-06-28
The exact message I get w/o the terminal is:
```
Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system.
```
Incidentally, that's not one but two comma splices, but I suppose not all programmers are grammarians. 

And yes to your second question: 
```
lrwxrwxrwx 1 root root 28 2007-06-23 22:35 /usr/bin/mozilla-thunderbird -> /opt/thunderbird/thunderbird
```

The output of your third message is:
```
jah      10902  0.0  0.0   2884   800 pts/0    S+   09:07   0:00 grep thunder\|mozilla

```

---

### Post by nanotube on 2007-06-28
hmm, ok, so your process list does not show any mozilla processes...

what about:
```
ls -al .thunderbird/*.default/.parentlock
```
does this show that the .parentlock file exists?

if so, delete it, and try running from menu again.

also try the "lock" file in the same location.

also, could you tell me what extensions you have installed for thunderbird?

---

### Post by tolremeno on 2007-06-28
Ok, I figured it out. Sorry for all the effort. Turns out it was a corrupted profile. For all of the years I've spent using mozilla, I should've thought of that sooner. Thanks!

---

### Post by nanotube on 2007-06-28
> **tolremeno said:**
> Ok, I figured it out. Sorry for all the effort. Turns out it was a corrupted profile. For all of the years I've spent using mozilla, I should've thought of that sooner. Thanks!

heh well, i'm glad it all worket out. :)
out of curiosity, i wonder, did you figure out what exactly was corrupted about it, or did you just start with a fresh one?

---

### Post by tolremeno on 2007-06-28
I just started with a fresh one. 

I think something was wrong with the prefs.js, but it was too much effort to try to fix it, so I just created a whole new profile.

---

### Post by nanotube on 2007-06-28
> **tolremeno said:**
> I just started with a fresh one. 

I think something was wrong with the prefs.js, but it was too much effort to try to fix it, so I just created a whole new profile.

i see :) well, whatever works :)

---

